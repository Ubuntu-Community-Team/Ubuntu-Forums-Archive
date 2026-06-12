---
title: "Slow startup after deleting swap"
date: 2018-08-17
forum: General Help
---

### Post by checoimg on 2018-08-17
I'm using and SSD and wanted to get rid of Swap partition, erased the swap partitio and erased the line on /etc/fstab for this swap partition. Now when I boot up my laptop it takes a long time to start as compared to what I'm used to with this same SSD.

---

### Post by RichardLinx on 2018-08-18
That's kind of interesting. Might you consider creating a new swap partition and seeing if it rectifies the issue?

---

### Post by checoimg on 2018-08-19
> **RichardLinx said:**
> That's kind of interesting. Might you consider creating a new swap partition and seeing if it rectifies the issue?

I tried, didn't fix it

---

### Post by tea for one on 2018-08-19
> **checoimg said:**
> I tried, didn't fix it

You have to verify that the UUID of the new swap is the same UUID in /etc/fstab.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

As a matter of interest Ubuntu 18.04 now uses a swapfile folder rather than a swap partition. I suspect that this helps prevent the problem you are trying to solve.

However, I do not know Ubuntu Mate at all so I could not advise if a swapfile folder would help.

Good luck

---

### Post by checoimg on 2018-08-22
Ok, I had the quotes on UUID, after fixing fstab the boot time was better but now I know I don't need a swap partition. Should I get ird of the swap partition again?

---

### Post by checoimg on 2018-08-22
Just tested commenting out the fstab line for the swap parition and the boot time was the same so it is unrelated to swap.

---

### Post by HermanAB on 2018-08-22
You can run without swap space until the day you open the 2001st tab in your browser and then the machine will just kind of stop...

A swap file costs nothing.  Read ‘man swapon’ for details.  It is a very good man page and tells everything you need to know.

---

### Post by checoimg on 2018-09-21
Hey thanks everyone, I am using a swap partition and it has been some time since I don't have slow boots

---

### Post by tea for one on 2018-09-24
> **checoimg said:**
> Hey thanks everyone, I am using a swap partition and it has been some time since I don't have slow boots

Splendid - can you mark the thread as solved to help other users with a similar dilemma?

---

### Post by JonPaul on 2018-10-17
I just had exactly this problem. I had a second hdd which had the swap on it. I removed that hdd and created a swap file on first disk. Boot takes 30 seconds longer. systemd-analyze says the delay is in the kernel. I discovered I had a file called resume in /etc/initramfs-tools/conf.d/ which contained the UUID of the deleted swap file. I deleted that file and boots fine now...

---

