---
title: "Can't write to removable drives??"
date: 2007-01-21
forum: General Help
---

### Post by Boomy on 2007-01-21
I have a USB flash drive and I can't write to it. The way Ubuntu handles external drives is horrible. I have a removable 120 gig drive with 2 partitions. One is ntfs, the other fat32. I have edited my fstab a long time ago and it works as it should MOST of the time. I do not have that drive connected and when I plug in my flash drive, Ubuntu doesn't know that it is a different drive, it thinks it is my removable ntfs partition and mounts it to that directory, and it calls it "sdc1", the device name of my other drive. Now sometimes, Ubuntu will consider it sdd1, and mount it to another directory that I have assigned in my fstab file for sdd1. I give that directory the group and ownership permissions of my use name, but I still can't write to it. It's a total mess the way this works. What can I do to fix it? I'm getting pissed. Why doesn't Ubuntu keep this **** straight? I tried Mepis with the live CD and mouting the flash drive seemed to work just fine.

---

### Post by Boomy on 2007-01-21
The problem is that Ubuntu thinks my flash storage drive is read only. wtf? ](*,)

---

### Post by bodhi.zazen on 2007-01-21
> **Boomy said:**
> I have a USB flash drive and I can't write to it. The way Ubuntu handles external drives is horrible. I have a removable 120 gig drive with 2 partitions. One is ntfs, the other fat32. I have edited my fstab a long time ago and it works as it should MOST of the time. I do not have that drive connected and when I plug in my flash drive, Ubuntu doesn't know that it is a different drive, it thinks it is my removable ntfs partition and mounts it to that directory, and it calls it "sdc1", the device name of my other drive. Now sometimes, Ubuntu will consider it sdd1, and mount it to another directory that I have assigned in my fstab file for sdd1. I give that directory the group and ownership permissions of my use name, but I still can't write to it. It's a total mess the way this works. What can I do to fix it? I'm getting pissed. Why doesn't Ubuntu keep this **** straight? I tried Mepis with the live CD and mouting the flash drive seemed to work just fine.

I suggest you either eliminate the fstab entries for your removable devices or mount by either label or uuid rather then /dev/sdxy 

The "problem" is the /dev/sdxy is not unique to a removable device and may change depending on what you have in your usb slots and in what order.

Better fstab enterise would be

LABEL=<label> /mount_point .....
UUID=<###> /mount_point ...

where <label> is the label or a partition and <###> is the uuid.

To list your devices by label or uuid, first pulg them in, give a minute or so fro them to be recognized, then:

ls /dev/disk/by-label -l

OR

ls /dev/disk/by-uuid

Again, the disadvantage of using fstab is that devices may no longer auto mount, but you can easily mount them from the CLI or nautilus...

If you prefer automount just remove all enteries from fstab and the device will mount in /media :p

See here for further information:

[http://www.ubuntuforums.org/showthread.php?&t=283131](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Boomy on 2007-01-21
Thanks for the reply, I'll try to do it by label. :D

---

