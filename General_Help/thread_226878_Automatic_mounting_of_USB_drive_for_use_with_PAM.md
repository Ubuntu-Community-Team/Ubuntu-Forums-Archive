---
title: "Automatic mounting of USB drive for use with PAM"
date: 2006-07-31
forum: General Help
---

### Post by VonBraun on 2006-07-31
I've searched far and wide for an answer to this problem, so I'm fairly sure this post is not redundant.

My overall goal is to use a private key stored on a USB drive along with a password to login to my computer.  To do this, PAM needs to be able to access the USB drive in a fixed location like "/media/COOLUSB".  Unfortunately my USB drives mount as "/media/sd?1".  When I first isntalled Ubuntu, they would mount with the label as the name ("/media/COOLUSB") but somewhere between installing Kubuntu and installing ATI graphics drivers this functionality change to the less desirable "/media/sd?1" format.

_Solutions that do not work (AFAIK)_

[LIST=1]
[*]use fstab to point to /dev/somefixedname - Doesn't work because it doesn't mount automatically.  It seems taht I would have to have the USB plugged in at boot for this to work.  I want to be able to walk up to the computer at a login prompt, insert my usb "key" and type username and password.
[*]use pmount - I know pmount is how you mount devices in ubuntu 6.06, but that doesn't help me because I want it to be automatically mounted when I insert the USB drive into the USB port
[/LIST]
_Solution? _

I have a good tutorial on how to setup PAM to do authentication so that's not the question.  I'd like to figure out how to get a USB drive to automatically mount itself to a specific location in the FS before logging in.

Thanks,
VonBraun

---

### Post by VonBraun on 2006-08-02
Any ideas?

---

### Post by skidrash on 2007-06-04
plug in the drive

at the prompt, 

dmesg | less

figure out what device the system assigns to the USB device (probably something like /dev/sdd1 or /dev/sde1)


now use the vol_id command
at the prompt command below, put your device that you just got in place of /dev/sdd1

[FONT="Courier New"]vol_id -u /dev/sdd1
50EC-1809                    [/FONT]    <--- this is what mine is 

now put this number in your fstab, like so (this is one line, HTML may split it)

[FONT="Courier New"]UUID=50EC-1809  /permanent/mount/point   vfat    rw,user,nosuid,nodev,noexec,noatime,uid=1000,gid=1000   1       1[/FONT]

now unmount and remount the stick

[FONT="Courier New"]umount /dev/hdd1

mount /dev/hdd1 [/FONT]

and now it should be in the permanent position.

---

