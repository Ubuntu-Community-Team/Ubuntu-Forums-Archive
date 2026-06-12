---
title: "Need USB devices to be recognized by Winxp virtual server."
date: 2007-11-28
forum: General Help
---

### Post by Calybos on 2007-11-28
Anyone know how to make Winxp in Vmware virtual server recognize USB devices?

---

### Post by illbashu on 2007-11-28
i am haveing this same prob! [My thread](http://ubuntuforums.org/showthread.php?t=625998)

---

### Post by Calybos on 2007-11-28
Yeah i read that. I'm still trying to get it to work and looking in other forums. If i can't get it to work soon, ill just have to call on the I.T. dept. of my company to fix this. As soon as i can get this working all post what they did to make it work for you.

---

### Post by fjgaude on 2007-11-28
> **Calybos said:**
> Anyone know how to make Winxp in Vmware virtual server recognize USB devices?

See this post, msg #4, for solution:

[http://ubuntuforums.org/showthread.php?t=626062](http://ubuntuforums.org/showthread.php?t=626062)

Good luck.

---

### Post by Calybos on 2007-11-28
Thank you very much for your time. I'm sorry for the double posting, just didn't think i was clear enough.

---

### Post by illbashu on 2007-11-28
ya, i dont get what he means by "Lines 42-45 get uncommented, starting with #mkdir -p /dev/bus/usb/.usbfs."

---

### Post by fjgaude on 2007-11-28
> **illbashu said:**
> ya, i dont get what he means by "Lines 42-45 get uncommented, starting with #mkdir -p /dev/bus/usb/.usbfs."

Make the four lines look like this in the text file:

	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

You remove the "#" mark to uncomment. You will have to do it with the superuser command "sudo". Count down the lines in the file until you get to "mkdir -p    " and delete the #s in front of each of the four lines.

---

### Post by Floppyjoe on 2007-12-01
> **fjgaude said:**
> Make the four lines look like this in the text file:

	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

You remove the "#" mark to uncomment. You will have to do it with the superuser command "sudo". Count down the lines in the file until you get to "mkdir -p    " and delete the #s in front of each of the four lines.

I tried the above and the virtual machine still does not recognize any USB devices. Do you need to reboot the computer? I powered down the virtual machine then shutdown vmware and restarted vmware after the changes.

---

### Post by fjgaude on 2007-12-01
You need to reboot, yes.

Or

```
sudo /etc/init.d/mountdevsubfs.sh start
```

That should do it also.

Then go into VM tab once you have VMware loaded and Windows running and click Removable devices. From there click on the USBs you want active. Of course you have installed the VMware Tools, eh?

---

### Post by Floppyjoe on 2007-12-01
> **fjgaude said:**
> You need to reboot, yes.

Or

```
sudo /etc/init.d/mountdevsubfs.sh start
```

That should do it also.

Then go into VM tab once you have VMware loaded and Windows running and click Removable devices. From there click on the USBs you want active. Of course you have installed the VMware Tools, eh?

Yes Vmware tools installed. That worked perfectly for me now. Thanks!
Now I can use my Garmin GPS 18 device in the Virtual Machine using the Windows software and maps. Works great. Thanks Again!

---

### Post by illbashu on 2007-12-02
> **fjgaude said:**
> You need to reboot, yes.

Or

```
sudo /etc/init.d/mountdevsubfs.sh start
```

That should do it also.

Then go into VM tab once you have VMware loaded and Windows running and click Removable devices. From there click on the USBs you want active. Of course you have installed the VMware Tools, eh?
its still not working for me, when i try that sudo i get this

```
ln: creating symbolic link `/dev/bus/usb/devices' to `.usbfs/devices': File exists
```

i restarted my comp too, vm still wont see my psp! :mad:

---

### Post by fjgaude on 2007-12-02
Did you uncomment those four lines, as suggested in earlier posts?

---

### Post by illbashu on 2007-12-02
yes... this is how they look...

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs mountvirtfs
# Required-Start:    mountkernfs
# Required-Stop:
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO

PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT="-osize=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm $SHM_OPT

	#
	# Mount /dev/pts. Create master ptmx node if needed.
	#
	domount devpts "" /dev/pts -ogid=$TTYGRP,mode=$TTYMODE

	#
	# Magic to make /proc/bus/usb work
	#[B]
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb[/B]
}

case "$1" in
  "")
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
	do_start
	;;
  start)
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountdevsubfs [start|stop]" >&2
	exit 3
	;;
esac

```

---

### Post by fjgaude on 2007-12-03
Good, looks correct, now:

Did you go to the VM menu tab and click it, then click Removable Devices, then USB Devices? Select the USBs you wish active.

Let us know how things go.

---

### Post by illbashu on 2007-12-03
it still says empty... :mad: i have vm tools installed :/

---

### Post by fjgaude on 2007-12-03
That's about the limit of my knowledge... maybe others will be of more help.

---

### Post by illbashu on 2007-12-04
i think i know whats wrong, ubuntu is putting my psp as a root drive instead of a tape drive, when i go to change it, it says "you do not have the permission"

---

### Post by fjgaude on 2007-12-04
Let us know when you get it all working correctly, eh?

---

### Post by illbashu on 2007-12-10
i have been working on this for hous i just cant get it to work!!!!! :( :cry: i even reinstalled the whole thing! someone plz help me!!!!!!

---

### Post by fjgaude on 2007-12-10
> **illbashu said:**
> i have been working on this for hous i just cant get it to work!!!!! :( :cry: i even reinstalled the whole thing! someone plz help me!!!!!!

Okay, try putting this in your fstab file and reboot:

usbfs           /proc/bus/usb   usbfs     auto               0       0

---

### Post by illbashu on 2007-12-10
i tried that too!!!!!!!1 and it still doesn't work! man i hate linux! :mad: :cry: do i have to reboot my comp?

i rebooted my comp and it still doesn't ****ing work! :mad:

---

### Post by illbashu on 2007-12-10
YES! i got it to work!!!! WOOT!!!!!!!!!!!!! i went into "edit virtual machine" then i click on add and click on usb controller and it is seeing my psp and my usb devises !!!!!

---

### Post by illbashu on 2007-12-10
i found out something about my way. the usb drive **has to** be mounted on ubuntu when u activate it or else it will say "unknown usb drive" or something like that when try to connect it to windows... it will basicly not know what type of usb it is, hence wont have any drivers for it.

sry for the triple post...

---

### Post by fjgaude on 2007-12-11
Gosh, it sounds like you don't rate Linux afterall. <smile>

Finally, you got it right. Congratulations... patience is the best teacher when it comes to these kinds of things, eh?

---

### Post by High_Noonan on 2008-01-20
> **illbashu said:**
> YES! i got it to work!!!! WOOT!!!!!!!!!!!!! i went into "edit virtual machine" then i click on add and click on usb controller and it is seeing my psp and my usb devises !!!!!

THANK YOU!!!!!!!!!:popcorn:

---

### Post by laffys on 2008-02-04
Quote:
Originally Posted by illbashu View Post
i have been working on this for hous i just cant get it to work!!!!! i even reinstalled the whole thing! someone plz help me!!!!!!
Okay, try putting this in your fstab file and reboot:

usbfs /proc/bus/usb usbfs auto 0 0


how do i add this to my fstab file?

---

