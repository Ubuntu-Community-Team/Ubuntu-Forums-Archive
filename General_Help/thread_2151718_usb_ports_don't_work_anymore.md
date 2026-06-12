---
title: "usb ports don't work anymore"
date: 2013-06-05
forum: General Help
---

### Post by tubunter on 2013-06-05
hello, 

I' m coming across a problem: my three usb ports don'twork anymore. I tried to edit the modules file by adding the line "usb-storage" and got one of the three ports working, but at the further restart it fails again...
could anyone help me to solve this?

thanks

PS ubuntu 12.04

---

### Post by varunendra on 2013-06-05
A fresh installation? If yes, it could be a corrupt installation source or otherwise broken installation. Also check your BIOS to make sure USB is enabled there.

Please post outputs of -
```
lspci -nnk | grep -iA2 usb
usb-devices
```

---

### Post by tubunter on 2013-06-06
```
user@user-L51RI1:~$ lspci -nnk | grep -iA2 usb
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller [1002:4374] (rev 80)
    Subsystem: Uniwill Computer Corp Device [1584:2b04]
    Kernel driver in use: ohci_hcd
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller [1002:4375] (rev 80)
    Subsystem: Uniwill Computer Corp Device [1584:2b04]
    Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
    Subsystem: Uniwill Computer Corp Device [1584:2b04]
    Kernel driver in use: ehci_hcd
user@user-L51RI1:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-45-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:13.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-45-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-45-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
user@user-L51RI1:~$ 

```

the output of lsusb command, with usb device plugged in:

```
user@user-L51RI1:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 008: ID 0951:1665 Kingston Technology **
user@user-L51RI1:~$ 

```

the ports are enabled in the bios (the usb mouse works fine for example).

Thanks

---

### Post by matt_symes on 2013-06-06
Hi

> **Bus 001 Device 008: ID 0951:1665 Kingston Technology**

What is exactly is this piece of equipment ?

You say the USB mouse is working correctly so is it only that peice of equipment above that is not working ?

Do usb pen drives work for instance ?

Please give more details as to what and what is not working.

Kind regards

---

### Post by tubunter on 2013-06-06
> You say the USB mouse is working correctly so is it only that peice of equipment above that is not working ?

Exactly.

> What is exactly is this piece of equipment ?

an usb pen drive.
Ports don't work with any usb pen drive...

---

### Post by matt_symes on 2013-06-06
Hi

Open a terminal and type

```
tail -f /var/log/syslog
```

Insert the USB pen drive into the computer and leave for 10 seconds or so.

Copy and paste the output produced into your next post.

This may have nothing to do with the USB ports on your system.

Kind regards

---

