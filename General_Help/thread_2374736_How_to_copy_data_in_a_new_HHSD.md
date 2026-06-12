---
title: "How to copy data in a new HHSD"
date: 2017-10-18
forum: General Help
---

### Post by tziulm on 2017-10-18
Hello,
I'm using a double booting Asus X552CL laptop with Ubuntu 16.04 and Windows 8.1 on it. I would like to copy all of my data (both the two OS and the other files) from my current 500 GB WD5000LPVX-80V0TT0 HDD to a new 1TB Seagate Firecuda ST1000LX015 SSHD. What software (for Ubuntu or Windows) should I use to to that without damaging any of the partitions, and how? I would like to be able to just put the new disk in the laptop, turn it on and use it immediately, if possible. Also, when I installed Ubuntu I made the mistake of not encrypting that partition. I would like to do it now, following [this guide]("https://help.ubuntu.com/community/PostInstallationEncryption"), is it fine if I do it directly on the new disk or should I do it before the copy? I don't have a lot of free space on this one. Also, would my Windows partition be fine If I do it, or would I risk damaging it?

---

### Post by TheFu on 2017-10-18
Anytime you screw with disk partitions, you risk partition damage and total data loss.

To clone a disk, use dd, ddrescue, fsarchiver, etc ... whatever.  Those tools will leave the data and partitions exactly as they are. Bit for bit copies. You can reorganize things after-the-fact.  If you change the partitions at all, then the UUID will change and you'll need to manually fix the fstab. 

As for encrypting an Ubuntu install - post install.  That is a highly non-trivial act.  Best to backup your data and do a fresh install choosing whole disk encryption.  Plus, doing this will leverage LVM, which is a good thing.  However, the Ubuntu installer doesn't like whole disk encryption sharing another OS, so expect Windows to be wiped.  In short, I don' think you can get there from here. Very few encryption guides are correct, so be prepared if/when the guide you are using fails.  Someone wrote a how-to in the forums in the last 12 months that I think is the best option.  That person did lots of testing.

Windows needs to be installed first.  Encrypted Ubuntu wants to be the only OS installed on a disk. See the difficulty? Those 2 mandates are not compatible.

Encrypting just the HOME isn't nearly as good.  I'd just setup a subdirectory under HOME any encrypt that - or just save/create an LV and encrypt that as you like.

I'm not a fan of Seagate stuff. Been burned many times since 2007.  Please, please, ensure you have excellent backups.  That is 100x more important if encryption is involved.  The data recovery method with encryption is to wipe the partition and reload from backups.

---

### Post by tziulm on 2017-10-21
OK, thank you very much for your answer. In the end I used clonezilla, it worked fine. I will see later about encryption, I can't delete the Windows partition, because I need it for work. The guide I posted talks about encrypting the /home folder, I would be perfectly fine with it, as long as I get to have both OS to work fine.

---

