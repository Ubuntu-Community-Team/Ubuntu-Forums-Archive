---
title: "I can't mount CD-Rom. scd0 does not exist!"
date: 2007-01-16
forum: General Help
---

### Post by jofre on 2007-01-16
Hi ,

I was trying to just read a CD and it was not working. I tried to mount manually, but:

jofre@jofre-desktop:/dev$ sudo mount /media/cdrom0/ -o unhide
mount: special device /dev/scd0 does not exist

When you go to check the /etc/fstab file you find that:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

How can I mount the cdrom? It is this a bug on Edgy?

Thanks a million

---

### Post by pay on 2007-01-16
Maybe the cd is damaged or a format that isn't being detected. Try changing udf,iso9660 to auto

---

### Post by jofre on 2007-01-16
I get the same message.  scd0 still does not exist.

---

### Post by hal10000 on 2007-01-16
see if your devices exist:
[COLOR="Red"]ls -l /dev/scd*[/COLOR]
and 
[COLOR="Red"]ls -l /dev/cdrom*[/COLOR]

And maybe you should try another cd which you know it's not damaged.

---

### Post by jofre on 2007-01-16
Hi Hal, 
here is what I get:

jofre@jofre-desktop:~$ ls -l /dev/scd*
ls: /dev/scd*: No such file or directory
jofre@jofre-desktop:~$ ls -l /dev/cdrom*
ls: /dev/cdrom*: No such file or directory



I never had any problem with Dapper. I just realize is the first time I tried to read a cdrom since I installed Edgy from scratch...

---

### Post by hal10000 on 2007-01-16
There seems to be something wrong with your hardware detection, because the necessary devices in your /dev directory don't exist. They should be automatically created.
Have you installed the hal, udev and discover1 (or discover2) packages?

What about the other hardware on your system?
Did you verify that your cdrom works with other Systems (e.g. Windows)?

---

### Post by jofre on 2007-01-16
I check and I had installed hal and udev, but not discover1. I install discover1, but I when I try to used, there is no output, and it is not said where the output goes in the man file.

It works fine in windows.

It is strange... taking into account I install Edgy with this unit!

(By the way: thanks!)

---

### Post by hal10000 on 2007-01-16
Try the hdparm command: [COLOR="Red"]sudo hdparm /dev/scd0[/COLOR]
and [COLOR="Red"]ls -l /dev/ | grep hd[/COLOR]
and post the outputs.

EDIT: the hdparm won't work sice you hve no scd0 device

---

### Post by hal10000 on 2007-01-16
Try the command [COLOR="Red"]dmesg | grep scd[/COLOR]

Was your cdrom once working with ubuntu?

---

### Post by jofre on 2007-01-16
Hi Hal, 

Here is the output you were asking for:

jofre@jofre-desktop:~$ ls -l /dev |grep hd
jofre@jofre-desktop:~$ sudo hdparm /dev/scd0
/dev/scd0: No such file or directory
jofre@jofre-desktop:~$ ls -l /dev |grep hd
jofre@jofre-desktop:~$ dmesg | grep scd


let me say that if I was typing just dmesg, I was getting a hell of staff, among it:
[17179751.548000] sdc: Write Protect is off
[17179751.548000] sdc: Mode Sense: 27 00 00 00
[17179751.548000] sdc: assuming drive cache: write through
[17179751.548000] SCSI device sdc: 156301488 512-byte hdwr sectors (80026 MB)
and similar things. It is this type of information you were looking after? If it is, I don't know why did not pop out with grep.

I had no problem with Dapper and Breezy.

Thanks again,
Jofre.

---

### Post by hal10000 on 2007-01-16
All the comand could not find any sata or scsi cdrom device.

I have three last ideas:
1. shut down your computer, open the case and look if all cables are plugged in.
2. just reboot (maybe your computer had a hiccough when booting the last time)
3. install the lshw package, run [COLOR="Red"]lshw |less[/COLOR] and look if there is any cdrom found (lshw has a lot of output).

---

### Post by hal10000 on 2007-01-16
> I had no problem with Dapper and Breezy
does this mean the error occured after an upgrade?

---

### Post by jofre on 2007-01-16
Thanks a lot for your time Hal.

2- I had reboot already a few times.
3- I did not see any cdrom when I run "lshw |less"  (I saw the hard drives, cpu, display, sound, usb,...)
4- The cd-rom works fine with Windows XP SP2, (I just tried) (so no need for 1.-)


"does this mean the error occured after an upgrade?"

Yes and no. I did not upgrade, I did a clean Edgy install. I never upgrade, I read too many scary things about it, I found it is just easier have a partition for home, and do a clean installation. As I said earlier, I had no problems with Dapper and Breezy. I wonder if I should reinstall Dapper... I would not like to go backwards do...

---

### Post by hal10000 on 2007-01-16
That's very very strange to me.

The only thing i could do now was to look throgh the packages to see if there are hardware related packages that could be tested

Sorry.

---

### Post by jofre on 2007-01-16
Thanks anyway Hal10e4.

At least you tried:)

---

### Post by enix on 2007-02-03
eek! I get the same error mesg but am still using dapper, my symptoms are exact. I hope people still read this, i see its old.

---

### Post by dr_d12 on 2007-02-11
Hi,
I just had the same symptoms trying to read a CD or DVD from a USB drive. Rebooting with the drive plugged in didn't help. The I tried unplugging and replugging the USB while the computer and drive were on, then it auto-mounted.
Dave

---

### Post by sda5150 on 2007-02-11
Just a suggestion......

I think the previous people were on the right track...  Maybe your CD-ROM has assumed a different device name. Check out what is in your /dev directory.

---

### Post by Nucktown on 2007-02-28
I've been having the same exact problem, the outputs I've gotten have all been the same as well.

The drive works perfectly fine in XP.

In my /dev .. nothing looks like it'd be my DVD/RW drive, just 3 sdas, 3 sdbs, and 3 sdcs

---

### Post by Nucktown on 2007-02-28
also, I booted into the older kernel, 2.6.17-10... and it's working fine.. but it won't work on 2.6.17-11

kernel bug?

---

### Post by ~viper~ on 2007-04-06
yea, recently came across this error, since i hadnt mounted cd for a while...

before I had edited /etc/fstab to mount   /dev/scd0 at the location /mnt/cdrom0:
```
/dev/scd0       /mnt/cdrom0   udf,iso9660 rw,user,noauto     0       0
```

i guess edgy must have played w/ the naming ... for if i change the device in the line above to /dev/cdrom, then it mounts fine.

**Note:** I prefer the noauto option, so that I can go into the /mnt directory and manually mount the cd with something like 'sudo mount cdrom'  since /mnt/cdrom is simply a link to /mnt/cdrom0 on my system.

---

