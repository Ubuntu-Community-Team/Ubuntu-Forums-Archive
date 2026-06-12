---
title: "HP Laserjet P1005"
date: 2007-12-18
forum: General Help
---

### Post by acdc1982 on 2007-12-18
HI, 

  I have an HP Laserjet P1005 attached by usb to a machine running Ubuntu 7.10. The printer is recognized and ubuntu installs a driver for it, I think it installs a 2000 series driver for it. I can't get it to print a test page with any of the drivers that I try for it. Has anyone had any success with this printer?

---

### Post by stchman on 2007-12-18
> **acdc1982 said:**
> HI, 

  I have an HP Laserjet P1005 attached by usb to a machine running Ubuntu 7.10. The printer is recognized and ubuntu installs a driver for it, I think it installs a 2000 series driver for it. I can't get it to print a test page with any of the drivers that I try for it. Has anyone had any success with this printer?

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1005](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1005)

The laserjet 1005 uses the Zenographics print engine.  You need to update the foo2zjs driver.  Luckily I have a tutorial for this with a script for Gutsy.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Be sure to select the script for Gutsy and your printer model.  I have my Laserjet 1000 working perfectly under Feisty.

---

### Post by acdc1982 on 2007-12-18
Thanks for the reply and the help. I ran the script but I still can't get the printer to print. I've restarted ubuntu a few times and the printer. I've also re-ran the script but I'm not sure what I'm doing wrong here.

---

### Post by stchman on 2007-12-19
> **acdc1982 said:**
> Thanks for the reply and the help. I ran the script but I still can't get the printer to print. I've restarted ubuntu a few times and the printer. I've also re-ran the script but I'm not sure what I'm doing wrong here.

I have found the problem.  There is a difference between the Laserjet 1005 and the Laserjet P1005.  They are two different printers.

I am going to update the script and attach it to this post.  I wish HP would have not done the "P" in front for new printers.

Use the uninstall portion first then install the driver.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

When you run the script use P1005 as the foo2zjs identifier.  Remember Linux is case sensitive.

Wait until this evening as I need to update the foo2zjs drivers that the script calls.

---

### Post by acdc1982 on 2007-12-21
Ok it worked this time, thanks a lot, I have been trying everything to get that printer to work.

---

### Post by stchman on 2007-12-21
> **acdc1982 said:**
> Ok it worked this time, thanks a lot, I have been trying everything to get that printer to work.

No problem.  I just don't like how HP added the P in front and it is a new printer.

Glad to be of help.

---

### Post by cdrappier on 2008-01-11
I have an HP laserjet printer as well, and I have read this thread and followed the directions.  I downloaded the script and ran it with the option P1005 and it seemed to install everything fine. however, when i try to print something, the document remains in 'pending' status. and if i try to cancel the job, i get this message: "There was an error during the CUPS operation: 'client-error-not-possible'." any further help w/ this situation would be appreciated.

---

### Post by stchman on 2008-01-15
> **cdrappier said:**
> I have an HP laserjet printer as well, and I have read this thread and followed the directions.  I downloaded the script and ran it with the option P1005 and it seemed to install everything fine. however, when i try to print something, the document remains in 'pending' status. and if i try to cancel the job, i get this message: "There was an error during the CUPS operation: 'client-error-not-possible'." any further help w/ this situation would be appreciated.

Did you download the proper script?  It says in your profile that you are using Feisty.  Gutsy uses a different printer manager than Feisty and earlier.  Refer to my foo2zjs page.  Gutsy uses a different script than Feisty or earlier.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

If you downloaded and ran the improper script then do the removal portion first.

---

### Post by cdrappier on 2008-01-17
yes, i was using the proper script. I am on gutsy now, just forgot to change that in my profile, I ran the uninstall and install a couple of times to the same effect.  I am sure that I've done everything your page said to do, yet the printer still does not work. :(

---

### Post by ale3andro on 2008-02-13
It worked for me. I run Ubuntu Gutsy and now I can print on a shared HP LaserJet P1005 on an WinXP machine. I just made a small change in the printer URI.
Thankz for the great tutorial / script.

---

### Post by ChrisQ on 2008-02-29
it's odd that this works because that printer doesn't use the foo2zjs driver, it uses the foo2xqx driver. I'm having the same problem on hardy though. print jobs disapear into the ether...

---

### Post by ChrisQ on 2008-03-02
just a heads up, installing the driver from the official driver website and rebooting fixed this for me. I think the hardy drivers are missing the printer firmware.

---

### Post by vetch101 on 2008-05-05
Hi,

I have the same problem with Hardy and my P1005 - how did you resolve it?

Cheers,

Jx

---

### Post by alexef on 2008-05-13
> **vetch101 said:**
> Hi,

I have the same problem with Hardy and my P1005 - how did you resolve it?

Cheers,

Jx

I have a HP P1005 and to get it working on Hardy I had to download and install the latest official HP driver (HPLIP) from: [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html) . 

It's working like a charm, the only thing I don't like is the HP icon in system tray, but I'll get rid of it soon.

Good luck!

---

