---
title: "Pause a program in terminal"
date: 2024-05-25
forum: General Help
---

### Post by usoviet on 2024-05-25
I want to pause a program in terminal, not the way of hitting ctrl+z or ctrl+s, that only can make the program run in backgroud or stop output (I can see a program using internet). I want it be like ctrl+p to VMs in VBox, everything inside the window is frozen, after hitting ctrl+p, everything start running.

---

### Post by currentshaft on 2024-05-25
You can use docker pause, which uses freezer cgroups

[https://www.kernel.org/doc/Documentation/cgroup-v1/freezer-subsystem.txt](https://www.kernel.org/doc/Documentation/cgroup-v1/freezer-subsystem.txt)

---

### Post by TheFu on 2024-05-25
Most hypervisors have a "suspend" option on the "Start/Shutdown" menu.

In virsh, the manpage says:
```
VIRSH(1)                           Virtualization Support                           VIRSH(1)

NAME
       virsh - management user interface

SYNOPSIS
       virsh [OPTION]... [COMMAND_STRING]

       virsh [OPTION]... COMMAND [ARG]...

DESCRIPTION
       The virsh program is the main interface for managing virsh guest domains. The program
       can be used to create, pause, and shutdown domains. It can also be used to list  cur&#8208;
       rent domains. Libvirt is a C toolkit to interact with the virtualization capabilities
       of recent versions of Linux (and other OSes). It is free software available under the
       GNU Lesser General Public License. Virtualization of the Linux Operating System means
       the ability to run multiple instances of Operating Systems concurrently on  a  single
       hardware system where the basic resources are driven by a Linux instance. The library
       aims at providing a long term stable C API.  It currently supports  Xen,  QEMU,  KVM,
       LXC, OpenVZ, VirtualBox and VMware ESX.

       The basic structure of most virsh usage is:

          virsh [OPTION]... <command> <domain> [ARG]...
...
    suspend
       Syntax:

          suspend domain

       Suspend a running domain. It is kept in memory but won't be scheduled anymore.
...
  nodesuspend
       Syntax:

          nodesuspend [target] [duration]

       Puts  the  node (host machine) into a system-wide sleep state and schedule the node's
       Real-Time-Clock interrupt to resume the node after the time duration specified by du&#8208;
       ration is out.  target specifies the state to which the host will be suspended to, it
       can be "mem" (suspend to RAM), "disk" (suspend to disk), or "hybrid" (suspend to both
       RAM  and  disk).   duration specifies the time duration in seconds for which the host
       has to be suspended, it should be at least 60 seconds.
...
       • paused

         The domain has been paused, usually occurring  through  the  administrator  running
         virsh  suspend.  When in a paused state the domain will still consume allocated re&#8208;
         sources like memory, but will not be eligible for scheduling by the hypervisor.
...
       • pmsuspended

         The  domain  has  been  suspended  by  guest power management, e.g. entered into s3
         state.

       Normally only active domains are listed. To list inactive domains specify  --inactive
       or --all to list both active and inactive domains.
```

So, from any terminal, you can use 
```
$ virsh suspend regulus
```
to suspend the regulus virtual machine.  virsh is part of the libvirt tools, so any of the hypervisors supported would work.

For LXC containers, check the manpages for how to suspend them.  I'd guess "stop" would be the command option.

To my knowledge, there's no way to have a tree of processes stopped, like you seem to want. They need to be grouped, somehow.  That would be inside a VM or a Container.

---

