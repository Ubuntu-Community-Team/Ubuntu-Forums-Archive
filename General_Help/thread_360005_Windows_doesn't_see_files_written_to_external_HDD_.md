---
title: "Windows doesn't see files written to external HDD from Ubuntu"
date: 2007-02-12
forum: General Help
---

### Post by OrionsGlory on 2007-02-12
I have an Acomdata 250GB USB2 External that I use for backup and to store all my music. It works great with both my Edgy install and Windows separately, and I can access files written from Windows in Ubuntu, but not vice versa. When I write files from Ubuntu, Windows simply doesn't show them when I look at the drive, but going back to Ubuntu allows me to view them, etc.

This is on an IBM T43p laptop, dual booting with the most up to date Edgy install and Windows Vista (though the same occurred when I was using XP).

Any thoughts? I'd really like to be able to use the external to transfer files between the OSs and so that I can rip CDs from both Ubuntu and Windows.

---

### Post by llamakc on 2007-02-12
How is the external drive formatted? What filesystem are you using?

---

### Post by OrionsGlory on 2007-02-12
Oops, sorry. The external is FAT32.

---

### Post by dcstar on 2007-02-12
> **OrionsGlory said:**
> Oops, sorry. The external is FAT32.

How big is the drive partition?, I seem to remember reading about FAT32 size limitations, and it may be that XP is using a different directory structure to what Ubuntu is capable of handling.

---

### Post by OrionsGlory on 2007-02-12
The entire external is FAT32, so it's 250GB FAT32 (about 232 in actuallity). My laptop's hard drive is about 53.5GB NTFS, 1.5GB Swap, and 20GB ext3.

---

### Post by dcstar on 2007-02-12
> **OrionsGlory said:**
> The entire external is FAT32, so it's 250GB FAT32 (about 232 in actuallity). My laptop's hard drive is about 53.5GB NTFS, 1.5GB Swap, and 20GB ext3.

That is a massive partition for FAT32, I wouldn't mind betting a partition of less than 32GB will work without any issues.

---

### Post by OrionsGlory on 2007-02-12
What would you suggest making the rest? I'm under the impression that Linux doesn't do very well writing to NTFS. I also currently have about 112GB of the drive used up and don't really want to mess that up.

---

### Post by dcstar on 2007-02-12
> **OrionsGlory said:**
> What would you suggest making the rest? I'm under the impression that Linux doesn't do very well writing to NTFS. I also currently have about 112GB of the drive used up and don't really want to mess that up.

Just make multiple partitions of the biggest size Ubuntu can support on the drive.

I don't know the exact maximum size for FAT32 under Linux, but if you tried to partition the drive using Linux tools then they may only allow you to set the maximum (whatever it actually is).

I'm sure Windows will be able to work with oversize FAT32 partitions, but it is probably using some MS "workaround" that Linux hasn't caught up with quite yet.

---

### Post by igknighted on 2007-02-12
> **OrionsGlory said:**
> What would you suggest making the rest? I'm under the impression that Linux doesn't do very well writing to NTFS. I also currently have about 112GB of the drive used up and don't really want to mess that up.

Fat32 is easily corruptable, and can't have files larger than 4GB (ie, no saved DVDs).  I would strongly recommend using the linux native ext3 file system, as it has no such limitations.  You have to install a driver for it in windows, but (thank you open standards) it works flawlessly.  While I have never tried this with a USB disk, I have used it with a disk in my computer and it worked great.

---

