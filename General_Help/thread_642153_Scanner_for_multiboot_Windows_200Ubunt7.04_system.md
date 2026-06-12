---
title: "Scanner for multiboot Windows 200/Ubunt7.04 system"
date: 2007-12-16
forum: General Help
---

### Post by Howard Kaikow on 2007-12-16
I have a multiboot Windows 2000/Ubuntu 7.04 system.

Scanner is an Epson 1240U, used only in Windows, never tried the critter in  Ubuntu.
I am sticking with 7.04 until at least sometime next year.

I likely need to replace the Epson 1240U.
Which scanners are supported by Ubuntu 7.04?
I have only begun to look, but none of the scanners I have looked at on theCanon web site list Linux as a supported OS.

---

### Post by linuxwizard on 2007-12-16
Look through this list shows supported and non supported scanners for linux

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

---

### Post by Howard Kaikow on 2007-12-16
> **linuxwizard said:**
> Look through this list shows supported and non supported scanners for linux

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

Thanx.

That document states that my scanner, the Epson Perfection 1240U, is COMPLETEly supported by SANE.

Sew, I booted to Ubuntu and scanned. I changed no settings.

Ugh! ... Ugh!

The first two sheets I scanned were awful, nothing was readable.

The 3rd sheet I scanned was the first page of my condo association's newsletter, Green paper with black text.

The Green was not picked up. Is there a setting I need to choose to get colors?

The margins seemed to be cut down.

I saved the image and opened the image with the image viewer. Crapped out trying to print to the printer, Was able to print to PDF.

Results very unsatisfactory.

So, I do not have much faith in the SANE list stating that something is COMPLETE;y supported.

I'll try to call Canon and Epson on the 'morrow to get their recommendations for Ubuntu.

---

### Post by linuxwizard on 2007-12-16
Look over this. It is the manpage from Sane for your scanner.

