---
title: "Epson scanner kippered by upgrade to 20.04"
date: 2021-05-09
forum: General Help
---

### Post by Timothy Taylor on 2021-05-09
I have recently upgraded from Ubuntu 18.04 to 20.04.

My ET-2650 was working perfectly over USB in 18.04, with the [epson-inkjet-printer-escpr_1.6.33-1lsb3.2_amd64] and [imagescan-bundle-ubuntu-18.04-1.3.38.x64.deb] packages installed.
Since upgrading to 20.04 and installing the new *Epson Scan 2* software, I get "unable to communicate with scanner. make sure it is connected and turned on" errors. This is odd, because I can print OK and the ET-2650 is listed in the "select a device" dialog.  The new *Document Scanner* app behaves similarly - it correctly ID's the ET-2650 but throws an "unable to connect to scanner" error when I try to scan.

Luckily, I put 20.04 on a new HDD.  The scanner still works fine with *Simple Scan* if I boot from my old 18.04 disk.

How can this happen with a later release??  What happened to *Simple Scan* ?
If it's not broken, don't fix it!

---

### Post by blackbird34 on 2021-05-10
Have you tried other scanning apps for linux? Skanlite and gscantopdf are both free software and might help. 

See [https://alternativeto.net/software/simple-scan/?license=opensource&platform=linux](https://alternativeto.net/software/simple-scan/?license=opensource&platform=linux)

---

### Post by Timothy Taylor on 2021-05-11
> **blackbird34 said:**
> Have you tried other scanning apps for linux? 

Yes, I tried *Skanlite* and *Xsane*, but they gave similar communication errors.  I saw a comment on another forum which said that *VueScan* worked when all else did not, so I tried that.  And BINGO!  The free version only saves to pdf with a watermark though.  Out of curiosity I tried Document Scanner again - that also worked!  As did *Epson Scan 2* and all the others.

It would seem that the *VueScan* install sets something to do with (USB?) comms that the other installers don't?

Anyway, the wretched thing works now and I can stop wasting my time struggling with stupid stuff that should just work - and stay working between upgrades!
I was reluctant to upgrade because I've had these sort of issues before...

---

