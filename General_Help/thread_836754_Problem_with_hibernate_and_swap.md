---
title: "Problem with hibernate and swap"
date: 2008-06-21
forum: General Help
---

### Post by ztrange on 2008-06-21
Hello, When trying to hibernate, I get the following error and return to the session untouched:

```

[numbers.numbers] uvcvideo: Failed to query(1) UVC control 2 (unit0): -71 (exp. 26)
[numbers.numbers] uvc video 5-8:1.1: resume error -5
[numbers.numbers] swsusp: Cannot find swap device try swapon -a
```
Note: these lines are fast-copied from the screen...

when I try the swapon -a suggested:

```
mario@beula:~$ swapon -a
swapon: cannot canonicalize /dev/disk/by-uuid/c60429a4-3ba9-4324-8420-2645c422bf68: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/c60429a4-3ba9-4324-8420-2645c422bf68: No such file or directory
```

Also, I have to say that i moved a lot the partitions after the Hardy install to make them the sizes and positions I wanted. I'm affraid I did something wrong...

Any help will be appreciated

---

### Post by ztrange on 2008-06-21
I tried to enable my swap editing /etc/fstab and using de /dev/name as it says in [this]("http://ubuntuforums.org/showthread.php?t=802398") thread but now i get this:

```

mario@beula:~$ swapon -a
swapon: /dev/sda5: Operation not permitted

```

Am I doing sometihng wrong or the swap is completely messed up...

Here is my /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d6fab30f-8767-473c-971b-6b945c16c2bc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
#UUID=c60429a4-3ba9-4324-8420-2645c422bf68 none            swap    sw              0       0
/dev/sda5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda3	/home/mario	ext3	defaults 0 0

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

```

---

### Post by ztrange on 2008-06-21
Well, the operation not permitted was just because of not using sudo my BIG mistake...

So, now I have a functional swap, I think because I get this:
```

mario@beula:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	4192956	0	-1

```

Well, but the main thing, the hibernate, is still not working, I still get the firs two lines that I got at first and some others that pass very fast before my laptop shutting down:

```

[numbers.numbers] uvcvideo: Failed to query(1) UVC control 2 (unit0): -71 (exp. 26)
[numbers.numbers] uvc video 5-8:1.1: resume error -5

```

Well, any help aimed to solve this hibernate problem will be appreciated.

---

### Post by jimzat on 2008-06-24
I have been running Gutsy on my Dell Inspiron 7500 since shortly after its release and until recently hibernation worked great.  Sometime in the past few weeks, whenever I try to reboot from hibernation the swap partition won't mount.

I log in to a virtual terminal (XFCE loads too slowly w/o the swap) and load parted.  The "print" command shows the swap partition's file system field blank.  I have to define it and then execute "swapon" and all is well again.

This happens every time I try to hibernate, but not if I do a full shutdown.

jimzat

---

### Post by jimzat on 2008-06-24
I just did some more digging and found bug #113232 <https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/113232>



The solution proposed is to edit your /boot/grub/menu.lst file and add "resume=/dev/<path to your swap>" at the end of the line beginning with
"# defoptions=".

You will also want to add the "resume" information to the line indicating the kernel you are booting.


I did this and now when I hibernate the system comes back just like I left it.  (I only tried it once.)


Hope this helps,

jimzat

---

