---
title: "Removing Partitions"
date: 2007-05-06
forum: General Help
---

### Post by tlinux on 2007-05-06
I currently have a dual boot system loaded with Windows XP and Kubuntu 7.04. I'd like to remove Kubuntu and it's partitions so that the entire hard drive will be available for Windows. Can I remove these partitions without wiping out my Windows installation? If so, how?

Thank you!

---

### Post by public_void on 2007-05-06
I'd suggest using GParted LiveCD, it allows you to change your partitions by booting into a minimal Linux environment.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by tlinux on 2007-05-15
I tried GParted but couldn't get it to work. I downloaded the iso and burned it to a CD. Then I booted with it in the CD drive. What I got was a GRUB prompt and I was never able to get past it. GParted has a forum but it's not very active. I searched it and others have had similar problems but I didn't find any solutions. 

Looks like I just may  not be able to install Kubuntu on this machine.:(

---

### Post by merlinus on 2007-05-15
If you got to a grub menu, then your computer did not boot from the cd.

Make sure you burned the disk as a cd image, not data, and that your machine is set up in the bios to boot from the cd drive before the hard drive.

Then you will be able to use gparted.

Sometimes re-starting with ctrl-alt-del at the grub menu will ensure the machine boots from the cd drive, in my experience, if it did not the first time.

hth....

-merlin

---

### Post by tlinux on 2007-05-16
Merlinus,

Following your comments about how to burn an iso file. I tried several different ways to get the latest version of GParted (0.3.4-6) to load form the live disk, but I always got a GRUB prompt. I never found a way around it. However, when I went back to an older version of GParted (0.3.3-0)  it would boot up and install.  Once opened it seemed to be functional but finicky. The terminal and other icons weren't functional and I was unable to exit the program. There were two options: 1) remove disk and reboot, and 2) reboot.  The disk could be removed but I was never able to reboot or otherwise get out of the program normally. I had to shut down the computer and reboot it.


Given all these troubles, it seems to me that the program is still buggy. This makes me afraid to use it. What do you think?

---

### Post by merlinus on 2007-05-16
Don't worry about having to manually reboot after using gparted.  This happened to me, but all of the partition changes and formatting were fine.

But what do you mean by,"it would boot up and install."?  You are not trying to install gparted, but to use the live cd for partitioning.

Forgive me if I misunderstood....

And perhaps your download of the newer version is corrupted???  I believe you can use mdsum to verify that it is okay.

The cardinal rule is to make doubly, even triply, certain that you have backed up vital data beforehand, especially in your Windows partitions.  You never know....

But that's what makes the world of computing and Ubuntu special!  :lolflag: 

-merlin

---

### Post by tlinux on 2007-05-17
merlinus,
> 

But what do you mean by,"it would boot up and install."? 

I misstated the situation. I meant to say that it booted up completely. That is, it ran.

I've backed up all my Windows files on the C drive and I even backed up the D drive. I'm trying to be cautious.

Thanks for your help.

---

