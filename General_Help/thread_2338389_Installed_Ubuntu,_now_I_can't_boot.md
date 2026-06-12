---
title: "Installed Ubuntu, now I can't boot"
date: 2016-09-27
forum: General Help
---

### Post by psycho-vapist on 2016-09-27
I had a running version of Kali on one hard drive and a running version of Windows on a second hard drive. When I installed Kali the step where it asks you about GRUB (not sure exactly what it says but the part about managing boot order) I hit no. **I think this is my issue.** Anyway I had Kali running for a long time and when I wanted to boot into I would just turn off the windows drive. Now today I tried to install Ubuntu and after a successful install I couldn't boot into either, 

both the drives are encrypted

Ubuntu would show cursor blinking and black screen when screen and blinking cursor (tried right shift, alt <arrow>, alt F1), Kali says *filler until I can get the actual error* I thought that maybe it was my graphics card and removed it.

Tried running the repair boot program

Assumed GRUB was not installed for whatever reason (Ubuntu install never asked about GRUB which I thought it would)

Followed instructions at
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

```
/mnt/dev does not exist
```

Because the drive is encrypted?

Tried to mount using
[https://bbs.archlinux.org/viewtopic.php?id=160028](https://bbs.archlinux.org/viewtopic.php?id=160028)
[]("https://ubuntuforums.org/showthread.php?t=2228150")
```
Device /dev/sda2 is not a valid LUKS device
```

So according to that I don't have enough partitions, is there anyway to save my Kali drive/install GRUB if that is my issue


[ATTACH=CONFIG]271377[/ATTACH]

---

