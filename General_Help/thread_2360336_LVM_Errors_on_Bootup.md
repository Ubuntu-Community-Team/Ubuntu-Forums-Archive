---
title: "LVM Errors on Bootup"
date: 2017-05-03
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-05-03
When I boot into Ubuntu 16.04.2 I get three errors.  Two appear right on boot up and one appears about 30 to 40 seconds later.  I looked in /var/log/boot.log and found this.  Does anyone know how to activate or install lvmetadad.socket.  if that's not the problem does anyone have any suggestions on how to get rid of the errors?

```
lvmetad is not active yet, using direct activation during sysinit 
  Volume group "ubuntu-vg" not found 
  Cannot process volume group ubuntu-vg 
  /run/lvm/lvmetad.socket: connect failed: No such file or directory 
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning. 
  Reading all physical volumes.  This may take a while... 
  Found volume group "ubuntu-vg" using metadata type lvm2 
  /run/lvm/lvmetad.socket: connect failed: No such file or directory 
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning. 
  2 logical volume(s) in volume group "ubuntu-vg" now active
```

---

### Post by Xian on 2017-05-04
Let's give this a try:

```
[COLOR=#333333][FONT=Ubuntu]sudo dpkg-reconfigure lightdm[/FONT][/COLOR]
```

---

### Post by shane_faulkinbury2 on 2017-05-04
Hmm, why lightdm and not lvmetad?

---

### Post by shane_faulkinbury2 on 2017-05-04
I haven't rebooted, but check this out.

```
frank@frank-110-194:~$ sudo dpkg-reconfigure lightdm
[sudo] password for frank: 
frank@frank-110-194:~$ sudo dpkg-reconfigure lvmetad
dpkg-query: package 'lvmetad' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: lvmetad is not installed
frank@frank-110-194:~$ sudo apt-get install lvmetad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lvmetad
```

---

### Post by shane_faulkinbury2 on 2017-05-05
Well after completing the lightdm command and rebooting the errors are still there.  ](*,)

---

### Post by Dennis N on 2017-05-05
These look like warnings, not errors. I see similar messages about "lvmetad not active", etc. on an lvm install, but it does not affect usability - it still boots to the desktop and all is normal. Maybe the daemon lvmetad is not starting soon enough, and a fallback scan is performed. 

So, if the system boots up anyway, I think you just ignore the warnings.   

I looked into it once, and lvmetad is a demon that runs in the background and maintains and caches info about the state of the volumes on the disk to avoid unneeded scanning of disk state when doing lvm commands. Speeds things up.

BTW, You can google the warning messages, and find much discussion on this.

---

### Post by shane_faulkinbury2 on 2017-05-06
After my first restart after running the [COLOR=#333333][FONT=Ubuntu]sudo dpkg-reconfigure lightdm command I got the same messages.  Yesterday when I booted there were no messages as was today!  So I'm going to consider it fixed and try it on my laptop.

Thanks, [/FONT][/COLOR][COLOR=#000000]Xian[/COLOR]

---

