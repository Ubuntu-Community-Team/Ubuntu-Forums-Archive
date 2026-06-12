---
title: "Booting on kernel 2.6.19"
date: 2006-12-01
forum: General Help
---

### Post by Kikoolol on 2006-12-01
Hi guys !

I have compiled the last linux kernel (2.6.19), and everything went fine, but when I wanted to boot, init didn't start !

However, the kernel boots properly (nothing particular in dmesg, almost the same I had with my previous 2.6.18 kernel), but then when it's time to launch init, nothing happens. :confused:  So I have to hit ctrl+alt+suppr to reboot the computer ... 

Any idea people ? Thanks in advance ! :) 

Kikoolol

---

### Post by Kikoolol on 2006-12-01
In fact the problem is that the computer hangs on : 
"Waiting for root file system ..."

I compiled my kernel using make-kpkg, like I did for the 2.6.18 version on Dapper (I'm on Edgy now). Maybe something has changed in make-kpkg command ?

Thks,

Kikoolol

---

### Post by 64mgb on 2006-12-01
Yea, I had the same problem...well, I don't know if it's exactly the same problem, but after I recompiled with 2.6.19 I couldn't boot.  At least I did it on a test box...

Rich

---

### Post by Kikoolol on 2006-12-01
64mgb,

You can try to edit the boot command in grub loader to boot without the "splash" and "quiet" options, so that you can see if the boot sequence stops when the system tries to mount the root filesystem.

I think this problem might be related to the switch init -> upstart during the upgrade from Dapper to Edgy (now the partitions are no longer identified by /dev/sd* etc, but by the UUID) ... :-k 

Hope somebody will find a solution :) 

Kikoolol

---

### Post by nfm on 2006-12-01
Hello!

I'm having the same issue. I run Edgy and have compiled new kernel as usual, but v2.6.19 hangs on mounting root file system, after that I get a message saying "/dev/sda8 does not exist". 

I wonder if v2.6.18.4 would work, since both kernels are recent they shouldn't differ much from each other.

I will try v2.6.18.4 in few minutes.

---

### Post by Kikoolol on 2006-12-02
Nice to see I'm not the only one experiencing this problem :-D 

nfm, if you're unsuccessful then it probably means that the replacement of /dev/sd* by the UUID in edgy is in cause, because my current kernel is a 2.6.18 that I have compiled on dapper, and it's the one I'm using right now, on edgy.

If we can manage to compile the last kernel from kernel.org, maybe it will work if we do it using the source contained in linux-source-2.6.19 package from the ubuntu repositories (including ubuntu patches), because I saw some feedback from people who tried the 2.6.19 kernel on feisty, and it went fine for them.

Kikoolol

---

### Post by 64mgb on 2006-12-02
I should have given more info in my post.  When it restarts, it goes to the splash screen and the progress bar shows just one small sliver of progress.  It sits there for a couple of minutes then goes to an ash shell and says

/bin/sh: can't access tty: job control turned off

Any ideas?  I was running 2.6.18.2 on this box.

Rich

---

### Post by nfm on 2006-12-02
Hi Kikoolol,

So you're saying that If I went ahead and compiled kernel v2.6.19 on dapper and installed it on edgy it would do the trick?
Right now I'm using kernel v2.6.18.4 that I compiled on edgy and installed it. It works fine. I always use sources from kernel.org
Once I will find v2.6.19 from Ubuntu repository, I will try it.

nfm

---

### Post by geoff123 on 2006-12-02
Same problems here.  Seemed to compile fine, but stopped half way through the boot up. Had to pull the cord. 
2.6.18.2 is what I've been running for a couple weeks and it has worked great.  It really does run alot faster than the ubuntu default kernel as a desktop with these changes:
Enable Processor type and features > 
	Pentium4 (assuming you have this)
	Disable Generic x86 support
	Enable SMT
	Premptible Kernel (Low-Latency Desktop)
	Timer frequency to 1000 Hz.
Disable Kernel Hacking > Kernel debugging

---

### Post by Kikoolol on 2006-12-02
Hi guys, and thks for your feedback :) 

nfm, if you have successfully compiled & booted a 2.6.18.x version on edgy, then it's not a whole "kernel from kernel.org & edgy" issue (which was my first guess, so people running dapper should have the same issue) ... :-k

What the hell with this new kernel ?!! :mrgreen: 

Kikoolol

---

### Post by mrvanes on 2006-12-03
I had exactly the same problems after upgrading to 2.6.19 and they were solved by checking Serial ATA support and the appropriate SATA controller module for the 2.6.19 kernel. There seems to be some module layout shift from 2.6.17 to 19 that caused these modules to be disabled, hence rendering the SATA disks to ordinary IDE disks that do not result in sda/b/c/d disks but hda/b/c/d and therefor can not be mounted with a kernel commandline that tells to mount root at /dev/sda1

So, in short: I have SATA disk controller, that breaks upgrading Edgy to 2.6.19, which is fixed by selecting SATA support + module(s) in 2.6.19.

Hope this helps,
Martin

---

### Post by Kikoolol on 2006-12-04
Thanks a lot !

I will try it later today, and mark this topic as resolved if I'm successful !

Kikoolol

---

### Post by Logima on 2006-12-04
> **mrvanes said:**
> So, in short: I have SATA disk controller, that breaks upgrading Edgy to 2.6.19, which is fixed by selecting SATA support + module(s) in 2.6.19.

Hope this helps,
Martin

I had the same problems too and this worked! Thanks! :D

---

### Post by nfm on 2006-12-04
Thank you Martin, works for me now also :p

---

### Post by Kikoolol on 2006-12-05
Worked for me too ! Thks a lot guys ! :) 

Kikoolol

---

### Post by marlijs on 2006-12-05
Could some one tell me please, where do I exactly need to check to enable SATA support when making menuconfig

---

### Post by Kikoolol on 2006-12-05
Hi Marjis !

You need to go in section "Device Drivers" then "Serial ATA ... drivers", enable "ATA Device Support", and then choose the things to compile according to you hardware. If you don't know what to choose, then you can do one of the following thing :
- take a look at your old .config to find what was compiled before
- do a : "dmesg | grep -i ata" to grab some info
- compile all the "SATA support" options as modules, so you are sure that yours is included :p 

Hope this helps !

Kikoolol

---

### Post by marlijs on 2006-12-05
Thank you, I am in a linux world for a while, and finally decided to compile my first own kernel :D

---

