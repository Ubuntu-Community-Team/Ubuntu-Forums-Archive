---
title: "resized M$ parttion"
date: 2007-03-24
forum: General Help
---

### Post by Doug11 on 2007-03-24
I just resized my windows partiton to make room for Ubuntu. I used the live cd partioner. Now my Vista hangs on the boot,,even with a boot from the dvd. Then it hit me that I resized the partition, so the core of my problem I'm guessing is from this action. Can anyone point me in the right direction to get my Vista to boot back up. Grub is working fine, I still have a boot menu, but as soon as windoze starts to load,,it just freezes and I have to reboot. Even with the dvd..Stumped!

---

### Post by floke on 2007-03-24
GParted is a bit naff at resizing Vista. You have to use a Windows CD and use the fixmbr command to do it. If you don't have a hard copy of Vista - try the advice here

[http://ubuntuforums.org/showthread.php?t=391603](http://ubuntuforums.org/showthread.php?t=391603)

---

### Post by Doug11 on 2007-03-25
ok thanks. will give it a shot

---

### Post by Doug11 on 2007-03-25
Well, seeing as I don't have a floppy, and i can't seem to get my machine to boot from my usb key, I put in an old XP disc and let it boot to the point where it was going to reformat my ntfs partition, then cancelled out, rebooted and my Vista booted again. Don't know why it would not boot from the Vista disc but it would on the XP disc. Strange. Anyway, thanks for the help.

---

### Post by corbeau on 2007-03-25
Just one question to Doug11

I have a similar problem I am trying to resolve.

You said: ```
I put in an old XP disc and let it boot to the point where it was going to reformat my ntfs partition, then cancelled out, rebooted and my Vista booted again.

```

I have being trying to mount my Vista into a directory and it does not make any difference. I guess that somehow, your windows XP disk repaired the MBR but I know next to nothing about these things.

My question is the following: 
I understand you bought your computer with a Vista installed on it, is that right ?

---

