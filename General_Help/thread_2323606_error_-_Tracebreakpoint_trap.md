---
title: "error - Trace/breakpoint trap"
date: 2016-05-06
forum: General Help
---

### Post by marchello_lippi2 on 2016-05-06
Hi all, 

Got this error when trying to start syncthing manually: 

user1@host:/usr/local/bin$ syncthing
Trace/breakpoint trap

Tried to start it manually because it did not start automatically. 


$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty




syncthing version should be v0.12.22, Linux (32 bit), because it was installed from the same repository on my other pc and it does work on that "other pc" for now.

Tried to reboot. 
Tried to remove and install again. 
No luck. 


What to do to solve it?

---

### Post by marchello_lippi2 on 2016-05-09
[FONT=Helvetica]I have seen workaround tips.[/FONT]
[FONT=Helvetica]Tried:[/FONT]
[FONT=Helvetica]$ sudo echo 1 /proc/sys/kernel/modify_ldt 1 /proc/sys/kernel/modify_ldt[/FONT]
[FONT=Helvetica]But without any luck:[/FONT]
[FONT=Helvetica]$ sudo ls /proc/sys/kernel/modify_ldt ls: cannot access /proc/sys/kernel/modify_ldt: No such file or directory[/FONT]
[FONT=Helvetica]Tried also:[/FONT]
[FONT=Helvetica]$ sudo echo 1 /proc/sys/ksplice_modify_ldt 1 /proc/sys/ksplice_modify_ldt[/FONT]
[FONT=Helvetica]the same result:[/FONT]
[FONT=Helvetica]$ sudo ls /proc/sys/ksplice_modify_ldt ls: cannot access /proc/sys/ksplice_modify_ldt: No such file or directory[/FONT]
[FONT=Helvetica]Tried:[/FONT]
[FONT=Helvetica]$ sudo echo 1 > /proc/sys/kernel/modify_ldt -bash: /proc/sys/kernel/modify_ldt: No such file or directory[/FONT]
[FONT=Helvetica]Tried:[/FONT]
[FONT=Helvetica]$ sudo echo 1 > /proc/sys/ksplice_modify_ldt -bash: /proc/sys/ksplice_modify_ldt: No such file or directory[/FONT]
[FONT=Helvetica]Still the same error:[/FONT]
[FONT=Helvetica]$ syncthing Trace/breakpoint trap[/FONT]
[FONT=Helvetica]
What else I can do to solve it?[/FONT]

---

### Post by treefiddy05 on 2016-05-09
I've actually been having the same issue over the past few days and have not yet come to a solution. Was syncthing previously running on that machine? Mine *was* running for almost a year :(

---

