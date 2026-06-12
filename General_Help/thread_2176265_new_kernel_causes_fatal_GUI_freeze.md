---
title: "new kernel causes fatal GUI freeze"
date: 2013-09-23
forum: General Help
---

### Post by bugbear6502 on 2013-09-23
Following a kernel upgrade:

2013-09-07 06:28:45 install linux-image-3.2.0-53-generic <none> 3.2.0-53.81

I experienced intermittent freezes. Sadly I have no simple sequence to reproduce these. They occur when I am using the machine (a Celeron laptop with 768Mb of ram) heavily; 2 active desktops under LXDE, running firefox multiple tabs, with PDF plugin, and running Gramps (a python app), viewnior, multiple LXTerminals and Gimp.

(I am doing genealogy - essentially searching for records, viewing, enhancing or editing scans of paper records, and storing them)

"sometimes" during this heavy loading the mouse would freeze. I rapidly learnt that this was game over - I could not even use ctrl-alt-f1 to get a terminal.

I discovered that "REISUB" would restart the machine after a freeze. Nothing else worked (apart from pulling the plug)

I have run a 1 hour memory test from boot, with no faults reported.

I knew (from the install logs) that I had also installed an X11 update, so I couldn't be sure of the cause of the freeze at first.

2013-09-13 16:47:48 status installed libx11-6 2:1.4.99.1-0ubuntu2.2

However, using GRUB to load the old 3.2.0-52 kernel made the freezes stop.

This is my current normal mode of working.

Versions:

uname -a

Linux bugbear-fs 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:23:24 UTC 2013 i686 i686 i386 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

How do I proceed?

   BugBear

---

### Post by searchfgold6789 on 2013-09-23
Hmm... which graphics card do you have?

---

### Post by bugbear6502 on 2013-09-24
> **searchfgold6789 said:**
> Hmm... which graphics card do you have?

The well known (or is that notorious) intel 855 (or similar)

Actually, my 9 year old laptop is probably on its last legs - the batteries have failed, so it's mains adapter only, it's a non-PAE Celeron, and my spc900 webcam (the astrophotograhpy classic) has a crashing driver.

   BugBear

---

### Post by mörgæs on 2013-09-24
It's not uncommon to have to use the second-newest kernel for some time if the newest one has a bug. One option is simply to wait for the next kernel to appear.

Before you deem the computer hopeless I would suggest Bodhi. There's a link in my signature. You will soon have to abandon 12.04 anyway so it's a good time for an experiment.

---

### Post by bugbear6502 on 2013-09-24
> **mörgæs said:**
> It's not uncommon to have to use the second-newest kernel for some time if the newest one has a bug. One option is simply to wait for the next kernel to appear.

Before you deem the computer hopeless I would suggest Bodhi. There's a link in my signature. You will soon have to abandon 12.04 anyway so it's a good time for an experiment.


Thanks for some very helpful comments - I was (fairly) happy to use the earlier kernel (must look into uninstalling the new one), but felt I should report the fault.

 BugBear

---

### Post by mörgæs on 2013-09-24
If you want to report the bug, which will be appreciated, Launchpad is the place. Developers rarely visit the pages here.

---

### Post by bugbear6502 on 2013-09-25
> **mörgæs said:**
> If you want to report the bug, which will be appreciated, Launchpad is the place. Developers rarely visit the pages here.


I don't have (even close to) a reproducible failure. :(

 BugBear

---

### Post by bugbear6502 on 2013-09-27
Can anyone advise on a procedure to uninstall linux-image-3.2.0-53-generic (which is no use to me)
such that GRUB will correctly use linux-image-3.2.0-52-generic as the default to boot from?

Can I (info from
[http://k12-tech.com/safely-remove-old-kernels-from-ubuntu-server/](http://k12-tech.com/safely-remove-old-kernels-from-ubuntu-server/))

use a purge to remove the new one (assuming I've booted from an old one)

sudo apt-get purge linux-image-2.6.32-21-server

And then "just" do a 

sudo update-grub

Or are there other "dangerous" files I need to get rid of?

  BugBear

---

### Post by bugbear6502 on 2013-09-30
Since I don't have a reliable way of triggering the big I can't be sure.

But since the linux-image-3.2.0-54-generic (NB:54) arrived
on Saturday, I haven't experienced a crash.

   BugBear (fingers crossed)

---

### Post by mörgæs on 2013-09-30
Good, please mark the thread 'solved' if the system is stable when tested over a few days.

If you have some free space on the hard drive it would be interesting to install Lubuntu 13.04 in a dual boot and see how it behaves.

---

