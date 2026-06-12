---
title: "Hard drive lost partition table"
date: 2013-05-05
forum: General Help
---

### Post by KamiMegumi on 2013-05-05
Hi everyone, 

Since I'm not a complete noob, I decided to ask help here in this subforum; however, if this thread does appear to be stupid, please be kind to me, I am really trying to grasp everything I can about my system. 
So here's the deal: I've been using my new laptop, Asus UX32A, for little more than five months now. When I got it, it only had Windows 7 installed; having it completely wiped out, I installed Ubuntu 12.10 on it.
Hardware: it has a 500GB Hitachi SATA drive (where I mounted the /home) and a smaller SanDisk SSD, which I use to store the application data and the rest of the system stuff (basically, SATA only holds the media and my documents). I did this in order to get the booting time shorter, and indeed it was able to boot up in 2 seconds.
On Tuesday I decided to reboot the laptop (usually it runs without shutdowns as I extensively use its computational abilities overnight) because of a small glitch in Ubuntu (namely, LibreOffice didn't show up in the list of running applications when commanded by Alt+Tab). However, when it tried booting up, my /dev/sda (the SATA drive) was failing to read its own boot data.
I tried looking into BIOS, but the table looked OK there. Then I took my PartedMagic liveUSB (I've had problems with the formatting of hard drives before under Ubuntu, and PartedMagic proved to help) and booted from it, and ran several tests under TestDisk, gdisk, sgdisk and parted. At first TestDisk was able to find my lost partition (and locate files on it), but was unable to recover it (tried several times to go through Deep Search and then to write the found partition; all resulted in errors). Then I ran gdisk and recovered the backup tables and headers from the recovery menu, after which gdisk and sgdisk both showed up a nice non-corrupted GPT and MBR data structures with one big partition; however, its type is declared as MS Data. 
GParted was still unable to locate this partition and showed all the 465.8 GiB as unallocated.
Thus, I tried TestDisk again, and this time it found _multiple_ MS Data partitions of size 465.8 GiB as well as several Mac HFS and EFI partitions, all of which sum up nicely to something like ~1000 TB. Also, for the MS Data partitions it cannot read the filesystem, which is why I presume that TestDisk results show that there are several partition tables "glued" into one, and thus the one and only partition I need to be declared as ext4 shows up several times.
I would really appreciate any suggestions. Right now I'm writing it from another laptop, which is why I'm not uploading any log files; I will do that if that appears to be necessary.

The main question I have, though, is if I zap all the GPT data from my disk, will it still have its media there? In other words, is there any way I could tell any of those utilities to write a new partition table with one ext4 partition of known size, and what was initially written into those sectors will not be damaged?

---

### Post by oldfred on 2013-05-05
MS data is probably correct.

gdisk & gparted did create a new type relatively recently for Linux data but both Windows & Linux have used the same gpt partition type for data.

Testdisk finds all your old partitions, you have to select which one or combinations that do not overlap is the correct version to restore. You do not add them up.

       Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

Did you make a backup of the gpt data?
      
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by KamiMegumi on 2013-05-05
I have tried all of the suggested routes of repairing GPT disks; the problem is, all of the MS data partitions that TestDisk finds seem to have a corrupted filesystem, as none of them has the files I had on the drive (well, thanks to Ubuntu One, I didn't lose anything ubiquitously important, but still, losing almost 350 GB worth of data is not something I want to do right now), and thus I don't know which one to restore when it finds them with Deep search.
Currently I can get GParted to see the device but it freezes when I try to find filesystems in the unallocated space (which is, well, all of the disk).

---

### Post by oldfred on 2013-05-05
Does gdisk or sgdisk show partitions? Usually it says primary is corrupt, restore from backup or something similar?

What does gdisk show for each drive?

---

### Post by KamiMegumi on 2013-05-05
gdisk at first showed a damaged GPT and non-existent MBR; after recovery from backups it has a valid GPT and protective MBR (again, only the SATA is damaged, SSD is ok). gdisk and sgdisk both show one partition of size 500GB - although with no flags.

---

### Post by oldfred on 2013-05-05
Was it one large partition? Or several as testdisk found as old partitions?

---

### Post by KamiMegumi on 2013-05-05
It was one big partition for the whole disk, as I was only using it for media data.

---

### Post by KamiMegumi on 2013-05-05
Also, [here]("http://askubuntu.com/questions/227958/need-help-with-testdisk-output") is a question _very_ similar to mine. This is pretty much what testdisk gives me.

---

### Post by oldfred on 2013-05-05
I am no expert on testdisk, but post yours.

---

