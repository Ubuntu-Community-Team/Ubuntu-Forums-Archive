---
title: "i try to use ubuntu for the recovery my hdd folders but i cant acess to hdd"
date: 2014-06-17
forum: General Help
---

### Post by atakan2 on 2014-06-17
i create live usb stick and start using in my crashing leptop(prepare automatic repair loop) when i try to access my hdd folder i cant access it this error massage

---

### Post by Mark Phelps on 2014-06-17
You can't mount your hard drive because Windows 8 uses a new form of hibernation by default that keeps the filesystem mounted even after you've shut it down.

If you ever get it working again, you would have to disable FastStartup to turn off the hibernation.

But until then, you will not be able to mount the drive in Linux.

---

### Post by atakan2 on 2014-06-17
how i shut it down win8 i cant access win8

---

### Post by atakan2 on 2014-06-19
how i save my folders

---

### Post by Mark Phelps on 2014-06-19
Sorry to keep saying this -- but you can NOT fix this problem using Linux.

Your best bet , at this point, would be to post the problem on a Windows 8 forum (eightforums.com is an example).  They know how to deal with Win8 problems and there may be some way to boot your PC using a CD or USB so that you can disable FastStartup and then mount the NTFS partition in Linux.

---

### Post by The Cog on 2014-06-19
The eror message says that you can only mount the drive read-only, which should be enough to be able to copy your files off to an external USB drive. But the GUI utility is trying to mount it read-write so you will have to mount it by command line instead. Try this command:
```
sudo mount -o ro /dev/sda5 /mnt
```
If that works, your files should be visible in /mnt and you should be able to copy them off.

---

### Post by atakan2 on 2014-06-19
thank you i can i find my folder but i want to ask some thing.i think my leptop had crashed for the some virus if i copy my folder to extarnal hdd it is effect my other folder because i have 500 gb folders in my external hdd

---

### Post by The Cog on 2014-06-22
Sorry for the delay in answering but I've been busy. I think that if you copy the hard disk files to the external hard disk, then there is the possibility that you will copy some files infected by a virus. But then if you've already had that external drive connected to that computer you are not really making much difference. I would think that at this stage, the important thing is to rescue your data - you can run a virus scanner over it later.

---

### Post by uRock on 2014-06-22
If you can download and burn their download to disk, then this may help. [http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

---

