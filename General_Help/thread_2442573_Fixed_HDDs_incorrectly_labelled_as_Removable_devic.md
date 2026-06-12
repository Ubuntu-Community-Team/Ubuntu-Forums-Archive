---
title: "Fixed HDDs incorrectly labelled as Removable devices"
date: 2020-05-05
forum: General Help
---

### Post by shag00 on 2020-05-05
In Dolphin file manger a number of HDDs are listed as removable storage when they are not. All of these drives are mounted in fstab however, I suspect the problem arises because they are all mounted through a PCIE to SATA controller. Why anything connected to a PCIE port is considered removable is beyond me. Anyway, is there a way to force the system to recognise these disks as devices rather than removable devices?  Please note that everything works as expected except for this one small issue.

---

### Post by ajgreeny on 2020-05-05
Where in the file system does fstab mount these drives?

---

### Post by shag00 on 2020-05-05
```
# <FILE SYSTEM>                             <MOUNT POINT>              <TYPE> <OPTIONS>           <DUMP>    <PASS>
#--------------                                -----------                   ----    -------           ----         ----
/swapfile                                    none                        swap   sw                  0          0
UUID=6F97-1999                               /boot/efi                 vfat   umask=0077              0          2
UUID=c1c09fb2-70bf-4918-b204-0c6622f6d555    /                           ext4   errors=remount-ro    0          1
UUID=62f9c1ad-aa3a-449d-af27-636cbc78dd9f    /media/data/disk01        ext4     defaults            0          2
UUID=4d009d0b-155f-466b-a89b-961c78c1cfec    /media/data/disk02        ext4     defaults            0          2
UUID=474961bc-e95f-4b12-b6ad-19c803df253b    /media/data/disk03        ext4     defaults            0          2
UUID=2bf5a4b2-36de-4dd8-8b1c-d20f823a6dc6    /media/data/disk04        ext4     defaults            0          2
UUID=b8be779a-6bbd-4614-bc85-552373da27fd    /media/data/disk05        ext4     defaults            0          2
UUID=d894f718-8c2e-4100-b298-a7e05662c750    /media/data/disk06        ext4     defaults            0          2
UUID=b8f24a86-be5f-4f33-a036-57dbbf0688bd    /media/data/disk07        ext4     defaults            0          2
UUID=52c1c03e-9f9a-4339-9abb-576dc3b24ab3    /media/data/disk08        ext4     defaults            0          2
UUID=c661be70-bd57-42eb-8644-710d11e4ed4f    /media/data/disk09        ext4     defaults            0          2
UUID=86381412-44a2-48df-a26e-b007343eceae    /media/data/disk10        ext4     defaults            0          2
UUID=a0cd798e-0b68-4970-8e95-571b47798893    /media/data/disk11        ext4     defaults            0          2
UUID=96891f4f-53e6-42cf-acdf-c26301cfb906    /media/parity/.parity01   ext4     defaults            0          2
UUID=af020c8c-fe94-4326-9d35-16341e7f76b0    /media/parity/.parity02   ext4     defaults            0          2
#
#Mergerfs pool
/media/data/*    /media/pool    fuse.mergerfs    category.create=epmfs,defaults,allow_other,minfreespace=100G,fsname=pool 0 0    
```

---

### Post by CelticWarrior on 2020-05-05
Anything mounted in /media is considered "removable".

---

### Post by ajgreeny on 2020-05-05
Change those mount points to something else, eg /mnt/data and they will disappear as removable drives.

Strictly ***/mnt*** is for temporary mounted devices but it works fine for an internal disk drive as well as I have done that myself, but you could also create a separate filesystem folder called /data with command ***sudo mkdir /data*** and mount the disks there instead if you prefer.

---

### Post by scottbomb on 2020-12-29
> **CelticWarrior said:**
> Anything mounted in /media is considered "removable".

Interesting response but that has not been my experience. I have 5 HDDs mounted at /media and all but one are listed in Dolphin under "Devices" but not "Removable Devices" like USB drives would be.

The reason I resurrected this old thread is because I'm curious to know if Dolphin has a limit on the # of HDDs it will list under Devices. Interestingly, every time I do a new install (since I've been using Kubuntu - 16.04) it only lists 4 of my 5 drives and it's the same one that never appears so I had to make a spot for it under Places. It's just a 4 TB SATA drive like the others. Granted, it was once "removable" as it was in a case and connected via USB but I ripped off the case and it now connects with its normal SATA connectors and not the USB interface it originally used. I have another drive that also started its life within a plastic shell with a USB interface but it does show up with the other SATA drives, as it should.

So I can't help but wonder... is there a hard limit of 4 HDDs Dolphin will list under Devices or perhaps it knows that particular 4 TB drive was once within a plastic shell?

---

### Post by shag00 on 2020-12-29
Several months after penning this thread I actually happened upon a partial answer to this question. To get Dolphin to display the disks as (fixed) devices you need to set them as NON hot-pluggable in BIOS. That takes care of all HDDs plugged into a mother board SATA port but still no answer to HDDs plugged into a PCIE to SATA controller.

---

