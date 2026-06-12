---
title: "Accidentally destroyed partition and windows wont boot"
date: 2007-09-02
forum: General Help
---

### Post by elmutt on 2007-09-02
2 seperate issues cause by apparently 1 thing.

I booted off burned iso image to the ubuntu desktop (which im posting from now, seems nice) and attemped to install it.  I started to resize a windows partition that I use to store movies and music.  My main windows installation is on a separate drive entirely which I did not touch.

So I tried the resize once and it failed for whatever reason so I tried again selecting "Guided-Use the largest continuous space" .  Then i tried to mount it and it wouldn't mount!  Then decided to restart to windows and see if windows saw it but when i restarted I got no operating system found message.

The drive my windows install is still fine and I can mount and use it from linux but it just wont boot.  Hope fully this is a simple issue and im not too concerned as the data is still there, more concerned about the other drive that seems compeltely screwed.

Any help is appreciated, thanks

---

### Post by 505 on 2007-09-02
Probably the master boot record is flawed. You have two options:
1. use the Windows one. Get the XP disk, bott from the CD into recovery mode and run 'fixmbr'
2. use Grub. This boot manager will be installed by Ubuntu, so it might be a good choice to install this anyway. Boot into a live CD and [follow these instructions](http://ubuntuforums.org/showthread.php?t=224351).

---

### Post by elmutt on 2007-09-02
when i do this step:

"find /boot/grub/stage1"

It says: "find /boot/grub/stage1"

Sorry such newb questions

---

### Post by merlinus on 2007-09-02
Did you follow the preceding steps?  Did you press Enter after each command?

Just checking....

-merlin

---

