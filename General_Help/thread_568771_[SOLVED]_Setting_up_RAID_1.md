---
title: "[SOLVED] Setting up RAID 1"
date: 2007-10-06
forum: General Help
---

### Post by theelk801 on 2007-10-06
Here's the deal. I recently built a new computer with a motherboard that has a built in RAID controller and 2 160gb hard drives that I would like to have in a RAID array. I already did it in the BIOS, but I apparently need to install software, too. How can I do that if I have my OS installed already. Oh, and as a side note, should I use RAID 0 or 1? I want the extra space, but I don't know if it's worth the decreased liability...

---

### Post by fjgaude on 2007-10-06
Well, so many options. Linux has what is called dmraid that will recognize motherboard raid setup software.

How old is your motherboard, your two drives? What version of Ubuntu?

What raid is it you have, Silicon Images, Intel, nVidia, VIA?

---

### Post by lintoon on 2007-10-06
RAID 0 stripes the data across both drives and delivers better performance whereas RAID 1 mirrors the data onto both drives.  RAID 0 will give you the full storage capacity of your drives.  RAID 1 will give you 50% storage with 2 drives (2x160Gb = 160Gb with RAID 1).  If 1 drive fails in a RAID 0 system the array becomes useless.  If 1 drive fails in RAID 1 your data is safe on the other drive.
It's a choice between performance or redundancy.  If you want performace go for RAID 0.  If you want your data to be safer go for RAID 1. 

This link should explain it better than me.

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by theelk801 on 2007-10-07
I know what they both mean. I was just wondering if I should worry too much about how safe my data is. Anyway,  [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128012R&Tpk=ga-965p-ds3")'s my motherboard info.
I'm using feisty fawn, and the two drives are [here]("http://www.newegg.com/Product/Product.asp?item=N82E16822136075")
The problem is, how am I supposed to set up RAID if I already installed the OS?

---

### Post by fjgaude on 2007-10-08
Okay, Ubuntu is setup. Make sure you have mdadm installed.

> sudo apt-get install mdadm

Then get the man page for it, man mdadm.

Study the area to create an array. It goes like this:

> sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda[ab]1


This will create the array as raid1, mirror; --level=0 would be stripped. You of course booted from some drive other than sda1 or sdb1.

---

### Post by dstomov on 2007-10-08
mdadm will create software raid. i have similar problem. my raid controler is promise fasttrakck. i want to set it without mdadm, because when i created raid1, and when i started to copy large files of data, my kernel failed.i coudn`t even reboot in normal way. please if somebody knowes how it can be donel tell us.

---

### Post by fjgaude on 2007-10-08
> **dstomov said:**
> mdadm will create software raid. i have similar problem. my raid controler is promise fasttrakck. i want to set it without mdadm, because when i created raid1, and when i started to copy large files of data, my kernel failed.i coudn`t even reboot in normal way. please if somebody knowes how it can be donel tell us.

Is your raid1 your boot disk? Likely not... unless Promise has a driver that works under Ubuntu Linux.

Large files shouldn't be a problem... are you sure your disks are not full, or in poor shape?

---

### Post by dstomov on 2007-10-09
yes my raid1 is not my boot disk and i am using new very empty disks :), but unfortunately the driver on promise store is for kernel 2.4.,but i have ubuntu with kernel 2.6 :( and i cannot make the driver
 or may be i am missing something

---

### Post by fjgaude on 2007-10-09
> **dstomov said:**
> yes my raid1 is not my boot disk and i am using new very empty disks :), but unfortunately the driver on promise store is for kernel 2.4.,but i have ubuntu with kernel 2.6 :( and i cannot make the driver
 or may be i am missing something

Okay, there is a Linux program that recognizes such arrays. It's called dmraid and can be installed using apt-get or Synaptic.

```
sudo apt-get install dmraid
```

After install use the man page to get some idea what it does, man dmaid.

Then try

```
dmraid -l
```

```
sudo dmraid -r
```

From there you will now know what your array is called.

You mount the array to your chosen mount-point like so:

```
sudo mount /dev/mapper/pdc_abcdefgxxx /mount-point
```

where the "abcdefgxxx" is whatever you got from the -tay command and the "pdc" is the code for your Promise controller.

Let us know how you do.

---

### Post by dstomov on 2007-10-09
yes \\:D/
after installing dmraid , this tool recognize the promise controler and
i can manage /dev/mapper/pdc_gjbee.....

 10Q very much

---

### Post by fjgaude on 2007-10-09
Wow, congratulations! Please mark this post [SOLVED] using the Thread Tools at the top of the message.

---

### Post by dstomov on 2007-10-10
i solved my problem :guitar:, but the thread must be edited by theelk801

---

### Post by jackfusion on 2007-10-26
I have two promise devices and only one is being displayed how do I figure out which one is being displayed when I do```
sudo dmraid -r
```?
 I have an on board one and a PCI Card. 

Mods please delete or forget about this please.

---

