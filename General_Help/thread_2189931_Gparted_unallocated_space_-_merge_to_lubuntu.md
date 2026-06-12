---
title: "Gparted unallocated space - merge to lubuntu"
date: 2013-11-24
forum: General Help
---

### Post by davidafranklin on 2013-11-24
Hello,

I have shrunk Win 7 so I now have 19.53 GB of free space that I want to merge with my exisitng Lubuntu.

My partitions are:
- Windows system reserved, sda1, ntfs
- Windows, sda2, ntfs
- Unallocated pace (19.53 GB)
- Lubuntu /dev/sda3 (26.70 GB) extended:
        - sda6 (lubuntu 24,77 GB) - ext4
        - sda5 (only 957mb) - linux swap

I am on a live cd, I can format resize the unallocated partion but there are not options to merge it. I needs to move the space to the lunbuntu partition withci at the right of the empty space.

Can someone help?
Thanks

---

### Post by oldfred on 2013-11-24
You will have to move partition left. You need a good backup as any power failure or interruption will corrupt system. It usually works, but it seems to know if you do not backup and then that is the only time it does not work. :)

You have to move extended partition left into the unallocated space. And run that change with check mark. Then you have the unallocated inside the extended partition and can move sda6 left.

---

### Post by davidafranklin on 2013-11-24
If I select sda6, i can onlyrelease about 1285 MB to its right. I ran it, then it gave me an error message and nothing happened. I "unmount" and everything was back to the way it was.

---

### Post by davidafranklin on 2013-11-24
here a screenshot

Sorry, can upload an image!

---

### Post by oldfred on 2013-11-25
Use screenshot so it is small and in advanced editor use the paperclip icon.
Occasionally it may say it is too large even when not, just try again later.

did you move start of sda3 left first?
You have to run from live installer as all partitions have to be unmounted including swap. Often live installers mount swap, so click on it in gparted and right click unmount.

---

### Post by davidafranklin on 2013-11-25
I was not able to do anything. I was using gparted from my live cd and it did mot offer me to "unmount" the partitions.
I formatted the partition in NFTS so it allows me to use it as an external drive.
I do think that Gparted need to be much easier.  am a beginner and between sda... ext... mount and unmount, have the space after the partition instead o before./..it is not very clear and I hope Ubuntu will be easier in the future in order to compete with Windows.
Thanks again.
Regards

---

### Post by westie457 on 2013-11-25
A bit late now but would this have helped you?

[http://ubuntuforums.org/showthread.php?t=2189997](http://ubuntuforums.org/showthread.php?t=2189997)

---

### Post by Mark Phelps on 2013-11-25
> I do think that Gparted need to be much easier.

While I agree, this has nothing whatsoever to do with Ubuntu.  GParted is a partitioning tool, and has an appearance much like ALL the other partitioning tools, including Windows tools.

If you don't know how to use a partitioning tool, you should ask for help with specific concerns -- before you use it.

---

