---
title: "Issues with LVM"
date: 2017-03-14
forum: General Help
---

### Post by dylan98c on 2017-03-14
Hopefully this is the right place for this. I have an HP Proliant ML350 G6 being used has a home file server. Originally had 3x 146GB 15K SAS drives for boot and 3x 2TB 7.2K SAS drives as the main share. Both were RAID5 through the integrated HP P410i. I decided to transfer the boot responsibilities to an SSD to save the power. I installed the SSD to the built in SATA controller and installed Ubuntu Server 16.04.2 LTS as usual. I vaguely remember it yelling at me when I chose to Create a new partition and enable LVM, I'm guessing this was due to the original RAID5 being LVM already. I manually formatted the SSD and installed on an ext4 partition. Booted up and long story short, the 3x 2TB RAID5 will mount, but only when the original 3x 146GB RAID5 is in and enabled (tested by removing drives in between boots and disabling the logical volume). I'm guessing this 4TB logical volume was part of the original LVM then, how I can get this work without the original LVM volume without reformatting? Here are the results of lsblk with and without the original volume.

With: 
```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL,UUID
NAME                  FSTYPE        SIZE MOUNTPOINT LABEL   UUID
sda                               111.8G                    
&#9500;&#9472;sda1                ext4         79.8G /                  48bd7079-2b6d-4130-b736-0a96971283e4
&#9500;&#9472;sda2                                1K                    
&#9492;&#9472;sda5                swap           32G [SWAP]             0df434da-2c00-45ce-85df-64afc4e3a013
sdb                               273.4G                    
&#9500;&#9472;sdb1                ext2          243M                    0371a986-3833-4bd3-a084-8c148dc35b5f
&#9500;&#9472;sdb2                                1K                    
&#9492;&#9472;sdb5                LVM2_member 273.2G                    MjZz0Z-cSa5-VNoV-5bdH-dkF1-V0Pt-IrNCNr
  &#9500;&#9472;Server--vg-root   ext4        253.2G                    903e05db-282d-4835-858b-d75598d17567
  &#9492;&#9472;Server--vg-swap_1 swap           20G                    afd60367-e03c-49e9-9801-89033f459232
sdc                   ext4          3.7T /Storage   Storage 9a78a03a-56f3-46da-9e50-2c16c9a147a1


```

Without:
```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL,UUID
NAME   FSTYPE   SIZE MOUNTPOINT LABEL UUID
sda           111.8G                  
&#9500;&#9472;sda1 ext4    79.8G /                48bd7079-2b6d-4130-b736-0a96971283e4
&#9500;&#9472;sda2            1K                  
&#9492;&#9472;sda5 swap      32G [SWAP]           0df434da-2c00-45ce-85df-64afc4e3a013
sdb             3.7T                  
```

---

### Post by kingneutron on 2017-03-15
--It's been some time since I ran LVM on my system, but my guess is that you'll have boot with everything connected and start going through ' vgdisplay ' and ' lvdisplay ' to figure out what is associated with what. Even installing Webmin (it runs on port 10000) may help.

