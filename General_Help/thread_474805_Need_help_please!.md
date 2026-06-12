---
title: "Need help please!"
date: 2007-06-15
forum: General Help
---

### Post by m4ttjirM on 2007-06-15
Hi,

I have been up all night working on this.  Okay so here is my deal - I wanted to try out ubuntu because I've only heard good things, and I have a pretty good knowledge about computers.  I have 2 hard drives in my computer, C: which is 40 GIGS, and D: which is 80 gigs.  C: is master and D: is slave.

I decided I would format drive D: and install ubuntu on this.  C: has windows xp installed on it with a lot of information.

Anyways, I go to the main ubuntu website, and I download the install disk.  I boot from CD and I get into ubuntu fine.  I mess around with it and I learn some things, so I decide that I would install ubuntu in the morning.

I install UBUNTU and select it to use the entire drive D: .  During installation, probably about 80 or 90 percent through, the computer totally locks up. So then I restart the computer because I have no choice, and when I try to boot from CD again I get this error:

"GRUB Loading stage 1.5.



GRUB loading, please wait...
Error 15"

Here is the main problem, when I try to boot back into drive C: which has my windows installation on it, I get the same problem.  I can't even boot from the live cd anymore.  I'm basically stuck.  I can't boot into my XP, and I can't use the Live cd to try to boot back into ubuntu.  I don't think my C: should be effected because I definately chose drive D: for ubuntu install

I have already googled it and read many forums but I dont think there are many problems similar to this, I can't boot to the live cd or my previous XP install.  Also, I'm a linux noob so I don't even know what GRUB is.  Any help would be greatly appreciated because I have a lot of info on my C: drive that I really need.

Thanks,

Matt

---

### Post by jasonlfunk on 2007-06-15
GRUB is the bootloader that boots the operating systems. What you will want to do is make sure that your CDROM comes before your hard drives in the boot sequence so the CD gets loaded even before grub tries to start. Once you do that, then try to install again.

---

### Post by m4ttjirM on 2007-06-15
Okay, 

but why am I getting a GRUB error when trying to boot from drive C:?  I installed Ubuntu on Drive D:

My boot sequence is this - CD ROM, then C: , then Floppy

I never messed with drive C: at all that is where I am getting confused :confused:

---

### Post by jasonlfunk on 2007-06-15
GRUB replaced your Windows Boot loader which was on drive C:. None of your data on drive C: was lost. If you want, you can boot with your Windows XP disk and go into the recovery consolue and type ```
fixmbr
```.

---

### Post by m4ttjirM on 2007-06-15
Okay,

I have pinpointed the problem down to my first CD Rom drive.

I put the ubuntu cd in my secondary cd rom drive, and the ubunu install cd ran.  I am going to re install ubuntu.  The thing that is scaring me is this - will I be able to boot up to windows still?  I Got a grub error when I chose to boot to drive C: , those are my windows files.  Drive D: should be ubuntu.  

I will let you know what happens after this second re install

---

### Post by m4ttjirM on 2007-06-15
Okay,

THank you.  So I should install ubuntu, then put the XP cd in again amd do the fix master boot record command.  After that I should be able to boot into ubuntu and xp?

---

### Post by jasonlfunk on 2007-06-15
No. Install Ubuntu. It is usually smart enough to see Windows and automatically add it to GRUB. While it is possible to add ubuntu to your windows boot loader, i've never tried. Grub has always worked well for me.

---

### Post by m4ttjirM on 2007-06-15
I'd like to say thanks for all your help.  It's so weird I guess the reason the install froze is cause my LITEON dvd player gave out on me.  Well its only been 5 years since i built this comp.... its time for me to make the switch over to linux/ubuntu.

---

