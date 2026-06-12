---
title: "Canon ip1800 Printer not installing"
date: 2008-02-22
forum: General Help
---

### Post by bigred1 on 2008-02-22
I plugged in my new Canon PIXMA iP1800 Printer to the USB port and was pleased to see "ip1800" magically appear in the System->Administration->Printing interface. 

However, attempts to print from apps (e.g., TextEditor) fail. When I attempt to   print a test page, I get "CUPS server error. There was an error during the CUPS operation: 'client-error-document-format-not-supported'."


I also tried using the Printing interface to install a New printer. Canon PIXMA ip1800 did not appear there, but a  "Canon BJ-5 Foomatic/bj10e"  driver appeared, asnd I tried that. With this one, I don't get the error message on printing a test page, though still nothing prints.

What should I do to get this printer working?

(Using Gutsy on a commodity Intel 32-bit system).

---

### Post by linuxwizard on 2008-02-23
According to this > [http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1800](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1800) > you need this driver > [http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20iP1800%0amenu%3d%3dDownload%0aos%3d%3dLinux&](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20iP1800%0amenu%3d%3dDownload%0aos%3d%3dLinux&)

---

### Post by bigred1 on 2008-02-25
The  drivers at support-au.canon.com.au  are RPM which is not supported by Ubuntu.

They have been repackaged into deb files here: [http://caletalinux.blogspot.com/2007/07/canon-ip1800-drivers-en-ubuntu-feisty.html](http://caletalinux.blogspot.com/2007/07/canon-ip1800-drivers-en-ubuntu-feisty.html) 

I installed both these deb files, but still my printer didn't work.

I then created a "new printer" in Ubuntu by pointing to the *ppd *file extracted from the deb archive. This produced a nice test page. However, print jobs still did not execute -- until I restart the computer, and then the print job runs as the computer restarts!

Help will be appreciated.

---

### Post by linuxwizard on 2008-02-25
RPM package will work on Ubuntu but you need to convert it to a Debian package.
[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

Are you using Feisty or Gusty ? Those files you installed are for Feisty.

---

### Post by bigred1 on 2008-02-25
Thanks, I am using Gutsy. I was hoping that those deb files would work. I will try the alien conversion.

---

### Post by fenian on 2008-02-25
Deb files and intructions can be found[ here]("http://hex1a4.net/xubuntu/howto.php?htid=04") (page takes a while to load for me)

---

### Post by bigred1 on 2008-02-25
Linuxwizard, about the alien conversion: It seems that the rpms are in  a forma which cannot be converted by alien, as stated in the  page referenced by fenian: 
[http://hex1a4.net/xubuntu/howto.php?htid=04](http://hex1a4.net/xubuntu/howto.php?htid=04) (I also gave alien a try. and it did not work.)

So, I will try the deb files at that page.

---

### Post by bigred1 on 2008-02-25
Resolved! 

[This page]("http://hex1a4.net/xubuntu/howto.php?htid=04") mentioned by fenian has  instructions and packaged  deb files.

Note that the second link to a deb file on that page may be wrong, but you can get both deb file [from here]("http://hex1a4.net/xubuntu/HOWTO/dl/").

---

### Post by x1a4 on 2008-02-25
> **bigred1 said:**
> Note that the second link to a deb file on that page may be wrong, but you can get both deb file [from here]("http://hex1a4.net/xubuntu/HOWTO/dl/").

I mistyped the file name in the link.  It is now fixed.

---

### Post by placa1783 on 2008-03-18
My sister have a low pc p2 6gb hd and 64+32 ram running windows 98. She lovs windows  and buy a Canon Pixma IP1800 with usb wire. the drivers are only 4 XP and i couldnt find a way to install it on win98. A friend told me that try CUPS.
How do i get a cups binari that has the driver of Canon Pixma IP1800 for win 98 or how do i get this driver and plug it to the cups?.
How do i instal cups on win?
THANKS VERY MUCH!! u can post here or send me a mail to [email]placa1783@gmail.com[/email]. If i found by my self the way ill post it here.

---

### Post by Golem XIV on 2008-05-01
> **placa1783 said:**
> My sister have a low pc p2 6gb hd and 64+32 ram running windows 98. She lovs windows  and buy a Canon Pixma IP1800 with usb wire. the drivers are only 4 XP and i couldnt find a way to install it on win98. A friend told me that try CUPS.
How do i get a cups binari that has the driver of Canon Pixma IP1800 for win 98 or how do i get this driver and plug it to the cups?.
How do i instal cups on win?
THANKS VERY MUCH!! u can post here or send me a mail to [email]placa1783@gmail.com[/email]. If i found by my self the way ill post it here.


Your problem is that Windows 98 does not have full support for USB.  Even if there were iP1800 drivers for Windows 98, the printer probably would not run since Windows 98 wouldn't know how to communicate with it through the USB port.  If you need a printer for a Windows 98 system, make sure it has a parallel port connection and not a USB one.

Oh, and as for your friend - I don't think you can install CUPS on Windows.  CUPS stands for **C**ommon **U**nix **P**rinting **S**ystem, so it's designed for Unix systems and not the Windows architecture.  Even if you compiled the source code on a Windows compiler, it wouldn't run.

---

### Post by josta7 on 2008-05-07
> **fenian said:**
> Deb files and intructions can be found[ here]("http://hex1a4.net/xubuntu/howto.php?htid=04") (page takes a while to load for me)

THANK YOU!  This worked great for me.:KS

---

### Post by wide-load on 2008-05-12
I'm running 64 bit 8.04.  I tried installing the 2 files recommended here and got a message that they were for "Wrong Architecture i386"****]  Any suggestions as to how to make my pixma ip1800 work on this distribution?

---

### Post by sda3 on 2008-05-16
I am having the same issue as post above.

---

### Post by BobE on 2008-05-29
> **x1a4 said:**
> I mistyped the file name in the link.  It is now fixed.
I'd been using ip1800 on 7.10 then I install 8.04 HH (386 desktop) to a new hd so I needed help.  I found Ur site yesterday & I'm happy to say my  ip1800 prints now, 'thx'!  BobE

---

### Post by Reteip on 2008-06-01
> **bigred1 said:**
> Resolved! 

[This page]("http://hex1a4.net/xubuntu/howto.php?htid=04") mentioned by fenian has  instructions and packaged  deb files.

Note that the second link to a deb file on that page may be wrong, but you can get both deb file [from here]("http://hex1a4.net/xubuntu/HOWTO/dl/").

Hi all
I have Hardy installed. I followed the instructions on the page [from here]("http://hex1a4.net/xubuntu/howto/04/") however, in step 4 when I got to the end (clicked on Modify Printer) there was an error message: Bad device-uri "cnij_usb:/dev/usb/lp0"!

The solution to this is: 
Where it says "On the second screen you have to select which device you want to use, select the one that reads .... " you need to choose - Canon iP1800 series USB #1 (Canon iP1800 series) - instead of the suggested selection. I found this to be the default anyway.
Now all is good!

---

