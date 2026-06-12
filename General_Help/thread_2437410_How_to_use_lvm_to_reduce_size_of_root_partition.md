---
title: "How to use lvm to reduce size of root partition"
date: 2020-02-23
forum: General Help
---

### Post by frankvw on 2020-02-23
I've just installed Lubuntu on my old Samsung NC10 netbook and so far I'm quite impressed how well it works on such an old bitty box. Sylpheed is a bit unstable at times, but I understand that's a work in progress so I'm not too worried yet.

However, in my wisdom I decided to use logical volumes when installing Lubuntu, something I have never done before but, given the limited amount of disk space, I thought might be a good idea here. However, Lubuntu has now been installed all on a single root partition that spans the entire harddisk.

Output of 'pvs' command:
```

  PV         VG         Fmt  Attr PSize    PFree 
  /dev/sda1  lubuntu-vg lvm2 a--  <149.05g 40.00m

```

Output of 'vgs' command:
```

  VG         #PV #LV #SN Attr   VSize    VFree 
  lubuntu-vg   1   2   0 wz--n- <149.05g 40.00m

```

Output of 'lvs' command:
```

  LV     VG         Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   lubuntu-vg -wi-ao---- 148.05g                                                    
  swap_1 lubuntu-vg -wi-ao---- 976.00m

```

I want to resize the root partition to about 30GB (currently less than 4 GB is in use) and assign the space thus freed to a new volume to be mounted on /data.

I have never done this with logical volumes, and I'm worried about nuking my entire system, since lvm appears to be a tool that can move mountains or take off both your legs at the knees with equal facility. Having gone through manpages I've seen a lot on the various command line options (lvchange, lvresize, lvreduce) but I'm not too clear on what to do in which order, 

My questions:

1. Is there a good how-to or walk-through anywhere on how to do the above? I have Googled extensively but have not found an "easy" solution that simply outlines the steps involved.
2. Is there a GUI tool to do this on Lubuntu?
3. Since this is the root partition, must I reboot from the distro USB stick (using the try-without-installing option) as I would have to if this were a physical root volume? Or does the fact that this is a logical volume mean I can do it on a running system? (I doubt it, but who knows.)

All suggestions appreciated! 

// FvW

---

### Post by TheFu on 2020-02-23
boot from Try Ubuntu, install LVMtools, if needed, activate the VGs, then resize any LV you like.  Probably want to make the swap LV 4.1G while you are there.

```
sudo vgchange -ay
sudo lvresize  --resize-fs     -L -120G /dev/mapper/to-the-lv-device-name
```

 /dev/mapper/to-the-lv-device-name will be some combination of the vg-name and the lv-name.

Some helpful manpage options:
```
       -L, --size [+|-]LogicalVolumeSize[bBsSkKmMgGtTpPeE]
              Change  or set the logical volume size in units of megabytes.  A
              size suffix of M for megabytes, G  for  gigabytes,  T  for  terâ
              abytes, P for petabytes or E for exabytes is optional.  With the
              + or - sign the value is added or  subtracted  from  the  actual
              size  of  the logical volume and rounded to the full extent size
              and without it, the value is taken as an absolute one.
....
       -r, --resizefs
              Resize  underlying  filesystem  together with the logical volume
              using fsadm(8).

```

For the swap, just delete the LV, recreate it using **lvcreate** a new one 4.1G size and use **mkswap**.

Probably want to create an LV for /home.  The trick with LVM is to size for known needs the next 3 months.  Resizing up on an active, mounted, LV is 5 seconds, but only if there is unused space in the VG. [https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987) is my layout on an SSD.  For longer SSD life, having 20% unused drastically helps.

No GUI that can be trusted exists for LVM work.

---

### Post by EuclideanCoffee on 2020-02-23
Using a disk boot, go to the terminal and try the following.

1. Make sure root is unmounted.
2. e2fsck -f /dev/mapper/lubuntu-vg
3. resize2fs /dev/mapper/lubuntu-vg 30G
4. lvreduce -L 30G /dev/mapper/lubuntu-vg

It should return 30G in df -h.

Good luck.

---

### Post by frankvw on 2020-02-24
You, sirs, rock! This got me sorted. Thank you so much!!

---

