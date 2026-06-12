---
title: "new printer: CLP-300N"
date: 2006-11-15
forum: General Help
---

### Post by Vinger on 2006-11-15
Hello,

My father bought a new printer at home (Samsung CLP-300N) and this is working fine on all his windows-pcs. Now, mine is a Kubuntu 6.06LTS (with installed gnome). I can't get it installed.

I tried the cd, but after 3 times giving my root password, it stops working. (nothing happens anymore.)
I tried downloading the driver from the Samsung site, but there it stops after giving the root-password.

I think i have every requirements installed > 
Requirements :
- GTK+ 1.2 libraries ; these usually come with the GNOME desktop environment,
but if your distribution didn't install those by default, you will need to
install them before you can use the graphical tools from this package.
- A working Ghostscript installation
- CUPS 1.1.x is the preferred printing system for this package, but the
Linux Package will accommodate any other printing system based on LPD.
CUPS 1.1.14 packages are provided as a convenience with this program, and can
be installed or upgraded from the installer. However, users of Debian and
Slackware distributions should make sure they have an active printing system
(such as LPD) before proceeding with the installation. 
How can i control that?
> koen@Kubuntu:~$ gs
ESP Ghostscript 815.02 (2006-04-19)
Copyright (C) 2004 artofcode LLC, Benicia, CA. All rights reserved.
This software comes with NO WARRANTY: see the file PUBLIC for details.

I really want to be able to print again...

---

### Post by Vinger on 2006-11-15
I managed to start the installprogram, (sudo ./setup.sh)...

In the end, he says -> installation succesfull.
But i get an error message:
CUPS_BackEnd: get-printers failed: client-error-not-found

When i go to printers, there is no new printer. When i search the list for printers, my printer isn't in the list.

How can i add my (network)printer?

---

### Post by fragos on 2006-11-15
Didn't find your printer in [http://www.linuxprinting.org](http://www.linuxprinting.org) list of compatable printers.  It may be too new to be listed.  Printers can be a sore spot with Linux.  Some companies like HP and Epson are very good at seeing their printers are supported by Linux.  Canon for example is not.  I don't know what effort Samsung makes to support Linux.

---

### Post by Vinger on 2006-11-16
But i downloaded the driver from the Samsung site, so i think it's supported. (otherwise, there wouldn't be drivers for linux???)

it's just the error i get at the end of the install...](*,)

---

### Post by Vinger on 2006-11-16
I managed to end the program without popping up an error.
But in the shell, i get folowing error:
> koen@koen-laptop:~/Desktop/image$ sudo sh setup.sh
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
Warning: LPP_Init() failed! Waiting 2 seconds...
Warning: LPP_Init() failed! Waiting 2 seconds...
Warning: LPP_Init() failed! Waiting 2 seconds...
/home/koen/Desktop/image


