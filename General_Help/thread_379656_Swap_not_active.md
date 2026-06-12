---
title: "Swap not active"
date: 2007-03-08
forum: General Help
---

### Post by mk04 on 2007-03-08
Each time I turn on my computer I have to activate swap manually "sudo swapon /dev/hda5". Is there a way for it to turn it on automatically?

---

### Post by taurus on 2007-03-08
You do that in /etc/fstab.  What does your /etc/fstab look like anyway?  There should be an entry in there that would look something like this.

```
/dev/hda5   none   swap   sw   0   0
```

---

### Post by mk04 on 2007-03-08
here is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=e810623f-c168-475a-b363-c6a3bd701321 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=31950178-c64a-4156-8db6-0d27347debdf none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by erdalronahi on 2007-03-09
I have the same problem. My swap partition is listed in fstab, but somehow it doesn't get activated automatically anymore. This problem occured only this week (Herd 5), I didn't have it before.

---

### Post by llamakc on 2007-03-09
> **erdalronahi said:**
> I have the same problem. My swap partition is listed in fstab, but somehow it doesn't get activated automatically anymore. This problem occured only this week (Herd 5), I didn't have it before.

Herd 5? You're using Feisty? Ask in that forum on how to fix it.

One can check the correct uuid with:

```

sudo vol_id -u /dev/hda5

```

For /dev/hda5.

Compare that with what's in your /etc/fstab.

---

### Post by taurus on 2007-03-09
> **mk04 said:**
> here is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=e810623f-c168-475a-b363-c6a3bd701321 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
**UUID=31950178-c64a-4156-8db6-0d27347debdf none swap sw 0 0**
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Replace the one in bold with this line.

```
/dev/hda5   none   swap   sw   0   0
```
You can edit /etc/fstab with

```
gksudo gedit /etc/fstab
```
Once you're done editing, save the change and _reboot_.  Now, what is the output of this command from a terminal after the system is up again?

```
free
```

---

### Post by mk04 on 2007-03-10
Taurus, that worked perfectly! Thanks.

Here is the output of "free":

```
             total       used       free     shared    buffers     cached
Mem:        450788     322768     128020          0      10080     167812
-/+ buffers/cache:     144876     305912
Swap:      1317288          0    1317288

```

---

### Post by erdalronahi on 2007-03-10
Replacing the UUID with the device number worked for me, too. :)

---

### Post by llamakc on 2007-03-10
Additionally, one may activate a swap partition without rebooting with

```

sudo swapon /dev/hd??

```

...replacing the above with the correct partition of course. To make it active on next boot, you still need to add it to /etc/fstab.

---

### Post by erdalronahi on 2007-03-10
```
sudo swapon -a
```
is even simpler.

---

