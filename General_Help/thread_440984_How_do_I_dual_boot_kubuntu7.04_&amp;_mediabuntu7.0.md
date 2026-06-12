---
title: "How do I dual boot: kubuntu7.04 &amp; mediabuntu7.04 with one home partition."
date: 2007-05-12
forum: General Help
---

### Post by iggyboy on 2007-05-12
hiya...

My current system basic specs. are as below:

1 X AMD64 2800+ Sempron
1 X 1.5GB RAM
1 X Geforce 6600 VGA

1 X 250 PATA HDD
      -> Partition 1: 16GB NTFS (windowsXP) <-- I want to replace this to mediabuntu
      -> Partition 2: 16GB FAT32 (for windowsXP Document Settings)
      -> Partition 3: 100GB FAT32 (for Audio Files)
      -> Partition 4: 100GB FAT32 (for Video Files)
      -> Partition 5: 2GB (Windows Swap File)

1 X 250 SATA HDD
      -> Partition 1: 4GB (Linux Swap File)
      -> Partition 2: 12GB Ext3 (Kubuntu 7.04)
      -> Partition 3: 30GB Ext3 (Linux Home)
      -> Partition 4: 200GB Ext3 (for Data Files)

Okey... my windowsXP has been there doing nothing at all for almost a year now, (I started with Dapper 6.06LTS). I decided to wipe it and install mediabuntu7.04, release yesterday if I'm not wrong.

Below are my questions:

Can I make use of my current Kubuntu7.04 Home and SWAP Files share it with newly going to install mediabuntu7.04 without breaking anything to my original kubuntu7.04. I mean sharing program settings between them like firefox, torrent, kopete, etc. 

My current kubuntu works fine (just plain old kubuntu without any eye candy) and I basically  using it for my actual work. I plan to install another variant of buntu for testing and tweaking.

These are the main things that I plan to have fun with my secondary mediabuntu: VMWare, Wine, Compiz/Berly etc. Say, after installation of this programs in my secondary mediabuntu, will my primary kubuntu performance, home folder settings (desktop etc) or anything will be effected.

opps... there is another thing: I want to use trucrypt for my whole Audio, Video and Data partitions. Will there be any problems with this.

Is there anything that I should care for and any suggestion or ideas. Thank you in advance.

---

### Post by john_spiral on 2007-05-12
try setting the /etc/fstab file's  swap & /home lines to the same values.

---

### Post by iggyboy on 2007-05-12
> **john_spiral said:**
> try setting the /etc/fstab file's  swap & /home lines to the same values.

ThankX John_Spiral, I have that in mind :) I just completed mediaUbuntu download, maybe tomorrow night I will do the installation.

---

### Post by iggyboy on 2007-05-12
:oops:Opps... made a mistake, it's actually  UbuntuStudio 7.04 and not mediaUbuntu. arrrggg... #-o silly me  ](*,) ](*,) ](*,)

---

### Post by strabes on 2007-05-12
When you're installing ubuntustudio, just select the existing home and swap partitions as home and swap but make sure you don't reformat them.

---

