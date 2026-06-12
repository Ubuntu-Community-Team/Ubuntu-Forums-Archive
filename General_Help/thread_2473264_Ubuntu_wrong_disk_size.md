---
title: "Ubuntu wrong disk size"
date: 2022-03-30
forum: General Help
---

### Post by eduramosaldana on 2022-03-30
Hi everyone, This is the first time I use Ubuntu and this forum, I hope you can help me.. so I have a problem, I had windows 8.1 installed then I try to make a clean Ubuntu Install "20.04.4 LTS" in my 320 Gb notebook Harddrive as you can see in the image
[[img]https://i.postimg.cc/9RTzPgpk/Captura-de-pantalla-de-2022-03-29-22-02-27.png[/img]](https://postimg.cc/9RTzPgpk)
But when I open "Gparted" tool it show me a 290 Gb space only as the image. [[img]https://i.postimg.cc/SJzqnYgZ/Captura-de-pantalla-de-2022-03-29-22-01-57.png[/img]](https://postimg.cc/SJzqnYgZ)
The problem is when I try to ReInstall Windows 8.1 again the installation wizard show me the partitions that Gparted show me before and not the real harddrive size... [[img]https://i.postimg.cc/SnDZqDcH/20220329-230119.jpg[/img]](https://postimg.cc/SnDZqDcH)

I try to delete all partitions from windows wizard install and reinstalled windows and it still show me 290 Gb.
I try to delete all partitions from ubuntu too and format my 320 gb from Disk utility

I dont know what to do , thanks for you help

---

### Post by deadflowr on 2022-03-30
All sizes are right.
Windows installer and Gparted show the sizes in gibibyte, as opposed to Disks which shows the sizes in gigabytes.

---

### Post by eduramosaldana on 2022-03-30
Thank you this is the first time I read about gibibytes xd

---

### Post by QIII on 2022-03-30
Note that your image actually shows about 298GiB and a bit of change when you add all three partitions.

Disk manufacturers engineer their products in multiples of 1000, because that is how mechanical engineers think.   So for them a kilobyte is 1000 bytes.  That makes a GB 1000*1000*1000 = 1,000,000,000

But that's not the way computers "see" numbers.  They think in terms of bits (0s and 1s) forming bytes.  To "talk" to computers in their binary world, we use a KB as 1024 bytes. A GiB happens to be 1024*1024*1024 = 1,073,741,824

A GB is roughly 93% of a GIB.  320 * 0.93 is approximately 298.  I'm not going to look at the ratios to 10 decimal places, so that'll have to do.

So, your 320 GB disk provides roughly the same amount of storage space as a 298GiB disk.

---