REF:
[http://doxfer.webmin.com/Webmin/Logical_Volume_Management](http://doxfer.webmin.com/Webmin/Logical_Volume_Management)

--Personally, I had to add '  vgchange -v -a y ' to my /etc/rc.local to get everything working back in the day, this may/not apply in your case.

--Also, a bit of been-there-done-that advice: Both LVM and RAID5 are somewhat deprecated these days, you might want to look into ZFS if you end up wanting to re-do everything. I will be more than happy to help you in that case with advice and best practices.

REF:
[http://www.zdnet.com/article/why-raid-5-stops-working-in-2009/](http://www.zdnet.com/article/why-raid-5-stops-working-in-2009/)

[http://www.enterprisestorageforum.com/technology/features/article.php/3849556/10-Reasons-Why-ZFS-Rocks.htm](http://www.enterprisestorageforum.com/technology/features/article.php/3849556/10-Reasons-Why-ZFS-Rocks.htm)

[https://github.com/zfsonlinux/zfs/wiki/Admin-Documentation](https://github.com/zfsonlinux/zfs/wiki/Admin-Documentation)

[https://github.com/zfsonlinux/zfs/wiki/FAQ](https://github.com/zfsonlinux/zfs/wiki/FAQ)

---

### Post by dylan98c on 2017-03-15
I am currently saving for a newer (more power efficient) server, so I haven't really bothered with changing things. I do understand the issues with RAID5 and drives larger than 1TB as well as the slow bit decay. Next server will be ZFS for sure. Here are the results of those commands, it doesn't look like the 4TB pool is part of an LVM, is there any other reason it would not let me mount that drive unless the original disks are in?

```

[COLOR=#000000][FONT=Andale Mono]vgdisplay[/FONT]
[FONT=Andale Mono]  --- Volume group ---[/FONT]
[FONT=Andale Mono]  VG Name               Server-vg[/FONT]
[FONT=Andale Mono]  System ID             [/FONT]
[FONT=Andale Mono]  Format                lvm2[/FONT]
[FONT=Andale Mono]  Metadata Areas        1[/FONT]
[FONT=Andale Mono]  Metadata Sequence No  3[/FONT]
[FONT=Andale Mono]  VG Access             read/write[/FONT]
[FONT=Andale Mono]  VG Status             resizable[/FONT]
[FONT=Andale Mono]  MAX LV                0[/FONT]
[FONT=Andale Mono]  Cur LV                2[/FONT]
[FONT=Andale Mono]  Open LV               2[/FONT]
[FONT=Andale Mono]  Max PV                0[/FONT]
[FONT=Andale Mono]  Cur PV                1[/FONT]
[FONT=Andale Mono]  Act PV                1[/FONT]
[FONT=Andale Mono]  VG Size               273.16 GiB[/FONT]
[FONT=Andale Mono]  PE Size               4.00 MiB[/FONT]
[FONT=Andale Mono]  Total PE              69929[/FONT]
[FONT=Andale Mono]  Alloc PE / Size       69927 / 273.15 GiB[/FONT]
[FONT=Andale Mono]  Free  PE / Size       2 / 8.00 MiB[/FONT]
[FONT=Andale Mono]  VG UUID               nXqti0-Fiaj-w60j-M4ue-hom4-OyzI-nBak9G[/FONT][/COLOR]

```

```

[COLOR=#000000][FONT=Andale Mono]lvdisplay[/FONT]
[FONT=Andale Mono]  --- Logical volume ---[/FONT]
[FONT=Andale Mono]  LV Path                /dev/Server-vg/root[/FONT]
[FONT=Andale Mono]  LV Name                root[/FONT]
[FONT=Andale Mono]  VG Name                Server-vg[/FONT]
[FONT=Andale Mono]  LV UUID                vXXaZB-DawN-PcRA-5rdH-YGFd-9WgU-80p2A0[/FONT]
[FONT=Andale Mono]  LV Write Access        read/write[/FONT]
[FONT=Andale Mono]  LV Creation host, time Server, 2016-06-24 19:42:22 -0500[/FONT]
[FONT=Andale Mono]  LV Status              available[/FONT]
[FONT=Andale Mono]  # open                 1[/FONT]
[FONT=Andale Mono]  LV Size                253.16 GiB[/FONT]
[FONT=Andale Mono]  Current LE             64810[/FONT]
[FONT=Andale Mono]  Segments               1[/FONT]
[FONT=Andale Mono]  Allocation             inherit[/FONT]
[FONT=Andale Mono]  Read ahead sectors     auto[/FONT]
[FONT=Andale Mono]  - currently set to     256[/FONT]
[FONT=Andale Mono]  Block device           252:0[/FONT]

[FONT=Andale Mono]  --- Logical volume ---[/FONT]
[FONT=Andale Mono]  LV Path                /dev/Server-vg/swap_1[/FONT]
[FONT=Andale Mono]  LV Name                swap_1[/FONT]
[FONT=Andale Mono]  VG Name                Server-vg[/FONT]
[FONT=Andale Mono]  LV UUID                bsXuCP-wmCL-jdZ8-n4ZQ-biSr-c7Wf-xK3tCW[/FONT]
[FONT=Andale Mono]  LV Write Access        read/write[/FONT]
[FONT=Andale Mono]  LV Creation host, time Server, 2016-06-24 19:42:22 -0500[/FONT]
[FONT=Andale Mono]  LV Status              available[/FONT]
[FONT=Andale Mono]  # open                 2[/FONT]
[FONT=Andale Mono]  LV Size                19.99 GiB[/FONT]
[FONT=Andale Mono]  Current LE             5117[/FONT]
[FONT=Andale Mono]  Segments               1[/FONT]
[FONT=Andale Mono]  Allocation             inherit[/FONT]
[FONT=Andale Mono]  Read ahead sectors     auto[/FONT]
[FONT=Andale Mono]  - currently set to     256[/FONT]
[FONT=Andale Mono]  Block device           252:1[/FONT][/COLOR]



```

---

### Post by kingneutron on 2017-03-17
--You will probably need to get more information than that. ' vgdisplay -v ' will show you the PV's allocated to your VG's.

>  long story short, the 3x 2TB RAID5 will mount, but only when the original 3x 146GB RAID5 is in and enabled 

--Worst case scenario, I would back up the data you have on the 3x146GB RAID5 and take them out of LVM entirely.

** NOTE ** _I take no responsibility for your data_, the following commands are only a suggestion and I strongly recommend you BACKUP everything:

' man lvremove '
' man vgremove '
' man pvremove '

--If you don't want to go about messing with things manually, try installing Webmin as recommended before; it will at least give you a GUI interface to LVM.

---

