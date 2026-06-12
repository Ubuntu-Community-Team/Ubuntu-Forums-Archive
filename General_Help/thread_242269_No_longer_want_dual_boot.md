---
title: "No longer want dual boot"
date: 2006-08-23
forum: General Help
---

### Post by yodaky on 2006-08-23
After solving some frustrating problems installing Ubuntu I would like to remove my other OS, SUSE 10.0

I have SUSE installed on my 200GB drive and Ubuntu on my 80GB drive.  I have tried formatting the 200GB drive and mounting it to /mnt but that doesn't seem to have worked.  What can I do to utilize this drive or should I just reinstall everything before I get too much furth in to Ubuntu?

---

### Post by Tomosaur on 2006-08-23
You could try using parted to simply extend your Ubuntu partition to completely cover the rest of the hard drive? If the command line ain't your thing, try GParted instead, which just throws a nice GUI over parted anyway.

---

### Post by DeShark on 2006-08-23
As long as Grub is controlled by Ubuntu, formatting it should be ok. Then you should be able to mkdir /mnt/hda5 or whatever and then mount /dev/hda5 /mnt/hda5. Depending on what number the partition has. Then edit your menu.lst file to remove the option of SUSE and set Ubuntu as your default and alter the countdown if necessary.

---

### Post by yodaky on 2006-08-23
Thanks for the info on formatting and mounting.  I got it working.  However, is there a way to make the mounting "permanent"?  I would prefer not to have to run the mount command every time I boot up.  Thanks again.

---

### Post by christhemonkey on 2006-08-23
Add it to the file /etc/fstab:
```
gksudo gedit /etc/fstab 
```

Then add a line something like:
```
/dev/hda5 /mnt/hda5 ext3 defaults,errors=remount-ro,auto,rw,dev,exec,suid,nouser,data=writeback 0 1 
```
To the end of the file.

---

### Post by DeShark on 2006-08-23
You have to change your "fstab" (File System Table I think) file. It's at /etc/fstab. You want to add the information about the partition in a new line as so...

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

i.e.

```
/dev/hda5   /mnt/hda5     ext3     defaults  0  0
```

That should do the trick

---

### Post by yodaky on 2006-08-23
Thanks for the info.  Got it working :)

---

