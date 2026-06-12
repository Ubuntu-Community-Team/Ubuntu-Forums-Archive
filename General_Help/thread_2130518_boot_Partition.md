---
title: "/boot Partition"
date: 2013-03-29
forum: General Help
---

### Post by SPMcKinney on 2013-03-29
Just a quick question what would you recommend the size of a /boot partition to be?

Currently on my ma's computer it is 190mb which seems incredibly stupid to me, but I also don't like separate partitions (I'd rather have all my files in one partition just for the ease) so I'm at a loss. The guy who installed Ubuntu on her computer is the one who did the partitioning (I would of installed it but ever Ubuntu based OS hates me and never works) but I have no Idea what he was thinking as my ma uses it for internet and a church program. I know there is a way to extend the partition if need be with a live cd (which I will need to get if you think 190mb is to small for a /boot partition) and reading the way to do it seems simple enough (it was also a excellently written guide [here]("http://ubuntuforums.org/showthread.php?t=1219270") which I hope is still valid :?).

Ok enough rambling...thanks in advance

---

### Post by dabl on 2013-03-29
/boot can fit with lots of spare room on a 500MB partition.  However, there are only a relatively few reasons why you would need to separate /boot from the "/" filesystem.  So for a new installation, if you don't know of a solid reason why you need it, then don't bother making it separate.

To increase the size of an existing partition, you can boot a live CD and use GParted.  Personally I like to use a Parted Magic Live USB stick, but you can use a GParted Live or Ubuntu or other Linux Live CD.  However, you will have to free some space before you can expand the /boot partition -- like maybe shrink whatever is to the right of /boot by 100MB first, and slide it right on the drive so there is 100MB of unallocated space alongside the /boot partition.

---

### Post by coldcritter64 on 2013-03-29
> **SPMcKinney said:**
> Just a quick question what would you recommend the size of a /boot partition to be?

Currently on my ma's computer it is 190mb which seems incredibly stupid to me, but I also don't like separate partitions (I'd rather have all my files in one partition just for the ease) so I'm at a loss. The guy who installed Ubuntu on her computer is the one who did the partitioning (I would of installed it but ever Ubuntu based OS hates me and never works) but I have no Idea what he was thinking as my ma uses it for internet and a church program. I know there is a way to extend the partition if need be with a live cd (which I will need to get if you think 190mb is to small for a /boot partition) and reading the way to do it seems simple enough (it was also a excellently written guide [here]("http://ubuntuforums.org/showthread.php?t=1219270") which I hope is still valid :?).

Ok enough rambling...thanks in advance
/boot only hold the kernel images & some files needed for booting the system.

A good practice is usually to only keep the latest kernel and one older "known good" kernel (usually the second newest kernel released tested well on the machine).

In such a case 190MB is more than adequate for /boot, personally I wouldn't have used it, but if you keep to the latest 2 kernels (1 well tested + newest) you really don't need to alter it in my opinion.


**Edit:** as an afterthought OP, check in /boot  for installed kernels with the terminal code,
```
ls /boot | grep vmlinuz
``` this will give installed kernels.

And for the current size,
```
du -ah /boot
``` this should include all (-a) and output in a human readable form (-h), you may need to precede the command with "sudo" (to get accurate results, I'm not sure and can't test this on Android).

Knowing how many kernels are currently installed and how big /boot currently is may help you make a decision on whether to repartition or not. Cheers.

---

### Post by SeijiSensei on 2013-03-29
On modern drives, I usually allocate 512 MB to /boot.  One annoying feature of Ubuntu is that it doesn't do a good job of deleting stale kernels when they are updated.  People here have run out of space in /boot because they have five or more kernels and associated files stored there.  If you are diligent and clean out the cruft in /boot on a regular basis you can get away with less, but really what are a few hundred megabytes more or less these days on drives that are hundreds of gigabytes in size?

The smallest partition I've assigned to /boot is 256 MB.

---

### Post by andrew.46 on 2013-03-30
Perhaps my usage is a little primitive: I have one monster partition for everything and a smaller one for swap:

```

root@skamandros/home/andrew#**[COLOR="#FF0000"] lsblk [/COLOR]**
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda1   8:1    0   1.8T  0 part /
&#9492;&#9472;sda2   8:2    0   3.8G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  
sr1     11:1    1  1024M  0 rom 

```

Mind you that is still a decent size for a swap.....

---

### Post by agillator on 2013-03-30
There are many arguments for and against multiple partitions. It finally boils down to personal preference and that is often just an arbitrary decision. The main argument for a separate boot partition is that it decreases the chances of corrupting the system files and eases recovery in case of file system corruption elsewhere. Valid? I don't know. However the argument against one massive root partition again goes back to basic file system corruption. Corrupt a one partition system and you lose everything. Hopefully you have backups of anything valuable, but even with that there is always something you forgot or failed to back up. Using several partitions means that, since each is a separate file system, corrupt one and the others are probably still ok. Even if you have to totally reload the system, at the end you can get back to existing partitions and their contents. This also helps when upgrading the system. Personally I use a separate boot partition and several other partitions and it has saved my neck a number of times. But then I don't mind the little bit of extra effort multiple partitions require and I can't/won't disagree with someone who prefers to use one (or a dozen). Oh, I will say one thing with a high degree of certainty: At some point, some day, a file system on your computer will become corrupted and unusable. The odds are it will happen sooner rather than later. Hasn't happened yet? That just increases the odds of it happening today.

---

### Post by SPMcKinney on 2013-03-30
***Wanted to reply to everyone but wanted to cut down clutter of using full posts***


> **dabl said:**
> ...
Ya If it was up to me I would of had everything in one partition and thanks for confirming the way to expand the partition and mentioning using a Parted Magic Live USB stick, Does the computer need to be able to boot from USB to be able to use it? If so I gotta get a Live Disc as her computer cant boot from usb :(.


> **coldcritter64 said:**
> ...
Thank you for the codes and that was the exact problem I was having...stupidly for some reason I thought Ubuntu would get rid of the older kernels and headers or like your saying keep a backup and the newest. Turns out that isn't the case at all as the kernels were from the start of 12.04 :? (if I remember right 8 or 9 of them).


> **SeijiSensei said:**
> ...
512mb seems much more sensible thing that through me off is the computer has 320gb of hard drive space but ya your right I'm used to Debian who actually gets rid of the old kernels and headers.


> **andrew.46 said:**
> ...
Yup I'm with you 100% I make my Swap 4gb (amount of ram I have) and the rest my OS


> **agillator said:**
> ...
It does seem valid and for the advance user or even one that isn't an older woman who uses a computer for internet, a church program, and nabbing families facebook pics...not so much. About the partition becoming corruptible you meaning the hard drive outright dying?

---

### Post by dabl on 2013-03-30
> **SPMcKinney said:**
> 


Ya If it was up to me I would of had everything in one partition and thanks for confirming the way to expand the partition and mentioning using a Parted Magic Live USB stick, Does the computer need to be able to boot from USB to be able to use it? If so I gotta get a Live Disc as her computer cant boot from usb :(.



You'll have to use a Live CD if her computer can't boot USB.  The Parted Magic ISO image can be burned to a CD, instructions [**[color=green]here[/color]**](http://partedmagic.com/doku.php?id=downloads).

Because of the small size of the /boot partition, and that fact that there are very few changes to the data on it (basically addition and deletion of kernels only), it makes little sense to impose the overhead and media "wear" of journalling, so an ext2 filesystem is recommended.  I just checked the /boot partition on my 2+ year old Debian system and it is sitting at 117MB usage, on a 512MB partition.

---

### Post by agillator on 2013-03-30
A corrupted partition (actually file system) is simply one that cannot access its contents for any reason. The drive itself may be physically healthy. If the system cannot read the inode table, or the table itself is garbled, or something happens to make it unreadable or unusable then the system is corrupted, that is it cannot recover the files. That is one thing that can happen. A corrupted file system normally has nothing to do with the health of the drive itself. From what you have also said I wonder if you realize that using multiple partitions is normally transparent to the user. Everything in Linux is a file and to the user appears as one large tree or file system. Unless you look and ask you have no idea and don't care how many partitions and devices you are using. The only times you deal with partitions are when you initially mount them, which is most often done automatically with entries in the /etc/fstab file, or when one fills up which need never happen. So the 'old woman' consideration really does not apply. From what you say I would certainly put the directory containing the pictures on a separate partition and back it up regularly to protect them. I'll bet those are something she certainly wouldn't want to lose if something were to happen. She would never know or need to know anything about partitions, just that if something short of physical destruction happened to her computer you are a genius because you fixed it and she didn't lose her pictures.

---

### Post by AndyOpie150 on 2013-03-30
As far as the "cant boot from USB" problem: If the computer has the option in the BIOS but just doesn't seem to boot into USB drive even with it placed in the top of the order then try Plop Boot Manager. It allowed my ten year old machine to install distros from my flash drive. I made sure I selected the Windows Boot install script which gave me two options in the grub menu, Windows and Plop. 
After picking Plop it takes me to it's screen where I now have the option to boot into anything listed in the BIOS without having to manipulate the order in the BIOS.

---

### Post by oldfred on 2013-03-30
I agree with agillator.

And one of the most common reasons for file corruption is power failure. We have seen users with many reasons for power failure including, dog, cat, foot, brother, sister, no battery as well as the usual power company or lighting. And unless moving partitions or a major upgrade a fsck will usually fix a journaled file system.

---

### Post by SPMcKinney on 2013-03-30
***Forgot to mention but I'm sure its more than clear I'm still a newb at Linux***

> **dabl said:**
> ...
Thanks for the site on Parted Magic I've heard good things about it rather have a Live CD in case something does happen to her computer.

> **agillator said:**
> ...
Ahh I assume that was the intention of when he partitioned it like that and the pictures are no big deal as she nabs them off Facebook anyways lol. With the mounting of the drives I have an administrator account to handle updating and what not but I am unable to mount a drive where it is mountable when logged into her account.

> **AndyOpie150 said:**
> ...
It doesn't have the option to boot usb at all in the bios, I have tried Plop Boot Manager on my older computer but never got it to work.

---

