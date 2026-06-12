---
title: "Slow Operating Speed"
date: 2008-01-01
forum: General Help
---

### Post by The Spy on 2008-01-01
I have a AMD 64 Athlon X2 CPU, 1GB of RAM (two sticks), and Ubuntu is installed on an IDE 40GB hard drive.

The problem is that all of the sudden Ubuntu started starting up slow. It gets to the login window fine, but after I login it takes a minute or to load the desktop. I had Compiz installed before it got slow, and it ran fine. I turned off all the startup apps that I don´t need. I was thinking of defraging the hard drive, but I looked at some forums about that, and most of them said and ext2 filesystem does not need to be defragged. So something is sucking up my memory, or something.

It isn´t just startup. Once the desktop is pulled up I´ll click on Places> Documents for example, but it doesn't pull up until after a while.
I am dual booting with Windows, but that shouldn´t do anything to effect the performance of  Ubuntu. 
I guess it could be a hard drive problem, ´cause when I first startup my computer one of my hard drives starts making this buzzing, whirring sort of sound like it is spinning to fast, but after a minute or so it slows down and doesn´t make the noise while running the computer. Also I am booting from two hard drives (one for Windows the other for Ubuntu), but I have a third hard drive that I have to have in there connected to the Ubuntu hard drive to make it work, or else the bootup to GRUB is slow. So I guess it could be a hard drive issue.

Any help on this would be extremely appreciated. Thanx

The whirring noise was actually my front fan.

---

### Post by ~LoKe on 2008-01-01
Hard drives do need to be checked occasionally, but it should do that after every 34-37 reboots (unless you changed it).  It would be done using "fsck", but you'd have to boot up a LiveCD and run it that way (never run fsck on a mounter partition).

---

