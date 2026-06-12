---
title: "The Disk Drive for /home is not ready yet or not present."
date: 2015-04-05
forum: General Help
---

### Post by zach29 on 2015-04-05
I have installed Xubuntu and put the root folder on the main hard drive, and the home folder on a USB 3.0 Hard Drive - both are ext4. 
Everytime I restart, 90% of the time I get the following two problems. 

First screen:
18042 no controller found
ACPI PCC PROBE FAILED
USB 1-4 String Descriptor 0 read error: -22

Then it's followed by this screen:
The Disk Drive for /home is not ready yet or not present.
Continue to wait, or press S to skip mounting or M for manual recovery

I just keep restarting until I finally get into the OS. 

Any ideas? It's super frustrating. I've clean installed three times now, and it keeps happening.

---

### Post by dino99 on 2015-04-05
acpi pcc is a recent kernel feature that works only with compatible mobo (error is harmless if your mobo does not provide that feature)

as /home is on a usb drive, be sure you have an entry into /etc/fstab to get it mounted at boot time. Its uuid may change each time you plug/unplug it, so set a label to mount it instead of using the default uuid

---

### Post by zach29 on 2015-04-05
> **9d9 said:**
> acpi pcc is a recent kernel feature that works only with compatible mobo (error is harmless if your mobo does not provide that feature)

as /home is on a usb drive, be sure you have an entry into /etc/fstab to get it mounted at boot time. Its uuid may change each time you plug/unplug it, so set a label to mount it instead of using the default uuid


THANK YOU!!!

I don't know how to set that, any advice?
Thanks again!


Edit: I went to Settings -> Disks, and set labels, is that it?

---

### Post by zach29 on 2015-04-05
Bump.

---

### Post by sandyd on 2015-04-05
Can you post the output of ```

cat /etc/fstab
sudo blkid
```
Side note:
If your device does not have a label, you will have to create one for it.

---

### Post by zach29 on 2015-04-05
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a397bbd2-a7dc-462d-90b3-64cb8ebd8a52 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=40bf1781-bc08-4a81-936e-f695f33bfeb7 /home           ext4    defaults        0       2
# /tmp was on /dev/sdb6 during installation
UUID=487c1505-3bc9-45bb-a897-f33538e7237c /tmp            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=6f0b2d73-9b99-419c-b521-0c0c5fd1d224 none            swap    sw              0       0


And


/dev/sda1: LABEL="ZHome" UUID="40bf1781-bc08-4a81-936e-f695f33bfeb7" TYPE="ext4" PARTUUID="0015bc4a-01" 
/dev/sda5: UUID="02DBAB993709A0CE" TYPE="ntfs" PARTUUID="0015bc4a-05" 
/dev/sda6: UUID="487c1505-3bc9-45bb-a897-f33538e7237c" TYPE="ext4" PARTUUID="0015bc4a-06" 
/dev/sdb1: LABEL="SSD" UUID="a397bbd2-a7dc-462d-90b3-64cb8ebd8a52" TYPE="ext4" PARTUUID="e8707c46-01" 
/dev/sdb5: UUID="37919486-3262-4b07-8e66-dd2090b7fc4d" TYPE="swap" PARTUUID="e8707c46-05" 



Thanks!!!

---

### Post by sandyd on 2015-04-05
Type in
```

sudo nano /etc/fstab
```

Change the the line
```

UUID=40bf1781-bc08-4a81-936e-f695f33bfeb7 /home ext4 defaults 0 2

```
to
```
LABEL=ZHome /home ext4 defaults 0 2
```
so that it looks like
```

# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda1 during installation
UUID=a397bbd2-a7dc-462d-90b3-64cb8ebd8a52 / ext4 errors=remount-ro 0 1
# /home was on /dev/sdb1 during installation
**LABEL=ZHome /home ext4 defaults 0 2**
# /tmp was on /dev/sdb6 during installation
UUID=487c1505-3bc9-45bb-a897-f33538e7237c /tmp ext4 defaults 0 2
# swap was on /dev/sda5 during installation
UUID=6f0b2d73-9b99-419c-b521-0c0c5fd1d224 none swap sw 0 0
```
Control +X to save, press Y when it asks.

Reboot.

---

### Post by zach29 on 2015-04-06
> **sandyd said:**
> ```

sudo nano /etc/fstab
```

Change the the line
```

UUID=40bf1781-bc08-4a81-936e-f695f33bfeb7 /home ext4 defaults 0 2

```
to
```
LABEL=ZHome /home ext4 defaults 0 2
```
so that it looks like
```

# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda1 during installation
UUID=a397bbd2-a7dc-462d-90b3-64cb8ebd8a52 / ext4 errors=remount-ro 0 1
# /home was on /dev/sdb1 during installation
**LABEL=ZHome /home ext4 defaults 0 2**
# /tmp was on /dev/sdb6 during installation
UUID=487c1505-3bc9-45bb-a897-f33538e7237c /tmp ext4 defaults 0 2
# swap was on /dev/sda5 during installation
UUID=6f0b2d73-9b99-419c-b521-0c0c5fd1d224 none swap sw 0 0
```
Control +X to save, press Y when it asks.

Reboot.


Sorry, I'm pretty new to some of this. What commands do I need to type in to change this?

Thanks!

---

### Post by sandyd on 2015-04-06
> **zach29 said:**
> Sorry, I'm pretty new to some of this. What commands do I need to type in to change this?

Thanks!

updated above :)

---

### Post by zach29 on 2015-04-06
I changed that, but it still was giving me the errors for both Home and TMP. 

I then changed the label of my tmp partition to tmp, and restarted. Now I can't even get into ubuntu and it keeps telling the temp isn't available, I hit s to skip, then the same for home, then I finally get to the login screen, but can't obviously log in since the home and tmp directories are missing.

Edit:

I kept restarting, and finally got into the desktop. I did notice I also saw a "can't mount [COLOR=#000000][FONT=Ubuntu Mono]UUID=40bf1781-bc08-4a81-936e-f695f33bfeb7"   [/FONT][/COLOR] Not sure if that was the actual numbers though.

---

### Post by sandyd on 2015-04-07
Hmm...

It sound like its having a race condition between mounting and loading the modules needed for USB

System asks for mount -> Device modules not yet loaded -> System thinks there is no device and device fails to mount

---

### Post by zach29 on 2015-04-07
> **sandyd said:**
> Hmm...

It sound like its having a race condition between mounting and loading the modules needed for USB

System asks for mount -> Device modules not yet loaded -> System thinks there is no device and device fails to mount

Could it be firmware related? I'm running this on an Asus Chromebox. I'm guessing no because I didn't have this problem when I tried Windows 8.1 on it. 
Any other ideas?

Thanks for your help, I really appreciate it.

---

