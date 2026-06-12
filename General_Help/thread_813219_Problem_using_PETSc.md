---
title: "Problem using PETSc"
date: 2008-05-30
forum: General Help
---

### Post by paulreetz on 2008-05-30
I am trying to learn to use PETSc in order to solve engineering-type problems.  Currently I am trying to get a basic program to run and I seem to be having problems with the complier finding "petsc.h".  I have downloaded libmesh0.6.0, libpetsc2.3.3, and petsc2.3.3-doc from Synaptic.  I have been following [this]("http://www-unix.mcs.anl.gov/petsc/petsc-2/documentation/exercises/compiling/index.html") guide and am having problems.

First I run:

```
export PETSC_DIR=$PWD   (When i'm in /usr/share/doc/petsc2.3.3-doc)
export PETSC_ARCH="linux"
```

then

```
lamboot
```

lamboot seems to work fine and running it has allowed me to run basic mpi programs on my laptop before.  In this case however, I have the following problem:

My working folder is PETScTrials; it contains makefile.html and ex2.c (a basic program a got from the link above).

I run:

```
mpiexec -np 2 ex2.c
```

and get

```
Lamnodes Failed!
Check if you had booted lam before calling mpiexec else use -machinefile to pass host file to mpiexec
```

ok cool, I'll try that:

```
paul@paul-laptop:~/Documents/PETScTrials$ mpiexec -machinefile -np 2 ex2.c
mpirun: cannot start 2 on n0 (o): No such file or directory
mpirun failed with exit status 2
```

maybe sudo?

```
paul@paul-laptop:~/Documents/PETScTrials$ sudo mpiexec -machinefile -np 2 ex2.c
[sudo] password for paul: 
-----------------------------------------------------------------------------
It is a Very Bad Idea to run this program as root.

LAM was designed to be run by individual users; it was *not* designed
to be run as a root-level service where multiple users use the same
LAM daemons in a client-server fashion.

Especially with today's propensity for hackers to scan for root-owned
network daemons, it could be tragic to run this program as root.
While LAM is known to be quite stable, and LAM does not leave network
sockets open for random connections after the initial setup, several
factors should strike fear into system administrator's hearts if LAM
were to be constantly running for all users to utilize:

        1. LAM leaves a Unix domain socket open on each machine in the
           /tmp directory.  So if someone breaks into root on one
           machine, they effectively have root on all machines that
           are connected via LAM.  

        2. Indeed, there must have been a .rhosts (or some other trust
           mechanism) for root which must have allowed you to run LAM
           on remote nodes.  Depending on your local setup, this may
           not be safe.

        3. LAM has never been checked for buffer overflows and other
           malicious input types of errors.  We don't *think* that
           there are any buffer-overflow types of situations in LAM,
           we've never checked explicitly (hence, per Mr. Murphy,
           there are certainly some hiding somewhere).

        4. LAM programs are not audited or tracked in any way.  This
           could present a sneaky way to execute binaries without log
           trails (especially as root).

Hence, it's a Very Bad Idea to run LAM as root.  Please login as a
different user and run LAM again.
-----------------------------------------------------------------------------
-----------------------------------------------------------------------------
It seems that there is no lamd running on the host paul-laptop.

This indicates that the LAM/MPI runtime environment is not operating.
The LAM/MPI runtime environment is necessary for the "lamhalt" command.

Please run the "lamboot" command the start the LAM/MPI runtime
environment.  See the LAM/MPI documentation for how to invoke
"lamboot" across multiple machines.
-----------------------------------------------------------------------------

```

Also, if I just go to the directory and:

```
make ex2.c
```

I get:

```
mpirun: cannot start ex2.c on n0 (o): Permission denied
mpirun failed with exit status 13
```

So I don't really know what to do, it seems to want me to not run it as root but when I don't sudo it will not allow me permission!  Also, just for the record: 
```

paul@paul-laptop:~$ lamboot

LAM 7.1.2/MPI 2 C++/ROMIO - Indiana University
```
lamboot works.  When I try to use mpiexec a strange file shows up in my working folder but then disappears when the process ends.

Any and all help is appreciated, I really need to figure this out for a summer project.

---

