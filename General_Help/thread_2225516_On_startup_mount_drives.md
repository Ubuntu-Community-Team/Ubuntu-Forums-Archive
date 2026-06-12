---
title: "On startup mount drives"
date: 2014-05-21
forum: General Help
---

### Post by Tom_Temple on 2014-05-21
Hi all when Ubuntu starts up this comes up I know I did it some but how do I get rid of it..??????????

                                  ......    Continue to wait, or Press S to skip mounting or M for manual recovery.     .....

---

### Post by squakie on 2014-05-22
It looks like the message you get when you have added a device/file system to /etc/fstab but the device isn't there upon boot.  One way to get this is if you put in a mount for an external USB drive but then don't have it plugged in at boot.

---

### Post by hyperreal on 2014-05-22
You can get rid of it by editing the /etc/fstab file and removing the line containing the mount point for the device that isn't being mounted at boot time.

---

### Post by coldcritter64 on 2014-05-22
> **hyperreal said:**
> You can get rid of it by editing the /etc/fstab file and **removing** the line containing the mount point for the device that isn't being mounted at boot time.

The entry may be something you want or need OP, rather than removing check the details of all your partitions with 
```
sudo blkid -c /dev/null
```
This code will give you all details for all of your partitions you need to fix fstab entries,

Post  the output of the code above and the next code if you can't find the problem to fix it; people here will be able to check them for you.
```
cat /etc/fstab
```

Copy / paste the above 2 terminal outputs to code boxes in your editor here, use the advanced editor. Place the outputs between [noparse]```

```[/noparse] tags by highlighting the output and pressing the "#" symbol on the editor toolbar. Doing this preserves the formatting of the output and enables easier reading of your results for helpers.

---

### Post by squakie on 2014-05-22
I know there is a parameter you can add on the mount in fstab to make it NOT a requirement to be present at boot time.  At one time a user posted this and said it was the correct way to do things, the next time they claimed just the opposite.  I'll see if I can find it and post it back here - for you to try at your own risk!

EDIT:  okay, the parameter is nobootwait

Of course, I will assume for any USB devices such as external hard disks, you are referencing by UUID (don't use the /dev/xxx -> it changes for USB devices!!).  Here's a sample:

UUID=<your UUID HERE> <your mount point> <file system type>  <other options as needed - like rw, permissions, etc.)> nobootwait 0 0

---

