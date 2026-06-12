---
title: "Ubuntu and Lubuntu 16.04.1 freezing"
date: 2016-08-18
forum: General Help
---

### Post by vitor.lopes on 2016-08-18
Hello there, I work in a lab with 13 PCs, 12 of them running Lubuntu and the last one running Ubuntu. Recently I dicided to update these systems so I did update 2 of them (the Ubuntu and one of the Lubuntu, I've used apt-get update and apt-get dist-upgrade). Since then the Lubuntu and the Ubuntu that I have updated are freezing randomly (the PC freezes and I have to restart it using the power button of the case), I can't find any particular reason that would lead these PCs to freeze, they have 4GBs of RAM (Lubuntu) and 8GBs of RAM (Ubuntu) and run all the time with more than 2,5GB free (the Lubuntu run most of times with over than 80% of CPU utilization, though). These two PCs with problems run Ubuntu 16.04.1 and Kernel 4.4.0-34, the others that run without any problem are using Ubuntu 16.04 and Kernel 4.4.0-24

I would really appreciate if you could help me understand and fix what's causing this problem, if I missed or if you need any extra information just tell me and I'll post it.

---

### Post by grahammechanical on 2016-08-18
Are you getting error reports of system problems? When you run apt update & apt upgrade do you get a warning that there are broken packages?

The dist-upgrade command will avoid package conflicts by removing packages if necessary. Using dist-upgrade rarely causes problems but it does have the possibility to cause problems. The dist-upgrade command will bring in packages that are held back when we use the upgrade command. But they are held back for a reason.

Regards

---

### Post by vitor.lopes on 2016-08-18
> **grahammechanical said:**
> Are you getting error reports of system problems? When you run apt update & apt upgrade do you get a warning that there are broken packages?

The dist-upgrade command will avoid package conflicts by removing packages if necessary. Using dist-upgrade rarely causes problems but it does have the possibility to cause problems. The dist-upgrade command will bring in packages that are held back when we use the upgrade command. But they are held back for a reason.

Regards

No errors reports and no warning while using apt-get update and upgrade

---

### Post by Portaro on 2016-08-18
Maybe if you install the Kernel that you have in the othe machines with no 16.04 installed you can solve the problem because the problem can be related with the type of kernel ad the default config of Ubuntu 16.04.
Is very simple all that  you need is open synaptic and search for linux-image and see if the kernel&#8594;
4.0.4.24 is present , if is, install it and choose this kernel to the boot preference (you can do this with simple software like grub-customizer) then apply and reboot a see if work and the freezing stop.


If the problem is with the kernel of 16.04 version with updates probably the problem is solved but this require time and probably updates for graphic performance or by type of architecture and kernel , I think .

---

### Post by vitor.lopes on 2016-08-19
An outdated Lubuntu has just freezed, so it's not only a problem with the updated systems, but I can tell that these freezes happen waaaaay more often in the updated Lubuntu. Isn't there a way to track this issue? should I try first installing the 4.4.0-24 Kernel?

By the way, I remember when I first installed Lubuntu on these PCs they had a lot of bad sectors, can that be related?

---

### Post by vitor.lopes on 2016-08-22
Any idea guys?

---

### Post by banceu_sergiu_ione on 2016-08-22
You can check as others said if it is kernel related. At boot time, use left SHIFT key and chose a kernel version prior to the update. Try reproduce the conditions at freeze time.
It does no matter that others pc run good or not, you have to do it for the one that is relative to the issue.
You could also check the /var/log/Xorg.0.log for words as errors or warnings  or stuck ....at freeze time. Could try see also the /var/log/syslog at the event time.

---

### Post by vitor.lopes on 2016-08-24
> **banceu_sergiu_ione said:**
> You can check as others said if it is kernel related. At boot time, use left SHIFT key and chose a kernel version prior to the update. Try reproduce the conditions at freeze time.
It does no matter that others pc run good or not, you have to do it for the one that is relative to the issue.
You could also check the /var/log/Xorg.0.log for words as errors or warnings  or stuck ....at freeze time. Could try see also the /var/log/syslog at the event time.

There is no special conditions when the freezes happen, at least I can't notice, maybe with the logs I'm able to find a special condition, these are all the logs I should be checking? or is there any other?

I'll be downgrading the Kernel to 4.4.0-24 to see what happens

---

### Post by banceu_sergiu_ione on 2016-08-25
You can have a look about [logs file here]("https://help.ubuntu.com/community/LinuxLogFiles").
There are a lot of things that could issues a freez. From bad hardware to kernel/drivers to hangs processes and so on. Even a bad ram. I would run a memetes86+ for it.

Did you try to log in console ( Ctrl+Alt+F1 ) log in and run top and iotop (  need to be installed first ) and check the situation of the cpu and hdd .... see if there is any process that could cause the freez.

---

### Post by Topsiho on 2016-08-25
I have exact this same problem on one of my computers, and for this reason I reinstalled Ubuntu 14.04 on it. It ran for years and years on ubuntu 10.04, 12.04 and 14.04 with no problems at all.
I checked memory, and the hard disks is still OK, though i'll have to replace it within a not too long time, as it is Old age, and even Prefail for some of it's attributes. I also changed the nouveau driver for the graphics card for another proprietary one, as it experienced another sudden halt and reboot the other day (which, I remember it did also some years ago wit the nouveau driver).
I am running the computer now for some time, and challenging fate reacting on this forum, but so far so good.

My two cents :)

