---
title: "Doesn't recognize my new Kindle HD"
date: 2012-12-28
forum: General Help
---

### Post by lynyl on 2012-12-28
I have Ubuntu 12.04 on System 76 64-bit computer. I just got a Kindle HD and wanted to transfer pix to it. BUT when I connect via USB my computer doesn't see it plus I get the message on the Kindle that I need to have a free file transfer utility. I go to the directed web page and - while transfer file utilities are there for download for the PC and MAC - for the LINUX it just says: "Linux users with either a Kindle Fire 2nd Generation or Kindle Fire HD will need to install a Media Transfer Protocol (MTP) USB driver to complete USB transfers."  GRRRRRR.  So I looked for an MTP in the Software Center and found Qlix but it didn't seem to download plus another reviewer said it did't work on the KF anyway!  Can anybody help me?  Thanks in advance!

---

### Post by Mopar1973Man on 2012-12-28
Just doing a search in Synaptic Package Manager there is a Media Transfer Protocol listed.

```
sudo apt-get install libmtp9
```

Or fire up synaptic and search for "Media Transfer Protocol" there...

---

### Post by 2F4U on 2012-12-28
I've found two posts which sound promising:

[http://askubuntu.com/questions/177555/managing-kindle-fire-with-on-12-04-via-micro-usb](http://askubuntu.com/questions/177555/managing-kindle-fire-with-on-12-04-via-micro-usb)
[http://maketecheasier.com/manage-files-on-your-kindle-fire-hd-with-ubuntu/2012/11/07](http://maketecheasier.com/manage-files-on-your-kindle-fire-hd-with-ubuntu/2012/11/07)

---

### Post by houseworkshy on 2012-12-29
I've tried the advice in both the mentioned posts and in both cases files can't be found or dependancies are unresolved.  That said I'm trying to do this in !0.04.  
Has anyone been able to browse and trancefer files in Kindlfire HD from Ubuntu via the usb cable or visa versa.  At the moment I can send things via blue tooth but that's all and it's very slow.

---

### Post by lynyl on 2012-12-29
:):):)

Thanks to you all I now can transfer my files! This link:
[http://maketecheasier.com/manage-files-on-your-kindle-fire-hd-with-ubuntu/2012/11/07](http://maketecheasier.com/manage-files-on-your-kindle-fire-hd-with-ubuntu/2012/11/07)  did the trick!  Thanks 2F4U!

---

### Post by houseworkshy on 2013-01-03
I'm glad that you've sorted it out, unfortunately for me the link in the above post leads me to an
[B]"Error establishing a database connection".[SIZE=1]
[/SIZE][/B][SIZE=2]If the same info exists elsewhere I'd be grateful if someone would point me at it or , if copywright allows, maybe paste it here.[/SIZE][B][SIZE=1]
[/SIZE][/B]

---

### Post by cwsnyder on 2013-01-03
[Try this link:]("http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access")

---

### Post by houseworkshy on 2013-01-03
Thanks for the reply and link.  I've tried to follow the guide, I'd already put in all the mtp stuff I found in the repositories but did it again just in case I'd missed something.  At the point where it suggests *mtp-detect | grep idVendor *[FONT=Arial]I got stuck as mtp-detect didn't find anything.  The Kindlefire HD doesn't give any options on usb types either.      [/FONT]I put in the man pages for mpt too so had a bit of a read in those and tried the mount option but it doesn't seem to be that either.  
The only aknowlagement of any connection between the devices, bar when I use the bluetooth, is a "usb cable connected"  plus "connected to low Power charger" which shows in the kindlefire.  I had a peek into Ubuntus' disk utility and the kindlefire doesn't show up their either.  I've also put in Qlix which gives "no devices found"

---

### Post by HermanAB on 2013-01-03
Howdy, 

I installed the ES file manager and transfer files over wifi using ssh. Note that you first have to disable the spelling correction/screw-up misfeature else you cannot type hostnames and passwords!

Sent from my Kindle HD using the Opera mobile browser.

---

### Post by houseworkshy on 2013-01-03
Thanks for that.  I actually try to avoid wi fi as I live in wi fi range of dozens of households though I suppose it is about time I got my head round securing it instead of simply turning it off in the router and relying on the wire.  
I've posted a new thread here [http://ubuntuforums.org/showthread.php?p=12435800#post12435800](http://ubuntuforums.org/showthread.php?p=12435800#post12435800) as this one has been marked solved, rightly,  because the above fixes seem to work for 12.04 even if not for 10.04.

---