### Post by tubunter on 2013-06-06
```
user@user-L51RI1:~$ tail -f /var/log/syslog
Jun  6 12:49:48 user-L51RI1 kernel: [ 7930.078124] sd 8:0:0:0: [sdb] No Caching mode page present
Jun  6 12:49:48 user-L51RI1 kernel: [ 7930.078134] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jun  6 12:49:48 user-L51RI1 kernel: [ 7930.085109] sd 8:0:0:0: [sdb] No Caching mode page present
Jun  6 12:49:48 user-L51RI1 kernel: [ 7930.085122] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jun  6 12:49:48 user-L51RI1 kernel: [ 7930.104537]  sdb: sdb1
Jun  6 12:49:48 user-L51RI1 kernel: [ 7930.113029] sd 8:0:0:0: [sdb] No Caching mode page present
Jun  6 12:49:48 user-L51RI1 kernel: [ 7930.113048] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jun  6 12:49:48 user-L51RI1 kernel: [ 7930.113059] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Jun  6 12:49:53 user-L51RI1 kernel: [ 7934.692219] usb 1-8: USB disconnect, device number 9
Jun  6 13:17:01 user-L51RI1 CRON[7709]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  6 13:34:32 user-L51RI1 kernel: [10613.720094] usb 1-8: new high-speed USB device number 10 using ehci_hcd
Jun  6 13:34:32 user-L51RI1 kernel: [10613.862694] scsi9 : usb-storage 1-8:1.0
Jun  6 13:34:32 user-L51RI1 mtp-probe: checking bus 1, device 10: "/sys/devices/pci0000:00/0000:00:13.2/usb1/1-8"
Jun  6 13:34:32 user-L51RI1 mtp-probe: bus: 1, device: 10 was not an MTP device
Jun  6 13:34:33 user-L51RI1 kernel: [10614.925292] scsi 9:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 4
Jun  6 13:34:33 user-L51RI1 kernel: [10614.933776] sd 9:0:0:0: Attached scsi generic sg2 type 0
Jun  6 13:34:34 user-L51RI1 kernel: [10615.615103] sd 9:0:0:0: [sdb] 30916608 512-byte logical blocks: (15.8 GB/14.7 GiB)
Jun  6 13:34:34 user-L51RI1 kernel: [10615.616469] sd 9:0:0:0: [sdb] Write Protect is off
Jun  6 13:34:34 user-L51RI1 kernel: [10615.616479] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
Jun  6 13:34:34 user-L51RI1 kernel: [10615.617718] sd 9:0:0:0: [sdb] No Caching mode page present
Jun  6 13:34:34 user-L51RI1 kernel: [10615.617729] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun  6 13:34:34 user-L51RI1 kernel: [10615.624573] sd 9:0:0:0: [sdb] No Caching mode page present
Jun  6 13:34:34 user-L51RI1 kernel: [10615.624589] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun  6 13:34:34 user-L51RI1 kernel: [10615.643850]  sdb: sdb1
Jun  6 13:34:34 user-L51RI1 kernel: [10615.648839] sd 9:0:0:0: [sdb] No Caching mode page present
Jun  6 13:34:34 user-L51RI1 kernel: [10615.648855] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun  6 13:34:34 user-L51RI1 kernel: [10615.648865] sd 9:0:0:0: [sdb] Attached SCSI removable disk
```

---

### Post by matt_symes on 2013-06-06
Hi

The device is being recognised. Let's try to mount it.

With the device plugged in and from the terminal again.

Try to mount the device.

```
sudo mount /dev/sdb1 /mnt
```

Then please post the outpout of the following command.

```
mount  &&  ls -ld /mnt
```

Finally umount the device.

```
sudo umount /mnt
```

If either the mount or unmount commands return errors then please post them back here as well.

Kind regards

---

### Post by varunendra on 2013-06-06
> **tubunter said:**
> 
```
user@user-L51RI1:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation **[COLOR="#FF0000"]1.1 root hub[/COLOR]**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation **[COLOR="#FF0000"]1.1 root hub[/COLOR]**
**Bus 001 Device 008: ID 0951:1665 Kingston Technology **
user@user-L51RI1:~$ 

```
:shock:

USB devices are backward compatible, so this may not be the cause for the problem, but how old is this computer really? 2 out of 3 of your USB ports (hubs) appear to be **USB 1.1**.

If that's true, and not a BIOS misconfiguration, then I doubt if a computer this old should even be able to run Ubuntu 12.04. What are its specs?
If that's not true, and the computer is rather new (even 10 years old is considered 'newer' in this aspect), then almost certainly there is something wrong with your BIOS settings. Try resetting BIOS to defaults.

---

### Post by matt_symes on 2013-06-06
Hi

> **varunendra said:**
> :shock:

USB devices are backward compatible, so this may not be the cause for the problem, but how old is this computer really? 2 out of 3 of your USB ports (hubs) appear to be **USB 1.1**.

If that's true, and not a BIOS misconfiguration, then I doubt if a computer this old should even be able to run Ubuntu 12.04. What are its specs?
If that's not true, and the computer is rather new (even 10 years old is considered 'newer' in this aspect), then almost certainly there is something wrong with your BIOS settings. Try resetting BIOS to defaults.

@varunendra.

I wondering if the usb pen sticks are not being auto-mounted anymore and the OP is misinterpreting the problem. From that perspective it may look like a problem with the USB ports.

Other USB devices are being recognised - such as the mouse - and the output from lsusb, usb-devices and syslog, when a pen drive is inserted, all look good.

