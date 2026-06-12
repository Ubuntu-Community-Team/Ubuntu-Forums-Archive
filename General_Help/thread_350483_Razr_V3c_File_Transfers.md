---
title: "Razr V3c File Transfers?"
date: 2007-01-31
forum: General Help
---

### Post by computergee on 2007-01-31
I have a Motorola Razr V3c, and I can't figure out how to transfer photos, music, ringtones etc.  It is a the verizon version, but I did a seem edit, and file transfers should be unlocked. Bitpim gives me a "phone is not responding" message. Anyone know how to get this phone to work?

---

### Post by ewankho on 2007-01-31
[Moto4lin]("http://moto4lin.sourceforge.net/wiki/Main_Page")

---

### Post by computergee on 2007-01-31
That dosn't work for me either. I get: 

[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name

---

### Post by ewankho on 2007-01-31
Did you see something like "Phone plugged in"? Did you connect?

---

### Post by computergee on 2007-02-01
yeah, it sees the phone as connected, but it can't do anything with it. i'm getting the same error as on here.

[http://moto4lin.sourceforge.net/wiki/Razr_V3c](http://moto4lin.sourceforge.net/wiki/Razr_V3c)

---

### Post by dabl on 2007-02-01
I spent more hours than I care to recall a few weeks back trying to get my Razr to talk to my Kubuntu Edgy system.  Eventually I got it to connect in "P2K" mode, so that it would recognize the manufacturer and model.  But I never got to where it could download anything, or even see the files.  As far as I know, it hasn't been done -- if you find a way, I'd love to see it posted.

---

### Post by beerorkid on 2007-02-01
I tried everything with the last few releases, nothing worked.

Got me a cheapo bluetooth adapter
[http://www.newegg.com/Product/Product.asp?Item=N82E16833147117](http://www.newegg.com/Product/Product.asp?Item=N82E16833147117)

went to synaptic installed bluetooth and kdebluetooth started kdebluetooth enabled bluetooth on my razr  V3c and bam I was transferin both ways.

almost too simple for $13

---

### Post by computergee on 2007-02-01
Ha, maybe I'll go out and get a bluetooth adaptor than, I'm sure it will come in hand for other things too.  I have it so I can see the file system in bitmip, but I can't transfer. Ill keep at it until I get the bluetooth adaptor.

---

### Post by colek on 2007-02-18
I figured out how to transfer files from the RAZR V3 today. The solution I found today is not elegant, but it is functional and easy to install.

First of all you need to install Gnome-bluetooth from Synaptic (make sure all your repositories are enabled) 

Read Randy Sparks post here:
[http://ubuntuforums.org/showthread.php?t=94713&highlight=bluez](http://ubuntuforums.org/showthread.php?t=94713&highlight=bluez)

Then to transfer files, read page 23-25 of the RAZR V3 user manual which tells you how to connect your RAZR to your PC and COPY files (pictures, videos, etc) to your PC via Bluetooth. It saves them in your home/<username> folder. 

The RAZR motorola manual is here:
[http://www.motorola.com/consumer/v/index.jsp?vgnextoid=706eab651780b010VgnVCM1000008206b00aRCRD&show=productHome](http://www.motorola.com/consumer/v/index.jsp?vgnextoid=706eab651780b010VgnVCM1000008206b00aRCRD&show=productHome)

Click on the User Manual link on the left.

---

