---
title: "Just installed - First Windows, now Ubuntu won't boot"
date: 2008-02-22
forum: General Help
---

### Post by Papa.Gario on 2008-02-22
I installed Ubuntu yesterday morning. It worked great, and I was really enjoying it until I tried to switch back over to windows and I started getting:

A disk read error occurred
Press Ctrl+Alt+Del to restart

Windows wouldn't start at all, but Ubunto would no problem. So after reading around on the forums, I did what some others have and I repaired Windows... but now it goes straight to the error without giving me the chance to enter Ubuntu.

From what I understand, repairing Windows overwrites Grub, and I need to use Super Grub Disk or GParted reinstall/repair it.

Is that right? If so...

How do I do it? The more I read on here, the more my head spins. I've tried a couple of things already and everything I've done so far seems to either do nothing or make it worse. I tried using Super Grub Disk from a USB, but that did nothing except get an error telling me to remove the non system disk, then I found some instructions telling me I need to use a linux disk with it, and enter in stuff at the command prompt...

I've spent about 6 hours working on this so far, if you can help I'd really appreciate it.
__________________

---

### Post by Crooksey on 2008-02-22
Load the live CD, and then you can reinstall just grub.

---

### Post by Papa.Gario on 2008-02-23
Ok, I just did a complete reinstall, but I'm still having my original problem with the disk read error.

I'm sure I saw this problem in a FAQ somewhere -- I'm looking for it now.

---

### Post by Papa.Gario on 2008-02-23
Ok, I can't really find a way to fix the problem. 

I've tried reinstalling Ubuntu
I reinstalled Grub
I downloaded and booted with Gparted Live -- but I have no clue what to do with it, and the options that look like they might help didnt work.
I tried doing the system restore for windows, and all that did was delete grub and get me stuck at the "disk read error" at power on.

I'm still frantically looking around the forums, but any help would be appreciate.  I think I'm going to try booting with the super grub CD next.

---

### Post by ryth on 2008-02-23
> **Papa.Gario said:**
> Ok, I can't really find a way to fix the problem. 

I've tried reinstalling Ubuntu
I reinstalled Grub
I downloaded and booted with Gparted Live -- but I have no clue what to do with it, and the options that look like they might help didnt work.
I tried doing the system restore for windows, and all that did was delete grub and get me stuck at the "disk read error" at power on.

I'm still frantically looking around the forums, but any help would be appreciate.  I think I'm going to try booting with the super grub CD next.

Are you sure that your Grub entry for your Ubuntu install is pointing to the right partition?  I know that a long while ago when I installed windows post ubuntu install, windows manipulated the partitions and Grub was pointing at the wrong one.  I simply modified the grub entry for ubuntu, pointed it to the correct partition and then all was well.

Check that out. Hope it helps.

---

### Post by Papa.Gario on 2008-02-24
I can get into Ubuntu now, but I'm still getting the error when I try to boot windows

```
A disk read error has occurred
Press Ctrl+Alt+Del to restart
```

I tried repairing the MBR via the windows recovery cd, but that just makes it go straight to the error.
Then I have to use the super grub disk to fix that.

I'm so lost!  Let me post some system info that I posted in the other forum.

---

