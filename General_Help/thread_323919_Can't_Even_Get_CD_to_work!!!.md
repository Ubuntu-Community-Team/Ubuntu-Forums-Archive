---
title: "Can't Even Get CD to work!!!"
date: 2006-12-23
forum: General Help
---

### Post by hairmetal4ever on 2006-12-23
Hi. I downloaded Ubuntu and I CANNOT get the image to burn to CD. Every time I burn an .iso image, whether through Nero, or Roxio, or other burning software, I get a "failed" at the end. I've updated Nero, made sure my burner is "working correctly" in the Windows device manager (remember I am still on windoze at this point) and nothing.

I tried manually extracting with WinAce, and manually adding the files, and the CD shows the files, but it won't boot. I can't get it to boot to the CD.  It just boots right to windows, although the computer will boot to the Windows XP CD if I put it in there and reboot, and the BIOS settings are correct. Any idea what the problem is?

I can't install Ubuntu if I can't even get the CD to work right!!

---

### Post by meng on 2006-12-23
If you get a failed message immediately after burning, I suspect you have a corrupted download. Check the md5sum to make sure. This would also explain the boot to windows even though your BIOS settings are correct.

---

### Post by hairmetal4ever on 2006-12-23
It does this with ALL .iso files.  Even other types of Linux like Linux-XP.  MD5sum was fine and matched.

---

### Post by hairmetal4ever on 2006-12-23
OK - got a working, bootable CD.  Apparently, Nero 6 doesn't like .iso files.  I chose the burn image option, then chose the Image Writer as the CD burner.  I then created an .nrg file, then went back and wrote the nrg image to the CD through Nero.

Anyway, it worked.  I reboot, the CD boots...and...I get the start up menu.  It says "start OR install."  I let it start loading and it appeared to freeze at the line that said "HP Linux" something or other.

I'll try it tomorrow.  Is there a way to dual-boot with Windows?  I need Windows for work and don't want to overwrite it.  Also, how do I install Ubuntu to the second partition of my hard drive?  How do I install it at all for that matter?  It just runs off the CD right now it appears.

---

### Post by meng on 2006-12-23
The default Ubuntu install is to dual-boot with any existing OS.

---

### Post by OffHand on 2006-12-23
> **hairmetal4ever said:**
> OK - got a working, bootable CD.  Apparently, Nero 6 doesn't like .iso files.  I chose the burn image option, then chose the Image Writer as the CD burner.  I then created an .nrg file, then went back and wrote the nrg image to the CD through Nero.

Anyway, it worked.  I reboot, the CD boots...and...I get the start up menu.  It says "start OR install."  I let it start loading and it appeared to freeze at the line that said "HP Linux" something or other.

I'll try it tomorrow.  Is there a way to dual-boot with Windows?  I need Windows for work and don't want to overwrite it.  Also, how do I install Ubuntu to the second partition of my hard drive?  How do I install it at all for that matter?  It just runs off the CD right now it appears.

Start reading here. It will answer most of your questions: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by hairmetal4ever on 2006-12-23
Good site.

But what if I already partitioned my drives and just want to install Ubuntu on the FAT32 portion of my drive without re-partitioning it?  I have two hard drives, a 40 GB that is in two 20 gig portions, one NTFS (the C drive) and one FAT32 (the E drive) and then a second hard drive, the D: drive that is also NTFS and 80 GB.  I just want to put ubuntu on the E portion of the first drive, the FAT32 portion.

Also, when I load from the CD, I have to pick "SAFE" graphics mode to get the GUI to load, otherwise I get a command prompt and I don't know what to do with that as I barely remember DOS commands, let alone Linux.

---

