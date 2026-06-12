---
title: "Problem with XSane + HP printer..."
date: 2007-03-02
forum: General Help
---

### Post by Quibly on 2007-03-02
Ok, I have Ubuntu 6.06 LTS. I have the HP PSC 1315 all-in-one printer. I just installed my HP printer and its working all right. When I go to System->Admin.->Printing I see my printer on the list (although it says that my printer is PSC 1310 instead of 1315). When I go to Applications->Accessories-> HP device manager it also recognizes my printer. In the functions, when I click on scan, XSane opens up and says the following:

```
scanning for devices...
``` 

and then:

```
Failed to open device 'hpaio:/usb/psc_1310_series_?serial=************':
Error during device 1/0. 
```

if I open the XSane program again after a couple of seconds it says:

```
no devices available
```


This scanning works if I connect the printer to my Windows machine. 


What do I do?


Thanks!!

---

### Post by maxvonseibold on 2007-03-20
Hello - did you ever solve this? 

I am having similar troubles ...

---

### Post by 11hjpphty76lkjj on 2007-03-23
Can you please run

```
hp-check
```

and post the output?

---

### Post by fragos on 2007-03-23
My HP PSC 1410's scanner has come down with the same problem.  It worked before.  I'm running Ubuntu 6.10 and can't find hp-check anwhere to run or install.  What package is it a part of?

---

### Post by 11hjpphty76lkjj on 2007-03-23
If you do not have hp-check you'll want to install the latest version of HPLIP from;

[http://hplip.sf.net](http://hplip.sf.net)

---

### Post by Quibly on 2007-03-27
> **maxvonseibold said:**
> Hello - did you ever solve this? 

I am having similar troubles ...


The problem was solved when I completely re-installed ubuntu 6.10. This time I got the printer working by going to System --> Printing --> New Printer

This installed the printer and the scanner, which both work now.

---

### Post by fragos on 2007-03-27
> **fragos said:**
> My HP PSC 1410's scanner has come down with the same problem.  It worked before.  I'm running Ubuntu 6.10 and can't find hp-check anwhere to run or install.  What package is it a part of?

I did a clean install of Feisty Beta and both the printer and scanner are working again.  Still no "hp-check" but I'll wait until the release before installing outside of the Ubuntu repositories.

---

### Post by Quibly on 2007-03-29
I dont have hp-check either. I dont think that its that important. If I were you I wouldnt install anything that has to do with the printer from a source outside of the repositories. I think that that is what caused the problem.

---

### Post by 11hjpphty76lkjj on 2007-03-29
hp-check is installed with the latest version of HPLIP. The problem with the repos is that it is sometimes behind the latest version of HPLIP.  We work closely with the ubuntu team as well.  So if the repo doesn't work for you installing from source really isn't a big deal.  I test the install extensively on ubuntu as it's my fav distro. :)

If you are having problems, and do not having hp-check then you are using an old version of hplip, probably 0.9.7.  We are hoping that Feisty will include the latest 1.7.3 but we'll see.

Please upgrade from the hplip website, [http://hplip.sf.net](http://hplip.sf.net).

hp-check GREATLY helps troubleshoot possible problems on the system and will really help narrow down what your problem/s are.  As such it will also help save you time..

Hope this helps.

Edit: My comments are mostly directed at Quibly, not fragos. ;)

---

### Post by wgbuntu on 2007-05-15
I have this same problem.  HP Deskjet 3320 printer works fine in Windows XP but doesn't print in Feisty with HPLIP 1.7.4a (or 1.7.3).  HP-Check says all is "OK" but there is a message that "Open Device Failed, will retry in 30 seconds".  Everything else looks good, printer is detected at all points, just doesn't produce.

---

### Post by 11hjpphty76lkjj on 2007-05-15
The DJ3320 should be working..

Try disconnecting the printer, then run:

sudo /etc/init.d/hplip restart
sudo /etc/init.d/cupsys restart

then delete the printer from hp-toolbox.  Then reconnect the printer and run:

sudo hp-setup

What happens?

A

---

### Post by cssutto on 2007-06-29
I followed all instructions.

Hung at "be sure printer is connected and powerd up".

Left me with over 300 files on my desktop.

How do I get rid of them?

I cured the problem in another manner.

CSSJR

---

### Post by 11hjpphty76lkjj on 2007-06-29
Sorry I'm not exactly sure what you are talking about.  What left you with 300 files on your desktop?  By making sure your printer was powered on and connected?  There aren't even 300 files in the root of the hplip tar file...so...I dunno what you mean?

You could in theory delete them by running:

sudo rm -rf * in your ~/Desktop directory.  But this will delete everything you know--so if there are any other files you had before they'd be lost.  of course you may just want to do the old fashion highlight and press the delete button--then you know what you are deleting and wont remove something you wanted to keep.  I'd say just go with that route.  Might take a good 5 min to del them all. But you'll burn through 300 files pretty quick.

gl,
A

---

### Post by cssutto on 2007-09-27
I had the problem fixed for a while and then suddenly xsane can not find the scanner.

When I run HP-check, I get:

HP Linux Imaging and Printing System (ver. 0.9.7)
Dependency/Version Check Utility ver. 8.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Initializing. Please wait...
Traceback (most recent call last):
  File "/usr/bin/hp-check", line 186, in ?
    core.init()
  File "/usr/share/hplip/installer/core.py", line 302, in init
    version_description, version_public, version_internal = getHPLIPVersion()
  File "/usr/share/hplip/installer/core.py", line 132, in getHPLIPVersion
    version_description, version_public, version_internal = \
KeyError: 'internal-tag'


What next?

CSSJR

---

