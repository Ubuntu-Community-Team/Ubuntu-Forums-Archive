---
title: "Partition new HDD for multi-boot Linux/BSD"
date: 2008-04-12
forum: General Help
---

### Post by Perpetual on 2008-04-12
(Mods, please move this if it is in the wrong forum.  I thought Other OS but also thought General Help)

I have bought a new HDD for my laptop and plan to install 3 OS's.  I have done a lot of googling but I find a lot of dual-booting with Windows, so following is what is in my head but I would be thankful if someone could comment on whether this is right or wrong.

160 GB ATA-100 Notebook Hard Drive

/boot - 256MB

Partition 1 - Primary - 30GB
Logical Partition - Ubuntu

Partition 2 - Primary - 30GB
Logical Partition - Fedora 9

Partition 3 - Primary - 30GB
Logical Partition - PC-BSD (or FreeBSD)

Partition 4 - Primary - 40GB
/media/MyData - To be shared with all OS's where I will store documents, music, etcetera.

Swap - 2GB

My first question is, do I need the /boot?  I am thinking that I will install my bootloader there when I install Ubuntu and then do not install a bootloader when doing the rest of the installs.  After, manually edit grub to add the other OS's.

Because I am using the /media/MyData to store all important data, do I need to have a / and /home for each OS?

This is my first go at BSD and I am not sure how it is going to like all of this.  Was first looking at FreeBSD but thought I would go with PC-BSD first to get my toes wet.

Any thoughts?  Is this a mess?   I plan to use the Gparted live cd with the blank drive to create all of the partitions.  Should I create the Logical partions, including / & /home, with Gparted or create them with the OS installer?

Lastly, the 30GB Partitions will be basically a lot of wasted space since all of my data will be in /media/MyData.  However, I understand that a HDD can only have 4 Primary partitions, so I am unclear on how I could say, put 6 OS's on the drive.  Wouldn't I need a Primary partition for each OS?

Thanks for reading,

Landon

---

### Post by Nameless_one on 2008-04-12
You don't "need" a /home partition for each OS, but that means that if you ever lose one of them, your settings will also be lost. I would suggest having a common /home partition, at least for Ubuntu and Fedora, but I am not sure how that can turn out. It might prove unstable (meaning only that some application settings might not work very well,  nothing more serious than that). It might work, though. 

Seeing as you probably won't be making and ntfs partitions, I believe gparted is OK, especially if you download and use the latest LiveCD. 

As for the number of partitions, the limit is 4 partitions, but any of them can be an Extended partition, which can contain Logical partitions (I am not sure why you say your partitions are both primary and logical :) ). I don't think linux has any trouble being installed on a non-primary partition. 

Concerning size, in my installation, / and /home together, minus all data totals about 6 GBs right now. That includes one or two GBs for thumbnails and metatracker's data, which are usually large. My /home settings only take up about 120 MBs. 

I hope I answered some of your questions.

---

### Post by logos34 on 2008-04-12
I would go instead with a [dedicated Grub partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"), rather than /boot.

Like the previous poster said, 30 gb for each OS is overkill...~7 gb for each should be plenty if you store all user data on MyData partition.  But I wouldn't advise a combined /home.

Limit 4 primary partitions, or 3 + 1 Extended.  So put each OS on a primary, and swap, grub, and data inside the extended.  Might be best to first partition the disk from Gparted live cd or gparted on the ubuntu live cd--either will work fine--then choose Manual install option specifying each mount point.

---

### Post by Perpetual on 2008-04-13
Thanks for the responses.  I am still a little confused on how to have more than three OS's if I have to keep the OS's in Primary partitions, since I can only have 3 Primary's.  Within the Primary's can I have Logical partitions with numerous OS's?

---

### Post by logos34 on 2008-04-13
> **Perpetual said:**
> Thanks for the responses.  I am still a little confused on how to have more than three OS's if I have to keep the OS's in Primary partitions, since I can only have 3 Primary's.  Within the Primary's can I have Logical partitions with numerous OS's?

Linux root doesn't care whether it's on a logical or primary partition (mine's on a logical).  Put 'em all inside the extended if you want--doesn't matter.

---

### Post by Perpetual on 2008-04-14
> **logos34 said:**
> Linux root doesn't care whether it's on a logical or primary partition (mine's on a logical).  Put 'em all inside the extended if you want--doesn't matter.

logos34, thanks again for the responses.  I worked everything out with a large extended partition and created logical partitions within.  Ubuntu installed with no problems but Fedora did not like all of the partitions and would not install.  I went back in with gparted live cd and deleted all of the small partitions I'd created then did the install again with Fedora.  I created / and /home with the Fedora installer in the extended partition and all worked fine.

Having grub in it's own partition has worked out well.

Landon

---

### Post by logos34 on 2008-04-14
> **Perpetual said:**
> logos34, thanks again for the responses.  I worked everything out with a large extended partition and created logical partitions within.  Ubuntu installed with no problems but Fedora did not like all of the partitions and would not install.  I went back in with gparted live cd and deleted all of the small partitions I'd created then did the install again with Fedora.  I created / and /home with the Fedora installer in the extended partition and all worked fine.

Having grub in it's own partition has worked out well.

Landon

Good to hear.  Mark thread as 'solved' and enjoy!

---

### Post by confused57 on 2008-04-14
I believe PC BSD may need to be installed to a primary partition...I had planned to install BSD(never got around to it), but  read if you try to install to a logical partition, it will format & install to the entire extended partition.  I could be out in left field on this, but you may want to check if it's true or not.

---

### Post by maybeway36 on 2008-04-14
PC-BSD does need a primary partition. Tell it during install NOT to install the bootloader, then add PC-BSD's partition as a chainloader entry to GRUB's menu.lst (as you would do with Windows.)

---

### Post by logos34 on 2008-04-14
> **maybeway36 said:**
> PC-BSD does need a primary partition. Tell it during install NOT to install the bootloader, then add PC-BSD's partition as a chainloader entry to GRUB's menu.lst (as you would do with Windows.)

You're right. I stand corrected.  Just read this:

> Be aware that BSD operating systems, and hence PC-BSD, only recognise primary partitions and consider any logical partitions as a whole primary partition. Trying to install on a logical partition will convert your extended partition into a primary partition and erase all logical partitions of your system. PC-BSD can be installed on any primary partition; it doesn't necessarily have to be on the first one. Be careful and make sure you have a backup of your data.
source: [http://docs.pcbsd.org/guide/chap2.3.html](http://docs.pcbsd.org/guide/chap2.3.html)

Interesting.

---

### Post by Perpetual on 2008-04-14
> **confused57 said:**
> I believe PC BSD may need to be installed to a primary partition...I had planned to install BSD(never got around to it), but  read if you try to install to a logical partition, it will format & install to the entire extended partition.  I could be out in left field on this, but you may want to check if it's true or not.

Thanks for the tip!

---

### Post by confused57 on 2008-04-14
> **Perpetual said:**
> Thanks for the tip!
Glad to help...I think it's the main reason I didn't install BSD, most of my Linux installs are on logical partitions.

---

### Post by Perpetual on 2008-04-14
> **confused57 said:**
> Glad to help...I think it's the main reason I didn't install BSD, most of my Linux installs are on logical partitions.

I can add another Primary partition to this drive so I will probably still give it a go.  Just for the sake of trying.

---