Kind regards

---

### Post by varunendra on 2013-06-06
> **matt_symes said:**
> @varunendra.

I wondering if the usb pen sticks are not being auto-mounted anymore and the OP is misinterpreting the problem. From that perspective it may look like a problem with the USB ports.
Most probably.

I must admit that I slightly misread OPs post where outputs of usb-devices and lsusb were given. I thought they were both from when the pen drive was plugged in. Re-read the post and realized they were from different states. So yes, probably mounting is all that is needed.

But the version of hubs, accordingly the probable age of the system and the fact it is running Ubuntu 12.04 is still quite interesting to me :P

It may be also worth noting that the speed of detection and probing of the device may be too slow on USB 1.1 port, possibly resulting in failure of automount. Let's see what the OP comes up with after following your directions.

---

### Post by tubunter on 2013-06-06
```
user@user-L51RI1:~$ sudo mount /dev/sdb1 /mnt
[sudo] password for user: 
user@user-L51RI1:~$ mount  &&  ls -ld /mnt
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)
/dev/sdb1 on /mnt type vfat (rw)
drwxr-xr-x 4 root root 32768 gen  1  1970 /mnt
user@user-L51RI1:~$
```

---

### Post by matt_symes on 2013-06-06
Hi

> /dev/sdb1 on /mnt type vfat (rw)

It's mounting correctly so i suspect it's not automounting and this is the behaviour you are missing.

Some questions:

What did you see before when you inserted a USB pen drive that you are not seeing now ?

Did it used to open a file manager allowing you to see all the files on the pen drive automatically ?

What behaviour do you expect to see when you insert a pen drive ?

Are you using Ubuntu, Xubuntu, Lubuntu, Kubuntu or some other flavour ?

Please post the output of (case sensitive)

```
echo $DESKTOP_SESSION && cat /etc/lsb-release && uname -r
```

It may be easier to copy and paste the above line into the terminal.

Kind regards

---

### Post by tubunter on 2013-06-06
> Please post the output of (case sensitive)

```
gnome-fallback
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
3.2.0-45-generic

```

> What did you see before when you inserted a USB pen drive that you are not seeing now ?

Did it used to open a file manager allowing you to see all the files on the pen drive automatically ?

What behaviour do you expect to see when you insert a pen drive ?



Yes, it used to open the file manager automatically.
I don't expect necessarily this, but at least to access the pen drive content in some way. Actually I don't see the device in any "place", and I'm not able to do this trough the terminal...

---

### Post by matt_symes on 2013-06-06
Hi

I have no experience using gnome-fallback-session, however i assume it still uses gvfs.

Plug in the USB stick and then open a terminal and type

```
gvfs-mount --list
```

Post the results back here.

We are working our way up the stack looking for the problem area.

Kind regards

---

### Post by tubunter on 2013-06-06
No output...

---

### Post by matt_symes on 2013-06-06
Hi

> **tubunter said:**
> No output...

I have no experience with gnome-session-fallback and i don't have a copy of 12.04 available so i can't check on a system here, so if anybody else can lend a hand; that would be great.

However, what does this return ?

```
ps aux | grep gvfs
```

Kind regards

---

### Post by tubunter on 2013-06-06
```
user@user-L51RI1:~$ ps aux | grep gvfs
user   1339  0.0  0.2  48368  2248 ?        S    Jun05   0:00 /usr/lib/gvfs/gvfsd
user   1341  0.0  0.2 207908  2156 ?        Sl   Jun05   0:00 /usr/lib/gvfs//gvfs-fuse-daemon -f /home/user/.gvfs
user   1560  0.0  0.3  66444  3152 ?        S    Jun05   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
user   1704  0.0  0.2  56156  2436 ?        S    Jun05   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
user   1706  0.0  0.2 137896  2376 ?        Sl   Jun05   0:02 /usr/lib/gvfs/gvfs-afc-volume-monitor
user   1713  0.0  0.4  54172  4348 ?        S    Jun05   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.2 /org/gtk/gvfs/exec_spaw/0
user   1715  0.0  0.2  48500  2492 ?        S    Jun05   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.2 /org/gtk/gvfs/exec_spaw/1
user   1725  0.0  0.2  42328  2352 ?        S    Jun05   0:00 /usr/lib/gvfs/gvfsd-metadata
user  10770  0.0  0.4 226232  4328 ?        Sl   19:32   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.2 /org/gtk/gvfs/exec_spaw/2
user  14099  0.0  0.0   9428   876 pts/1    S+   23:11   0:00 grep --color=auto gvfs
user@user-L51RI1:~$
```

