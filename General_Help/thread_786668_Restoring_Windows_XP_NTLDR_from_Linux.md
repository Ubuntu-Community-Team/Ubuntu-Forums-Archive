---
title: "Restoring Windows XP NTLDR from Linux?"
date: 2008-05-08
forum: General Help
---

### Post by aescnt on 2008-05-08
Hi,

I used to run Ubuntu 7.10 + Windows XP (dual boot), but after some slight re-partitioning and installing 8.04 clean, I seem to have hosed the Windows XP partition.

First, it wasn't in the GRUB menu, which was easily remedied by editing menu.lst. When I try to boot to my Windows partition though, I get this error:

   "A disk read error occurred
    Press Ctrl+alt+delete to restart"

Upon inspection, my Windows XP (NTFS) partition is missing boot.ini and other NTLDR files. My first intuition was to try to use the Windows XP CD's recovery console but it doesn't work for me ("Setup did not find any drives" error).

Is there a way for me to salvage my Windows XP partition?

---

### Post by skymera on 2008-05-08
Google the problem, it will have much more solutions that a Linux forum.

It involves using the Windows disc, as mmuch as i can remember.

Google has many results, i had the same problem.

---

### Post by aescnt on 2008-05-08
My XP CD wasn't much of use. It can't even detect my harddisk. (It's not a SATA issue -- the CD worked for me before on the same computer!)

I was wondering if there was a way for me, from Linux, to restore it's NTLDR. (By the way, I have a fully-working WinXP installation under VirtualBox. I tried to manually copy the ntldr/ntdetect.com files from there, but it still doesn't work...)

---

### Post by mihailojocic on 2008-05-08
Tell me pls where you install 8.04? What partition changes? Do you format your WIN partition or...?

Once i have similar problem. I resolve it with MSDOS command FIX MBR. I killed Linux but... After that I was install Acronis OS selector and I don't have any problem. When something is broken (very often) on stupid XP I just boot with acronis boot CD and that's it.

---

### Post by aescnt on 2008-05-08
I removed an extra partition I had lying around, and put in an EXT3 in place of it (as a /home partition).

---

### Post by angry_johnnie on 2008-05-09
Have you seen [this]("http://ms-sys.sourceforge.net/")?  It used to be available from the repositories, but now I can't see it.  You can still get it from sourceforge, though, and [here]("http://ubuntuforums.org/showthread.php?t=622828") is how it's used.

---

### Post by ironwolfe on 2008-05-09
I had a similar problem, I used Super Grub boot disk which fixes alot of boot problems...

here is the web site:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Please post back if it works

---

### Post by aescnt on 2008-05-09
Cool! ms-sys seems like what I'm looking for, although I'm not sure if it can handle NTFS (I'll have to research on that). I'll check out Super GRUB disk too. Thanks guys. :)

---

