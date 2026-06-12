---
title: "Can't find scanner"
date: 2013-10-26
forum: General Help
---

### Post by jcoop114 on 2013-10-26
I'm new to Ubuntu and I have no idea how to get my scanner to work.

It's a Fujitsu fi-4340C ADF duplex scanner.

I installed Xsane from the software center, but it couldn't find the scanner.

I typed sane-find-scanner in the terminal and got the following result:

```
$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x8087/0x0024 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x8087/0x0024 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc05a at 001:003: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc31c at 001:004: Access denied (insufficient permissions)
could not open USB device 0x198f/0x8160 at 002:004: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0608 at 002:003: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

---

### Post by Bucky Ball on 2013-10-26
Is it a USB scanner? May sound like a silly question, but ...

Try this command:

```

sudo sane-find-scanner

```

... and if that doesn't work:

```


lsusb
```

Is it there? Also, do you need to install any other drivers for this device? Have you checked the Fujitsu site (* I just checked there and no Linux driver)?

This might help. It's definitely supported. ;)

[http://manpages.ubuntu.com/manpages/precise/man5/sane-fujitsu.5.html](http://manpages.ubuntu.com/manpages/precise/man5/sane-fujitsu.5.html)

---

### Post by jcoop114 on 2013-10-26
I think it is a USB scanner. When I tried:

```
lsusb
``` 

I found:

```
Bus 002 Device 007: ID 04c5:10cf Fujitsu, Ltd 
```

I don't know much about drivers, but the Internet led me to this program called XSANE. I also tried Simple Scan and SANE-pygtk from the Software Center, and downloaded a program called VUE Scan, but none of them can find the scanner.

I also tried following a tutorial 

[https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected](https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected)

The instructions tell me to go to 
[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

then enable the backend by

```
sudo gedit /etc/sane.d/dll.conf
```

and changing

```
#example-backend
```

to

```
#example-backend
```

then

```
sane-find-scanner
```

I did all that, but the instructions actually say "#example-backend" to #example-backend", so that's not clear to me. I assumed it meant for me to change "fujitsu" in the conf file to whatever the backend says at the sane-project website, but that says the Fujitsu fi-4340C's backend is "Fujitsu (117)". I tried changing the conf file every which way:

fujitsu117
fujitsu(117)
fujitsu 117
fujitsu (117)
Fujitsu117
Fujitsu(117)
#fujitsu
#fujitsu117
#Fujitsu

but nothing worked. That tutorial does not explain what to do if the scanner is not found after that, so I'm stuck there.

---

### Post by Bucky Ball on 2013-10-26
You've done good research and good work there, puzzling the apps are not picking up the scanner because the machine knows it's there. I'll think a bit more when I've woken up some! ;)

---

### Post by pqwoerituytrueiwoq on 2013-10-26
[FONT=courier new]scanimage -L[/FONT]
that command will list all scanners
this may be of use
[scanner-access-enabler-1.4.tar.bz2](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/scanner-access-enabler-1.4.tar.bz2?raw=true)
what does this command give you? [FONT=courier new]groups $USER[/FONT]

---

### Post by jcoop114 on 2013-10-26
```
scanimage -L
```

returns

```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

```
groups $USER
```

returns

```
jason : jason adm cdrom sudo dip plugdev lpadmin sambashare
```

I downloaded the link, but I have no idea what to do with it. I'm new to Ubuntu and I only know how to install stuff through the software center.

---

### Post by pqwoerituytrueiwoq on 2013-10-27
how about [FONT=Courier New]sudo scanimage -L[/FONT]

this is odd, i cant access mine either but www-data can (just upgrade to saucy the other day from raring)
if you install the scanner software linked in my signature you should be able to use the scanner that way
I just turned the scanner on and could not access it
ran [FONT=courier new]sudo adduser $USER lp[/FONT]
ran [FONT=courier new]sudo service saned restart[/FONT]
logged out
login in and i have access to my scanner as the normal user

---

### Post by Bucky Ball on 2013-10-27
> **pqwoerituytrueiwoq said:**
> how about [FONT=Courier New]sudo scanimage -L[/FONT]

this is odd, i cant access mine either but www-data can (just upgrade to saucy the other day from raring)
if you install the scanner software linked in my signature you should be able to use the scanner that way
I just turned the scanner on and could not access it
ran [FONT=courier new]sudo adduser $USER lp[/FONT]
ran [FONT=courier new]sudo service saned restart[/FONT]
logged out
login in and i have access to my scanner as the normal user

+1. Nice tip. Let's see if that works ...

---

### Post by jcoop114 on 2013-10-27
I tried sudo scanimage -L again, and received the same message.

Again, I am new to Ubuntu and I only know how to install from the Software Center; I could not install the stuff in your link.

I tried sudo adduser $USER lp, and received: Done.

Then I tried sudo service saned restart, and received: saned disabled; edit /etc/default/saned

I'll try to log out, but I don't know what you need me to log out of. I guess I'll just log out of my computer?

This doesn't sound like it's going to work, though.

There is a Fujitsu conf file in /etc/sane.d. Am I suppossed to edit that?

---

### Post by pqwoerituytrueiwoq on 2013-10-27
if scanimage -L with sudo did not see it it is not a permissions error as i suspected
sane.d/ files should be for sharing the scanner i think
maybe you need to modprobe something to get a driver working

---

### Post by jcoop114 on 2013-10-27
Thanks BB & PQ. Let me know if you come up with anything else. I'll post a reply once I figure it out.

---

