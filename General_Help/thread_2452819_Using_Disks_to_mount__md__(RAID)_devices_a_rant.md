---
title: "Using Disks to mount  md  (RAID) devices a rant"
date: 2020-10-28
forum: General Help
---

### Post by helen314 on 2020-10-28
```

# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).

```

Good advise, unfortunately juggling between  "label" and "name" which is "gparted" way to identify devices gives one a headache.

Part of much missing step , not covered by many tutorials, is to assign SOMETHING to fstab to automatically mount md (RAID ) at boot time. 

"Disks" uses BOTH :name or label"" and UUID. 

When you use "Disks" JUST to temporary mount RAID ( partition)  it does it by name or label  - I cannot tell I named them - in "gparted" SAME.

BUT 
when you want to mount SAME device automatically on boot - and use "advanced setup " -  you end up with UUID .
On top of that to decipher the data passed to "fstab"  one has to search "fstab man".
It is not that intuitive , for example passed "file format " is "auto ". 

It looks as fstab accepts data at random order WHEN each entry is labelled.  

 "Disks"  could not add LABEL= , FILE=  or similar so it is readable by humans and good for "fstab" also.  
BTW  - now "File"  shows RAID device by UUID!!!!. 
End of rant

---

### Post by oldfred on 2020-10-28
I do not use RAID.
But use a template for any entry in fstab.
And now I have it scripted as I am mounting the same data partition with every install, so UUID does not change.

I use these two commands a lot.
```
sudo blkid -c /dev/null -o list
ls -l /dev/disk/by-id
lsblk  -o NAME,LABEL,PARTLABEL,SIZE,MOUNTPOINT,UUID | egrep -v "^loop"
```

from Morbius1-----------------------------------------------------
I do not like Disks as it may not use correct parameters. Better to use template/example and adjust for your specifics
[https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup](https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