---

### Post by matt_symes on 2013-06-06
Hi

The gvfs daemons are all running so let's check udisks.

Plug the USB pen drive in and type

```
udisks --mount /dev/sdb1
```

Post back any output here.

Then post the output of 

```
mount && gvfs-mount --list
```

Kind regards

---

### Post by tubunter on 2013-06-06
```
user@user-L51RI1:~$ udisks --mount /dev/sdb1
Mounted /org/freedesktop/UDisks/devices/sdb1 at /media/KINGSTON
user@user-L51RI1:~$
```


```
user@user-L51RI1:~$ mount && gvfs-mount --list
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)
/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks)
Mount(0): KINGSTON -> file:///media/KINGSTON
  Type: GProxyMount (GProxyVolumeMonitorGdu)
user@user-L51RI1:~$ 
```

---

### Post by tubunter on 2013-06-06
ATTENTION!

after this command 

udisks --mount /dev/sdb1

I see the pen drive in the home folder!

what does it mean?

---

### Post by matt_symes on 2013-06-06
Hi
> 
ATTENTION!

after this command 

udisks --mount /dev/sdb1

I see the pen drive in the home folder!

what does it mean?

So udisks is mounting correctly when asked to do so and is being recognised by gvfs when it is mounted.

That should mean the udisks daemon is running but that can be checked with

```
ps aux | grep udisks
```

Have you check to see if automounting is enabled in gconf-editor/dconf-editor ?

Have you checked to see if there is an automount setting in Nautilus ?

Kind regards

---

### Post by tubunter on 2013-06-07
```
user@user-L51RI1:~$ ps aux | grep udisks
root      1562  0.0  0.4 201852  3804 ?        Sl   Jun05   0:02 /usr/lib/udisks/udisks-daemon
root      1563  0.0  0.0  45516   552 ?        S    Jun05   0:00 udisks-daemon: not polling any devices
user  16400  0.0  0.0   9428   876 pts/1    S+   07:21   0:00 grep --color=auto udisks
user@user-L51RI1:~$ 
```


> Have you check to see if automounting is enabled in gconf-editor/dconf-editor ?

Have you checked to see if there is an automount setting in Nautilus ?


I don't know how to do it...

---

### Post by matt_symes on 2013-06-07
Hi

> **tubunter said:**
> I don't know how to do it...

```
sudo apt-get install dconf-editor
```

or install it from the software center.

Start dconf-editor and in the tree on the left hand side, navigate to

org->gnome->desktop->media handling

and ensure automount is checked.

If you want a file browser to open when you insert a device the ensure automount_open is checked as well.

Kind regards

---

### Post by tubunter on 2013-06-07
both are checked but nothing happens...

---

### Post by matt_symes on 2013-06-07
Hi

The problem looks to be automounting or maybe dbus.

It's problematic for me as i don't have 12.04 installed, only 13.04, and 13.04 uses udisk2 and not udisks.

Something i would like to eliminate though.

Create another user, login as that user and insert a USB pen drive.

Does it automount ?

That will eliminate/implicate your user settings as the cause.

Kind regards

---

