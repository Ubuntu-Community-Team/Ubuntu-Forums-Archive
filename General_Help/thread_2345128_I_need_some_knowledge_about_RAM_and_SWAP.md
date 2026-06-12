---
title: "I need some knowledge about RAM and SWAP"
date: 2016-11-30
forum: General Help
---

### Post by aviator1 on 2016-11-30
Hello Friends:

I'm a long time computer user, and have a very good understanding of how to use various programs. I have been having a very difficult time with LibrOffice Calc 5 and have a post here about CPU and RAM usage.

I have received some help, but I'm thinking I need more knowledge of how RAM and SWAP really work. Maybe I don't have a setting or switch set correctly.

As I understand things, RAM is the memory, which is used to do "current" actions. The more RAM one has, the faster the actions can be completed.

In turn, if one does not have enough RAM, then a SWAP is done on a hard drive to essentially give more RAM.

Are these concepts correct?

If so, why does my computer with 16 GB RAM only use about 2 GB for anything I do? It is virtually a flat line on system monitor at 2 GB no matter what I am doing.

I have an 8 core CPU and on some actions, 1 of the CPU's will max out while the RAM stays at 2 GB. Why wouldn't the RAM be used extensively prior to maxing out a CPU core?

I have no SWAP, as I was advised against that due to using an SSD.

However, with 16 GB RAM, why isn't that being used before considering a SWAP anyway?

I really appreciate any help or advice anyone can give. Should I post in a different forum?

Regards.

---

### Post by papibe on 2016-11-30
Hi aviator1.
> **aviator1 said:**
> Are these concepts correct?
Yes. The other use for swap is hibernation.

Could you open a terminal, run these commands, and post back the results? (you can copy/paste the text)
```
free -m

swap

lsb_release -a

uname -a
```
Regards.

---

### Post by kpatz on 2016-11-30
CPU usage and RAM usage are two different things.  A process could be CPU heavy and max out a CPU core but use very little RAM, and if it's not multi threaded it'll use only one core.  Another process could use lots of RAM and use very little CPU.

When you say it's only using 2 GB RAM, is that in top, or htop?  Or something else?  Also are you running a 64-bit version of Ubuntu?  32-bit versions can only access 3-4 GB of RAM.

Even if you aren't "using" all your RAM, the OS still uses it for disk cache, so it's not being wasted.

---

### Post by aviator1 on 2016-11-30
> **kpatz said:**
> CPU usage and RAM usage are two different things.  A process could be CPU heavy and max out a CPU core but use very little RAM, and if it's not multi threaded it'll use only one core.  Another process could use lots of RAM and use very little CPU.

When you say it's only using 2 GB RAM, is that in top, or htop?  Or something else?  Also are you running a 64-bit version of Ubuntu?  32-bit versions can only access 3-4 GB of RAM.

Even if you aren't "using" all your RAM, the OS still uses it for disk cache, so it's not being wasted.

I am running 64-bit. How can I check top and htop? Type in terminal and copy the results here? Do I need to do it when one of the cores is locked?

---

### Post by aviator1 on 2016-11-30
Here is the info:
```
   dave@dave-desktop:~$ free -m
               total        used        free      shared  buff/cache   available
 Mem:          15949        1842       12693          37        1413       13726
 Swap:         16283           0       16283
 
 
 dave@dave-desktop:~$ swap
 No command 'swap' found, did you mean:
  Command 'smap' from package 'slurm-client' (universe)
  Command 'snap' from package 'snapd' (main)
  Command 'sswap' from package 'secure-delete' (universe)
  Command 'szap' from package 'dvb-apps' (universe)
  Command 'stap' from package 'systemtap' (universe)
  Command 'swarp' from package 'suckless-tools' (universe)
  Command 'swab' from package 'odin' (universe)
 swap: command not found
 
 
 dave@dave-desktop:~$ lsb_release -a
 LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
 Distributor ID:	Ubuntu
 Description:	Ubuntu 16.04.1 LTS
 Release:	16.04
 Codename:	xenial
 
 
 dave@dave-desktop:~$ uname -a
 Linux dave-desktop 4.4.0-51-generic #72-Ubuntu SMP Thu Nov 24 18:29:54 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux 
```

---

