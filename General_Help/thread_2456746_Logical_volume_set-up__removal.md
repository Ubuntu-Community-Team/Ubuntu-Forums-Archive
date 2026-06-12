---
title: "Logical volume set-up / removal"
date: 2021-01-18
forum: General Help
---

### Post by michael351 on 2021-01-18
I have a logical volume management question (see configuration below):

What I want to do is remove physical disk sdb which contains part of cl-home mounted as /home. I have removed /home contents.
I want to leave physical disk sda (which contains the OS) alone.

I noticed VG name is "CL". sda has cl-root, cl-swap and cl-home.

What command sequence do I use to remove only /home and subsequently remove sdb from my server (I'll probably have to recreate my user account)?
My fear is if I vgreduce /dev/sdb1 it will affect my root partition ("cl  ..." ?). And what line(s) do I delete from fstab for reboot
(/dev/mapper/cl-home ??)

Thanks for your help!

Below is my current configuration:
> 
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT

sda           8:0    0   1.8T  0 disk 
&#9500;&#9472;sda1        8:1    0     1G  0 part /boot
&#9492;&#9472;sda2        8:2    0   1.8T  0 part 
  &#9500;&#9472;cl-root 253:0    0    50G  0 lvm  /
  &#9500;&#9472;cl-swap 253:1    0  15.8G  0 lvm  [SWAP]
  &#9492;&#9472;cl-home 253:2    0   3.6T  0 lvm  /home
sdb           8:16   0   1.8T  0 disk 
&#9492;&#9472;sdb1        8:17   0   1.8T  0 part 
  &#9492;&#9472;cl-home 253:2    0   3.6T  0 lvm  /home

  > --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               cl
  PV Size               <1.82 TiB / not usable 3.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476931
  Free PE               0
  Allocated PE          476931
  PV UUID               FIRfBq-wFl4-X6Zn-AcKl-iMqm-faGZ-FJd3LJ

> /etc/fstab contents:

#
# /etc/fstab
# Created by anaconda on Sun Feb 23 17:13:36 2020
#
# Accessible filesystems, by reference, are maintained under '/dev/disk/'.
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info.
#
# After editing this file, run 'systemctl daemon-reload' to update systemd
# units generated from this file.
#
/dev/mapper/cl-root     /                       xfs     defaults        0 0
UUID=875d6fec-978b-4450-9fd6-66b96dd464fc /boot                   ext4    defaults        1 2
/dev/mapper/cl-home     /home                   xfs     defaults        0 0
/dev/mapper/cl-swap     swap                    swap    defaults        0 0
UUID=A228376928373B9B /mnt/data auto nosuid,nodev,nofail,x-gvfs-show 0 0

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

---

### Post by Dennis N on 2021-01-18
```
sudo pvmove /dev/sdb1
``` 
will move data on this PV to elsewhere in the CL volume group (if there is enough available space). 
Once this is done, you can then remove sdb1 from CL with pvremove. Then you could remove the physical partition sdb1 with a partition editor.

---

### Post by TheFu on 2021-01-18
xfs cannot be reduced. that is an XFS llmitation.

For lvm stuff, any lvm tutorial/guide from the last 15 yrs is fine. The OS doesn't matter.
We need to see
```
sudo pvs
sudo vgs
sudo lvs
```
to know what is truly happening.
Use code tags when posting.  [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by michael351 on 2021-01-18
Thanks for helping!

> PVS:
PV         VG Fmt  Attr PSize  PFree
  /dev/sda2  cl lvm2 a--  <1.82t    0 
  /dev/sdb1  cl lvm2 a--  <1.82t    0 

> VGS:
VG #PV #LV #SN Attr   VSize  VFree
  cl   2   3   0 wz--n- <3.64t    0 

> LVS:
 LV   VG Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home cl -wi-ao----   3.57t                                                    
  root cl -wi-ao----  50.00g                                                    
  swap cl -wi-ao---- <15.77g

---

### Post by TheFu on 2021-01-18
I'd create a new VG for non-OS needs, them move the home LV into that - but you'll probably want to change the size, so really using rsync to move all the data inside the "home" LV would be my method.  Then you can delete the home LV from the "cl" VG.

Spanning VGs across different physical disks when you aren't using RAID1 or RAID10 isn't the best idea. Long ago, I lost 80% of my data doing that.

And I'll ask again - code-tags please so output is readable. Don't make helping so hard, please.

---

### Post by michael351 on 2021-01-18
Creating a new VG makes sense, but how do I make sure it doesn't span the two drives?

---

### Post by Dennis N on 2021-01-18
> **michael351 said:**
> Creating a new VG makes sense, but how do I make sure it doesn't span the two drives?
Easy. A VG will only span two or more drives when you define it to include PVs on two or more drives. It's all specified in the vgcreate and vgextend command options.

---

### Post by TheFu on 2021-01-19
> **michael351 said:**
> Creating a new VG makes sense, but how do I make sure it doesn't span the two drives?

I guess you didn't actually click the link I provided above? Quotes are not code tags. The point is for columns to line up.
When a VG is created, 99% of the time, a single partition device is provided to be used.  To stay on a single drive, only provide 1 partition to be used.

**Any** LVM tutorial will cover this.  [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm) is one.  I disagree on a few of the commands they use.  For example, avoid the "XXXresize" commands. Use either "XXXextend" or "XXXreduce" commands instead. With resize, a tiny mistake can easily cause unintended data loss.  But humans think make bigger or make smaller and will correctly use "XXXextend" or "XXXreduce" commands every time.  I've already mentioned that XFS doesn't support reducing size.  Ext4 does.  If your storage is under 15TB, there isn't really much reason to choose XFS over EXT4, IMHO.
Also, both the lvextend and lvreduce commands have a --resizefs option which will handle resizing ext4 file systems on an LV at the same time.  1 less command to remember.  People always, always, always, forget to resize the file system after making an LV size change.

The link above is just an Ubuntu one, but none of the commands are ubuntu specific. Every Linux version uses the same LVM commands.  Tab-completion is really handy to see a list of commands.  
```
pv{tab}{tab}
vg{tab}{tab}
lv{tab}{tab}
```
will quickly show the commands for each LVM layer - physical, VG, and LV.  pvmove is the only "move" command. Most have vgchange and lvchange to alter how those layers work (within reason).  It is impossible to convert a 2-disk RAID1 setup into a 4 disk RAID10 setup. What would happen is a 4 disk RAID01 setup which isn't nearly as good.  With RAID10, we want the striping AND the redundancy.  See how physical limits of what is actually happening on the PV level matters?  Think through that stuff when making changes. What must the 3 layers do to accomplish what you ask through commands?

---

### Post by michael351 on 2021-01-19
> # /etc/fstab
# Created by anaconda on Sun Feb 23 17:13:36 2020
#
# Accessible filesystems, by reference, are maintained under '/dev/disk/'.
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info.
#
# After editing this file, run 'systemctl daemon-reload' to update systemd
# units generated from this file.
#
/dev/mapper/cl-root     /                       xfs     defaults        0 0
UUID=875d6fec-978b-4450-9fd6-66b96dd464fc /boot                   ext4    defaults        1 2
/dev/mapper/cl-home     /home                   xfs     defaults        0 0
/dev/mapper/cl-swap     swap                    swap    defaults        0 0
UUID=A228376928373B9B /mnt/data auto nosuid,nodev,nofail,x-gvfs-show 0 0

Can I move/copy /home to /boot 
I will delete the xfs filesystems and rebuild at ext4 and then re-create /home

Will this work?

---

