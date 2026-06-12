---
title: "a start job is running for snappy daemon"
date: 2018-07-04
forum: General Help
---

### Post by jmncrr on 2018-07-04
Snappy daemon fails to start during boot, and cant use new kernel after update. LTS 18.04

 I have to use and older one to boot up. I'm not sure what to do.

 Any help is appreciated.
Thanks

---

### Post by pihpilp on 2018-07-04
Hello everyone, I got (probably) a similar problem after an update a few days ago (also on LTS 18.04). I just want to share a few more infos with you such that you might be able to help us more easily.

So my problem is that the boot takes unusually long (5 to 10 minutes). After pressing Ctrl+Alt+F2 I can see the following messages:

"A start job is running for Wait until snapd is fully seeded."
"A start job is running for Hold until boot process finishes up."
"A start process is running for snappy demon."

So these messages appear there and somehow the computer waits a long time to run or boot something and at some point it says "See 'systemctl status snapd.service' for details".

I am not a computer expert and I have no idea what this means. Would be great if you could give me some insights into what snappy demon actually is and whether I can switch it off or somehow solve the problem in another way...

Thanks a lot!

---

### Post by wavesdontdie on 2018-07-04
Hi there, I think I also just experienced the same issue. The process failed 3 times but on the 4th try (or so) allowed me to get into my desktop.

---

### Post by bearyme on 2018-07-04
I got the same issue, I have upgrade to 18.04 about 2 week, but this issue appear only 3 days ago.

---

### Post by cromptonm on 2018-07-05
I have the same problem. Long wait for boot. Ctl-Alt-F2 shows alternatively "Failed to start snappy daemon..." and "Starting wait until snapd is fully seeded". This repeats for about 15 minutes, then system boots normally.

Anyone found a solution yet?

---

### Post by PaulW2U on 2018-07-05
> **cromptonm said:**
> I have the same problem. Long wait for boot. Ctl-Alt-F2 shows alternatively "Failed to start snappy daemon..." and "Starting wait until snapd is fully seeded". This repeats for about 15 minutes, then system boots normally.
Could be this bug: [Snapd gets stuck when starting Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1779948"). I'm not seeing it myself though.

---

### Post by cromptonm on 2018-07-06
> **PaulW2U said:**
> Could be this bug: [Snapd gets stuck when starting Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1779948"). I'm not seeing it myself though.

Yes, sounds like the same bug.

---

### Post by jmncrr on 2018-07-09
Any fix for this problem yet?

 Just use previous kernel for now i guess.

 What are the risks of not using the latest kernel?

---

### Post by Gravidar on 2018-07-09
Same happening here. 
Does this affect just 18.04?  I'll go back to 16.04 if so.  
Shame, I was liking 18.

---

### Post by mIk3_08 on 2018-07-09
> **cromptonm said:**
> I have the same problem. Long wait for boot. Ctl-Alt-F2 shows alternatively "Failed to start snappy daemon..." and "Starting wait until snapd is fully seeded". This repeats for about 15 minutes, then system boots normally.

Anyone found a solution yet?


I don't know if it will work to you but it work for me... I also have experience in a long boot process. I don't know if this is advisable and I don't know what exactly means but it really work.

I got this solution from this link;
[https://askubuntu.com/questions/1030867/ubuntu-18-04-how-to-diagnose-fix-very-slow-boot](https://askubuntu.com/questions/1030867/ubuntu-18-04-how-to-diagnose-fix-very-slow-boot)


Edit the file /etc/default/grub file so that the string noresume is included in the 
GRUB_CMDLINE_LINUX_DEFAULT line, for example:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noresume"
Run this command to update GRUB:


sudo update-grub
Reboot the computer

Then, I open the "Startup Applications" and I found out that there is a kerneloop in the start up. What I did is just unchecked it.
I don't exactly know why there is a loop of kernel in my start-up. 
Any advice what does it mean?

[ATTACH=CONFIG]280337[/ATTACH]

---

### Post by cromptonm on 2018-07-11
@mike082112
I believe the issue you referenced was a different problem. That relates to waiting for a network service. The problem in my case, and the OP, is about snapd.

---

### Post by Gravidar on 2018-07-11
I tried that idea, it's good to know about it but sadly has made no difference.

---

### Post by mIk3_08 on 2018-07-11
> **cromptonm said:**
> @mike082112
I believe the issue you referenced was a different problem. That relates to waiting for a network service. The problem in my case, and the OP, is about snapd.


There are snapd on this link;
[https://launchpad.net/ubuntu/bionic/+source/snapd](https://launchpad.net/ubuntu/bionic/+source/snapd)

And here how to remove if you have broken installations.
[https://ubuntuforums.org/showthread.php?t=2328152](https://ubuntuforums.org/showthread.php?t=2328152)

Hope it can help.

---

### Post by nate.j586 on 2018-07-12
Probably unrelated, but I was just having this issue after performing an update. I run Ubuntu 18.04 on virtualbox, and I figured out that if I have the virtual hard disk set to solid state drive in the options, the os won't boot, saying a start process is running for snappy daemon. If I uncheck that box, it boots normally.

---

### Post by mIk3_08 on 2018-07-13
> **jmncrr said:**
> Any fix for this problem yet?

 Just use previous kernel for now i guess.

 What are the risks of not using the latest kernel?


It most likely won’t break your system if you don’t update your kernel for your own risk reason, but sooner or later you’ll find programs and other packages that require a certain version of the kernel. It’s best to have the latest one so you know you won’t come across that issue.

---

### Post by pihpilp on 2018-07-19
So I had the same problem with snappy demon and very long boot times. After waiting for three weeks, updating and upgrading my system several times, the problem was still there. So I tried to get rid of snappy demon with

sudo apt purge snapd ubuntu-core-launcher squashfs-tools

Unfortunately, the general problem is still there (long booting time because the system waits for something). The messages I get now are 

[FAILED] Failed to start Network Manager Wait Online.
See 'systemctl status Network Manager-wait-online.service' for details
A start job is running for Hold until boot process finishes up

etc. Any ideas? It is quite annoying, especially my Laptop is quite new and I installed Ubuntu 18.04 from scratch...

---

### Post by Gravidar on 2018-07-22
I too removed snapd and the problem moved down the chain but didn't take as long to start as snapd, however...
The fix as per the bug report above has been released.  

I have updated the kernel to 4.15.0-29-generic using Software Updater and my VM starts very quickly with no "pauses"
There's an update too for snapd but as I have uninstalled that and have no expectation I'll be using it so will not be reinstalling it.

---

### Post by pihpilp on 2018-07-30
Hello everybody,

just wanted to mention that I got rid of the  problem now. Some upgrade during the last days must have done the job.  Absolutely no idea which one though.

All the best!

---

