# tsastat

This repo provides a solution for one of the exercises in the Chapter 5 of [Systems Performance, 2nd Edition by Brendan Gregg](), in specific:

> Develop a tool for Linux called tsastat(8) that prints columns for multiple thread state analysis states, with time spent in each. This can behave similarly to pidstat(1) and produce a rolling output.18


## Requirements

In order to run this script you need to have [bpftrace](https://github.com/bpftrace/bpftrace/tree/master). Note that, the script has been tested with `bpftrace` version `0.21.0`.  You can easily install `bpftrace` by following the instructions in the [official documentation](https://github.com/bpftrace/bpftrace/blob/master/INSTALL.md).

The script expects the `bpftrace` binary in the default path `/usr/bin/bpftrace`. 

## Usage

You can run the script by executing the following command:

```bash
user@ubuntu:~$ tsastat.bt
Attaching 7 probes...
Tracing scheduler events... Hit Ctrl-C to end.
^C
Thread state analysis:
COMM             PID       CPU   RUNQ    SLP    USL    SUS    LCK    DEA 
futex_contentio  32834       2    201    201      0      0    225      0
xdg-desktop-por  2401        7      0  58985      0      0      0      0
futex_contentio  33769       2    209    348      0      0    384      0
CacheThread_Blo  2727        0      0      0      0      0      0      0
futex_contentio  33207       3    352    402      0      0    503      0
futex_contentio  32026       2    138    160      0      0    166      0
kworker/u4:5     31410      19      0      0    110      3      0   3224
gmain            2410        1      0      0      0      0      0      0
ThreadPoolForeg  2744       32      0    746      0      0   7077      0

```