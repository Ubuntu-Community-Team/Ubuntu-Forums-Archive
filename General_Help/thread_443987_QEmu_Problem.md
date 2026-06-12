---
title: "QEmu Problem"
date: 2007-05-14
forum: General Help
---

### Post by Gathalimay on 2007-05-14
Hey, everyone. I have a problem here with Qemu

Whenever I load up QEmu

```
[Username]@[Username]-desktop:~$ qemu -localtime -cdrom /WindowsFat/WXPVOL_EN.iso -m 256 -boot d windows.img
Could not open '/dev/kqemu' - QEMU acceleration layer not activated

```

It says it can't load the acceleration layer. I'm assuming "/dev/kqemu" is like a little filesystem icon or something I should be able to see in the /dev folder. I'm not seeing anything. I'm assuming that this is also why it is really really slow on the install. Yes, the ram I put in is low (256) but I only have 768 Megs of RAM and VirtualBox seems to work perfectly with that. (The reason I want to try QEmu is because I want to see some things with the CD drive functionality).

I'm using an ISO because /dev/cdrom fails when I set that instead of the ISO. Another side problem.

Any Ideas?
Thanks in advance.

---

### Post by mitko_ on 2007-05-15
Try running the same command with super user privileges.

---

### Post by Gathalimay on 2007-05-15
I already did that. Didn't work :(

I think something is failing to create. I've even re-installed it.

---

### Post by mitko_ on 2007-05-16
I use this shell script to load the kqemu module.

```

#!/bin/bash

KQEMUMODULE=kqemu

DEVFILEPATH=/dev/kqemu

MODPROBE=`which modprobe`
MKNOD=`which mknod`
CHMOD=`which chmod`

if [ `id -u` -gt 0 ]; then
    echo "Need root permissions to run."
    exit 1
fi

echo "***Adding kqemu module..."
$MODPROBE $KQEMUMODULE

echo "***Making file $DEVFILEPATH ..."
$MKNOD $DEVFILEPATH c 250 0

echo "***Changing permissions to $DEVFILEPATH .."
chmod 655 $DEVFILEPATH

sleep 1

echo "$0 is done!"

```

As you can see, it creates the file */dev/kqemu*. The script maybe looks complicated, but what it really does is this: load the module, make the file and change the privileges. The short version is:

```

$ sudo modprobe kqemu 
$ sudo mknod /dev/kqemu c 250 0
$ sudo chmod 655 /dev/kqemu

```

Check to see if the module is loaded correctly with* lsmod*. It should look something like this:

```

mitko@mashina:~/qemu$ lsmod | grep kqemu
kqemu                 124580  0 

```

Good luck! :)

---

### Post by Gathalimay on 2007-05-16
It worked!!

Thanks a lot man \\:D/

---

