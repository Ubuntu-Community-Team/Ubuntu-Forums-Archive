---
title: "Lexmark z600 + x1270 Scanner Issue"
date: 2008-01-13
forum: General Help
---

### Post by gnomepage on 2008-01-13
So, I have scanned the other threads looking for a fix for getting my z600/x1270 scanner to work in gutsy.

I feel I came close when I logged in as 

[B]su
password
gedit /etc/sane.d/lexmark.conf[/B]

I get this:

[B]#usb /dev/usb/scanner0
usb 0x043d 0x007c[/B]

I read somewhere else that if I delete line 1 of that, and reinsert something this will get the scanner to become recognized and then options to pick my scanner from a list. Unfortunately, "Said Source: was confusing. 

When I do **sane-find-scanner** I get:

> markus@markus-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x043d, product=0x007d, chip=rts8858c) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
markus@markus-desktop:~$ 
markus@markus-desktop:~$

When I do **scanimage -L** I get:

> markus@markus-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
markus@markus-desktop:~$

Please bear with me, I am trying to get all of the correct info to get help with.

Please note, when I open Sane I get a pop-ups which reads **"No Devices Available"**

Thanks in advance.

---

### Post by gnomepage on 2008-01-14
EDIT: NM - Unsupported by SANE per

[http://www.sane-project.org/cgi-bin/driver.pl?manu=lexmark&model=&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=lexmark&model=&bus=any&v=&p=)

---

### Post by netlynx on 2008-04-24
Hey Gnomepage

I have both the printer and scanner working on Ubuntu 8.04 RC3 (and I am sure it would even work on previous versions).

You are correct, I checked the sane-project website, and it is classed as unsupported.  *However* more searching here, I came across a post (and I can't find it now), but it lead me to this website: 

[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/)

I realize that the website might be a little confusing with the broken english, but I installed the two files they listed at the top: z600cups*.deb, and z600llpddk*.deb (and I believe they just have the printer drivers).

Next I installed sane and sane-utils:

sudo apt-get install sane sane-utils

On the above website they list two more files to put in /etc/sane.d -- now I put those files in (overwriting the files that were currently there -- I suggest backup the files there already (I never really read the files -- might be a good idea too before replacing them as it may not be necessary)

The third thing they list there is a file into the $USER directory (this didn't apply to me as I am running a console based server, and this is an xwindows thing)

The fourth part something to do with /usr/lib/heal of which I actually skipped this step entirely *however*:
make sure you have the following files

/usr/lib/sane/libsane-lexmark.la
/usr/lib/sane/libsane-lexmark.so.1.0.19
/usr/lib/sane/libsane-lexmark.so.1 (which is a just a symlink to the 1.0.19 file)

Now that I have rambled all of this off to you, I then still had the exact same scanner not found error messages you got.  *However* (and I still looking for the solution to this, got some heavy manpage reading on all the above stuff I just told you yet so I can figure out what all the above *actually* does/means).

Anyhow:

$ sane-find-scanner
should give you something like this:
found USB scanner (vendor=0x043d, product=0x007d, chip=rts8858c?) at libusb:001:004
# Your USB scanner was (probably) detected. It may or may not be supported by
# SANE. Try scanimage -L and read the backend's manpage.

and:

$ scanimage -L

gives the 'No scanners were identified.' message

***BUT***

$ sudo scanimage -L

should give you:

device `lexmark:libusb:001:004' is a Lexmark X1200/USB1.1 flatbed scanner

so for some reason and this is where I am at thusfar is:

scanimage must be run as root (sudo).

If this doesn't solve your problem, then hopefully it will at least get you on your way.

Regards
Aaron

---

### Post by netlynx on 2008-04-25
Well, just a quick update, I just finished installing Ubuntu Desktop 8.04, what a great product!!!

Lexmark X1280 - Printing and scanning working "out of the box"!

(I had it connected during install, but I am sure that was not necessary)

I sure wish Ubuntu Server was as user friendly with hardware.  Took me a couple hours (granted I am no super tech by any stretch) to find the information and set up the drivers and get it working.

Regards
Aaron

---

### Post by Basket_Case on 2008-06-13
Hi Aaron,

I am a bit confused (easy with my IQ...). I eventually got my Lexmark scanner X1270 working with Xsane but the printer never worked "out of the box" (I too am using Ubuntu 8.04). I eventually got it going using a very involved procedure and the z600 driver. As the 'X1280 looks very closely related, have you therefore got a simpler solution? The add new printer screen did not offer 'X1280 as an option.

Regards

---

