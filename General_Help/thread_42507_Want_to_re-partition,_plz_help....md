---
title: "Want to re-partition, plz help..."
date: 2005-06-17
forum: General Help
---

### Post by stufff on 2005-06-17
Hello All,
I am a Ubuntu nubie.  I have the following issue:

I have a laptop running Windows XP.  I partitioned it using a Windows partitioner. 
I installed Ubuntu.
At first, I was skeptical about linux.  But now, Ubuntu is my primary OS!!!!


The problem is that I allocated _**ONLY 5 GB to Ubuntu in my 60GB Hard drive**_.  Now, I want to **RESIZE** it to at least 15 GB.  

[U]BUt, I dont want to screw up my Windows XP AND Ubuntu installs.
[/U]

Any ideas?
Thx.
Stufff...

---

### Post by Dogmeat on 2005-06-17
What's your XP filesystem? if it's NTFS you can try getting ntfsprogs with apt-get, it has a tool called ntfsresize that does exactly what you want. I used it myself and had no problems. Go to XP and defragment it as much as possible, you need to have 10GB free space in the end of the partition, then go to Ubuntu and use ntfsresize. You should read it's docs to be sure you won't do something wrong. After it exits successfully, you will have to erase the XP partition with fdisk and create it again with the new size. Then just get a live cd or something and move your ubuntu partition to the bottom of the XP partition, and resize it. That is, if your partitions are looking like this now: 

```
[XP       60GB             ][Ubuntu  5GB][Swap]
```

They will look like this:

```
[XP       50GB        ][Ubuntu    15GB][Swap]
```

I recommend you check [this site](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html) out, and good luck  ;-) 

If you're using FAT, then I'm sorry but I can't help you as I haven't used a fat partition in quite a while but you should be able to find some equivalent programs somewhere!

---

### Post by intangible on 2005-06-17
You'll want to look into a Live CD with qtparted or gparted, you can't resize a mounted partition unfortunately.
The commercial product "Partition Magic" is more flexible and easier to use (and you can use it from inside Windows), but, it's not free.

---

### Post by stufff on 2005-06-18
[QUOTE=Dogmeat]What's your XP filesystem? if it's NTFS you can try getting ntfsprogs with apt-get, it has a tool called ntfsresize that does exactly what you want. I used it myself and had no problems. Go to XP and defragment it as much as possible, you need to have 10GB free space in the end of the partition, then go to Ubuntu and use ntfsresize. You should read it's docs to be sure you won't do something wrong. _[COLOR=Red]After it exits successfully, you will have to erase the XP partition with fdisk and create it again with the new size.[/COLOR]_ Then just get a live cd or something and move your ubuntu partition to the bottom of the XP partition, and resize it. That is, if your partitions are looking like this now: 

```
[XP       60GB             ][Ubuntu  5GB][Swap]
```

They will look like this:

```
[XP       50GB        ][Ubuntu    15GB][Swap]
```

I recommend you check [this site](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html) out, and good luck  ;-) 

If you're using FAT, then I'm sorry but I can't help you as I haven't used a fat partition in quite a while but you should be able to find some equivalent programs somewhere![/QUOTE]

Thanks for the detailed explanation, Dogmeat... but will this not destroy my XP?  Yes, my XP is NTFS.
TIA for reply.

---

### Post by stufff on 2005-06-18
[QUOTE=intangible]You'll want to look into a Live CD with qtparted or gparted, you can't resize a mounted partition unfortunately.
The commercial product "Partition Magic" is more flexible and easier to use (and you can use it from inside Windows), but, it's not free.[/QUOTE]

Yep, intangible, I have a copy of PM with me.  I think I will use that to down-size XP by 10G and create a new linux partition for 10G. 
Will probably use this for my linux data..  :smile:

---

### Post by Dogmeat on 2005-06-18
[QUOTE=stufff]Thanks for the detailed explanation, Dogmeat... but will this not destroy my XP?  Yes, my XP is NTFS.
TIA for reply.[/QUOTE]

No it won't, I was scared too at first, you just have to recreate it with fdisk EXACTLY as it was before, with everything equal but the new size (including enabling boot flag, and start the partition on the same sector as the previous partition). Also make sure you make it the exact same size as what ntfsresize said. 

[QUOTE=http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.8.html]**SHRINKAGE**

    If you wish to shrink an NTFS partition, first use ntfsresize to shrink the size of the filesystem. Then you may use fdisk(8) to shrink the size of the partition by deleting the partition and recreating it with the smaller size. But be careful, do not make the partition smaller than the new size of the NTFS filesystem otherwise you won’t be able to boot and you might lose your data.[/QUOTE]

But since you have PM, you might as well use it!

---

