---
title: "Default Feisty Partition Tool, QTparted, OR Gparted? (Dual Boot)"
date: 2007-04-18
forum: General Help
---

### Post by enthusaroo on 2007-04-18
This is my first time using Linux / Ubuntu (Feisty). I want to have a dual boot system with both Ubuntu and Windows XP on my IBM / Lenovo Thinkpad R60e. I already have a fresh install of Windows XP.

I have one question though regarding installing Feisty. I'm not sure if I should start a separate thread so more people will see this question. I read that Feisty will include new tools for migrating from Windows to Ubuntu. However, all of the FAQs I've been reading about setting up a dual-boot system have said that it's best to use either QTparted or Gparted. My question is should I use the partition software that comes with Feisty tomorrow OR should I use QTparted or Gparted to create separate partitions. Setting partitions is DEFINITELY something new for me. I have never had to set a partition table up before. 

Actually, I already downloaded the Linux System Rescue CD iso and burned it on CD. However, I can not find the QTparted nor Gparted program included within the Linux System Rescue CD. Where can either QTparted or Gparted be downloaded? Which one is best / easiest? Should I use one of these or the partition program that comes packaged with Feisty?

The last FAQ I read that I need to make several partitions for Windows XP and Ubuntu (installation) of course, but also one for Linux Swap and FAT32 (for exchanging files between Windows and Ubuntu). 

Any other suggestions or advice before I install tomorrow?

Cheers. :)

---

### Post by notwen on 2007-04-18
If you're more comfortable working w/ visual aids(like me) I'd recommend using GParted(link [here]("http://gparted.sourceforge.net/download.php")) to partition your HDD.  I myself did not like the pre-packaged partition manager w/ Fiesty,  Edgy spoiled me, but hope this helps.  You can read up on info regarding GParted on their SF website. Good Luck. =]

---

### Post by enthusaroo on 2007-04-19
*bump*

---

### Post by spankymasterc on 2007-04-19
Gparted.....

---

### Post by dcstar on 2007-04-19
> **spankymasterc said:**
> Gparted.....

They are both front-ends to the same **parted** program underneath - choose either.

---

### Post by enthusaroo on 2007-04-19
...so the last question before 7.04 is officially released...

Does 7.04 come with the Gparted tool? OR should I use the version of Gparted on the Linux System Rescue CD before I install 7.04? Currently right now I just have Windows XP installed.

---

### Post by MonkeyBoy on 2007-04-19
The last few releases have had tools for resizing partitions and formatting them so you should be fine. :)

---

### Post by Tsen on 2007-04-19
Yeah, GParted will be on the Live CD

---

### Post by JanDM on 2007-04-19
> **enthusaroo said:**
> ...so the last question before 7.04 is officially released...

Does 7.04 come with the Gparted tool? OR should I use the version of Gparted on the Linux System Rescue CD before I install 7.04? Currently right now I just have Windows XP installed.

The setup will ask you for it, you don't need gparted at all, but please backup your most important documents of course. As always.

---

### Post by elyk on 2007-04-19
the partition tool included with the installer seems to be the simplest of the three that I've tried...but that simplicity comes at a price of not being as powerful. If you're just making a couple changes and don't have much experience, the built-in partitioner would probably be fine. If you want more options than it's allowing you, or you're going to be making a lot of changes, I would recommend gparted over qtparted; gparted seems better designed (for example you can modify a partition that's been created but not committed to disk; qtparted required me to undo the creation, then create a new partition). If gparted is not already installed (should be under administration), you can install it either with add/remove programs or (easier imo) ```
sudo aptitude install gparted -y
```

---

