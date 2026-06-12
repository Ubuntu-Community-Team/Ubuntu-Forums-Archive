---
title: "[SOLVED] Another  Gutsy HP Printer Problem"
date: 2007-10-20
forum: General Help
---

### Post by drs305 on 2007-10-20
SOLVED OR NOT SOLVED (latest):  It worked for a while, then stopped, but now my HP is working again. At the times it doesn't work the usb printer is still recognized but doesn't print. At the moment, it's working again. Whether it is working or not, I do not have gnome-cups-manager installed and I didn't have to go through all the steps needed in past versions to get HP printers to work. No clue, but the printer has been working consistently for a week now...


---
ORIGINAL POST:

I have an HP Laserjet 1000 and still can't get it to work, even through gnome-cups-manager. Using Gutsy, worked fine in Feisty, etc.  I originally posted this under another thread by FuturePilot but that thread has been marked as SOLVED.

In that thread, FuturePilot couldn't get gutsy to print from an HP printer even though it was recognized. He installed gnome-cups-manager and the printer began working. 

1. With gnome-cups-manager, do I have to fill in a code in location or is this just a generic name that I choose. the location entry is blank. When I try to print from the installed printer (even in gnome-cups-manager) nothing prints even though Gutsy knows the printer exists. In the error log, I still get the "No %%BoundingBox:" message. If there is a location code required, how do I find it?

This is the complete error log. The first message is generated when I click on the printer's properties. The second when I try to print a test page.
#
E [20/Oct/2007:14:21:26 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [20/Oct/2007:14:21:47 +0000] [Job 1] No %%BoundingBox: comment in header!
#

2. If others have gotten HP printers to automatically work in Gutsy, I'd like to know that also. I installed Gutsy via a daily build just prior to the official release, so if I have to reinstall with the official live cd I can do that IF I know that HP printers will automatically be recognized and work...

PS. I have looked at other links, but many are from versions prior to gutsy. Since gutsy was supposed to have a new printer recognition methodology, I'd like solutions particular to gutsy.

Thanks

---

### Post by RH9R on 2007-10-21
'Sounds familiar: I loved feisty so much i bought a printer to live w/ it - HP1020. Here I learned how the dark side has done w/ printer & other peripheral drivers - what they did w/ modems - load firmware at startup. 
I tried Gutsy from the live CD & have the same experience - it recognizes the printer just fine - all looks well, but no test print. I'm gonna stay w/ feisty until this gets fixed.

---

### Post by annikos on 2007-10-23
Look here: [http://ubuntuforums.org/showthread.php?t=200179](http://ubuntuforums.org/showthread.php?t=200179)


I have also a HP Laserjet 1000 and this worked for me.

---

### Post by drs305 on 2007-10-28
> **annikos said:**
> Look here: [http://ubuntuforums.org/showthread.php?t=200179](http://ubuntuforums.org/showthread.php?t=200179)


I used the same link but did things a little differently, never installing the printer using CUPS. I got the drivers from the referenced site but eventually installed the printer with the new interface and not using the gnome-cups-manager. I think the secret is not the cups system but getting HP drivers that work.

With all credit and thanks to the guys that did the work with f002zjs, here's what I did.

```

sudo apt-get install build-essential
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
tar zxf foo2zjs.tar.gz

```
Change into the directory just created (foo2zjs) The next step is what I used but make sure you are inside the foo2zjs folder after running the following command.
```

cd foo2zjs

```
In the next step, substitute your HP printer model for the "1000", e.g. if you have an HP 1020, you would use ./getweb 1020
```

make 
./getweb 1000
sudo make install
sudo make install-hotplug
sudo make cups

```

Here is where I varied from the linked thread. I did not change the hotplug file nor invoke the gnome-cups-manager. I went to System, Admininstration, Printing and installed the printer via the new gutsy interface. I selected New Printer, it detected my usb printer and that is what I selected. I forwarded through the selections using the highlighted selections. On the last page, instead of the one foo2zjs driver (recommended) that had always been listed, there were now 3. I decided to try the highlighted one which had not worked previously and the printer started working almost immediately after running the print test. I didn't use either of the 2 new drivers now available but assume that the recommended one had been altered in some way.

If this doesn't work for your HP printer, you may want to try following the instructions on the referenced link all the way through, including using the gnome-cups-manager. I didn't find that necesary.

Good luck.

I have also a HP Laserjet 1000 and this worked for me.

---

