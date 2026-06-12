---
title: "Should I erase my hard drive?"
date: 2007-12-01
forum: General Help
---

### Post by espressopigeon on 2007-12-01
I decided I should reinstall my OS (Kubuntu Feisty) one day, because it was accumulating all kinds of various digital debris, you know, unused programs, old files, sluggish performance, all that stuff that a tidiness-maniac like me can't stand. I had no important data on it, by the way. So I popped in the Kubuntu LiveCD and encountered the hated and feared "cannot access tty, job control turned off" error, which never happens to me when I boot into a hard disk. I don't want to mess with the vague and dangerous solutions and GRUB modifications and whatnot that other people have suggested in other threads, because (a) I'm fed up and (b) If I mess something up I'll not only be unable to boot, I'll also be unable to use a LiveCD, and (c) this computer was given to me and I would rather not tell the giver that I bricked their gift. So I was wondering if I could just totally wipe the hard drive, would that get rid of the error so that I could reinstall? Would my system be ruined? Would I have to erase GRUB separately? If erasing would be the best option, how would I do that?

---

### Post by jonnymccullagh on 2007-12-01
I don't really think you can mess up a system entirely just by playing with thte hard drive - messing with the BIOS might create a mess but you can wipe hard drives willy nilly.
Try downloading Gparted LiveCD and use it to wipe partitions on your hard drive.
Even just re-install Ubuntu and everything can be replaced (including Grub and existing partitions).
Even installing M$ Windows will format the drive and replace the Master Boot Record.
So the system is not lost - you can just install something new!

---

### Post by hackle577 on 2007-12-01
If you actually want to *wipe* your drive, try [DBAN]("http://dban.sourceforge.net/").

However, what jonnymccullagh said is true, reinstalling will write over whatever you have on the disk.

---

### Post by peterbrewer on 2007-12-01
> **espressopigeon said:**
> I decided I should reinstall my OS (Kubuntu Feisty) one day, because it was accumulating all kinds of various digital debris, you know, unused programs, old files, sluggish performance, all that stuff that a tidiness-maniac like me can't stand. I had no important data on it, by the way. So I popped in the Kubuntu LiveCD and encountered the hated and feared "cannot access tty, job control turned off" error, which never happens to me when I boot into a hard disk. I don't want to mess with the vague and dangerous solutions and GRUB modifications and whatnot that other people have suggested in other threads, because (a) I'm fed up and (b) If I mess something up I'll not only be unable to boot, I'll also be unable to use a LiveCD, and (c) this computer was given to me and I would rather not tell the giver that I bricked their gift. So I was wondering if I could just totally wipe the hard drive, would that get rid of the error so that I could reinstall? Would my system be ruined? Would I have to erase GRUB separately? If erasing would be the best option, how would I do that?

When I saw the title of this thread I assumed you were going to be vaporising hard drives, however I was dissapointed to learn this was not the case.  Please do not raise my hopes again in future - :p

If you go to the live cd and install again you can erase the contents of the disk.

---

### Post by espressopigeon on 2007-12-01
However, I cannot use LiveCDs, because I get hit with the c.a.t.j.c.t.o. error. I can still boot to my installed OS. So I guess my real question is: If I were to use a program to erase my disk, that should get rid whatever is causing the catjcto, including GRUB and other low-level things like that, and I should be able to reinstall with a LiveCD, right?

---

### Post by jonnymccullagh on 2007-12-01
ummmhh,
I would be careful if you are not able to boot LiveCDs .. how did you get Ubuntu installed initially if the machine won't boot from CD.
I'm not sure if the problem here is with the Hard Disk or the BIOS?

---

### Post by Craigus on 2007-12-01
Right. Dban is a good choice, and is easy to use.

---

### Post by peterbrewer on 2007-12-01
Is the cd booting at all or is it stopping mid way.  It could be due to damaged media.  GRUB is only part of the boot process when you boot from the hard drive, a cd boot will not involve GRUB at all.

---

### Post by Craigus on 2007-12-01
Agree. There's something odd going on here. To the OP : have you tried booting with more than one live cd?

---

### Post by espressopigeon on 2007-12-01
To jonnymcullaugh: It worked fine until, I think, I attempted an installation of Xubuntu which balked due to a corrupt CD.

To peterbrewer: I get to the menu, and choose "Start or install Kubuntu", then I get the error.

To Craigus: Tried Ubuntu 6.10, received dialog box saying "Boot Error" immediately after choosing "Start or Install".

---