Topsiho

---

### Post by vitor.lopes on 2016-09-09
Ok guys, after a long time testing many different kernels, I have came to a conclusion that none of them solves the this freezing problem, I have tried in the Ubuntu and Lubuntu. I just had 2 freezes (8:05 and 8:09), here are the logs
Xorg.0.log: [http://pastebin.com/23BRYwNu](http://pastebin.com/23BRYwNu)
syslog: [http://pastebin.com/XuzBdKc7](http://pastebin.com/XuzBdKc7)

Curious thing: the freeze at 8:05 wasn't even logged, all I see are "\00\00\00\" and when I open the file there is an warning: "There was a problem while opening this file, The file you have opened has some invalid characters", the freeze at 8:09 seems to be logged, though

-----------------------

About the RAM, I don't think it's the issue, because the freeze happens only on the PCs that I have upgraded to 16.04.1, but I'll run memtest86+. About monitoring the CPU and HDD with iotop, I did monitor it, but I didn't notice anything wrong.

-----------------------

That's sad to hear Topsiho, but we can't just let this problem occur without a fix

---

### Post by Topsiho on 2016-09-09
It seems the problem is now solved for me by installing a non-free driver: both in 16.04 and in 14.04.5 the computer is running perfectly.
I remember having had this same issue when upgrading from 14.04 to 16.04, 2 years ago, solving it in the same unsatisfactory way.

To be complete: the processor is an AMD Phenom II X6, and the graphics card is a GT 240 / PCIe / SSE2

My remarks about my hard disk being on the verge of failing appear to be untrue: the disk utility gives the same sort of BS information for all of my computers, old and new..

I am using this computer now again as my main computer, and so far am quite happy with 16.04 on all (5) of my computers :)

Topsiho

---

### Post by vitor.lopes on 2016-09-14
> **Topsiho said:**
> It seems the problem is now solved for me by installing a non-free driver: both in 16.04 and in 14.04.5 the computer is running perfectly.
I remember having had this same issue when upgrading from 14.04 to 16.04, 2 years ago, solving it in the same unsatisfactory way.

To be complete: the processor is an AMD Phenom II X6, and the graphics card is a GT 240 / PCIe / SSE2

My remarks about my hard disk being on the verge of failing appear to be untrue: the disk utility gives the same sort of BS information for all of my computers, old and new..

I am using this computer now again as my main computer, and so far am quite happy with 16.04 on all (5) of my computers :)

Topsiho

What do you mean by non-free driver? and what driver was this?

---

### Post by Topsiho on 2016-09-14
You can use the utility Extra drivers to find extra drivers for your system. In my case: for the graphics card Geforce GT240 the standard driver after install is the open source Nouveau display driver.
When I use the Extra driver (I translate this from Dutch) I find there are 3 other drivers available, which are not open source (so non free) binary drivers, from which I could choose. One of them is tested, the other two are not, so I chose the tested one: NVIDIA binary driver version 340.96 of nvidia-340, And this one appears to be working well.

Non free means that the source code is not made publicly available, and so can not be maintained by the Ubuntu developers. You have to trust nvidia on their blue eyes.

Hope this is all clear to you now :). YMMV

(BTW: 2 years ago I upgraded from 12.04 to 14.04, not from 14.04 to 16.04)

Topsiho

---

