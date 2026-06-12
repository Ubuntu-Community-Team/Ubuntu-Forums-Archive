---
title: "Man pages formatting messed up"
date: 2007-03-21
forum: General Help
---

### Post by auroraborealis on 2007-03-21
When I do `man fork', I get this output:
```
FORK(2)                                                                    Linux Programmer’s Manual                                                                   FORK(2)

NAME[m
       fork - create a child process

SYNOPSIS[m
       #include<sys/types.h>[m
       #include<unistd.h>[m

       pid_tfork(void);[m

DESCRIPTION[m
       fork)  creates a child process that differs from the parent process only in its PID and PPID, and in the fact that resource utilizations are set to 0.  File locks and
       pending signals are not inherited.

       Under Linux, fork) is implemented using copy-on-write pages, so the only penalty that it incurs is the time and memory required to duplicate the parent’s page tables,
       and to create a unique task structure for the child.

RETURNVALUE[m
       On  success,  the  PID  of the child process is returned in the parent’s thread of execution, and a 0 is returned in the child’s thread of execution.  On failure, a -1
       will be returned in the parent’s context, no child process will be created, and errno will be set appropriately.

ERRORS[m
       EAGAINfork) cannot allocate sufficient memory to copy the parent’s page tables and allocate a task structure for the child.

       EAGAINIt was not possible to create a new process because the caller’s RLIMIT_NPROCresource limit was encountered.  To exceed  this  limit,  the  process  must  have
              either the CAP_SYS_ADMINor the CAP_SYS_RESOURCEcapability.

       ENOMEMfork) failed to allocate the necessary kernel structures because memory is tight.

CONFORMINGTO[m
       SVr4, 4.3BSD, POSIX.1-2001.

EXAMPLE[m
       See pipe2) and wait2).

SEEALSO[m
       clone2), execve2), setrlimit2), unshare2), vfork2), wait2), capabilities7)

``` What's going on?

---

### Post by Mr. C. on 2007-03-21
Is this in Terminal , or a teminal emulator such as putty, securecrt, or ...?

You're seeing the output of bold or overstrike formatting, and your terminal type does not match the set terminal type.

```
echo $TERM
```

and see if this matches your terminal type.  If not, change either the emulator, or the TERM environment variable, as in:

```
TERM=vt100
TERM=xterm
TERM=linux
```

as appropriate.

MrC

---

### Post by auroraborealis on 2007-03-21
Awesome, that fixed it. Thanks.

---

