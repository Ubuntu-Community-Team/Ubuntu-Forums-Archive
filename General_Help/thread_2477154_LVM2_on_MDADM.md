---
title: "LVM2 on MDADM"
date: 2022-07-15
forum: General Help
---

### Post by rsteinmetz70112 on 2022-07-15
Earlier today I had some kind of a failure and one of my MD Arrays (level 1) went away. I was able to recover the mddevice but so far I haven't been able to recover the Pv, vl a or VG. I'm pretty sure they're still there so any help would be useful. 

```
vgcfgrestore backup
  WARNING: Couldn't find device with uuid C6UTtx-omjQ-hcNw-N8Vd-hxwy-1Yed-uT7PMc.
  Cannot restore Volume Group backup with 1 PVs marked as missing.
  Restore failed.

```

```
 pvcreate --test --uuid "C6UTtx-omjQ-hcNw-N8Vd-hxwy-1Yed-uT7PMc" /dev/md12
  TEST MODE: Metadata will NOT be updated and volumes will not be (de)activated.
  --restorefile is required with --uuid

```
```
 pvcreate --test --uuid "C6UTtx-omjQ-hcNw-N8Vd-hxwy-1Yed-uT7PMc" /dev/md127 --restorefile /etc/lvm/backup/backup
 TEST MODE: Metadata will NOT be updated and volumes will not be (de)activated.
 WARNING: Couldn't find device with uuid C6UTtx-omjQ-hcNw-N8Vd-hxwy-1Yed-uT7PMc.
WARNING: ext4 signature detected on /dev/md127 at offset 1080. Wipe it? [y/n]: n
  Aborted wiping of ext4.
 1 existing signature left on the device.

```
I'm not clear if the uuid needed is the uuid for the PV or if it's the UUID for the underlying device /dev/md127.



I do have backups but I'd prefer to recover if I can.

---

### Post by #&amp;thj^% on 2022-07-15
See if this helps, I refer to it a few times a year: [https://www.golinuxcloud.com/recover-lvm2-partition-restore-vg-pv-metadata/](https://www.golinuxcloud.com/recover-lvm2-partition-restore-vg-pv-metadata/)
And kudos for having backups.

---

### Post by rsteinmetz70112 on 2022-07-16
Thanks I found that one. I was concerned that none of the examples included this warning and how to deal with it.:
```
WARNING: ext4 signature detected on /dev/md127 at offset 1080. Wipe it? [y/n]: n  Aborted wiping of ext4.
```

I have recreated the PV and restored the VG but now I can't mount them. I'm getting this error:
```
# mount: /files: wrong fs type, bad option, bad superblock on /dev/mapper/backup-files, missing codepage or helper program, or other error.

```

lvdisplay shows this for the restored VG.

```
 WARNING: Device /dev/md0 has size of 1953257472 sectors which is smaller than corresponding PV size of 1953259520 sectors. Was device resized?
  WARNING: One or more devices used as PVs in VG backup have changed sizes.
  --- Logical volume ---
  LV Path                /dev/backup/files
  LV Name                files
  VG Name                backup
  LV UUID                IBkKF6-Tdj8-D49Y-dK2P-l5dt-d5pW-NsbcZA
  LV Write Access        read/write
  LV Creation host, time romulus, 2018-05-06 15:48:50 -0500
  LV Status              available
  # open                 0
  LV Size                465.69 GiB
  Current LE             119217
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:7


  --- Logical volume ---
  LV Path                /dev/backup/home
  LV Name                home
  VG Name                backup
  LV UUID                a7V2iM-uNKd-1Cht-v1D1-Cg3X-IItf-TNvO9i
  LV Write Access        read/write
  LV Creation host, time romulus, 2018-05-06 15:49:08 -0500
  LV Status              available
  # open                 0
  LV Size                465.69 GiB
  Current LE             119217
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:8

```

I ran 

```
# lvmdiskscan


  /dev/md3    [    <931.39 GiB] LVM physical volume



```
But no md0, which seems odd.

---

### Post by rsteinmetz70112 on 2022-07-16
OK, I've got it restored and everything seems to be working for now. I am a little concerned I may have a hard drive problem which caused the initial problem. I'll monitor it for a while before marking it solved.

---

### Post by DuckHook on 2022-07-16
> **rsteinmetz70112 said:**
> OK, I've got it restored and everything seems to be working for now. I am a little concerned I may have a hard drive problem which caused the initial problem. I'll monitor it for a while before marking it solved.
I'm probably missing something obvious, but, why both MDADM and LVM? Isn't this redundant? I've never run a server that way, but my understanding is that it greatly increases system fragility.

---

### Post by #&amp;thj^% on 2022-07-17
> **DuckHook said:**
> I'm probably missing something obvious, but, why both MDADM and LVM? Isn't this redundant? I've never run a server that way, but my understanding is that it greatly increases system fragility.
I'm glad you mention this, I felt the same.
But I feel rsteinmetz70112 is a seasoned hand at this, so I kept my pie-hole closed.:o
EDIT: The more I think about this though,  LVM can create logical volumes that are backed by a software RAID. You still get all the fancy bits of LVM, though. Like the ability to move which physical disk is holding the stripes of your RAID. Afaik

---

### Post by rsteinmetz70112 on 2022-07-17
When I set this up originally back in 2006-7 (the hardware has since been migrated multiple times), I don't believe lvm was able to do raid on its own. 

It's been my understanding that the lvm2 raid calls the same code and libraries that mdadm uses for raid. I also somewhat prefer the way md devices are presented, possibly because I'm used to it. I don't believe in moving things between hard drives since I typically use only RAID 1 to provide some protection against disk failures. I use mdadm to manage the raid arrays of physical disks and then use lvm2 to manage the volume groups inside the arrays. 

As for system fragility, I've not had any experience with that, this being the first serious problem in all this time. If you could point me to some information on that I'd be interested.

---

### Post by #&amp;thj^% on 2022-07-17
That's why I added your a seasoned user, and depending who you ask you'll likely get different responses.
LVM-RAID is actually mdraid under the covers. It basically works by creating two logical volumes per RAID device (one for data, called "rimage"; one for metadata, called "rmeta"). It then passes those off to the existing mdraid drivers. So things like handling disk read errors, I/O load balancing, etc. should be fairly mature.
I think and I'm assuming that DuckHook is just mentioning this is "redundant".
We all do things a bit different is all, and if it's not broke don't fix it. :)
For just myself i prefer LVM.

