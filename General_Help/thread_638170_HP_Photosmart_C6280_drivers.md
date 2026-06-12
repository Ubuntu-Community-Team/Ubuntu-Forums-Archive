---
title: "HP Photosmart C6280 drivers"
date: 2007-12-11
forum: General Help
---

### Post by underdog512 on 2007-12-11
is there any place to get dirvers for the 6200 series all-in-ones.  Specifically, I want to use the the scanner in xane and access the printer through Hplip toolbox.

---

### Post by shirilover on 2007-12-11
Sure,
```

sudo aptitude install hplip

```

Works for my deskjet 4215 all-in-one.

---

### Post by JohnnyVW on 2007-12-11
You have to get the lastest and greatest hplip.  The version in the Ubuntu repos doesn't support the 6280 yet.  I just got the Photosmart 6280 and with hplip v2.7.10, it works great!

Go here:  [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

I uninstalled the Ubuntu version through Synaptic first.  Download the script from the hplip site and run it as a regular user.  it will ask you for the root password while it's running.  

It really works well!  The only issue I'm having is that I can't share the 6280 with my other machines...  The other printers atached to my Ubuntu box share just fine.

---

### Post by underdog512 on 2007-12-16
install of the latest toolbox seem to be freezing up 

Here is what displays when the install halts:

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-reportlab libsane-dev python-imaging'
Please wait, this may take several minutes...
/



Anybody know whats going on?

---

### Post by BumbleBeeJeep on 2007-12-17
Same situation here with fresh install of Ubuntu Studio Gutsy.  Tried to install HPLIP, terminal suddenly freezes up.  The toolbox shows in the system dropdown, but it does nothing.  Ditto for launching toolbox from command line.  I've successfully installed the networked PhotoSmart C6180 on two other computers, one running Fiesty and the other Gutsy, both plain vanilla.  The printer is directly wired to the router, not wi-fi.  As I said, it works with the other computers.  I should mention that I am dual booting with XP, and it works fine there as well.

Here's where things stop working: right as I reach the point where the installer tells me to unplug the USB cable or restart the PC (did the restart) and sudo hp-setup.  The cursor just blinks away with the words "Please make sure your printer is connected and powered on at this time".  The HPLIP site recommended entering the root password at this point, but that's no help either.  I guess the next step is to try to do a manual install unless anyone has other ideas.

Thanks
Bb

---

### Post by caller#6 on 2007-12-26
BumbelBeeJeep and/or underdog512: were you able to get your 6280s installed? Are they up and running?

Before I run out to buy one, I'd like to hear some good news.

Thanks,

---

### Post by underdog512 on 2007-12-26
well I can print w/ the printer just fine.  still cannot scan.  doesn't seem like the 6200 drivers are out

---

### Post by caller#6 on 2007-12-28
> **underdog512 said:**
> well I can print w/ the printer just fine.  still cannot scan.  doesn't seem like the 6200 drivers are out

What version of hplip are you using? As mentioned above, the version in the Ubuntu repositories is 2.7.7, while the c6280 requires at least version 2.7.9. Newer versions are available at [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

I'll let you know when/if I get one and how/if I get it to work.

---

### Post by DonA on 2007-12-29
Hi there,

I was having a similar problem.  My daughter just moved out, taking her PhotoSmart 3200 with her.  I loved that printer.  So I replaced it with a PhotoSmart C6280.  Like others, I found that I could print, but couldn't scan in Ubuntu 7.10.  Following the hint from the previous post, I downloaded and installed the latest hplip from sourceforge.net.  (I believe it was version 2.7.12.) I ran the .run file from sudo, and ignored the warning about installing as root.  Everything went without a hitch.  My C6280 is network-connected.  To initiate a scan from the PC, I created a launcher with this command: 
[INDENT]xsane hpaio:/net/Photosmart_C6200_series?ip=192.168.1.111[/INDENT]
Regards:   ..DonA

---

### Post by chrigldigl on 2007-12-29
hi underdog and those of you who have the same problem as underdog: When running the hplip-*version>.9*.run script, the console freezes after the following output:

> DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-reportlab libsane-dev python-imaging'
Please wait, this may take several minutes...
/

If you scroll up in the console you will see that some required dependencies are missing. These are being downloaded in this apt-get command. Unfortunately the packet build-essential requires the ubuntu cd but the --force-yes option prevents apt from telling you this. So my solution:

* Stop the installation with ctrl+C.
* Kill apt  (i.e. sudo pkill apt-get)
* Install build-essential manualy
```
sudo apt-get install build-essential
```
* start the installer one more time

---

### Post by fulkrum on 2008-02-20
I am not sure if updated drivers are really required for this printer. I bought C6280 today and connected it to the network. I was able to add the printer using the printer config icon under "System settings". I selected TCP network printer and gave it the printer IP address and I was all set! For driver I sepected Photosmart C6100.

For scanning, I first installed xsane and other sane stuff (libsane was already installed). kooka does not recognize the scanner on the network yet, but xsane works perfectly using the command:

**xsane hpaio:/net/Photosmart_C6200_series?ip=192.168.1.3**

Thanks to DonA for the tip!

My setup:

Kubuntu 7.05
hplip 1.7.3-0ubuntu1.1 

I also have the hp tools installed, but I am not able to use them. hp-setup cannot see the printer (although its installed in CUPS - I can see it on the cups local server webpage) and asks me to set it up again. If I do so, I get 2 printers in CUPS and still the tools do not work. Maybe C6200 drivers are needed for this. At the moment, I don't care as things like ink level are very well seen on the printer's LCD display. For me printing and scanning is working across the network without much trouble and I love that!

---

### Post by herman moolenaar on 2008-06-01
For everybody interested in buying a HP C6280 all in one printer: it works flawlessly here with ubuntu 8.04. I'm using the tcp/ip connection.  According to the website hplip version 2.7.9 supports the C6200 series, but not in my case. I installed version 2.8.5, downloaded [here]("http://hplip.sourceforge.net/"). The correct dpp file that is needed during the installation can be downloaded [here]("http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C6200").

Printing works fine, double sided printing works also and xsane worked out of the box.
I've yesterday upgraded to Ubuntu 8.04 (fresh install) and printed about 10 pages all double sided up till now.

---

