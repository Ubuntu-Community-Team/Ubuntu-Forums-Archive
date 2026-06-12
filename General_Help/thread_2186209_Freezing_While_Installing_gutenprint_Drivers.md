---
title: "Freezing While Installing gutenprint Drivers"
date: 2013-11-06
forum: General Help
---

### Post by cessanfrancisco on 2013-11-06
I am trying to install gutenprint printer drivers and my computer keeps freezing.  I am trying to install using System Settings>Printers>...

I am using Ubuntu 13.10 on a Lenovo Z580 (if you need more info/specs please ask).

Can anyone help me figure this out?

Thanks in advance.

---

### Post by mc4man on 2013-11-07
I did notice that on 14.04 if trying to install from "Printers" the driver install starts but never finishes (at least in the time i gave it)

What did work & work quickly was to install gutenprint (5.0.1-1lsb3.1) from synaptic, or cli, (sudo apt-get install gutenprint),  then after done open Printers & add using the gutenprint entry (not the printer itself entry - screen 1
after done it show up properly in printers - scr. 2

( i just do basic text printing on linux so haven't bothered to look for Canon drivers as have them in Win7

---

### Post by philinux on 2013-11-07
> **cessanfrancisco said:**
> I am trying to install gutenprint printer drivers and my computer keeps freezing.  I am trying to install using System Settings>Printers>...

I am using Ubuntu 13.10 on a Lenovo Z580 (if you need more info/specs please ask).

Can anyone help me figure this out?

Thanks in advance.

There's a new system-config-printers going through the update process for saucy. I just got these through.

```
The following packages will be upgraded:
  libglamor0 python-cupshelpers system-config-printer-common system-config-printer-gnome
  system-config-printer-udev xserver-xorg-glamoregl
```

It might fix your problem.

[http://www.ubuntuupdates.org/package/core/saucy/main/updates/system-config-printer](http://www.ubuntuupdates.org/package/core/saucy/main/updates/system-config-printer)

To bypass the software-updater's phased method use the terminal.

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by cessanfrancisco on 2013-11-07
@philinux:
Thanks for the suggestion.  I tried that yet to no avail.

@mc4man:
Thanks for your suggestions, too.
I tried to install gutenprint via the Synaptic Package Manager but there are a lot of packages after doing a query for "gutenprint."  I'm not sure which one(s) to install.  I also tried the "sudo apt-get install gutenprint" command in the terminal, but it replied, "unable to locate package gutenprint."

Which packages in Synaptic should I install?  Thanks.

---

### Post by gwmcvay on 2013-11-08
Came across this thread while searching for a solution to this exact problem.  I have a Dell 2130cn that I am attempting to install on an Acer Aspire 5552-5619.  This is a fresh install of 13.10.  I have 13.10 on another laptop that was an upgrade and the printers continued to work.  If I come up with anything, I will of course post what resolution I find.

V/r,

Will

---

### Post by dpatterson2 on 2013-11-16
I am having the same problem with 13.10. The Gutenprint installation freezes while trying to install drivers for my Canon MP830. This is on a custom build PC.

---

### Post by l2ura on 2013-11-21
yes joy I am having this same problem with CANON Pixma 9882. Ubuntu 13.10 saucy.

---

### Post by cessanfrancisco on 2013-12-18
@mc4man
Thanks.  I followed your instructions and everything is working great now!

Thanks again!

---

### Post by djtarki on 2013-12-29
> **mc4man said:**
> I did notice that on 14.04 if trying to install from "Printers" the driver install starts but never finishes (at least in the time i gave it)

What did work & work quickly was to install gutenprint (5.0.1-1lsb3.1) from synaptic, or cli, (sudo apt-get install gutenprint),  then after done open Printers & add using the gutenprint entry (not the printer itself entry - screen 1
after done it show up properly in printers - scr. 2

( i just do basic text printing on linux so haven't bothered to look for Canon drivers as have them in Win7


Thanks mc4man!, it worked after following your instructions.

:guitar:

---

### Post by fredrik.floren on 2014-01-09
I'm having the same problems with freezing as described above. I've installed gutenprint (transitional-dummy) from synaptic package manager and then I try to add the (networked) Epson PX730WD I have on my LAN. The printer is found on and I choose the the driver gutenprint but the progress bar does not change in the following dialog (called "installing driver openprinting-gutenprint"). How can I troubleshoot the problem?

I am on 13.10. The installation of this printer went smoothly on an older laptop I previously used, also with 13.10.

Really want to print my photos!

---

### Post by joeoettinger on 2014-01-16
I'm not sure that this thread should be labelled solved.

The installation of gutenprint (now called openprinting-gutenprint) still hangs.

The wi-fi printer for which I've tried to install a driver is the canon MX410 wifi printer using ubuntu 13.10.

I tried mc4man's advice and in the cli entered
	sudo apt-get install
and that gave the message:
	E: Unable to locate package gutenprint

I installed synaptic package manager and the gutenprint packages listed were for version 5.2.9-1ubuntu2. There was no gutenprint(5.0.1-1lsb3.1)

So I installed the packages of version 5.2.9-1ubuntu2.
(One of these was called a transitional dummy package, with the description:
"This is a transitional package to install the CUPS driver based on
Gutenprint, which has been renamed to printer-driver-gutenprint.")

Then I rebooted and tried the installation again.

When I chose select device, I selected the option the new printer app offered:
	canon MX410(...)

When I came to "choose driver" there were the options:
gutenprint
Local Driver

gutenprint was hi-lited, so I clicked Forward

But ... the window titled 'Installing driver openprinting-gutenprint' hung again.

I even installed Mint 16 petra, and got the same result! Actually, I guess that isn't surprising as it's derived from ubuntu.

I'd really appreciate any advice on this problem.
I notice many other posts about the problem, going back several months.

By the way I don't think that this gets said often enough, by me and many others:
I think both Ubuntu and Mint are great OS's and certainly appreciate all the work of the administrators and contributors.

---

### Post by cessanfrancisco on 2014-01-16
I think this issue is tied to another issue:

[http://ubuntuforums.org/showthread.php?t=2042929](http://ubuntuforums.org/showthread.php?t=2042929)

When I have this in my sources list:

deb [http://www.openprinting.org/download...driver/debian/]("http://www.openprinting.org/download/printdriver/debian/") lsb3.1 gutenprint

the package, "gutenprint(5.0.1-1lsb3.1)" shows up in synaptics for me. Otherwise I don't see it in synaptics.

---

### Post by joeoettinger on 2014-01-17
cessanfrancisco, 
I tried editing /etc/apt/sources.list to add the entry you have in your sources.list file:
deb [http://www.openprinting.org/download...driver/debian/](http://www.openprinting.org/download...driver/debian/) lsb3.1 gutenprint

I assumed that the ... in the entry meant
deb 'http://www.openprinting.org/download/printdriver/debian/' lsb3.1  gutenprint
(minus the single quotes).
But when I saved that, and entered  
sudo apt-get install gutenprint
I again got the message
E: Unable to locate package gutenprint
And the package, "gutenprint(5.0.1-1lsb3.1)" didn't show up in synaptics.

I'm a novice at this, and I imagine I'm doing something stupid, 
but maybe if you can give me the exact line in your sources.list file
I can get it to work. (I think you have to put the line in single quotes to avoid
modification of the line by the app that prints these posts.) 
Thanks.

---

### Post by ian-weisser on 2014-01-17
That's right - there is no package called "gutenprint". But the gutenprint driver is not hard to find:

Using 13.10:
```
$ apt-cache search gutenprint
cups-driver-gutenprint - transitional dummy package for gutenprint printer driver
gutenprint-doc - users' guide for Gutenprint and CUPS
gutenprint-locales - locale data files for Gutenprint
libgutenprint-dev - development files for the Gutenprint printer driver library
libgutenprint-doc - documentation for the Gutenprint printer driver library
libgutenprint2 - runtime for the Gutenprint printer driver library
libgutenprintui2-1 - runtime for the Gutenprint printer driver user interface library
libgutenprintui2-dev - development files for the Gutenprint printer driver user interface library[B][COLOR=#008000]
[/COLOR][COLOR=#ff0000]printer-driver-gutenprint - printer drivers for CUPS[/COLOR][/B]
escputil - maintenance utility for Epson Stylus printers
foomatic-db-gutenprint - OpenPrinting printer support - database for Gutenprint printer drivers
gimp-gutenprint - print plugin for the GIMP
ijsgutenprint - inkjet server - Ghostscript driver for Gutenprint
ijsgutenprint-ppds - transitional dummy package for gutenprint printer driver
```
There it is.
```
sudo apt-get install printer-driver-gutenprint
```

---

### Post by cessanfrancisco on 2014-01-17
The way described by ian-weisser sounds far easier than my method.

My way was stumbled upon by me trashing about...

I opened my sources list:
```
gedit /etc/apt/sources.list
```

I added this to the end of my sources list:
```
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.1 gutenprint
```

Then I did:
```
sudo apt-get update
```

Then did a search in synaptic package manager for: gutenprint

The package was there and I installed it.  Then I followed the instructions by mc4man, earlier in this post

Having said all that, this may not be the most graceful or economical way to go about getting the job done, but it did get the job done...at least for me.  But like I said I stumbled upon this solution serendipitously.

---

### Post by joeoettinger on 2014-01-17
Thanks so much,   ian-weisser and cessanfrancisco!
I added
deb 'http://www.openprinting.org/download/printdriver/debian/' lsb3.1 gutenprint'
(again, without the single quotes) to /etc/apt/sources.list, then:
sudo apt-get install gutenprint
It actually did work, and allow me to use system settings > printers > add > network printer > etc
to install my wifi canon-pixma-mx410.

I bet there will be many ubuntu novices grateful for this!

---

### Post by andrewp-terra on 2014-03-07
I found that this solved the problem for me:
```

sudo apt-get install lsb

```

---

### Post by r_fujii on 2014-04-01
Hi - I followed the instrcutions given by mc4man and successfully installed gutenprint using synaptic.
However, upon opening Printers--> Add, I do not see a "gutenprint-usbXXX".
Have I missed a step in between ?  I am using ubuntu 13.04.

Thank you.
Robert

---

### Post by dcody on 2014-07-04
THANKS andrewp-terra

DID AS YOU DID AND EVERYTHING WORKS GREAT. AWESOME!!

---

### Post by edumuitoloco on 2015-05-26
> **cessanfrancisco said:**
> I think this issue is tied to another issue:

[http://ubuntuforums.org/showthread.php?t=2042929](http://ubuntuforums.org/showthread.php?t=2042929)

When I have this in my sources list:

deb [http://www.openprinting.org/download...driver/debian/]("http://www.openprinting.org/download/printdriver/debian/") lsb3.1 gutenprint

the package, "gutenprint(5.0.1-1lsb3.1)" shows up in synaptics for me. Otherwise I don't see it in synaptics.


Worked! Thanks!

---

### Post by mitchell22 on 2016-02-07
> **cessanfrancisco said:**
> I am trying to install gutenprint printer drivers and my computer keeps freezing.  I am trying to install using System Settings>Printers>...

I am using Ubuntu 13.10 on a Lenovo Z580 (if you need more info/specs please ask).

Can anyone help me figure this out?

Thanks in advance.



This walk through  solved my problem. 
[http://community.linuxmint.com/tutorial/view/194](http://community.linuxmint.com/tutorial/view/194)

---

