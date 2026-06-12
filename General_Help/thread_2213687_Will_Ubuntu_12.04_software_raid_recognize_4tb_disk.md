---
title: "Will Ubuntu 12.04 software raid recognize 4tb disks?"
date: 2014-03-28
forum: General Help
---

### Post by Tony_Lillie on 2014-03-28
I am working on building a file server using Ubuntu 12.04. I've already installed the OS on a small RAID 1 and am preparing to make a 16tb (12tb useable) RAID 5 using 4 x 4tb disks. I've read a variety of information about the 2tb limitations of mbr disks, and the need to use gpt for disks >2tb, but it's still a bit fuzzy for me.

The following tutorial worked PERFECTLY using small 250gb disks: [http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

But will it work for 4tb disks? Would someone please look and give an opinion?

The process seems to include a section where the partition is created using a gpt label, but I'm skeptical because I guess I thought it would be more complicated than this.

Thoughts anyone?

---

### Post by TheFu on 2014-03-28
Using GPT is all that is needed. I'd strongly recommend using lvm too, but that isn't mandatory.
Also - do not use fdisk/sfdisk/cfdisk anymore. Stick with parted, gparted and gdisk.

I always start with the official distro documentation - help.ubuntu.com - as the first source for stuff like this.

RAID isn't a replacement for backups - just sayin'.  There are a few active stories here about people using RAID who didn't have backups and lost everything.

---

### Post by Tony_Lillie on 2014-03-28
Thank you for responding. Yes I know that backups are vital, but thank you for the reminder.

Your response confirms my understanding that gpt is definitely needed, but I still need to verify if the following section of the tutorial I linked in my original post is doing everything necessary to create a gpt partition.

Here is the section of the tutorial I am referring to: ```
 
parted -a optimal /dev/sdb
GNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt 
(parted) mkpart primary 1 -1
(parted) align-check                                                      
alignment type(min/opt)  [optimal]/minimal? optimal                       
Partition number? 1                                                       
1 aligned
(parted) quit
```

Is that creating a gpt partition? The "mklabel gpt" command seems to be the clincher, but again I am skeptical because I really thought it would be more complicated than this.

---

### Post by TheFu on 2014-03-28
Sorry - don't know. 

I've always created them with gparted on other machines before placing the drive into a server. It is just 1 setting, then apply.  There isn't anything too special about GPT - just a different/better way to create a TOC for physical disk layouts.  Never bothered with any labels - but that might be needed with parted. I don't know.

I prefer to get my information from official ubuntu websites - though I didn't bother searching on this topic.

---

