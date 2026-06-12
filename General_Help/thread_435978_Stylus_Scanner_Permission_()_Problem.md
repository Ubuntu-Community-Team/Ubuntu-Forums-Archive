---
title: "Stylus Scanner Permission (?) Problem"
date: 2007-05-07
forum: General Help
---

### Post by arlorn on 2007-05-07
Hello. 

I have an Epson Stylus CX38100, which functions as a scanner. I set up the printer and scanner properly a few days ago, and was able to use both, but today my computer can't use the scanner.

I believe it's a permission problem, but I'm not sure what the conflict is with. 

**_[SIZE="4"]Here are a few printouts:[/SIZE]_**

**_As my user:_**
```

jess@jess-laptop:/$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0818) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

```

jess@jess-laptop:/$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

If I try to run xsane (with the command "xsane"), I get an error message "No devices available".

**_As root:_**
sane-find-scanner returns the same result as above.

```
root@jess-laptop:~# scanimage -L
device `epkowa:libusb:001:004' is a Epson Stylus CX3700/CX3800/DX3800 flatbed scanner

```

```
root@jess-laptop:~# xsane

(xsane:11994): Gtk-WARNING **: cannot open display:  
```

**_[SIZE="4"]What I've tried[/SIZE]_**
I've looked around for a solution, and given a few things I've seen a shot. 

[LIST]
[*]I tried creating a sym link between* /usr/local/etc/sane.d* and */etc/sane.d*.
[*]I tried changing permissions on */proc/bus/usb* to writeable. At 777, the behaviour didn't change.
[*]I've tried restarting the computer and printer, I've checked connections, etc.
[/LIST]

**_[SIZE="4"]Hardware & Versions[/SIZE]_**
[LIST]
[*]Epson Stylus CX38100 "All in one" via a USB connection
[*]Ubuntu Fiesty
[*]Gutenprint CUPS driver
[/LIST]

**_[SIZE="4"]Thanks[/SIZE]_**
Thanks for taking the time to read through this. If someone could just point me in the right direction, I'm sure I'll be just fine. I figured out how to get it set up in the first place, so it baffles me that suddenly it has stopped working, and that I'm unable to fix it now.

Thank you, once again, for your time and consideration,
   -Jess

---

### Post by arlorn on 2007-05-07
Alright, I restarted again and the problem went away. 

Can anyone offer any suggestions as to what to try if the problem arises again? I have a strong suspicion it will.

Thanks, very much,
   -Jess

---

### Post by domino1241 on 2008-03-04
bump

I have the same problem on my school's network scanner.  who and who-a don't seem to shed light on the situation (I'm the only one logged on)

---

### Post by Bogart on 2008-05-05
Maybe changing the permissions of /dev/bus/usb/.../... could solve the problem.

The command "sane-find-scanner" should give you the right address of the scanner. Something like 001:002. So then you could do something like:

sudo chown root:scanner /dev/bus/usb/001/002
sudo chmod 0664 /dev/bus/usb/001/002

Then as long as your user is added to the scanner group (should be by default), it will be allowed to use the scanner.

---

