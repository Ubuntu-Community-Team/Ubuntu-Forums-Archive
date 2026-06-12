---
title: "Moving ubuntu to a different hdd"
date: 2008-03-17
forum: General Help
---

### Post by LuisGMarine on 2008-03-17
Hello,

I'm sorta lost on how to go about this, some of the tutorials out there are confusing and I'm looking for a clear cut answer to what I need to accomplish. 

I have two hard drives in my computer,  I have ubuntu 7.10 installed on the first one.  The second hard drive is formated to ext3, with nothing in it.

I currently started college, and since I'm in the military a lot of classes have DATA disk that only work in Windodows, this is to help the process of doing classes faster since we have to deal with constant deployments that stop us from having normal semester hours.

Anyhow I need to install windows on my first HDD, for some reason trying to install windows gives me a problem about not finding my second HDD, but it finds the first one just fine.

So my question is, what can I do to clone my current ubuntu installation from my first HDD to my second one, then wipe the second hdd and go about installing windows.  Then I would boot the live CD and fix grub.  But what errors can I expect from ubuntu, since the partitions are named different.  

Also what programs would I use to clone my current installation?

This is my setup:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         436        6370    47672887+  83  Linux
/dev/sda2            6371       14593    66051247+  83  Linux
/dev/sda3               1         435     3494106   82  Linux swap / Solaris

I just need to replicate that one the second HDD and make sure everything works.  I'm afraid paths to files might get screwed up since it will be going from sda ( first HDD ) to second HDD ( sdb )

Any suggestions?:guitar:

---

### Post by gobbles414 on 2008-03-18
> **LuisGMarine said:**
> Hello,

I'm sorta lost on how to go about this, some of the tutorials out there are confusing and I'm looking for a clear cut answer to what I need to accomplish. 

I have two hard drives in my computer,  I have ubuntu 7.10 installed on the first one.  The second hard drive is formated to ext3, with nothing in it.

I currently started college, and since I'm in the military a lot of classes have DATA disk that only work in Windodows, this is to help the process of doing classes faster since we have to deal with constant deployments that stop us from having normal semester hours.

Anyhow I need to install windows on my first HDD, for some reason trying to install windows gives me a problem about not finding my second HDD, but it finds the first one just fine.

So my question is, what can I do to clone my current ubuntu installation from my first HDD to my second one, then wipe the second hdd and go about installing windows.  Then I would boot the live CD and fix grub.  But what errors can I expect from ubuntu, since the partitions are named different.  

Also what programs would I use to clone my current installation?

This is my setup:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         436        6370    47672887+  83  Linux
/dev/sda2            6371       14593    66051247+  83  Linux
/dev/sda3               1         435     3494106   82  Linux swap / Solaris

I just need to replicate that one the second HDD and make sure everything works.  I'm afraid paths to files might get screwed up since it will be going from sda ( first HDD ) to second HDD ( sdb )

Any suggestions?:guitar:

Have you searched your PC's BIOS for any relevant options? I wouldn't recommend cloning. I once encountered a similar problem to yours while trying to install Ubuntu on one hard drive and Windows on another. Windows seems to be more picky than Ubuntu about finding hard drives for installation. If you would like to try to save your current Ubuntu installation, use the following procedure:

A. Open your PC tower and disconnect the hard drive that has Ubuntu on it.
B. Close the tower and install Windows
C. Open the tower and reconnect Ubuntu's hard drive.
D. You'll need to use a LiveCD to repair your GRUB bootloader. Click [here]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/") for some nice instructions.

If you need to put Windows on Ubuntu's current hard drive and Ubuntu on your empty one, follow this procedure:

1. Create backups of your data in Ubuntu
2. Install Windows on the hard drive where Ubuntu is currently installed. This will erase Ubuntu.
3. Install Ubuntu on your other hard drive.

Do either of these help?

---

### Post by LuisGMarine on 2008-03-20
What I had to end up doing was just starting from scratch.  Installed windows vista on the first hdd then Ubuntu on the second hdd.  Thanks for the help anyway.  Next time I shall try this whole clone thing.

---

### Post by gobbles414 on 2008-03-20
> **LuisGMarine said:**
> What I had to end up doing was just starting from scratch.  Installed windows vista on the first hdd then Ubuntu on the second hdd.  Thanks for the help anyway.  Next time I shall try this whole clone thing.

IMHO, installing from scratch is better than cloning anyway. I'm glad that you've gotten both Windows and Ubuntu installed on your PC.

---

### Post by Sef on 2008-03-20
Check out [Clonezilla]("http://clonezilla.sourceforge.net/") as a stand alone app or combined with [GParted]("http://gparted-livecd.tuxfamily.org/").

---

