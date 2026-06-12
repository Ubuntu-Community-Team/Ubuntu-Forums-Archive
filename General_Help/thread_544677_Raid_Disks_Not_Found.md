---
title: "Raid Disks Not Found"
date: 2007-09-06
forum: General Help
---

### Post by condawg on 2007-09-06
Yes, this is a copy of a thread in General help, but I'm getting no help there after like, 10 hours (and I didn't know there was a Wubi forum), so any help would be appreciated.
Anyways, I just got finished installing Feisty Fawn with Wubi, and when I try and boot into it, I get an error about not finding the "Raid Disks".
It just won't start up at all.
Any help is appreciated!

---

### Post by ago on 2007-09-06
That's not really an error, it's only a message "You have no raid disks".

If you have an actual error, you should be dropped to a shell where you can look at the logs in /tmp using the command "more".

Feel free to paste here any relevant info

---

### Post by condawg on 2007-09-06
> **ago said:**
> That's not really an error, it's only a message "You have no raid disks".

If you have an actual error, you should be dropped to a shell where you can look at the logs in /tmp using the command "more".

Feel free to paste here any relevant info
Well, I'm new to Linux, so I don't know about any of this...
But, it won't let me boot into Ubuntu.
it says that I have no RAID disks, then nothing else happens.

---

### Post by condawg on 2007-09-06
Can you please help me out, Ago?
I'm looking forward to getting Ubuntu up and running ASAP, so I can start my learning process for it, and continue on to customize it limitlessly :)

---

### Post by ago on 2007-09-07
Sure,

Can you try with a fresh install? Do you get to some type of a shell? Can you try to disconnect any USB/Firewire/XYZ device? What is your setup in terms of hard disks and filesystems? Do you see something in C:\wubi\logs within windows?

---

### Post by condawg on 2007-09-07
> **ago said:**
> Sure,

Can you try with a fresh install? Do you get to some type of a shell? Can you try to disconnect any USB/Firewire/XYZ device? What is your setup in terms of hard disks and filesystems? Do you see something in C:\wubi\logs within windows?
I could try a fresh install, but later... I don't have time right now.

I'll try disconnecting USB and so forth.

I have 1 hard disk, I gave Wubi 15 gigs, altogether it has 160 gigs. Only 2 OS' installed. XP and Ubuntu.

That folder does not exist

---

### Post by condawg on 2007-09-07
Wait -- I just remembered, I have a USB keyboard... so I'll tell GRUB to run Ubuntu, then unplug that before it gets to it.

---

### Post by condawg on 2007-09-07
Didn't work :(
Forgot to answer, no, I don't get a shell... Just stays in DOS.
I did a fresh install then unplugged all USB, and still got the "No RAID Disks" message...
Is there a way to just make Ubuntu think I do have the RAID disks or something?

---

### Post by condawg on 2007-09-07
Sorry if I'm pissing you off, Ago... I'm not trying to, I just really need help.
I want to start customizing this as soon as I can, and learning how to use it, and I'm really excited but being held back by this message.

---

### Post by tuxcantfly on 2007-09-07
The issue is probably that your SATA disk controller isn't supported; it might be a general Ubuntu problem or a Wubi-specific issue, try installing using the standard Ubuntu CD, or if you don't want to bother using a CD use UNetbootin at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) and if you can get Ubuntu installed and working that way, post back, since that means it's a Wubi-specific issue.

---

### Post by condawg on 2007-09-07
Well, if my SATA disk controller isn't supported, what can I do?
The normal installer on my Feisty Fawn disk doesn't work.. I tried installing with that before I tried Wubi.
The partitioning part just doesn't work... it's weird.
I'll try UNetbootin.
Thanks

---

### Post by tuxcantfly on 2007-09-07
> **condawg said:**
> Well, if my SATA disk controller isn't supported, what can I do?
The normal installer on my Feisty Fawn disk doesn't work.. I tried installing with that before I tried Wubi.
The partitioning part just doesn't work... it's weird.
I'll try UNetbootin.
Thanks

Seems like Ubuntu 7.04 just doesn't like your hardware, in that case, since the standard CD installer didn't work either. Maybe you should try a different Linux distro (I've found that Fedora and Sabayon often work when Ubuntu doesn't), or check back to see if Ubuntu 7.10 supports your hardware once it's released.

---

### Post by condawg on 2007-09-07
> **tuxcantfly said:**
> Seems like Ubuntu 7.04 just doesn't like your hardware, in that case, since the standard CD installer didn't work either. Maybe you should try a different Linux distro (I've found that Fedora and Sabayon often work when Ubuntu doesn't), or check back to see if Ubuntu 7.10 supports your hardware once it's released.
Well that's a big dissapointment :(
I don't want another distro... I guess I'll wait for Gutsy.
Thanks

---

### Post by condawg on 2007-09-07
> **condawg said:**
> Well that's a big dissapointment :(
I don't want another distro... I guess I'll wait for Gutsy.
Thanks
Wait -- Just remembered.
I also tried to partition my drive with GParted... it didn't work.
Maybe my hard drive just can't be partitioned, and that's why the Ubuntu installer didn't work, either.
I could have made the Ubuntu installer wipe my drive and have a clean install, but I need Windows as well, so I figured Wubi would be a nice alternative considering the partitioning predicament I'm in.
So there may still be hope

---

### Post by condawg on 2007-09-08
Okay... I don't know what I did, but for some reason, it's actually working now. :D

---

### Post by 1234five on 2007-09-14
I've been having this problem too... I'm kind of a noob at this kind of stuff, so I'm not too sure what I should do. I've tried booting in quite a few times and every time it stops at no RAID disks...

---

