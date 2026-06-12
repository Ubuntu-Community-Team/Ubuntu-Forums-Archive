---
title: "LVM Naming"
date: 2023-04-26
forum: General Help
---

### Post by Quarkrad on 2023-04-26
I have a number of hard disks in my Desktop machine (22.04) that I use for backup and data storage - these being sda, sdb, sdc, sdd, and sde.  In addition I have a nvme disc that I have configured using LVM.  Under Devices in my caja file manager I 'see' the names of my sdx disks listed with their names. I.e. win10backp, backup, store12, win10 and backup2.  However, the lvm logical volumes are listed not with names (workspace, ub2204vm, win10vm, etc) but as 54 GB Volume - which is their physical size.   Is there a why of getting caja to list these lvm volumes with their name rather than their size?

```
dad@dadubuntu:~$ sudo lsblk -e7
NAME                   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda                      8:0    0 111.8G  0 disk 
&#9492;&#9472;sda1                   8:1    0 111.8G  0 part /media/dad/win10backup
sdb                      8:16   0   1.8T  0 disk 
&#9492;&#9472;sdb1                   8:17   0   1.8T  0 part /media/dad/backup
sdc                      8:32   0   1.8T  0 disk 
&#9492;&#9472;sdc1                   8:33   0   1.8T  0 part /media/dad/store12
sdd                      8:48   0 223.6G  0 disk 
&#9500;&#9472;sdd1                   8:49   0   100M  0 part 
&#9500;&#9472;sdd2                   8:50   0    16M  0 part 
&#9500;&#9472;sdd3                   8:51   0   223G  0 part /media/dad/win10
&#9492;&#9472;sdd4                   8:52   0   508M  0 part 
sde                      8:64   0   1.8T  0 disk 
&#9492;&#9472;sde1                   8:65   0   1.8T  0 part /media/dad/backup2
sr0                     11:0    1  1024M  0 rom  
nvme0n1                259:0    0 931.5G  0 disk 
&#9500;&#9472;nvme0n1p1            259:1    0   200M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2            259:2    0 931.3G  0 part 
  &#9500;&#9472;vg01-root          253:0    0    40G  0 lvm  /
  &#9500;&#9472;vg01-home          253:1    0    50G  0 lvm  /home
  &#9500;&#9472;vg01-workspace     253:2    0   250G  0 lvm  /media/dad/workspace
  &#9500;&#9472;vg01-swap          253:3    0     8G  0 lvm  [SWAP]
  &#9500;&#9472;vg01-ubuntu2204vm  253:4    0    50G  0 lvm  /media/dad/ub2204vm
  &#9500;&#9472;vg01-win10vm       253:5    0    50G  0 lvm  /media/dad/win10vm
  &#9500;&#9472;vg01-ub2204base    253:6    0    50G  0 lvm  /media/dad/ub2204base
  &#9500;&#9472;vg01-windows10vm   253:7    0    50G  0 lvm  /media/dad/windows10vm
  &#9492;&#9472;vg01-haskinsmarine 253:8    0    50G  0 lvm  /media/dad/haskinsmarine

```

---

### Post by TheFu on 2023-04-26
sudo lvs

---

### Post by Quarkrad on 2023-04-26
That command gives me the names of the logical volumes - that I already know.  How do I get my caja file manager to use the 'human'  names rather than the LSize?  I.e. the file manager lists the details in the LSize column, not the LV column.

```
dad@dadubuntu:~$ sudo lvs
  LV            VG   Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  haskinsmarine vg01 -wi-ao----  50.00g                                                    
  home          vg01 -wi-ao----  50.00g                                                    
  root          vg01 -wi-ao----  40.00g                                                    
  swap          vg01 -wi-ao----   8.00g                                                    
  ub2204base    vg01 -wi-ao----  50.00g                                                    
  ubuntu2204vm  vg01 -wi-a-----  50.00g                                                    
  win10vm       vg01 -wi-a-----  50.00g                                                    
  windows10vm   vg01 -wi-ao----  50.00g                                                    
  workspace     vg01 -wi-a----- 250.00g   
```

---

### Post by Dennis N on 2023-04-26
Give the LV file systems a label. In my MATE (20.04) LV devices show under Caja > Devices by label, otherwise the size displays.

---

### Post by Quarkrad on 2023-04-26
Thank you Dennis N - I had thought of that and wanted to try it but my limited experience of 'labelling' is via GParted.  Unfortunately GParted only shows my nvme having the single Volume Group (that is indeed has) not the individual Logical Volumes.  (Previous to implementing lvm I have always used GParted to set my HD's up but as I couldn't use this method I have set everything up (the lvm environment) using terminal commands.  I have changed the names of my logical volumes but this is not the same as the 'label'.  Is there a terminal command way of giving my l volumes a label name?).

---

### Post by Quarkrad on 2023-04-26
Dennis N - sorry, didn't read your post properly.  How/where do I get to the changing of Caja > Devices by label?

---

### Post by TheFu on 2023-04-26
File system tools can usually add a label to the file system.  How depends on which file system is involved.  For ext4, 
```
NAME
       e2label - Change the label on an ext2/ext3/ext4 filesystem
```

I don't really use file managers (generally too slow), so don't know much about them.

---

### Post by Dennis N on 2023-04-26
Specifically, based on your display in post #1, using the LV named workspace as an example:
```
sudo e2label /dev/vg01/workspace workspace
```
would assign "workspace" as the label of the file system of the workspace LV. 
To view the current label of this LV:
```
sudo e2label /dev/vg01/workspace
```
it either displays the label or a blank line if there is none.

---

### Post by Quarkrad on 2023-04-26
Thank you both - e2label came to my rescue!

---

