---
title: "Does Ubuntu installation format drive?"
date: 2008-05-22
forum: General Help
---

### Post by nubyrchrd on 2008-05-22
My friend has a virus-infested xp computer. I am going to help him try to install ubuntu today. The live cd does not recognize his hard drive - he gets an error message. Will installation solve this? Will installation wipe the drive clean, or must I format the drive first from the windows disc?

---

### Post by housam on 2008-05-22
Yes the installer will format the entire disk when choosing " use the entire disk ".

---

### Post by bingoUV on 2008-05-22
1. What is the error message for the hard drive?

2. Do you want to wipe the hard drive clean? It is easily possible (I think it is even default). You could try other options like shrinking windows partition, and creating other partitions to install Ubuntu. Then you could boot into either of them, choose at the beginning of the boot process.

First get the live CD running though. Its inability to boot might be a sign of the hardware being unrecognized, which generally means trouble for new linux users and fun for experienced ones.

---

### Post by wdaniels on 2008-05-22
You have the option to format or not. But I think you will need an ext partition at least for root, so if there is not already some unallocated space to create one, you will need to be able to shrink the Windows partition to make room (carefully :D).  But you need to expand on what you mean by the "live cd does not recognize his hard drive"? It has to at least see it as a device, or you will get nowhere fast. Use:

```
sudo fdisk -l
```

...to check this. If it just can't read the partition table or mount the Windows partition(s) then you may need to dump the whole lot. But if XP is still booting etc. then that shouldn't be the case.

Honest answer, without wanting to offend, you don't really seem to know enough about this to start taking any risks based on what you think the installer is going to do. I'm sure your friend won't thank you for trashing all his data, so if at all possible, back everything up first. And best of luck!

---

### Post by Rinzwind on 2008-05-22
> **nubyrchrd said:**
> My friend has a virus-infested xp computer. I am going to help him try to install ubuntu today. The live cd does not recognize his hard drive - he gets an error message. Will installation solve this? Will installation wipe the drive clean, or must I format the drive first from the windows disc?

Depends on the problem with the live cd.

The live cd is meant to test your hardware. When it fails and it is hardware related you might be in trouble getting Linux installed. 

Btw: can't you format the disc the windows installation cd?

---

### Post by nubyrchrd on 2008-05-22
> **housam said:**
> Yes the installer will format the entire disk when choosing " use the entire disk ".

Thank you.

---

