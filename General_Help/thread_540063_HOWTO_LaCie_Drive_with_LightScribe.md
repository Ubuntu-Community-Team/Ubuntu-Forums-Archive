---
title: "HOWTO: LaCie Drive with LightScribe"
date: 2007-09-01
forum: General Help
---

### Post by SuperMike on 2007-09-01
I purchased a LaCie CD/DVD Burner Drive with LightScribe, got it working 100% with Feisty Fawn, and wanted to give you some advice. The product info for mine was:

18X LIGHTSCRIBE DL LaCie P5 DVD+/-RW/RAM USB2 USA
301197U

First, I found that the drive works right off the bat just by plugging in the USB cable. Impressive! Next, I needed to get the Lightscribe working.

I had heard there were some dependency problems, so I did:

```
sudo su
apt-get install rpm
apt-get install alien
apt-get install libpng3
apt-get install libqt3-mt
exit
```

I don't know if they're needed, but what the heck. It was posted on this site here, so I figured it must be necessary.

Next, I went to **[lightscribe.com]("http://lightscribe.com/")** to get my Debian drivers. As I don't know if I can trust the links from changing, I went there and clicked Downloads, Linux, Lightscribe System Software, I Agree, then, when there, look for a link that reads "Please see our Pre Release Software Downloads page for a version for Debian-based distributions (such as Ubuntu)." and click that.

Scroll down and you'll see the two things you'll need first:

LightScribe System Software (LSS) Debian Install Package (0.5 MB)

& 

Simple Labeler Debian Install Package (6.7 MB)

Once you download these, install them at command line with...

```
sudo su
dpkg -i *<package>*
exit
```

...and do the LSS install first.

Now this puts the Simple Labeler software in /opt/lightscribeApplications/SimpleLabeler and you can fire it up with a menu shortcut that reads:

```
/usr/bin/gksudo  /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler
```

Yeah, you'll need to be root for SimpleLabeler to have the power to burn an image to the CDR/DVDR (or CDRW, DVDRW, etc.), which is why I used gksudo.

Now, this SimpleLabeler is for small stuff. If you want something more elaborate, go to Lacie's Linux page and install 4L. To find it, just go to **[Google]("http://www.google.com/search?hl=en&q=linux+site%3Alacie.com&btnG=Google+Search")** and do "linux site:lacie.com" and click the first LaCie link you see. (This is because the link may change.) It takes you to a page that reads "4L: LaCie LightScribe Labeler for Linux". On that page, click the link that reads "LaCie LightScribe Labeler for Linux" and ignore the one that says "Host Software". This is because you already have the latest host software recommended for Debian (Ubuntu in this case) already installed. Note that you must install this as root at command line and use...

```
sudo su
alien -i --scripts 4L*.rpm
exit

```
...to get it installed properly.

Once installed, you should now create another menu item that points to:

```
/usr/bin/gksudo /usr/bin/4L-gui
```

Now select that in the menus and it is sort of self-explanatory in the GUI when you hold a cursor over the buttons. You load an image, drag it around, resize it (using the slider bar on the form), then click the Print button.

Now here's something that might trip you up. I found it was telling me I had a dirty disc. This was just my stupidity -- I had the wrong side of the disc in. I flipped the disc and tried again, and it worked just fine.

Note it takes about 10-20 minutes per disc to burn an image with high resolution, and especially one with a lot of darker shaded areas.

So that's it.

P.S. I'm trying to start a software company with a CRM/helpdesk web app, and I'm a startup in bootstrap mode, so I needed the cheapest, yet most elegant way, to lower my operating costs. That's why I chose the Lightscribe technique in order to burn CDRs.

P.S.S. Note that Lightscribe CDRs come in multiple colors. So you don't have to go with gold if you don't want that.

---

### Post by esaym on 2008-01-05
Does the linux version of the software allow you to scribe pictures or only text?

---

### Post by SuperMike on 2008-01-06
both

---

### Post by esaym on 2008-02-11
Why does 4L-gui have to run as root?  Sorta strange.  Anyway around it I wonder?

---

