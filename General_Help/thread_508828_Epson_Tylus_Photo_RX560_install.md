---
title: "Epson Tylus Photo RX560 install"
date: 2007-07-24
forum: General Help
---

### Post by animammal on 2007-07-24
Hi All,

I've been messing with ubuntu and other distros for a while now but the one thing I never get working is my printer.  I have the Epson RX560 and the best post for a very similar printer is ([http://ubuntuforums.org/archive/index.php/t-2260.h...%3C/t-410142.html](http://ubuntuforums.org/archive/index.php/t-2260.h...%3C/t-410142.html)).

I have tried the very clear instructions by mabhatter in the above post but only get to the part where pipslite-install should create the ppd file. The pipslite dialog pops up as it should but does not detect the printer. lsusb lists the printer as being hp but I don't think its a problem as gnome-cups-manager recognises it fine:confused:

Can anybody help me with this as I so want to get everything working under Ubuntu!

Cheers peeps!

---

### Post by ddrichardson on 2007-07-24
Have you tried the Linux drivers from [Epson]("http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=lkuCfcvA9cyu0xA5GcjIWLImVk6PIZq9H6H33bg6TDQU003D&tc=6#7")?

---

### Post by animammal on 2007-07-28
Thanks for the reply.
Yes this is the driver i'm having trouble with. does anyone know why my printer is not being ditected?

---

### Post by davidjmayo on 2007-07-28
Try looking here [http://www.linux-foundation.org/en/OpenPrinting/Database/DatabaseIntro](http://www.linux-foundation.org/en/OpenPrinting/Database/DatabaseIntro)

I tried to look for your printer before giving the link but the site is running really slow (for me anyway). Hope you find it faster and find what you're looking for

---

### Post by yorkie on 2007-07-28
[http://ubuntufs.wordpress.com](http://ubuntufs.wordpress.com)

[http://ubuntuforums.org/showpost.php?p=2647245&postcount=4](http://ubuntuforums.org/showpost.php?p=2647245&postcount=4)

have a look at these may be of some use to you

---

### Post by animammal on 2007-07-28
Excellent! Looks like I'll be installing Gutenprint. Thanks peps for all your help. It's the main reason I love using Linux as there's always a few people that go the extra mile to make things easier!!

:)

---

### Post by animammal on 2007-07-29
Hey hey, it's all installed and working perfectly, Thanks guys!

---

### Post by bjornolai on 2007-10-08
I wrote down how I got the RX560 to work in case anyone might find it useful. I do not give any guarantee that this will work for you. Don't run commands in blind faith :) If this little howto is better suited elsewhere in the forums feel free to copy it. I am sorry that I will not be able to follow up. 

Epson Stylus Photo RX560 with Gutenprint 5.1.3

In Ubuntu Feisty (32 bit) this printer works great with the gutenprint-5.1.3. drivers (the release is development, and I could not find precompiled Ubuntu packages).

You can download gutenprint from here:

[URL="http://http://sourceforge.net/project/showfiles.php?group_id=1537&package_id=223929&release_id=516796"]http://sourceforge.net/project/showfiles.php?group_id=1537&package_id=223929&release_id=516796
[/URL]

Before compiling it make sure you have the dependencies installed.  

> 
	$ sudo apt-get install libcupsys2-dev libcupsimage2-dev libgtk2.0-dev libgimp2.0-dev libreadline5-dev libijs-dev 	debhelper zlib1g-dev flex gettext foomatic-db-engine chrpath dpatch


Compile as usual

Unpack it (Right click in Nautilus and select extract here)

In terminal navigate to the unpacked directory (gutenprint-5.1.3)

Run

	> $ ./configure 

Examine the last part of the output. Make sure it says "Build CUPS     yes". Otherwise you still have dependency troubles and will not be able to find the new drivers when adding the printer. Check the README file in the newly created gutenprint-5.1.3 directory. 

If configure output is OK run:

	> $ make clean
	$ make
	$ sudo install
	$ sudo /etc/init.d/cupsys restart

The new driver should now be installed, and you can use System > Administration > Printing to set it up. Alternatively navigate your web-browser to [http://localhost:631/](http://localhost:631/)


The scanner also works, but you need to help sane find it and change some permissions. Run

> $ man sane
 
Scroll down to the problems section. It explains what needs to be done. More extensive information can be found by unpacking and reading the file /usr/share/man/man5/sane-usb.5.gz

In order to get the permission for the usb device in /dev/bus/usb/ to be correct after bootup i made a really crude script (I know nothing of programming :) This might be a security risk. I don't know. But here's how I did it:

> $ sudo gedit ~/.scripts/S99usbscanner

wrote this into the new file:


> #!/bin/bash
chmod 7777 /dev/bus/usb/005/*


You might need to change 005. Run $ sane-find-scanner to find the correct path for you scanner. It's the number after libusb: My output was:

"found USB scanner (vendor=0x04b8 [EPSON], product=0x0827 [USB2.0 MFP(Hi-Speed)]) at libusb:005:002"
 
After saving your script you need to make it executable (just right click in nautilus). Then you must create a symbolic link from it to a directory in which Ubuntu looks for scripts at bootup: 

> $ ln -s ~/.scripts/S99usbscanner /etc/rc2.d/S99usbscanner

That should do the trick. Hope it works for anyone struggling with the RX560.

---

