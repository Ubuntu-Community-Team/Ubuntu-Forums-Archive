---
title: "Empathy Core Dumps Ubuntu 14.04.01 64"
date: 2015-01-19
forum: General Help
---

### Post by DantePasquale on 2015-01-19
Hi, I never have had Empathy working since installing it. It always has core dumped. I've tried uninstalling/re-installing and it always core dumps. Any ideas on what's going on? I haven't been able to find any info on this problem.

Here's a bit of strace output:

```

futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
mmap(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0x7ffa9dfc8000
mprotect(0x7ffa9dfc8000, 4096, PROT_NONE) = 0
clone(child_stack=0x7ffa9e7c7cb0, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0x7ffa9e7c89d0, tls=0x7ffa9e7c8700, child_tidptr=0x7ffa9e7c89d0) = 5096
futex(0x1b843c0, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\6\0\0\0\0\0\0\0", 16)         = 8
futex(0x1b2b430, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1b2b430, FUTEX_WAKE_PRIVATE, 1) = 0
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\2\0\0\0\0\0\0\0", 16)         = 8
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\1\0\0\0\0\0\0\0", 16)         = 8
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\2\0\0\0\0\0\0\0", 16)         = 8
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
read(4, 0x7fffac0f7d10, 16)             = -1 EAGAIN (Resource temporarily unavailable)
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=11, events=POLLIN|POLLOUT}], 1, 4294967295) = 1 ([{fd=11, revents=POLLOUT}])
writev(11, [{"\206\3\4\0\n\0@\5\0\0\0\0\21\0\0\0005\30\4\0\223\0@\5\7\0@\5\f\0\f\0"..., 3116}, {NULL, 0}, {"", 0}], 3) = 3116
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\1\0\0\0\0\0\0\0", 16)         = 8
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\1\0\0\0\0\0\0\0", 16)         = 8
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
read(4, 0x7fffac0f7d10, 16)             = -1 EAGAIN (Resource temporarily unavailable)
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
brk(0x1ff6000)                          = 0x1ff6000
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
mmap(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0x7ffa9d7c7000
mprotect(0x7ffa9d7c7000, 4096, PROT_NONE) = 0
clone(child_stack=0x7ffa9dfc6cb0, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0x7ffa9dfc79d0, tls=0x7ffa9dfc7700, child_tidptr=0x7ffa9dfc79d0) = 5097
mmap(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0x7ffa9cfc6000
mprotect(0x7ffa9cfc6000, 4096, PROT_NONE) = 0
clone(child_stack=0x7ffa9d7c5cb0, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0x7ffa9d7c69d0, tls=0x7ffa9d7c6700, child_tidptr=0x7ffa9d7c69d0) = 5098
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
brk(0x2017000)                          = 0x2017000
brk(0x2039000)                          = 0x2039000
brk(0x205a000)                          = 0x205a000
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
mmap(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0x7ffa9c7c5000
mprotect(0x7ffa9c7c5000, 4096, PROT_NONE) = 0
clone(child_stack=0x7ffa9cfc4cb0, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0x7ffa9cfc59d0, tls=0x7ffa9cfc5700, child_tidptr=0x7ffa9cfc59d0) = 5099
futex(0x1b843c0, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1ffd380, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\4\0\0\0\0\0\0\0", 16)         = 8
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
read(4, 0x7fffac0f7d10, 16)             = -1 EAGAIN (Resource temporarily unavailable)
futex(0x1b2b430, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1b2b430, FUTEX_WAIT_PRIVATE, 2, NULL) = -1 EAGAIN (Resource temporarily unavailable)
futex(0x1b2b430, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
mmap(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0x7ffa877ff000
mprotect(0x7ffa877ff000, 4096, PROT_NONE) = 0
clone(child_stack=0x7ffa87ffecb0, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0x7ffa87fff9d0, tls=0x7ffa87fff700, child_tidptr=0x7ffa87fff9d0) = 5100
futex(0x1b843c0, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\4\0\0\0\0\0\0\0", 16)         = 8
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
read(4, 0x7fffac0f7d10, 16)             = -1 EAGAIN (Resource temporarily unavailable)
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x20187d0, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\1\0\0\0\0\0\0\0", 16)         = 8
mmap(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0x7ffa86ffe000
mprotect(0x7ffa86ffe000, 4096, PROT_NONE) = 0
clone(child_stack=0x7ffa877fdcb0, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0x7ffa877fe9d0, tls=0x7ffa877fe700, child_tidptr=0x7ffa877fe9d0) = 5101
futex(0x1b843c0, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
read(4, 0x7fffac0f7d10, 16)             = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=11, events=POLLIN|POLLOUT}], 1, 4294967295) = 1 ([{fd=11, revents=POLLOUT}])
writev(11, [{"\206\3\4\0\n\0@\5\0\0\0\0\25\0\0\0005\30\4\0\235\0@\5\7\0@\5\f\0\f\0"..., 3108}, {NULL, 0}, {"", 0}], 3) = 3108
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\1\0\0\0\0\0\0\0", 16)         = 8
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
read(4, 0x7fffac0f7d10, 16)             = -1 EAGAIN (Resource temporarily unavailable)
brk(0x207b000)                          = 0x207b000
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
futex(0x1b1ce20, FUTEX_WAIT_PRIVATE, 2, NULL) = -1 EAGAIN (Resource temporarily unavailable)
futex(0x1b1ce20, FUTEX_WAKE_PRIVATE, 1) = 0
brk(0x209c000)                          = 0x209c000
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
mmap(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0x7ffa867fd000
mprotect(0x7ffa867fd000, 4096, PROT_NONE) = 0
clone(child_stack=0x7ffa86ffccb0, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0x7ffa86ffd9d0, tls=0x7ffa86ffd700, child_tidptr=0x7ffa86ffd9d0) = 5102
mmap(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0x7ffa85ffc000
mprotect(0x7ffa85ffc000, 4096, PROT_NONE) = 0
clone(child_stack=0x7ffa867fbcb0, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0x7ffa867fc9d0, tls=0x7ffa867fc700, child_tidptr=0x7ffa867fc9d0) = 5103
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\2\0\0\0\0\0\0\0", 16)         = 8
futex(0x1b2b430, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\2\0\0\0\0\0\0\0", 16)         = 8
futex(0x1b2b430, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
brk(0x20bd000)                          = 0x20bd000
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
futex(0x1b2b430, FUTEX_WAIT_PRIVATE, 2, NULL) = -1 EAGAIN (Resource temporarily unavailable)
futex(0x1b2b430, FUTEX_WAKE_PRIVATE, 1) = 0
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\3\0\0\0\0\0\0\0", 16)         = 8
futex(0x1def754, FUTEX_WAKE_OP_PRIVATE, 1, 1, 0x1def750, {FUTEX_OP_SET, 0, FUTEX_OP_CMP_GT, 1}) = 1
futex(0x1dec560, FUTEX_WAKE_PRIVATE, 1) = 1
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\1\0\0\0\0\0\0\0", 16)         = 8
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
read(4, 0x7fffac0f7d10, 16)             = -1 EAGAIN (Resource temporarily unavailable)
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
poll([{fd=11, events=POLLIN|POLLOUT}], 1, 4294967295) = 1 ([{fd=11, revents=POLLOUT}])
writev(11, [{"\206\3\4\0\n\0@\5\0\0\0\0\27\0\0\0005\30\4\0\246\0@\5\7\0@\5\f\0\f\0"..., 3132}, {NULL, 0}, {"", 0}], 3) = 3132
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
brk(0x20de000)                          = 0x20de000
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
brk(0x20ff000)                          = 0x20ff000
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
recvmsg(11, 0x7fffac0f7b70, 0)          = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=11, events=POLLIN}, {fd=12, events=POLLIN}, {fd=8, events=POLLIN}, {fd=3, events=POLLIN}], 5, 0) = 0 (Timeout)
brk(0x2120000)                          = 0x2120000
brk(0x214b000)                          = 0x214b000
brk(0x2180000)                          = 0x2180000
brk(0x21a8000)                          = 0x21a8000
--- SIGSEGV {si_signo=SIGSEGV, si_code=SEGV_MAPERR, si_addr=0x10} ---
+++ killed by SIGSEGV (core dumped) +++
Segmentation fault (core dumped)




```

---

