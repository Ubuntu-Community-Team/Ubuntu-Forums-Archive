---
title: "Installing perf on Ubuntu 14.04.2"
date: 2015-07-18
forum: General Help
---

### Post by Matt_John on 2015-07-18
I have installed Ubuntu Mate 14.04.2 and am attempting to use perf to profile a C++ application. I have installed linux-tools-common, linux-tools-generic-trusty, linux-tools-lts-trusty and linux-tools-generic. However, when I run the program using perf the output does not show function names or rather heavily obfuscated function names (similar to debugging without debugging symbols).

1) Program compiled using gcc 4.8.4 with -g flag
2) Program run using perf record progname

Output from perf report:

```
Samples: 39K of event 'cycles', Event count (approx.): 38860052841
  42.84%  lll  libc-2.19.so         [.] __mcount_internal
  19.32%  lll  libc-2.19.so         [.] _mcount
   7.87%  lll  lll                  [.] _Z13inner_productN9__gnu_cxx17__normal_iteratorIPd
   6.85%  lll  lll                  [.] _ZN9__gnu_cxx17__normal_iteratorIPdSt6vectorIdSaId
   5.01%  lll  lll                  [.] _ZNK9__gnu_cxx17__normal_iteratorIPdSt6vectorIdSaI
   4.13%  lll  lll                  [.] _ZN9__gnu_cxxneIPdSt6vectorIdSaIdEEEEbRKNS_17__nor
   3.15%  lll  lll                  [.] _ZNK9__gnu_cxx17__normal_iteratorIPdSt6vectorIdSaI
   1.40%  lll  lll                  [.] _ZNSt6vectorIdSaIdEEixEm
   1.27%  lll  lll                  [.] _Z10vector_subSt6vectorIdSaIdEES1_
   0.94%  lll  lll                  [.] _Z11scalar_multdSt6vectorIdSaIdEE
   0.80%  lll  lll                  [.] mcount@plt
   0.80%  lll  lll                  [.] _ZNKSt6vectorIdSaIdEE4sizeEv
   0.75%  lll  lll                  [.] _ZSt10__fill_n_aIPdmdEN9__gnu_cxx11__enable_ifIXsr
   0.36%  lll  lll                  [.] _ZNSt6vectorIS_IdSaIdEESaIS1_EEixEm
   0.31%  lll  lll                  [.] _ZNSt6vectorIdSaIdEE5beginEv
   0.25%  lll  libc-2.19.so         [.] _int_malloc
   0.23%  lll  libc-2.19.so         [.] _int_free
   0.19%  lll  lll                  [.] _ZN9__gnu_cxx17__normal_iteratorIPdSt6vectorIdSaId

```

When running perf test the following output is produced:

```
 1: vmlinux symtab matches kallsyms                        : FAILED!
 2: detect open syscall event                              : FAILED!
 3: detect open syscall event on all cpus                  : FAILED!
 4: read samples using the mmap interface                  : FAILED!
 5: parse events tests                                     : FAILED!
 6: x86 rdpmc test                                         : Ok
 7: Validate PERF_RECORD_* events & perf_sample fields     : FAILED!
 8: Test perf pmu format parsing                           : Ok
 9: Test dso data read                                     : Ok
10: Test dso data cache                                    : Ok
11: Test dso data reopen                                   : Ok
12: roundtrip evsel->name check                            : Ok
13: Check parsing of sched tracepoints fields              : FAILED!
14: Generate and check syscalls:sys_enter_open event fields: FAILED!
15: struct perf_event_attr setup                           : (omitted) Ok
16: Test matching and linking multiple hists               : Ok
17: Try 'use perf' in python, checking link problems       : FAILED!
18: Test breakpoint overflow signal handler                : Ok
19: Test breakpoint overflow sampling                      : Ok
20: Test number of exit event of a simple workload         : Ok
21: Test software clock events have valid period values    : Ok
22: Test converting perf time to TSC                       : Ok
23: Test object code reading                               : FAILED!
24: Test sample parsing                                    : Ok
25: Test using a dummy software event to keep tracking     : Ok
26: Test parsing with no sample_id_all bit set             : Ok
27: Test dwarf unwind                                      : FAILED!
28: Test filtering hist entries                            : Ok
29: Test mmap thread lookup                                : Ok
30: Test thread mg sharing                                 : Ok
31: Test output sorting of hist entries                    : Ok
32: Test cumulation of child hist entries                  : Ok

```

When running this on Arch Linux the correct functions names are displayed and two _mcount functions do not appear. I am completely baffled as to why this isn't working on Ubuntu, can anyone shed any light on this?

---

