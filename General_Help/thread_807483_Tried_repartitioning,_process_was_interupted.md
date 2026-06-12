---
title: "Tried repartitioning, process was interupted"
date: 2008-05-25
forum: General Help
---

### Post by werg on 2008-05-25
I was repartitioning my hard drive through the Gutsy Live CD (particularly, I was shrinking my ubuntu installation to make up space for a Windows installation). During the process, ubuntu strangely logged off and this stopped the shrinking process. I've rebooted and everything seems to work fine on my Ubuntu installation, and it is as if the the shrinking process actually ended, looking at what gparted now shows me. So what exactly happened, and what do I ought to be doing right now? Is it safe to install Windows on the apparently free space?

---

### Post by cariboo on 2008-05-25
If you've got enough space go ahead. Remember when you install windows it will over write the MBR and you won't have access to Ubuntu until you update grub.

---

### Post by werg on 2008-05-26
What I'm afraid of is that some of the files on my ubuntu installation weren't actually moved, and so that 'free space' could in reality not be free space at all, as there could be some files on it. Installing windows would then remove these files and damage the ubuntu installation (let alone cause the loss of valuable files). Is this a possibility?

---

### Post by housam on 2008-05-26
take a screen shot of gparted image and post it please.
also post the results of 
```
sudo fdisk -l
```
where -l is a small L

---

### Post by werg on 2008-05-26
Here's what I get:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8af0c27b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10088    81023827+  83  Linux
/dev/sda2           23569       24321     6048472+   5  Extended
/dev/sda5           23569       24321     6048441   82  Linux swap / Solaris


I've attached a screenshot.

---

### Post by werries on 2008-05-26
i really suggest backing up your data, documents, etc. just all your essential files. but i dont know about anything else at this point. i dont think theres anything on that unallocated space, but still, save your stuff on an external place.

---

### Post by strabes on 2008-05-26
Just reinstall windows on the empty space and then reinstall grub using the process detailed in the link in my signature.

---

