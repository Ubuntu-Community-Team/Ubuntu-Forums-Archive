---
title: "Help with Officejet AiO"
date: 2008-05-18
forum: General Help
---

### Post by Vryko Lakas on 2008-05-18
Seems the first post is always about something breaking, isn't it? 

I'm running Gutsy I have a problem with the HP Officejet 6310 All-in-One, which is connected through USB. We needed a printer, and after doing some research it seemed this model was supported well and that everything should work. 
At first, everything worked well. However, after scanning a grand total of two images, the scanner stopped working and returned an error message: "Error during I/O" when I ran either xsane or GIMP. 

I then used the automatic installer for the latest HPLIP release (2.8.5). It did not fix my problem, unfortunately. Being less smart than I think I am, I tried looking in Synaptic to see if the old version from the repositories was still installed: it was, so I uninstalled it. It also took another package with it, I think hpijs? 
Now my computer can't even find the printer. I definitely need the printer, and I really need the scanner to work. Some help would be much appreciated, and I'll try to cooperate as best I can. I'm still a Linux newbie, but I moved the family computer to Ubuntu after geting frustrated with Windows XP's security and performance issues.

---

### Post by Vryko Lakas on 2008-05-18
Quick update after a much-needed nap.
I unplugged the USB cable then plugged it back in, and an Ubuntu-style test page was automatically printed. So now the printer is back to square one: printing works, scanning still does not. This time xsane didn't even fully open, and after a significant amount of time an error message reads "Failed to open device 'hpaio:/usb/Officeject_6300_series?serial=CN81LFB33K04J5': device busy."

---

### Post by Vryko Lakas on 2008-05-25
After searching a bit online I opened a terminal and ran the following:
```
sudo tail -f /var/log/messages
```
Then, in another terminal window I entered the command 'xsane' and attempted to scan. In the first window it returned the following error:

May 25 14:02:44 Family-desktop xsane: scan/sane/io.c 57: unable to connect hpssd socket 2207: Connection refused 
May 25 14:03:29 Family-desktop xsane: ipConvert error=20 
May 25 14:03:31 Family-desktop xsane: scan/sane/io.c 57: unable to connect hpssd socket 2207: Connection refused

I really need to have a working scanner. Any help would be appreciated.

---

### Post by mmjo on 2008-06-23
Hi,

I had a similar problem, with a hp psc 1610 all in one, and running hardy.

Resolved it by installing some packages and removing the hpoj package.

as root:
apt-get remove hpoj

and:
apt-get install libcupsys2-dev cupsys-bsd openssl libjpeg62-dev libsnmp-dev libtool libusb-dev libsane-dev sane-utils libgcrypt11-doc gnutls-bin gnutls-doc krb5-doc libtool-doc libsane-extras-dev autoconf 

This was suggested by the hp-check program (which comes with the hplip package).

Regards,
   Mike

---

### Post by Vryko Lakas on 2008-06-24
Thanks for the reply, I had almost given up hope on this. 

Hmmm. It appears hpoj is not installed. 
```
Package hpoj is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libsmokeqt1 libphysfs-1.0-0 libqt0-ruby1.8 cd-discid plib1.8.4c2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
I went ahead and installed from your list what wasn't already installed:
```
 autoconf gnutls-bin gnutls-doc krb5-doc libgcrypt11-doc libsane-extras-dev libtool-doc m4
```
After installing them, xsane still returns the same error. 



According to hp-check: 

```
Officejet_6300_series_fax
-------------------------
Type: Fax
Installed in HPLIP?: Yes, using the hpfax: CUPS backend.
Device URI: hpfax:/usb/Officejet_6300_series?serial=CN81LFB33K04J5
PPD: /etc/cups/ppd/Officejet_6300_series_fax.ppd
PPD Description: HP Fax - HPLIP 2.7.12
Printer status: printer Officejet_6300_series_fax disabled since Fri 25 Apr 2008 02:03:4Backend /usr/lib/cups/backend/hpfax does not exist!
[COLOR="Red"]**error: Incorrect PPD file for fax queue 'Officejet_6300_series_fax'. Fax queues must use 'HP-Fax-hplip.ppd'.**[/COLOR]
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/Officejet_6300_series?serial=CN81LFB33K04J5' is a Hewlett-Packard Officejet_6300_series all-in-one


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------------
| USB I/O SETUP |
-----------------


Checking for permissions of USB attached printers...
 