---

### Post by TheFu on 2022-07-17
In the olden days, it was common for mdadm and lvm to be layered for a solution.  Really, only in the last 5 yrs has LVM's RAID capabilities been to the point that mdadm isn't needed.

As I have 1 system with mdadm, but it doesn't use LVM, I can't help with recovery efforts, sorry.
My newer systems are all LVM with a few key areas setup for RAID under LVM control.  I spend much more time with backups, since those are 1000x more important than RAID and are needed regardless.  

On my VM hosts, I stopped using RAID when all the VMs were put onto SSDs.  The failure rates for SSDs are so low that enterprise RAID/SSD vendors actually don't suggest it anymore, unless the client just wants to spend 2x the money. Many do and they are happy to take the money.  I have a buddy who works in the enterprise caching RAID controller industry. I started taking his advice about 4 yrs ago.  He's very clear about using quality SSDs, not the cheapo desktop kind that many people buy, however.

---

### Post by DuckHook on 2022-07-17
> **rsteinmetz70112 said:**
> …As for system fragility, I've not had any experience with that, this being the first serious problem in all this time. If you could point me to some information on that I'd be interested.

> **1fallen said:**
> …I'm assuming that DuckHook is just mentioning this is "redundant"…
My comment was made in the spirit of inquiry and mainly for my own education.

I am only familiar with LVM, so I am an ignoramus when it comes to the two in combination.

Some previous forum threads were posted by members who ran into trouble with LVM layered over mdadm. Solutions offered by those who are more knowledgeable than me was to simplify the setup by using only one or the other, not both. My comment was but an echo of that advice, which made sense to me, since we routinely advise people to keep their system as minimalist as possible.

---

### Post by rsteinmetz70112 on 2022-07-18
I've recently set up another computer using RAID on LVM. I found it more complicated to set up and more complicated to understand what was going on. But it works perfectly. Perhaps my reluctance is due to my unfamiliarity with using RAID on LVM. I primarily use RAID1 because I administer two sites separated by 500 miles and if I were to have a drive failure at one site it would almost certainly continue to run until I could get there and lay hands on it. I suppose I could call in someone to work on it but finding competent Linux techs is somewhat difficult and they invariably want to do everything over the way they would do it. Plus I'm really the only person who knows how there servers are set up.

---

### Post by TheFu on 2022-07-18
LVM RAID is pretty simple.  

1 command, lvconvert.  use either the "mirror" or RAID1 option.  Plus, if you want to, you can add a 2nd mirror as a way to clone to another disk, then break the 2nd mirror, unplug it and walk away.

Of course, practice this on tiny storage inside VMs so you convince yourself that you understand it.  Best of all, the OS installation is much easier, just setup a non-mirrored LVM storage on 1 disk, then add a 2nd disk to the VG and run the lvconvert command with the mirror option for each LV.  Let it sync and then you have mirrored storage without modifying the fstab or touching mdadm.
```
       Convert LV to raid or change raid layout
       (a specific raid level must be used, e.g. raid1).

       lvconvert --type raid LV
           [ -m|--mirrors [+|-]Number ]
           [ -I|--stripesize Size[k|UNIT] ]
           [ -R|--regionsize Size[m|UNIT] ]
           [ -i|--interval Number ]
           [    --stripes Number ]
           [ COMMON_OPTIONS ]
           [ PV ... ]

```

---