I folowed the latest post in this topic: [http://www.ubuntuforums.org/showthread.php?t=101774&page=2](http://www.ubuntuforums.org/showthread.php?t=101774&page=2)

anyone an idea?

---

### Post by fragos on 2006-11-16
I've never used a Samsung printer so I've no direct experience.  My only suggestion is to go back to the Samsung site and insure there isn't something else you needed to download.  For example the ksycoca database.  I Googled "ksycoca" and got 560 results.  Perhaps there's something in there that can help.

---

### Post by Vinger on 2006-11-17
This is the complete error message i get after a clean reinstall of kubuntu...

> 
koen@kubuntu:/cdrom$ sudo sh setup.sh
Warning: kbuildsycoca is unable to register with DCOP.
kbuildsycoca running...
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
CUPS_BackEnd: get-printers failed: client-error-not-found

Warning: LPP_Init() failed! Waiting 2 seconds...
CUPS_BackEnd: get-printers failed: client-error-not-found

Warning: LPP_Init() failed! Waiting 2 seconds...
CUPS_BackEnd: get-printers failed: client-error-not-found

Warning: LPP_Init() failed! Waiting 2 seconds...
/cdrom
scripts/profiled.sh: ./psu/install.sh: /bin/sh: bad interpreter: Toegang geweigerd
scripts/profiled.sh: ./smartpanel/install.sh: /bin/sh: bad interpreter: Toegang geweigerd


Anyone an idea?

---

### Post by fragos on 2006-11-17
I wish I could make further suggestions but I'm at a lose for anything remotely constructive.  I haven't used KDE in a while.  Linuxquestions.org has an active ubuntu forum.  You might try there as well.  [http://www.linuxprinting.org/](http://www.linuxprinting.org/) seems to have the printer related information.  They would also be a good place to check.

---

### Post by Vinger on 2006-11-18
I tried the opendrivers suggested in linuxprinting.org.

Now, i get errors, when i try to compile the source:

> 
koen@kubuntu:~/Desktop/splix-1.0.1-beta$ make
make[1]: Map '/home/koen/Desktop/splix-1.0.1-beta/src' wordt binnengegaan
g++ -O2 `cups-config --cflags`  -I../include   -c -o spl2.o spl2.cpp
g++ -O2 `cups-config --cflags`  -I../include   -c -o printer.o printer.cpp
g++ -O2 `cups-config --cflags`  -I../include   -c -o band.o band.cpp
g++ -O2 `cups-config --cflags`  -I../include   -c -o compress.o compress.cpp
g++ -O2 `cups-config --cflags`  -I../include   -c -o rastertospl2.o rastertospl2.cpp
In bestand ingevoegd door rastertospl2.cpp:22:
../include/raster.h:25:25: fout: cups/raster.h: Onbekend bestand of map
../include/raster.h:38: fout: ISO C++ forbids declaration of ‘cups_raster_t’ with no type
../include/raster.h:38: fout: expected ‘;’ before ‘*’ token
../include/raster.h:39: fout: ‘cups_page_header_t’ does not name a type
make[1]: *** [rastertospl2.o] Fout 1
make[1]: Map '/home/koen/Desktop/splix-1.0.1-beta/src' wordt verlaten
make: *** [src] Fout 2


anyone an idea?

---

### Post by fragos on 2006-11-18
I'm not an expert but I don't see anything that says "error."  After running make did you try "sudo make install"?  Its safe because if make failed the make install will instantly fail.

---

### Post by Vinger on 2006-11-18
In fact 'fout' is error in dutch...

What i get from sudo make install:
> 
koen@kubuntu:~/Desktop/splix-1.0.1-beta$ sudo make install
Password:
make[1]: Map '/home/koen/Desktop/splix-1.0.1-beta/src' wordt binnengegaan
g++ -O2 `cups-config --cflags`  -I../include   -c -o rastertospl2.o rastertospl2.cpp
In bestand ingevoegd door rastertospl2.cpp:22:
../include/raster.h:25:25: fout: cups/raster.h: Onbekend bestand of map
../include/raster.h:38: fout: ISO C++ forbids declaration of ‘cups_raster_t’ with no type
../include/raster.h:38: fout: expected ‘;’ before ‘*’ token
../include/raster.h:39: fout: ‘cups_page_header_t’ does not name a type
make[1]: *** [rastertospl2.o] Fout 1
make[1]: Map '/home/koen/Desktop/splix-1.0.1-beta/src' wordt verlaten
make: *** [install] Fout 2


---

### Post by Vinger on 2006-12-05
ok, some news here:

the splix driver doesn't work yet for the CPL-300(n). 
I retried to install the closed drivers from Samsung, and now, it finished. The drivers are installed, but when i try to add a new printer (sudo linux-config) i have to choose which type of connection.

I think it is a IPP connection i need, but what is the following parameters?
host: (ipp://ip-address/ipp   ???)
queue: ???
login -> my login
password -> my password..

anyone an idea what i need to type into host and queue?

tx!

---

### Post by Hende on 2006-12-29
Hello,

I bought also a Samsung CLP-300 (Network compatible). Trying first to use it through USB and got installation this far with Samsung's delivered software (Linux Print Package Tool v1.1):

[INDENT]sudo sh ./setup.sh
uninstall: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
Aborted
setupdb-bin.Yc7jJL: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
Aborted
Keeping existing configuration file.
/media/cdrom
scripts/profiled.sh: 89: ./psu/install.sh: Permission denied
scripts/profiled.sh: 92: ./smartpanel/install.sh: Permission denied
sh: Syntax error: "(" unexpected[/INDENT]

After that a Linux OPrinter Configuration screen opens, basicly everything seems to work, but all print jobs are stopped, even test page.

If [http://localhost:631/](http://localhost:631/) is opened, nothing special seems to be there, but jobs are getting stopped.

Anyone here who could help with this? 

Since my printer is a network equipped, do You know a good instructions anywhere how to set-up a connection between Ubuntu edgy and a network laser. I'm using DSL-modem outside, but inside has a four port router witha firewall. Should I assign an internal IP or what You'd recommend ?

Thank You in advance !

---

### Post by Hende on 2006-12-29
Just noticed that if trying to resume stopped job, I get a message: Unable to modify jobs, even started linux-config with sudo.

Do I still miss some authorisation somewhere from CUPS side?

---

### Post by fragos on 2006-12-29
> **Hende said:**
> Just noticed that if trying to resume stopped job, I get a message: Unable to modify jobs, even started linux-config with sudo.

Do I still miss some authorisation somewhere from CUPS side?

Applications installed in user space are the users but applications installed as a system resource require root access for administrative actions.  Perhaps if your printer was installed as local you'd have more control options.

---

### Post by Vinger on 2006-12-30
Hey,

I found a solution to use it under Kubuntu...
If you go to the samsung website, you can dowload the linux driver and the unified driver. 

The unified driver has installed itself without problems and i can print. Hope this helps for you also...

grz

---

### Post by Hende on 2006-12-30
Hei,

I tried that now and no help.. = ) I got following:

 sudo ./install.sh
./install.sh: 1232: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted

Any tips what I could try ?

---

### Post by fragos on 2006-12-30
Anything with .sh is a bash shell script.  You can open it with an editor to see what it's doing.  You can find where that error message was generated.  Sounds like all it wants is to know the hardware type, i386, AMD64 and etc.  Perhaps install.sh needs to be called with a parameter.  Did the this script come with a README?

---

### Post by Vinger on 2006-12-31
You have to read the readme file to see what other programs has to be installed... 

Then, it didn't gave any errors on my i386-platform...

grz

---

### Post by tweedledee on 2006-12-31
> **Hende said:**
> Hei,

I tried that now and no help.. = ) I got following:

 sudo ./install.sh
./install.sh: 1232: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted

Any tips what I could try ?

You need to open install.sh and replace "sh" in the first line with "bash."  That will eliminate the error you've just mentioned.  I also had to make a couple of other changes in the script to get my 550n installed, but most people get it working with only that single one.

Also, my printer actually works over the network with the JetDirect protocol only (port 9100), not IPP or the others.  Yours may or may not be the same, mine's a couple of years old now.

---

### Post by gregb49 on 2007-01-26
I'm failing as well, but on the CLP-300 CD is a folder called bin, with a sub folder - linux which contains ppc, x86 and x86-64 folders. I have copied the x86 folder into my etc folder. Its structure is a shown below. I've tried to install the printer through peripherals- printer (that's the extent of my knowledge), but the package doesn't recognise any of the files in the folder as being of any use. 

x86¬
.........bin¬
...............linux-config
...............linux-uninstall
...............llpr
.........filter¬
..................18 files including
...................lpdprint
...................pclprint
...................gdiprint
...................smbprint
........cfgen
........check
.........remove printer

Hope that info helps someone - but I'm just stuck at the moment.

Greg

(now KUBUNTU 6.10)

---

### Post by fragos on 2007-01-26
Placing the driver information in the right place may not be sufficient.  You may need to run a command line bit to rebuild the printer DB or install the drivers with KDE.  I'm an Ubuntu user so I can't be more specific than that.

---

### Post by palmik on 2007-02-16
Hello

I've had this nice printer for a couple of weeks now. It is connected via its' network connection to my 4-port ADSL box.

First I installed it to WinXP (boo :-) and with its installer utilities set the printers IP to a suitable 192.168.0. ... -one. Installation to Mac Mini was also straight forward. 

I had to do a couple of days of wrestling to set it up with Ubuntu Feisty Fawn x86_64. Driver installer From CD or Samsung site didn't do anything. Unified driver installer from Samsung site worked ok and even detected the network printer ok. But it didn't list the correct printer model to choose the driver. Fair enough, I tried to install the correct model via gnome-cups-manager, handing the ppd-file from the extracted unified driver file /cdroot/Linux/noarch/at_opt/share/ppd/CLP-300splc.ppd and partly succeeded - the test page only printed the top of the page and printing from elsewhere resulted in far from decent results on paper. Cups manager also warned about some missing rasterto-filter...
Then I uninstalled the unified driver configurator whichafter (lots of google) I copied rastertosamsungsplc to /usr/lib/cups/filter/ like:

sudo cp .../cdroot/Linux/x86_64/at_root/usr/lib64/cups/filter/rastertosamsung* /usr/lib/cups/filter/

and installed the printer again via gnome-cups-manager and selected as a connection: network printer, CUPS printer (IPP), URI: ipp://192.168.0. ...:631 and it did the thing.

By the way I didn't have any problem with /bin/sh -- /bin/bash mentioned earlier on in the thread as I've changed /bin/sh pointing from ubuntu default dash to bash by:

rm -f /bin/sh
ln -s /bin/bash /bin/sh

Got that from: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu).

In the process I did install splix and sane from the ubuntu repositories but haven't confirmed if they had any influence.

Hope this helps someone...

---

### Post by ceenvee703 on 2007-04-13
Is it obvious how to uninstall the unified drivers?

Printing from Ubuntu to a networked laser printer has been very frustrating for me: I was first unable to print to a LaserJet 1500 with JetDirect interface, and now my new CLP-300N (which shows up as "three penguins" and says "works perfectly") just sits there with docs in its queue.

---

### Post by almax00 on 2007-04-16
[http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/)

a linux printer driver for QPDL protocol
e.g. Samsung CLP-300, Samsung CLP-600, Xerox Phaser 6110

---

### Post by ceenvee703 on 2007-04-22
FINALLY! The foo2qpdl drivers worked! Can't believe I can print from Ubuntu after lo these many months. Thanks VERY much. As Lola Heatherton used to say, "I want to BEAR YOUR CHILDREN!" :)

---

### Post by Hende on 2007-05-01
Thanks !! works fine now..

---

### Post by ThomasNovin on 2007-07-15
> **palmik said:**
> 

By the way I didn't have any problem with /bin/sh -- /bin/bash mentioned earlier on in the thread as I've changed /bin/sh pointing from ubuntu default dash to bash by:

rm -f /bin/sh
ln -s /bin/bash /bin/sh



Do NOT do this! Removing /bin/sh will likely break lots of scripts in the future an can cause major problems. Best thing would be to edit the script you're executing to change for example '!/bin/sh' to '!/usr/bin/bash'. If you must, you can temporarily move sh, create the link, run the installer and then remove the link and restore sh again.

---

