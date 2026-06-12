---
title: "installing Canon ip2600 printer drivers on ubuntu 12.04"
date: 2012-10-14
forum: General Help
---

### Post by dragonfly41 on 2012-10-14
I'm trying to setup a Canon ip2600 printer on Ubuntu 12.04.1

I've already got an HP Laserjet 2100M working using HPLIP Toolbox and configuration via   [http://localhost:631](http://localhost:631)

But the Canon ip2600 printer driver is not listed in [http://localhost:631/admin/](http://localhost:631/admin/) 

If I go into Ubuntu Software Center and try to install cnijfilter-ip2600series I get this popup
[COLOR=Navy]
"Requires installation of untrusted packages[/COLOR]"

and I can proceed no further.. even if I press on o.k.

Are there any guidelines for installing Canon ip2600 drivers on Ubuntu 12.04?

Info of driver is .. 

info: cnijfilter-ip2600series 3.70.1-0~23~precise1

---

### Post by Kirk Schnable on 2012-10-14
I am running Ubuntu 12.04 as well, and I do not see cnijfilter-ip2600series in the repository.

I assume this means you're using a 3rd party software source to download the package?

If so, the error you're encountering may be harmless.  The error you're seeing is generally because you've installed a 3rd party software source but you have not correctly installed the GPG key.

The GPG key is used to verify that the software provider's server is really the server you're downloading from.

If it's a third party source, you need to properly install the GPG key, or otherwise just ignore the error and install the package anyway.

Kirk

---

### Post by pdc on 2012-10-15
Canon supply drivers for the ip2600 series;

they provide debian packages for Ubuntu;

if you go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html)

and download the [COLOR="Red"]common package[/COLOR] and install it first

[COLOR="Green"]IJ Printer Driver Ver. 2.90 for Linux (debian Common package)[/COLOR]

and then go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html)

for the [COLOR="Red"]specific ip2600 series[/COLOR] driver

[COLOR="Green"]IJ Printer Driver Ver. 2.90 for Linux (debian Package for iP2600 series)[/COLOR]

that should get you going

(are you running 32bit Ubuntu?)

---

### Post by dragonfly41 on 2012-10-15
Thanks for the replies.

I can only test the Canon ip2600 setup for short periods and at day to day intervals since it is running on another 32 bit Acer laptop (Ubuntu 12.04).  So I can only report between tests.

**Re: Kirk reply**
I now understand the requirement for GPG key.


**Re: pdc reply**

I had already found those downloads after earlier searching around.

But I find that cnijfilter-common requires libcupsys2

I also found this site ...

[http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html](http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html)

But when installing 

sudo apt-get install cnijfilter-ip2600series

I again find the dependency 

Depends libc6 (>=2.7)
Depends: libcupsys2 | libcups2
Depends: bpopt0(>=1.14)

so in Synaptic Package Manager the package is shown as "broken".

libcupsys2 is not in the Synaptic repository.

I did find libcupsys2_1.3.9-17ubuntu1_all.deb


When trying to install it I see this error ..

"Items cannot be installed or removed until the package catalogue is repaired."

I click on "Repair" but can't get past this stage.

I need to pre-install libcupsys2.   But from where?

---

### Post by pdc on 2012-10-15
as it is not a new printer, canon haven't updated the driver;

post #7 here

[http://ubuntuforums.org/showthread.php?t=1427098](http://ubuntuforums.org/showthread.php?t=1427098)

has a script that a french guy, demonipuich has written;

....and you can see the entire script to see it is good.......

..that he says overcomes this error you report

......what about you give that a whirl, and let us know how it goes?

I imagine when you click to download the file; it will offer to run as an .sh file

---

### Post by jdrichardson on 2012-10-15
Go to this website and follow the instructions given.

[https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)

I've successfully installed drivers for my iP2600 printer from this site

---

### Post by dragonfly41 on 2012-10-16
Thanks again ...

I'm able to test Canon deb package on ubuntu 12.04 but without the Canon ip2600 printer actually attached at this stage.

===========================================================

I did try the bash script from the French forum but it didn't work for me.   Probably because I had filters already installed.
[COLOR=Navy]
"Preparing to replace cnijfilter-common 3.70.1-0~23~precise1 (using cnijfilter-common_2.90-1_i386.deb) ..."[/COLOR]

So the script was changing "libcupsys2" to "libcups" and repackaging.

===========================================================

Referring to Synaptic Package Manager ... which I've installed on 12.04.

Searched for "cnij" ..

I had cnijfilter-common as installed version 2.90-1  .. but the latest version is 3.70.1-0~23-precise1

and I had cnijfilter-ip2600series as installed version 2.90-1  .. but the latest version is 3.70.1-0~23-precise1

Marked both for upgrade .. successful upgrade .. no dependency problems raised.

The older version had a dependency for libcupsys2 (which is not in ubuntu 12.04)

Checked again for dependencies with ..
[COLOR=Navy]sudo apt-get install -f[/COLOR]

I'll follow these steps when I revisit the other 12.04 laptop which has canon printer attached.     I'm hoping this solves the problem.

In fact I had previously added these to /etc/apt/sources.list
[COLOR=Navy]
deb [http://ppa.launchpad.net/michael-gruz/canon-trunk/ubuntu](http://ppa.launchpad.net/michael-gruz/canon-trunk/ubuntu) precise main
deb-src [http://ppa.launchpad.net/michael-gruz/canon-trunk/ubuntu](http://ppa.launchpad.net/michael-gruz/canon-trunk/ubuntu) precise main[/COLOR]

The conclusion is that I had older (**2.90-1**) filters installed from my earlier setup attempts which were not purged to allow latest versions (**3.70.1**) to be installed.   I should have upgraded the filters using Synaptic Package Manager.


[COLOR=DarkRed]
====================================================================================[/COLOR]

[COLOR=DarkRed]**Later Edit**

I've now had a chance to test a connected Canon ip2600 printer.

What I found on the other laptop was older version of cnij filter installed (which I marked as "Mark for Complete Removal")

I installed the latest cnij filters .. as mentioned above in setting up my first laptop .. but Canon printer still refused to print.

I had to go into systems settings > printers to uninstall/delete the Canon ip2600 printer then "Add New Printer" after the latest drivers had been installed.  Then "test page" and the printer came to life.

In short, everything has to be purged before installing new drivers.[/COLOR]

---