### Post by tubunter on 2013-06-07
Yes, it works! (really, one of the three ports seems to be dead, but at this point it doesn't matter...)

so...what do you propose?...

---

### Post by matt_symes on 2013-06-07
Hi

> **tubunter said:**
> Yes, it works! (really, one of the three ports seems to be dead, but at this point it doesn't matter...)

so...what do you propose?...

So the problem looks to be automount in your user settings in your home directory. 

Like i said though, i have no experience if gnome-fallback-session. For all i know it may use the same settings as Unity or may not.

Assume it uses the same settings..

You could reset your home settings back to default (you would lose any custom settings you may have set though).

```
dconf reset -f /
```

Seems a case of overkill to me that above command though.[LEFT][COLOR=#333333][FONT=UbuntuRegular][/FONT][/COLOR][/LEFT] If you run it run this command first

```
cp ~/.config/dconf/user{,.bk}
```

This should back up your user settings.

You could copy your files to the new users home directory and use that as your new user.

Even bigger case of over kill though.

I like neither of the above options though.  

So on a whim, open a terminal and type

```
grep -r mount ~ 2> /dev/null
```

Post the output back here and let's see if it returns anything useful.

If anybody actually has 12.04 installed and knows the solution then speak up :)

Kind regards

---

### Post by tubunter on 2013-06-07
how to copy my files in the new user account?

that command 

(grep -r mount ~ 2> /dev/null)

returns an infinite list, it works for hours...

---

### Post by varunendra on 2013-06-07
> **tubunter said:**
> how to copy my files in the new user account?
The best option in my opinion would be to copy to an external FAT or NTFS drive, then copy them back to the other user's home when logged in as that. This will be safer and won't cause permission issues.

> **matt_symes said:**
> If anybody actually has 12.04 installed and knows the solution then speak up :)

I have it installed, but not sure what to speak :D
Let me know if you want me to test or cross-check something. I'm on 12.04 64 bit, with default Unity (no gnome-fallback, but am sure the basic settings are same as I used it once before on Natty).

---

### Post by tubunter on 2013-06-11
so guys, finally I resolved by moving my files to the new user account, and that's all.
seems that there is some big mess somewhere on the hard disk as bad or damaged sectors, even if the test says not (I have some difficulties to start up...)...

that seems to be the best workaround at the moment.

I thank you for the availability to support me so far, I really appreciated so much! 

kind regards

---

### Post by matt_symes on 2013-06-12
Hi

> seems that there is some big mess somewhere on the hard disk as bad or  damaged sectors, even if the test says not (I have some difficulties to  start up...)...

Run a SMART test in the hard drive.

You can run this from disk utility or from the command line...

```
sudo apt-get install smartmontools
```

```
sudo smartctl -t long /dev/sda
```

That will take a while to complete but it should gives you a finishing time.

To see the SMART report

```
sudo smartctl -a /dev/sda
```

Post the log back here.

If the log returns no problems then run fsck on the drive from a liveCD/USB of fro the recovery console.

You you need instruction on how to do this then post back.

Kind regards

---

### Post by tubunter on 2013-06-13
```
user@user-L51RI1:~$ sudo smartctl -a /dev/sda
[sudo] password for user: 
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-45-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD1600BEVS-60RST0
Serial Number:    WD-WXEX07H52716
LU WWN Device Id: 5 0014ee 2ab5d150f
Firmware Version: 04.01G04
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Jun 13 18:33:15 2013 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 6780) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  87) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       333
  3 Spin_Up_Time            0x0003   188   184   021    Pre-fail  Always       -       1600
  4 Start_Stop_Count        0x0032   090   090   000    Old_age   Always       -       10820
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   079   079   000    Old_age   Always       -       15699
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   093   093   000    Old_age   Always       -       7113
187 Reported_Uncorrect      0x0032   100   064   000    Old_age   Always       -       321
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   053   032   040    Old_age   Always   In_the_past 47
192 Power-Off_Retract_Count 0x0032   199   199   000    Old_age   Always       -       1332
193 Load_Cycle_Count        0x0032   159   159   000    Old_age   Always       -       123684
194 Temperature_Celsius     0x0022   100   079   000    Old_age   Always       -       47
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 313 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 313 occurred at disk power-on lifetime: 11619 hours (484 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c4 81 35 e0  Error: UNC 1 sectors at LBA = 0x003581c4 = 3506628

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 c4 81 35 12 00      02:48:43.718  READ DMA EXT
  35 00 01 c3 81 35 12 00      02:48:43.718  WRITE DMA EXT
  25 00 01 c3 81 35 12 00      02:48:43.718  READ DMA EXT
  25 00 01 c4 81 35 12 00      02:48:40.815  READ DMA EXT
  25 00 01 c3 81 35 12 00      02:48:40.667  READ DMA EXT

Error 312 occurred at disk power-on lifetime: 11619 hours (484 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c4 81 35 e0  Error: UNC 1 sectors at LBA = 0x003581c4 = 3506628

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 c4 81 35 12 00      02:48:40.815  READ DMA EXT
  25 00 01 c3 81 35 12 00      02:48:40.667  READ DMA EXT
  25 00 01 c2 81 35 12 00      02:48:40.667  READ DMA EXT
  35 00 01 c2 81 35 12 00      02:48:40.667  WRITE DMA EXT
  35 00 01 c1 81 35 12 00      02:48:40.666  WRITE DMA EXT

Error 311 occurred at disk power-on lifetime: 11619 hours (484 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c2 81 35 e0  Error: UNC 1 sectors at LBA = 0x003581c2 = 3506626

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 c2 81 35 12 00      02:48:37.216  READ DMA EXT
  35 00 01 c1 81 35 12 00      02:48:37.207  WRITE DMA EXT
  25 00 01 c1 81 35 12 00      02:48:37.207  READ DMA EXT
  25 00 01 c2 81 35 12 00      02:48:34.304  READ DMA EXT
  25 00 01 c1 81 35 12 00      02:48:34.303  READ DMA EXT

Error 310 occurred at disk power-on lifetime: 11619 hours (484 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c2 81 35 e0  Error: UNC 1 sectors at LBA = 0x003581c2 = 3506626

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 c2 81 35 12 00      02:48:34.304  READ DMA EXT
  25 00 01 c1 81 35 12 00      02:48:34.303  READ DMA EXT
  35 00 01 c1 81 35 12 00      02:48:34.303  WRITE DMA EXT
  35 00 01 c0 81 35 12 00      02:48:34.303  WRITE DMA EXT
  35 00 01 c1 81 35 12 00      02:48:34.303  WRITE DMA EXT

Error 309 occurred at disk power-on lifetime: 11619 hours (484 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 c1 81 35 e0  Error: UNC 1 sectors at LBA = 0x003581c1 = 3506625

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 c1 81 35 12 00      02:48:30.722  READ DMA EXT
  35 00 01 c0 81 35 12 00      02:48:30.722  WRITE DMA EXT
  25 00 01 c0 81 35 12 00      02:48:30.722  READ DMA EXT
  25 00 01 c1 81 35 12 00      02:48:27.687  READ DMA EXT
  25 00 01 c0 81 35 12 00      02:48:27.687  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     15695         -
# 2  Extended offline    Completed without error       00%     15341         -
# 3  Short offline       Completed without error       00%     11691         -
# 4  Short offline       Completed without error       00%     11622         -
# 5  Short offline       Completed: read failure       90%     11616         6243928
# 6  Short offline       Completed: read failure       90%     11615         6243928
# 7  Short offline       Aborted by host               90%     11511         -
# 8  Short offline       Completed: read failure       90%     11511         6243928
# 9  Short offline       Completed: read failure       90%     11511         6243928
#10  Short offline       Completed: read failure       90%     11511         6243928
#11  Extended offline    Aborted by host               90%      6937         -
#12  Short offline       Completed without error       00%      6937         -
#13  Short offline       Aborted by host               90%      6937         -
#14  Short offline       Aborted by host               90%      6928         -
#15  Extended offline    Aborted by host               90%        32         -
#16  Short offline       Completed without error       00%        32         -
#17  Extended offline    Aborted by host               90%        32         -
#18  Short offline       Completed without error       00%        32         -
5 of 5 failed self-tests are outdated by newer successful extended offline self-test # 1

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

user@user-L51RI1:~$ 
```


what do you think about?

---

### Post by matt_symes on 2013-06-13
Hi

> what do you think about?

Looks fine there.

What are your difficulties starting up ?

Kind regards

---

