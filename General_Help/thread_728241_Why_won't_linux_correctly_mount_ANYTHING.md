---
title: "Why won't linux correctly mount ANYTHING?"
date: 2008-03-18
forum: General Help
---

### Post by yochaigal on 2008-03-18
Hello Everybody.  
One of the biggest problems I think we as a community face is the fact that some stuff just doesn't work right ---- I'm not going to list any of these things, as everyone has different experiences with different distros and all ---- but I  do think we can all agree that GNU/Linux isn't perfect, no OS is.

One major flaw I've found is with mounting devices.  Here's an example:

A new linux user is using Ubuntu Gutsy Gibbon, Gnome or KDE.
They have one external USB hard drive, and one USB flash drive.  Let's say they first plug in the external drive, it mounts under /dev/sda1  (successfully, let's assume hotplugging works) to the location /media/disk.
The user plugs in the flash drive. It mounts as /dev/sda2 to the location /media/usbdisk.  
Success!  But wait, what happens if the user unmounts both devices, and then reverses the procedure? What if he mounts the usb drive first?

Lo and behold, the opposite happens:it configures them as /dev/sda2 and /dev/sda1, respectively mounting the external drive to /media/usbdisk, and vice-versa.
Now, /etc/fstab allows you to assign device markers (/dev) to certain mountpoints, right? But how can one effect which new device is assigned which marker?  With UUIDS, right? 
But when one assigns UUIDs to certain /devs, it effectively disables hotplugging!
So where are we? Back at the beginning!  
Now, I may be wrong about a few of the particulars here, and if so, please, please correct me.  But does anyone know a way around this?  
In Windows XP, Vista, and Mac OS X, one can assign a mount point/drive/partition a permanent name.
This is very annoying; for example if I have shifting mount points then my ktorrent, amarok saved locations get screwed up. Also, my thumbnails disappear and have to re-load (I have thousands of video files).  Annoying.

Any help? I should mention this happens in Gnome up to 2.22, KDE 3.5 and 4.0. 

Thanks for reading

---

### Post by justin whitaker on 2008-03-18
This is actually more of an Ubuntu bug than a "Linux in general" bug. I've noticed this behavior in both Gutsy and Hardy, but not in Mandriva, Slackware, Fedora, etc...that said , so long as it is mounted, and read/write-able that is a GIGANTIC step forward from the bad old days. :)

---

### Post by yochaigal on 2008-03-18
I completely agree.
But I've had the exact same problem in Fedora and PCLINUXOS.
You are right, though --- I should try other distros as well.

Oh, it's an XFCE problem as well.

---

### Post by PeterJS on 2008-03-18
There isn't a clean way to do this graphically. But you could write some custom udev rules to recognize devices by manufacture ID, serial number, or some other unique trait, and then have udev give them unique names based on that, back when I was running gentoo I had my ipod set up to show up as /dev/ipod.

Here's a thread on writing udev rules:
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

### Post by yochaigal on 2008-03-18
Yeah I've tried that before -- to some success.
Again, this is something that should be easier (ie graphical) because it's pretty basic and new users get turned off by it.

thanks!

oh, has anyone used this partition mounting tool? 
[http://flomertens.free.fr/disk-manager/features.html](http://flomertens.free.fr/disk-manager/features.html)

also, look at this:
[https://blueprints.launchpad.net/ubuntu/+spec/fstab-gui](https://blueprints.launchpad.net/ubuntu/+spec/fstab-gui)

and this:
[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

### Post by justin whitaker on 2008-03-18
> **yochaigal said:**
> Yeah I've tried that before -- to some success.
Again, this is something that should be easier (ie graphical) because it's pretty basic and new users get turned off by it.

thanks!

oh, has anyone used this partition mounting tool? 
[http://flomertens.free.fr/disk-manager/features.html](http://flomertens.free.fr/disk-manager/features.html)

also, look at this:
[https://blueprints.launchpad.net/ubuntu/+spec/fstab-gui](https://blueprints.launchpad.net/ubuntu/+spec/fstab-gui)

I haven't used the first one, but it looks interesting.

---

### Post by kamicosmos on 2008-04-24
I have also been concerned about the way Ubuntu seems to uncleanly mount USB devices.  I'm paranoid about making sure the devices are powered off and such before I remove them, I've had friends kill flash cards and iPods by just yanking them off the docks and such.

Biggest concern is now that my Creative Zen is talking and transferring files with Amarok, every time after I 'disconnect' it, the device is hung, and I have to reset it.  I've had this device for over a year and a half, and it has never froze up on me, and it's been mounted on many PC's running Win2K, XP and even MacOSX!  I didn't even know it had a reset button on it till I mounted it under Ubuntu, heh.  Any way to manually verify that the device is unmounted correctly, so it stops freezing up?


I do agree though, compared to a couple years ago, just being able to auto-mount and access USB devices in linux is Amazing!  It's almost like 1997 when Win95C became USB compatible or something!  :P

---

