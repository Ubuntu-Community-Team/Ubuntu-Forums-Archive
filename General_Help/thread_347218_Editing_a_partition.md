---
title: "Editing a partition"
date: 2007-01-26
forum: General Help
---

### Post by puffy1980 on 2007-01-26
I installed ubuntu on a 3GB and 2GB partition. I want to edit this so its now just a 5GB partition. I cant do this in ubuntu, as its using HD1 as its primary partition and I cant edit it while its mounted. I know you can do this via a live CD, but seeing as I dont have one, and DSL doesnt include a disk partition manager, I was wondering if you can do this via windows, and save me the hassle of a download of 700mb. Please reply with any ideas, all your help would be make me so thankful

---

### Post by dcstar on 2007-01-27
> **puffy1980 said:**
> I installed ubuntu on a 3GB and 2GB partition. I want to edit this so its now just a 5GB partition. I cant do this in ubuntu, as its using HD1 as its primary partition and I cant edit it while its mounted. I know you can do this via a live CD, but seeing as I dont have one, and DSL doesnt include a disk partition manager, I was wondering if you can do this via windows, and save me the hassle of a download of 700mb. Please reply with any ideas, all your help would be make me so thankful

There are CD utility images you can download that to this - do a web search for disk resize utilities and you should have a few to choose from, like this one:

[http://www.sysresccd.org/Index.en.php](http://www.sysresccd.org/Index.en.php)

---

### Post by Imsati on 2007-01-27
Puffy, just out of curiosity, why do you want to make the two into one partition? You need 1 for Swap, and 1 for Root (and preferably 1 for Home). No, you can't do it in Windows, only Delete them; Same with fdisk.

---

### Post by foxmulder881 on 2007-01-27
Use the GParted LiveCD. It's only a couple of MB to download and completely free.

---

### Post by HereInOz on 2007-01-27
Try downloading GParted Live CD iso - it is only about 30MB and burns to a bootable CD which will allow you to edit the partition table of your hard disk.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Make sure that you back up all your data before doing anything relating to partition editing - it has a horrible habit of coming unstuck in the worst possible way.

---

### Post by puffy1980 on 2007-02-02
Thanks for the replies guys. I actually downloaded Puppy Linux, installed it on my 1GB pendrive and did it from that. Was actually really useful

---