HP Device 0x5311 at 005:003: 
    Device URI: hp:/usb/Officejet_6300_series?serial=CN81LFB33K04J5
    Device node: /dev/bus/usb/005/003
    Mode: 0660

-----------
| SUMMARY |
-----------

**[COLOR="Red"]error: 1 error or warning.[/COLOR]**

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html


Done.

```

The only error it found appears to be tied with the fax function. I don't know if that is causing the muck-up with scanning or not. I haven't ever tried to fax with this machine. 
Should I try again with the latest automatic installer from the hp-lip site?

---

### Post by mmjo on 2008-06-24
I see a couple of avenues:

- upgrade to hardy
- upgrade hplip from the hp site
- run 'dpkg-reconfigure hplip'
- run 'dpkg-reconfigure xsane'

These are in no particular order and can be combined.

Good luck,
    Mike

---

### Post by Vryko Lakas on 2008-06-24
Well, I have tried dkpg-reconfigure for both hplip and xsane. I installed the latest HPLIP drivers using the automatic installer from the site. In the process, I had to disconnect/reconnect the USB from the computer to the printer. 

When all was said and done, I still got the same error. The message on the printer's LCD console tells me the scan was canceled, and I don't know how to clear it. For some reason the scanner seems to get hung up after attempting to scan, even though printing continues to work fine.


I tried to power down the printer and turn it back on, hoping it would release whatever it's getting stuck with. As before, a new scan attempt went through the motions of scanning (i.e. things made noise and moved), but I wind up with the error (this time "Error during read: Error during device I/O).

I ran hp-check again, and this time got two errors: 
```
Officejet_6300_series_fax
-------------------------
Type: Fax
Installed in HPLIP?: Yes, using the hpfax: CUPS backend.
Device URI: hpfax:/usb/Officejet_6300_series?serial=CN81LFB33K04J5
PPD: /etc/cups/ppd/Officejet_6300_series_fax.ppd
PPD Description: HP Fax - HPLIP 2.7.12
Printer Backend /usr/lib/cups/backend/hpfax does not exist!since Fri 25 Apr 2008 02:03:49 AM EDT -
error: Incorrect PPD file for fax queue 'Officejet_6300_series_fax'. Fax queues must use 'HP-Fax-hplip.ppd'.
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/Officejet_6300_series?serial=CN81LFB33K04J5' is a Hewlett-Packard Officejet_6300_series all-in-one


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
[B][COLOR="Red"]error: NOT FOUND OR FAILED TO LOAD! Please reinstall HPLIP and check for the proper installation of scanext.
[/COLOR][/B]
-----------------
| USB I/O SETUP |
-----------------


Checking for permissions of USB attached printers...
 
HP Device 0x5311 at 005:006: 
    Device URI: hp:/usb/Officejet_6300_series?serial=CN81LFB33K04J5
    Device node: /dev/bus/usb/005/006
    Mode: 0666

-----------
| SUMMARY |
-----------
[B]
[COLOR="Red"]error: 2 errors and/or warnings.[/COLOR][/B]

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html

```

---

### Post by mmjo on 2008-06-25
Did you look at:
[http://hplip.sourceforge.net/troubleshooting/index.html](http://hplip.sourceforge.net/troubleshooting/index.html)

Maybe running kooka (KDE variant of scanner software) helps?

Or change the distribution - upgrade to ubuntu 8.04 or try fedora 9.

Good luck.

---

### Post by Vryko Lakas on 2008-06-25
I really am appreciating all the help. 
Yes, I've already checked the hplip FAQs, but there didn't seem to be an issue related to my problem. 
Kooka at least gives me an error message that might point me in the right direction. 
```
**Problem: No Scanner was found**
Your system does not provide a SANE (Scanner Access Now Easy) installation, which is required by the KDE scan support. 
Please install and configure SANE correctly on your system. 
```
So maybe using Kooka under GNOME is not going to work, or maybe the problem is SANE itself. For some reason, the Python SANE extension wasn't installed when I tried to upgrade to the latest hplip, or I wouldn't have gotten that error message, right? 
I'll pop in the Hardy LiveCD and see if that's configured in a way that my scanner can work. But I'd really hate to upgrade right now, over a scanner that SHOULD work with Gutsy.

---

### Post by mmjo on 2008-06-25
Yes, its annoying to have to upgrade for some hardware.

Anyway, you could file a bug at:
[http://hplip.sourceforge.net/mailing_lists.html](http://hplip.sourceforge.net/mailing_lists.html)

Regards,
    Mike.

---

