---
title: "enable a previously shared swap"
date: 2007-07-15
forum: General Help
---

### Post by seshomaru samma on 2007-07-15
I used to dualboot Etch and Feisty with a shared swap 
I installed Etch first but now I only run Feisty (cause of better wireless support)
Now I want to get hibernation/sleep working and downloaded uswsusp which claimed that I don't have a swap partition , when I ran swapon I got :
```
swapon: cannot stat /dev/disk/by-uuid/7cae9164-d06b-4185-8426-64868f802fb1: No such file or directory
```
This is the entry from my fstab:
```
# /dev/sda5
UUID=7cae9164-d06b-4185-8426-64868f802fb1 none            swap    sw              0       0
```
and my fdisk 
```
/dev/hda1               1        4255    34178256   83  Linux
/dev/hda3            4256        4437     1461915    5  Extended
/dev/hda4            4438        7112    21486937+  83  Linux
/dev/hda5            4256        4437     1461883+  82  Linux swap / Solaris

```
i have no experience with swap and not sure where to proceed...

---

### Post by 5-HT on 2007-07-15
Is that UUID correct? You can check by```
ls -l /dev/disk/by-uuid/
``` and edit your fstab if not. Alternatively, what about just getting rid of the UUID entry in fstab and replace it with /dev/hda5?

---

### Post by dougfractal on 2007-07-15
> This is the entry from my fstab:
# /dev/sda5
UUID=7cae9164-d06b-4185-8426-64868f802fb1 none            swap    sw              0       0


> and my fdisk
Code:
/dev/hda5            4256        4437     1461883+  82  Linux swap / Solaris


There seams to be an typo in the fstab using a SATA HD, rather than Primary IDE HD , I'm still a bit old school try
in the /etc/fstab
```
/dev/hda5  none swap sw 0 0

```

---

### Post by seshomaru samma on 2007-07-16
Thanks !!!
 It was indeed a wrong UUID , probably because I installed Etch first 
I solved it by replacing it with 
```
/dev/hda5  none swap sw 0 0
```
however , hibernation still doesnt work:(
but that's a different issue.....

---

### Post by strabes on 2007-07-16
If you have an ATI card you'll also need to follow the link in my signature to get suspending/hibernating working.

---

### Post by louieb on 2007-07-16
Don't know if this is related. But found the UUID of my swap partition had changed and swap wasn't being used. To get hibernate to work again had to put correct UUID in 2 places.
/etc/fstab
/etc/initramfs-tools/conf.d

Then had to run   ```
sudo dpkg-reconfigure  initramfs-tools 
``` Tired to find the thread where I got this info but could not locate it.

---

