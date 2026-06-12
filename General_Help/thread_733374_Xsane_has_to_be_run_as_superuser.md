---
title: "Xsane has to be run as superuser"
date: 2008-03-23
forum: General Help
---

### Post by feanor512 on 2008-03-23
I just did a fresh install of Ubuntu 8.04 Beta on a spare system.

If I run xsane, I get the error "No devices available." However, if I run sudo xsane, it detects my scanner and works perfectly. How can I get it to detect my scanner without being a superuser?

My scanner is an Epson Stylus Photo RX620 connected via USB. I don't know if this is specific to 8.04 Beta because I've only used this scanner with Windows. Thanks.

---

### Post by alenis on 2008-03-23
Maybe you should add your normal account to the "scanner" group

---

### Post by feanor512 on 2008-03-23
> **alenis said:**
> Maybe you should add your normal account to the "scanner" group
I already did that.

---

### Post by MetalMusicAddict on 2008-03-23
I have this same issue and have reported it. [Bug #205628]("https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/205628")

---

### Post by scottro on 2008-03-23
It's probably a setting in /dev.  In FreeBSD, one uses /etc/devfs which is where I've done it.  LInux has udev and I assume there's some way to do it there.  

For example, create the scanner group, add yourself to it.  Then edit whatever udev file you have to (sorry, I can't be much help there) so that scanners have rights.  

(You can always, as a quick fix, just change the permissions on the scanning device listing in /dev to 666, or if you are a member of the scanner group and that is the group that owns it, 660.)

If you're not familiar with this, the commands are (I don't know what Ubuntu calls the scanner in /dev--for this example, let's say it calls it scanner)

chown :scanners /dev/scanner
chmod 660 /dev/scanner

Note the colon in front of the word scanners--that's for a group.  This is a kludge but it should at least enable you to use sane. 

Hopefully, someone will see the thread and tell you what files to change and how in udev.  

(There may be another file that can be edited instead, this is one case where I'm not familiar with how Linux does it, though the basic premise will be the same, changing permissions and access on a device.)

---

### Post by monraaf on 2008-03-24
> **scottro said:**
> It's probably a setting in /dev.  In FreeBSD, one uses /etc/devfs which is where I've done it.  LInux has udev and I assume there's some way to do it there.  

In Ubuntu 7.10 there is the file */etc/udev/rules.d/45-libsane.rules* which doesn't exist in 8.04, i copied it but it didn't help.

Manually changing the group does work.

```
dmesg:

usb 5-2: new full speed USB device using uhci_hcd and address 4
```

```
sudo chgrp scanner /dev/bus/usb/005/004
```

---

### Post by feanor512 on 2008-03-24
> **monraaf said:**
> Manually changing the group does work.

```
dmesg:

usb 5-2: new full speed USB device using uhci_hcd and address 4
```

```
sudo chgrp scanner /dev/bus/usb/005/004
```

Through trial and error with the USB devices that showed up, I got it. Now xsane will detect my scanner as a normal user. However, when it closes, it gives the error message
```
Failed to create file: Permission denied
```
six times. The actual device looks like:
```
crw-rw-r-- 1 root scanner 189, 130 2008-03-24 09:52 003
```
so my normal user who's in the scanner group should be able to write to it, right? Maybe xsane is trying to write somewhere else.

---

### Post by MetalMusicAddict on 2008-03-24
I have marked my bug as a dupe of this one: [Bug #205496]("https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/205496") It actually goes closer to the issue.

---

### Post by monraaf on 2008-03-24
> **feanor512 said:**
> 
```
Failed to create file: Permission denied
```
six times. The actual device looks like:
```
crw-rw-r-- 1 root scanner 189, 130 2008-03-24 09:52 003
```
so my normal user who's in the scanner group should be able to write to it, right? Maybe xsane is trying to write somewhere else.

Yes xsane is trying to write to files in *~/.sane*, but because you have run xsane as root those files are owned by root.
You can either change the ownership back to you or remove the *~/.sane* directory and let xsane create new files.

---

