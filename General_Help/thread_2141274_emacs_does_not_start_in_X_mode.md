---
title: "emacs does not start in X mode"
date: 2013-05-02
forum: General Help
---

### Post by barna on 2013-05-02
Hi,
I have recently installed 13.04, and emacs24. While emacs starts in konsole mode with the -nw option, nothing happens if I start in X mode, without this option. Any ideas?
Thank you

---

### Post by barna on 2013-05-02
Checking it with strace, this is the end of the output, up to the point where it hangs:
```

close(9)                                = 0
eventfd2(0, O_NONBLOCK|O_CLOEXEC)       = 7
write(7, "\1\0\0\0\0\0\0\0", 8)         = 8
rt_sigprocmask(SIG_SETMASK, ~[RTMIN RT_1], [], 8) = 0
eventfd2(0, O_NONBLOCK|O_CLOEXEC)       = 8
write(8, "\1\0\0\0\0\0\0\0", 8)         = 8
mmap2(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0xb3827000
mprotect(0xb3827000, 4096, PROT_NONE)   = 0
clone(child_stack=0xb4027264, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0xb4027ba8, {entry_number:6, base_addr:0xb4027b40, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb4027ba8) = 15965
futex(0x85dc270, FUTEX_WAKE_PRIVATE, 1) = 1
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGCHLD, {0xb6defb80, [], SA_RESTART|SA_NOCLDSTOP}, NULL, 8) = 0
waitpid(15964, 0x85db190, WNOHANG)      = -1 ECHILD (No child processes)
poll([{fd=7, events=POLLIN}], 1, -1)    = 1 ([{fd=7, revents=POLLIN}])
poll([{fd=7, events=POLLIN}], 1, -1)    = 1 ([{fd=7, revents=POLLIN}])
read(7, "\1\0\0\0\0\0\0\0", 16)         = 8
poll([{fd=7, events=POLLIN}], 1, -1

```

---

### Post by barna on 2013-05-03
Removing ~/.config/gtk-2.0 ~/.config/gtk-3.0 and ~/.config/oxygen-gtk solved the problem (they remained from a previous ubuntu version, probably)

---

