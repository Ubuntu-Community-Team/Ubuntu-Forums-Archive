---
title: "HD Partition"
date: 2006-11-06
forum: General Help
---

### Post by TheLoneMan on 2006-11-06
A few days ago, I began a fresh install of Ubuntu 6.10. I used the slider to partition my hard drive (50%), and then the installer partitioned my hard drive and I got to the final screen where you look over all of the options you chose. At this point, I urgently needed to go, and I had to use my laptop for the next class, so I exited the installer and turned off the computer, ejecting the disc and then rebooting to Windows XP Professional.

Now, however, when I try to install Ubuntu 6.10 again, the slider doesn't show up, but instead the choices "Partition hard drive manually", "Erase entire hard drive", and "Use largest continuous free space". The slider is nowhere to be found.

Also, in Windows XP Professional, when I right click on my hard drive icon, it shows me that my hard drive's total capacity for Windows is 32.5 GB, however I used to have a total capacity of 80 GB.

I can infer from this information that the Ubuntu installer successfully partitioned my hard drive. I am wondering, however, if there is any way to access the partition that was created, and how to install to it. Also, can I use this partition to install Kubuntu 6.10 or Kubuntu 6.06.1? Because after more reading I have decided that Kubuntu seems like the better choice for me.

Thanks in advance for anybody who might be of help, sorry for the long post.

Cheers!

---

### Post by TheLoneMan on 2006-11-06
Bump :KS

---

### Post by Stochastic on 2006-11-06
From the sounds of it, the Windows partition was successfully resized and windows is fuctioning, correct?  If that's the case then you should have a chunk of free space at the end or beginning of the drive (probably end).  You can check this without going through the install process by opening the Gnome Partition Editor in the Live CD (this software maybe different for Kubuntu live CD, possibly QTParted).

If that's the case, then simply choose 'Manually Edit the Partition Table' or 'Partition the Hard Drive Manually' (whichever way it's worded).  This should bring up the partition editor, just double check the layout is how you'd like - with a swap partition and a main partition for Ubuntu - then continue onto the next step where it will most likely ask you which partitions to use where in the system.

Let us know if that works for ya.

---

### Post by TheLoneMan on 2006-11-07
OK, excuse the nubliness, but how do I manually partition the hard drive?

How do I designate a Swap partition and a main one, and what kind do I use (ext3, ext4, linux-swap, etc.)?

As detailed as instructions as possible, because I have absolutely no experience with partitions. This is for a fresh install of Ubuntu 6.06.1.

Thanks so much!

Cheers!

---

### Post by TheLoneMan on 2006-11-07
Bump ](*,)

---

### Post by TheLoneMan on 2006-11-07
Double-bump?

---

### Post by bg1256 on 2006-11-07
> **TheLoneMan said:**
> OK, excuse the nubliness, but how do I manually partition the hard drive?

How do I designate a Swap partition and a main one, and what kind do I use (ext3, ext4, linux-swap, etc.)?

As detailed as instructions as possible, because I have absolutely no experience with partitions. This is for a fresh install of Ubuntu 6.06.1.

Thanks so much!

Cheers!

Okay, it's really not as difficult as it seems.

First thing we would need to know is:
did you successfully resize your Windows partition?  And do you have a free chunk of hard drive space?

If so, then it's very simple.

You need to create a swap partition, and you can simply right click on the free space and select resize.

The recommended swap size is roughly double your RAM.  For example, I have a laptop with 512 MB of RAM, so I created a 1 GB swap.

After that, you should still have free space remaining.  Make that your root partition, and you should be good to go!

---

### Post by TheLoneMan on 2006-11-08
But how do I designate one as the swap partition and one as the root partition? That's my last question and then we can all go home.

---

### Post by bforbes on 2006-11-08
Which program are you using?

---

### Post by TheLoneMan on 2006-11-08
The 5th step of the Ubuntu 6.06.1 installation :P.

---

### Post by bforbes on 2006-11-08
From memory when you create the partition, there's a dropdown box for partition types. Swap is listed there. Can you screenshot it?

---