### Post by marchello_lippi2 on 2016-05-10
[**[COLOR=#000000]treefiddy05[/COLOR]**]("http://ubuntuforums.org/member.php?u=1420937"),
the same for me, was running successfully many weeks and suddenly after some update became broken. 
Any solution someone?

---

### Post by treefiddy05 on 2016-05-10
I did see that they think the problem is related to their compiler (Go).
[https://forum.syncthing.net/t/syncthing-exits-with-trace-breakpoint-trap-due-to-missing-modify-ldt-system-call-in-386-systems/6936](https://forum.syncthing.net/t/syncthing-exits-with-trace-breakpoint-trap-due-to-missing-modify-ldt-system-call-in-386-systems/6936)

There was a related bug report that has been marked as solved on the Golang website just a few days ago. Maybe all we need to do is wait for them to rebuild syncthing with an updated compiler. But my knowledge in this area is very limited, so maybe it won't help. I find it hard to believe that this would be affecting so few people (two?).

---

### Post by marchello_lippi2 on 2016-05-11
[treefiddy05]("http://ubuntuforums.org/member.php?u=1420937"),
yes, I've seen link you mentioned.

> 
Solved! It turns out for some odd reason ksplice changs the name of the file: All this time all I needed to do was:
  echo 1 /proc/sys/ksplice_modify_ldt

  The ksplice is added to the filename in my instance. Sorry for all  the trouble. Still a bug in go, which uses a syscall it really should  not.




Looks like solution found. What does this mean for regular users? 

> echo 1 /proc/sys/ksplice_modify_ldt

it did not help me, with or without sudo.

Got another reply on [https://forum.syncthing.net/t/error-trace-breakpoint-trap/7316/3](https://forum.syncthing.net/t/error-trace-breakpoint-trap/7316/3)

> I have been having the same issues over the last few days as well. None of the above workarounds work. I'm running on Debian 7.10 (wheezy) 32 bit.
$ strace syncthing
execve("/usr/bin/syncthing", ["syncthing"], [/* 14 vars */]) = 0 modify_ldt(1, {entry_number:7, base_addr:0x8b2edfc, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, 16) = -1 EPERM (Operation not permitted) --- SIGSEGV (Segmentation fault) @ 0 (0) --- +++ killed by SIGSEGV +++ Segmentation fault

Ok, tried to do it, installed strace using apt-get and : 

> $ strace syncthing
execve("/usr/bin/syncthing", ["syncthing"], [/* 26 vars */]) = 0
modify_ldt(1, {entry_number:7, base_addr:0x8b2edfc, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, 16) = -1 EPERM (Operation not permitted)
--- SIGTRAP {si_signo=SIGTRAP, si_code=SI_KERNEL} ---
+++ killed by SIGTRAP +++

Trace/breakpoint trap

Did not help me much. 
Would someone please translate it into human language? Thanks ahead. 

Got another reply on [https://forum.syncthing.net/t/error-trace-breakpoint-trap/7316/6](https://forum.syncthing.net/t/error-trace-breakpoint-trap/7316/6)

> The operation that Syncthing needs to do is not permitted or not supported by your kernel. Upgrade, or talk to your hosting provider if they are using some weird VPS variant.


That's what I've got on machine where syncthing doesn't work (VPS):
$ uname -r 2.6.32-042stab113.11
This is what I've got on machine where syncthing does work (office PC):
$ uname -r 3.13.0-85-generic
This is just FYI. Will speak to VPS support team.

ok, my vps rejects upgrading to newer kernel version, it is OpenVZ and I can't do it by myself. 

Got another reply on [https://forum.syncthing.net/t/error-trace-breakpoint-trap/7316/7](https://forum.syncthing.net/t/error-trace-breakpoint-trap/7316/7) 
It is only compiler issue. 
People suggest me to compile syncthing it by myself.

Any howto please?

---

### Post by treefiddy05 on 2016-05-15
[FONT=verdana][SIZE=2]It looks like this may affect many OpenVZ VPS users who will be running  kernel version 2.6.32. As far as I can tell, OpenVZ kernel 3.10 has not  officially been released yet.

I have tried installing Go 1.3.3 and compiling the basic "hello world" program, but I get that damn Trace/breakpoint trap error. If you are going to attempt compiling, I suggest starting somewhere earlier than 1.3.3. Also, when installing Go, you need to restart your ssh session for the PATH variable to take effect, otherwise it will appear Go is not installed (command not found).

I will have another Go at this later today. :)

Update: I've also tried Go 1.3 and the latest version of Go but no luck (breakpoint trap). I also tried gccgo but I'm afraid it's too much for me. Since this is not a new issue to Go or syncthing, it must be related to my VPS provider and a recent server migration.

Update 2: I also found this [https://github.com/v2ray/v2ray-core/issues/137](https://github.com/v2ray/v2ray-core/issues/137)
It's in Chinese, but I think the essence is that the "echo 1 /proc/sys/kernel/modify_ldt" etc commands don't work because they are modifying the kernel, which is shared on the OpenVZ platform. I can see why an OpenVZ client would not be able to make changes to the host kernel.
Apparently reinstalling the OS fixed the problem for him. Considering that I can't even run a basic "hello world" program, I'm going to assume that it will fix my problem also. I'm not sure if I will have the time in the next week to set up my server again.

[/SIZE][/FONT]

---

### Post by treefiddy05 on 2016-05-16
**I've found a workaround**. I changed to a 64 bit OS and now Syncthing will run without the trace/breakpoint error (I'm assuming it will run, but nothing is else is set up yet). It's not great but it's something.

Simply reinstalling the OS did not work for me unfortunately (same error).
Hopefully this will work for you too if you are set on keeping syncthing/32-bit applications compiled in Go.

---

### Post by marchello_lippi2 on 2016-05-24
Ok, I would stick to rsync for getting files from my vps (while all other my computers will continue to use syncthing). Unfortunately, changing to 64 bit OS is not the way to go in my case. Syncthing is only one of many services I use at this vps and rsync is my workaround.

---

