---
title: "How to test for a module and remove or disable it"
date: 2007-04-12
forum: General Help
---

### Post by voipfc on 2007-04-12
How do you test for the existence of a module, and remove or disable it if necessary? I want to find out if a module named EVMS is on my system and remove it.

---

### Post by kidders on 2007-04-12
Hi there,

You could try something like **modprobe -l "*evms*"** to find a matching module.[LIST]
[*]List only loaded modules: **lsmod | grep evms**
[*]Unload specified module: **rmmod evms**[/LIST]Removing kernel modules is _not_ a good idea for a variety of reasons. If you don't want a module to be loaded automatically, you should blacklist it in /etc/modprobe.d/blacklist ... but only if you know what you're doing.

---

### Post by voipfc on 2007-04-12
I checked the command and evms is not listed in it.

What do the numbers listed under the 'used by'  column in lsmod indicate?

Installed Xen and I now can't mount volumes on my second hard disk.

I googled around and EVMS is one of the things that came up, but it is apparently not installed.

Is there some way to diagnose what modules and routines might be the cause?

---

### Post by kidders on 2007-04-12
Hey again,

> **voipfc said:**
> I checked the command and evms is not listed in it.A standard Ubuntu install doesn't contain a module called "evms".

> **voipfc said:**
> What do the numbers listed under the 'used by'  column in lsmod indicate?The usual output format of **lsmod** is  "name, size, use count, referring modules", eg "bluetooth 62340 8 rfcomm,hidp,l2cap,hci_usb".

> **voipfc said:**
>  Installed Xen and I now can't mount volumes on my second hard disk.The reason for that very much depends on *why* you can't mount them. For instance...

[LIST]
[*]Is your hard disk detected?
[*]Are all the partitions on it detected?
[*]What is the result of an attempt to mount one of them?[/LIST]

---

### Post by voipfc on 2007-04-12
> **kidders said:**
> 

[LIST]
[*]Is your hard disk detected?
[*]Are all the partitions on it detected?
[*]What is the result of an attempt to mount one of them?[/LIST]

```
admin@ubuntu606m:~# mount /dev/sdb1 /backup1
mount: /dev/sdb1 already mounted or /backup1 busy

```

The hard disks are definitely detected.

---

### Post by kidders on 2007-04-12
> **voipfc said:**
> mount: /dev/sdb1 already mounted or /backup1 busy
Yep, your disk is working alright. :-)

Are the suggestions "mount" offers sensible?

**/dev/sdb1 already mounted**
You can check that by typing something like **mount | grep sdb1**. Linux can object to double-mounting things, but you *can* "rebind" a mounted filesystem to a second location, if you wish.

**/backup1 busy**
That's a curious idea! Even if **lsof | grep backup1** produced results (indicating that it, or something in it, was in use), mount shouldn't complain about it. Equally, I've never known mount to moan about mounting something at /backup1, and then mounting something else right on top of it ... so I have no idea what would fit this description.

I'm a little confused by this one :-( (although it might help if I knew how Xen worked lol!) Apparently it's a sort of a virtual machine gizmo. If using it involves running chrooted environments (just a wild guess), it can sometimes be difficult to pin down exactly what's mounted, and where (multiple mtabs).


Is any of this *any* help at all?!

---

### Post by voipfc on 2007-04-12
> **kidders said:**
> Yep, your disk is working alright. :-)

Are the suggestions "mount" offers sensible?

**/dev/sdb1 already mounted**
You can check that by typing something like **mount | grep sdb1**. Linux can object to double-mounting things, but you *can* "rebind" a mounted filesystem to a second location, if you wish.

**/backup1 busy**
That's a curious idea! Even if **lsof | grep backup1** produced results (indicating that it, or something in it, was in use), mount shouldn't complain about it. Equally, I've never known mount to moan about mounting something at /backup1, and then mounting something else right on top of it ... so I have no idea what would fit this description.

I'm a little confused by this one :-( (although it might help if I knew how Xen worked lol!) Apparently it's a sort of a virtual machine gizmo. If using it involves running chrooted environments (just a wild guess), it can sometimes be difficult to pin down exactly what's mounted, and where (multiple mtabs).


Is any of this *any* help at all?!
Yes

I have searched around and it appears it could be due the the device mapper. Xen appears to have installed some addition stuff relating to it. If it is not needed I will simply turn it off

---

