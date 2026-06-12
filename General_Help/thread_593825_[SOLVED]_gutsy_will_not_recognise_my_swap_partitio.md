---
title: "[SOLVED] gutsy will not recognise my swap partition"
date: 2007-10-27
forum: General Help
---

### Post by Matticus on 2007-10-27
I need to know how to get gutsy to re-recognise my swap partition.

I had some issues when a MEPIS install crashed and killed my mbr, I fixed that now I have hda1 for storage (was windows, was going to be MEPIS, but it wont be now) hda2 is my root ubuntu partition, and hda3 is swap.

But the swap wont turn on, I have tried swapon in GParted several times, but to no avail.

I was under the impression that ubuntu would automatically recognise it, and start using it.

---

### Post by Matticus on 2007-10-27
Nevermind, I rebooted again and tried swap on in gparted just for the sake of it, and it worked.

So I assume it was just being a bit buggy for whatever reason.


[COLOR="Red"]EDIT:

Doesnt work after reboot

I assume I've got to change something in /etc/fstab, but I dont know what.

Can anyone help??[/COLOR]

---

### Post by louieb on 2007-10-27
Formatting a partition will sometime change its UUID
Check the uuid in /etc/fstab
to list uuid
```
ls -l /dev/disk/by-uuid/
```[http://louboldt.com/ilinuxmisc.htm#uuid](http://louboldt.com/ilinuxmisc.htm#uuid)

---

### Post by taurus on 2007-10-27
Post

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Matticus on 2007-10-27
louieb that worked just great thanks.

tauras thanks also, I thought you where going to have to save me again. 2 times in one day would have been pretty good :biggrin:

cheers guy, now it really is officially solved.

---