[http://www.sane-project.org/man/sane-epson.5.html](http://www.sane-project.org/man/sane-epson.5.html)

---

### Post by Howard Kaikow on 2007-12-16
Thanx.

Looks like I need to run xsane or xscanimage.
I'll see if they are installed.

---

### Post by Howard Kaikow on 2007-12-16
Yes, xsane worked better.
But it is chopping the margins entirely in at least one document.

---

### Post by Howard Kaikow on 2007-12-17
Apparently, only Epson and HP have significant numbers of scanners listed as having "Complete" support.
Canon has a few, but I was told that tey are no longer manufactured.

Which scanners offering "Complete" support are recommended?

---

### Post by Howard Kaikow on 2007-12-17
I ordered the Epson V200.
I'll let y'all know if it works in Ubuntu.

---

### Post by Howard Kaikow on 2007-12-20
You folkes are going to have fun with this  one.

I decided to replace the Epson Perfection 1240U because there were two problems:

1. Near the end of the scan of a page, there was a physical problem that caused loud noises at the end of the page traversal.

2. Streaks were getting added to most pages.

Well, my new scanner, the Epson Perfection V200 is due to be delivered today (as we speak, it's on a UPS truck).

So I figured that I'd power down the computer and reposition things as the new scanner has to be turmed 90 degrees from the position of the old scanner.

Gues what!
The problems on the old scanner have disappeared!!!!

The first problem was mechanical, so moving the scanner might have jiggled something.

But, it seems more likely that the problems were fixed by reseating the USB and power cords. I had checked the cords, but I may have not checked properly.

Oh well, I'll now have two scanners, but not enough USB connectors to keep them both connected at same time.

I'll disconnect one of my USB drives to see whether the scanners can co-exist in Windows.

I'll hook up just the V 200 to see whether it works in Ubuntu 7.04.

---

### Post by Howard Kaikow on 2007-12-20
> **Howard Kaikow said:**
> I ordered the Epson V200.
I'll let y'all know if it works in Ubuntu.

Does not work in Ubuntu 7.04, device is not found

---

### Post by linuxwizard on 2007-12-20
Where did you find that Epson V200 was supported in linux ? Or was you just hoping that it would work in linux.

---

### Post by Howard Kaikow on 2007-12-21
Somebody sent me the following:

> Read the note in the V200 entry on the SANE page. You'll probably have to install the no-cost but proprietary Epkowa driver before Ubuntu will recongise the scanner.  SuSE and Red Hat (Enterprise) do this for you but Ubuntu and Fedora do not. 

Installing the driver is not hard, but gets a little involved.

But I have not found such an entry.

I bought the critter, on the hope that support would be added, as Epspm scanners seem to be bettr supported.

My older scanner seems to have fixed itself, so the 1240U  now runs.

By the time I use Ubuntu often, I would expech such problems to b eresolved.

---

### Post by linuxwizard on 2007-12-21
I can't find any listings or anything on the V200 on Sane also. Not sure if you looked here but you can get a driver for it. Not sure if it will work or not.
[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)
If you look around you might find some docs on installing it.

Look down this page for scanner section.
[http://avasys.jp/hp/menu000000500/hpg000000443.htm](http://avasys.jp/hp/menu000000500/hpg000000443.htm)
The one link there shows that driver was tested on & supported for Suse,Redhat,Fedora.

My understanding if you have a scanner or going to buy one use Sane listing of supported devices to see if it is supported or not and if it is going to work. Glad to hear you got your old scanner working. Good Luck

---

### Post by Howard Kaikow on 2007-12-21
> **linuxwizard said:**
> I can't find any listings or anything on the V200 on Sane also. Not sure if you looked here but you can get a driver for it. Not sure if it will work or not.
[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)
If you look around you might find some docs on installing it.

Look down this page for scanner section.
[http://avasys.jp/hp/menu000000500/hpg000000443.htm](http://avasys.jp/hp/menu000000500/hpg000000443.htm)
The one link there shows that driver was tested on & supported for Suse,Redhat,Fedora.

My understanding if you have a scanner or going to buy one use Sane listing of supported devices to see if it is supported or not and if it is going to work. Glad to hear you got your old scanner working. Good Luck

Epson told me that Linux is not supported.
Of course, the persom to whom I spoke had never heard of Linux.

You can find the reference to V200 by using [http://www.sane-project.org/cgi-bin/driver.pl?manu=Epson+&model=&bus=any](http://www.sane-project.org/cgi-bin/driver.pl?manu=Epson+&model=&bus=any).

I'm not a regular Linux user now, that's at least a year or two away.

If Linux is to succeeed, better scanner support, among other things, has to be added.

---

### Post by old_salt on 2008-01-05
USB Scanners are USB Scanners. They all have to comply with IEEE standards.Control signals are all the same and yes; features are different however;  Why cant the coders spend a few extra minutes to at least provide basic connect ability and functionality. It's because they all have their own agenda and are lazy. 

Most of these scanners are nothing more than updated versions of prior releases repackaged in a new container so marketing can make money for the company. Linux really needs to step back and re-assess the situation and proceed from there. Also, when providing code they also need to equally provide for 64 bit systems as well. Even Microcrap has announced discontinued dates for the 32bit OS. Linux has been the leader in 64 bit yet fails to provide a complete package. 

This is frustrating!!!!!

---

### Post by Howard Kaikow on 2008-01-06
> **old_salt said:**
> USB Scanners are USB Scanners. They all have to comply with IEEE standards.Control signals are all the same and yes; features are different however;  Why cant the coders spend a few extra minutes to at least provide basic connect ability and functionality. It's because they all have their own agenda and are lazy. 

Most of these scanners are nothing more than updated versions of prior releases repackaged in a new container so marketing can make money for the company. Linux really needs to step back and re-assess the situation and proceed from there. Also, when providing code they also need to equally provide for 64 bit systems as well. Even Microcrap has announced discontinued dates for the 32bit OS. Linux has been the leader in 64 bit yet fails to provide a complete package. 

This is frustrating!!!!!

USB is not the issue.
Support for different scanner chip sets and, perhaps, protocols is the problem.

---

