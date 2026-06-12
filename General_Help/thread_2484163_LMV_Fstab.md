---
title: "LMV Fstab"
date: 2023-02-19
forum: General Help
---

### Post by Quarkrad on 2023-02-19
I have set up a LVM environment in a vm prior to implementing on a new HD.  Everything seems to be OK in that I have 3 logical volumes, one for **/**, one for **/home**, and one other - my plan is to expand, decrease all of these to get my head around LVM (or rather part of it as my single Desktop machine will only utilise a small part of LVM capability).  Where I need help at this point is fstab - can somebody point me to a good source of what one needs to do, from scratch, in terms of fstab permanently mounting all three LVs?  Additionally, from what I have read so far there is no mention of things like noatime or other, standard/non lvm, fstab entries.  At the moment I permanently mount a win10 volume, which I may not want to do in my new build.  The fstab entry is:

```
UUID=BE28F47928F4324F UUID=BE28F47928F4324F /media/dad/win10  ntfs-3g nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002


```

I appreciate/believe in an lvm system fstab the **UUID=.......** bit is going to have a different nomenclature because of LVM but what about the  */media/dad/win10  ntfs-3g nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002*  section?  If you created a logical volume with a ntfs file system would it corresponding fstab entry be the same.  

I guess what I'm asking is .... is the fstab difference just the UUID=.... bit, because one is using logical volumes rather than perhaps, physical partitions, and the rest of the fstab entry stays the same?

---

### Post by Dennis N on 2023-02-19
All the LVs have UUIDs just like partitions - both are block devices. So you can use those in fstab. But instead of UUID, you can also label the file system on the LV and use that to mount it. I tend to do it that way instead of UUID.

My fstab line entry to mount my separate data LV:
```
# mount data LV
LABEL=Common /mnt/Common-Files ext4 defaults 0 2

```

In regard to a VM, I can mount a USB drive to the VM's file system by plugging it in. You can also add a 2nd virtual disk to the VM.  Maybe, but I doubt the host's partitions are mountable to the guest file system.  Never seen a way to do that. I connect to the host via the network using SSH.

VM structure (not LVM):
```
NAME   LABEL  FSTYPE   MOUNTPOINT
sda                    
&#9492;&#9472;sda1 MyData ext4     /media/dmn/MyData
sr0                    
vda                    
&#9500;&#9472;vda1                 
&#9500;&#9472;vda2        vfat     /boot/efi
&#9492;&#9472;vda3        ext4     /
vdb                    
&#9492;&#9472;vdb1 Common ext4     /mnt/Common-Files
```

sda: a usb drive that was plugged in.
vdb: a second virtual disk added to the vm. vdb1 mounts in the vm file system through fstab.

---

