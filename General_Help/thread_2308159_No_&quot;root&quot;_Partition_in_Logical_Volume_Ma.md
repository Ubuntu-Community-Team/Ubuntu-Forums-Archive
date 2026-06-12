---
title: "No &quot;root&quot; Partition in Logical Volume Management"
date: 2015-12-31
forum: General Help
---

### Post by robo731 on 2015-12-31
I'm new to Ubuntu so please bear with me. I've been following [this guide]("http://linuxhomeserverguide.com/server-config/LVM.php"). I want to set up a virtual partition for my media, but I realized that I do not have a partition for "root" or "swap." I would like to find out if I should make these partitions before I proceed to avoid future issues. I'm not even really sure what swap is or what it's for, but I have a feeling it might be important to have a partition for "root" to avoid it being overwritten or something. I simply don't know enough about partitioning or Ubuntu to proceed though. Also, if you don't mind briefly explaining what these partitions will be for, that would be great.

[COLOR=#0000ff]Edit: I ran: ```
lsblk
``` which returned [this]("http://paste.ubuntu.com/14333310/"), so maybe the partitions are there and they're just not showing up in webmin?
[/COLOR]

---

### Post by sandyd on 2015-12-31
whats the output of
```

sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```

---

### Post by grahammechanical on 2015-12-31
> if you don't mind briefly explaining what these partitions will be for

If you do not have a root ( / ) partition then you do not have Linux installed.

When system memory (RAM) becomes close to being full Linux will move data out of memory to a previously allocated area of the hard disk that is the swap partition. This process will free up memory. When that information is needed again Linux will move the data back into memory by swapping out some other data.

If we use hibernation the contents of system memory is stored in the swap partition to be reloaded back into memory when the OS comes out of hibernation.

Regards

---

### Post by robo731 on 2015-12-31
Here's the output of those commands: [pv]("http://paste.ubuntu.com/14337654/"), [vg]("http://paste.ubuntu.com/14337993/"), [lv]("http://paste.ubuntu.com/14338032/").

Thanks for the explanation grahammechanical. That makes sense.

---

### Post by sandyd on 2015-12-31
> **robo731 said:**
> Here's the output of those commands: [pv]("http://paste.ubuntu.com/14337654/"), [vg]("http://paste.ubuntu.com/14337993/"), [lv]("http://paste.ubuntu.com/14338032/").

Thanks for the explanation grahammechanical. That makes sense.

Partitions are fine, you have 912.14 GiB remaining in your volume group that can be used.

issue should be with webmin, which I don't use, so i can't help you here.

---

### Post by robo731 on 2015-12-31
Ok, that's a relief, at least the existing partitions are okay. Do you think I should just create the new LVM I want via the CLI then?

---

### Post by sandyd on 2015-12-31
> **robo731 said:**
> Ok, that's a relief, at least the existing partitions are okay. Do you think I should just create the new LVM I want via the CLI then?

Yep,

Use something like
```

sudo lvcreate -L10G -nmylv UbuntuServer-vg

```

The above will create a 10G LVM LV with the name of 'mylv'

---

### Post by robo731 on 2015-12-31
Ok, thanks. I'll use that, but will that make a it contiguous or non-contiguous? Also, I intend to use the folder to hold media, mostly video files and I plan to access those files from windows systems. What file system will that command create? Should I be concerned with which filesystem to use for this LV or does it not matter since I'm using samba?

---

### Post by sandyd on 2015-12-31
Add the
```
-C y
```
flag if you want it to be contiguous.

Filesystem is up to you, ext4 is good for general stuff, jfs is good for small files, xfs is good for large files, I generally just use ext4 as there is not a massive difference.

---

### Post by robo731 on 2015-12-31
Ok, I think I'll leave it as non-contiguous and use ext4 as I can't find any advantages to using NTFS instead of ext4. I'll just make it a samba share. Thanks for the help.

---

