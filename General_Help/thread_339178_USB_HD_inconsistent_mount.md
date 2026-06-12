---
title: "USB HD inconsistent mount"
date: 2007-01-15
forum: General Help
---

### Post by jackocleebrown on 2007-01-15
Hi,

I'm having problems with my USB HD. The drive auto-mounts fine but, as I'm using this new drive to store all my music, I wanted to define a specific mount point of /musica/ (this is the location on my internal drive where I was storing my music files before I ran out of space) I had no problem doing this with an entry in /etc/fstab like this:

/dev/sdb1	/musica         ext3    user,auto,noatime,rw,async,noexec        0       0

I can then mount the drive to the correct mount point with a simple "mount -a".

The problem that I have is on boot. The drive does not always mount correctly: sometimes it does not mount at all. sometimes it auto-mounts to another location. sometimes it works fine.

I have also tried defining the fstab entry with the partition label:

LABEL=musica	/musica         ext3    user,auto,noatime,rw,async,noexec        0       0

but I run into the same problems. The problem can always be sorted with a "umount /dev/sdb1" followed by a "mount -a". But this is no good if my girlfriend is using the computer!

If I had to guess I'd say that it takes too long for the drive to "react" when the computer is powered on and it is not detected by the system until after the filesystems are mounted.

Any suggestions?

Thanks for your help in advance!

Jack.

---

### Post by jackocleebrown on 2007-01-16
Hi All,

Have given up on using Fstab to set the mount point for the moment. I have removed the fstab line & just put a symbolic link from /media/musica to /musica. Still interested to find the "proper" way to do this!

Thanks, Jack.

---

### Post by jackocleebrown on 2007-01-19
Right! Think I have cracked it!

The secret is to make a udev rule that mounts the drive when it is hot plugged.

What I did (The drive I am trying to mount is /dev/sdb1):

1) install sysfsutils - this allows you to identify devices by sysfs characteristics when they are hot-plugged

*sudo aptitude install sysfsutils*

2) find out some sysfs characteristic of the device that you are mounting

*udevinfo -a -p /sys/block/sdb*

This returns a load of stuff the section I picked out was:

[I]looking at device '/devices/pci0000:00/0000:00:03.3/usb4/4-4':
    ID=="4-4"
    BUS=="usb"
    DRIVER=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="UA09WS3C"
    SYSFS{product}=="Maxtor 3200"
    SYSFS{manufacturer}=="Maxtor Corporation"
    SYSFS{maxchild}=="0"
    SYSFS{version}==" 2.00"
    SYSFS{devnum}=="3"
    SYSFS{speed}=="480"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bcdDevice}=="0001"
    SYSFS{idProduct}=="3200"
    SYSFS{idVendor}=="0d49"
    SYSFS{bMaxPower}=="100mA"
    SYSFS{bmAttributes}=="c0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"[/I]

3) write a udev rule using the info above to identify the correct device

 *sudo gedit /etc/udev/rules.d/90-maxtor.rules*

You can call the file what you like but keep the "90-..." format as this defines the priority of the rule.

inside the file I have:

[I]# external HD
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="Maxtor 3200", SYMLINK+="MaxtorHD%n", RUN+="/bin/mount -a"[/I]

The entries with equality statements "==" identify the device to which the rule applies so...

*BUS=="usb"*  points SYSFS to the usb bus
*KERNEL=="sd*"* device will by default appear in /dev/ as sd(something)
*SYSFS{product}=="Maxtor 3200"* characteristic to match from above output

The rest of the rule defines actions to execute when the device is hot plugged

*SYMLINK+="MaxtorHD%n"* this creates symbolic links in /dev/ from sdb to MaxtorHD & sdb1 to MaxtorHD1 & sdb2 to MaxtorHD2..... This lets you refer to the device from fstab using one of the linked entries which will not change even if the default device path suddenly becomes something else, e.g. sdc

*RUN+="/bin/mount -a"* This one is the key - udev will try and mount all drives with "user" option in fstab when this device appears.

4) Finally add an entry in /etc/fstab/, something like this:

*/dev/MaxtorHD1 /musica         ext3   user,auto,noatime,rw      0       0*


Unplug the drive, plug the drive back in and it is done!

Phew! 

I'll post an update if I discover any problems but a couple of reboots so far & everything seems ok! 

udev rule syntax reference here:
[http://www.reactivated.net/writing_udev_rules.html#syntax](http://www.reactivated.net/writing_udev_rules.html#syntax)
useful stuff to know... there are all sorts of things that you could do with this....

I hope that this is helpful for someone!

Jack.

---

### Post by SoKaK on 2007-01-19
oo masallah h&#305;zl&#305;s&#305;n&#305;z wery good [http://kabus22.bz.tc](http://kabus22.bz.tc)

---

### Post by jackocleebrown on 2007-04-04
Argh, just got another one of these drives - the udev rule I wrote above cannot tell the difference between the drives as I'm only matching  SYSFS{product}=="Maxtor 3200" only an issue if you have exactly the same drive - safer to also match by serial number

my new udev rule is:

[I]# external HD
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="Maxtor 3200", SYSFS{serial}=="UA09WS3C", SYMLINK+="MaxtorHD%n", RUN+="/bin/mount -a"
[/I]

All the best, Jack

---

