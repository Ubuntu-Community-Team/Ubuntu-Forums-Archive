---
title: "Samsung Printer and Open Office"
date: 2006-12-23
forum: General Help
---

### Post by bgeek on 2006-12-23
Hi all,

I've got a ML-2570 Series Samsung Laser Printer running with Ubuntu 6.06.1 LTS.  Printing works fine with nearly everything.  However, the one application that does not seem to work correctly is Open Office.

Versions supplied with Ubuntu and those obtained from the OO website both have some weird printing issue that IMHO looks like some kind of bug with Ubuntu because the same versions print perfectly in Fedora Core 5 onwards.

Basically, when printing the page will print 2 or 3 inches to the right and even then only prints the end of the document.  It's almost as if OO printing is scaled wrongly or something (not sure that makes sense).  I want to print to a4.  Everything is set to use a4, but it simply doesn't print correctly - margins/borders/scale, i don't know :(

I can print okay from the command line, from browsers, pdfs, etc... all work great except OO.  I'm using the latest Samsung Unified Drivers.  I'm so disappointed I'm almost considering installing FC on the box because that works perfectly using the same version, same drivers :)

Has anyone else come across this before and found a solution?  I've read of similar problems on both here and the OO forums, but no solutions.  I've tried most things including changing /etc/papersize (it's already set to a4).

Many Thanks,

bg

---

### Post by laidback on 2006-12-23
I would suggest that your printer driver is not properly installed even though it would appear to be so. My solution is as follows:-

I am using a Samsung ML-1610 and have a lot of problems in Ubuntu. The Samsung driver works fine in Mandriva (eventually) but not Ubuntu. I wrote to Samsung to ask advice and they said that it just wasn't supported in Ubuntu. However, I did find a link in the Ubuntu forum to set up a Samsung ML-1740 posted on June 25th 2005 by user neurosion I think it was. Now the instructions there were not absolutely correct for a new installation but with some sensible adjustments I got mine to work. The problem I had was that I simply couldn't add a printer in the Samsung Unified Driver Config system, even though the Icon and software was apparently loaded and working. Once I had followed the instructions from neurosion all was sweetness and light. I had previously used the ML-1510 and 1710 drivers that are within the default Ubuntu printer setup system, but neither of these gave me graphics capabilities, which failed when I imported Excel files into OOo. These files had a lot of formatting within them and although the numbers were OK I simply couldn't print some of the pages. A real nuisance. Now I can. I can also print photgraphs, also a previous no no in Ubuntu. My OO Word prints OK too, at least so far.

The instructions as printed are as follows:-

1 Download the latest driver from Samsung site.
2 Extract the achive to somewhere you can get at it
3 Use package manager to fetch libgtk 1.2
4 Open a terminal window
5  Type: sudo adduser cupsys shadow
6 Type: sudo /etc/init.d/cupsys restart
7 Type: sudo passwd root [ sets a temporary root password]
8 goto whevetr you extracted the drivers and type: /setup.sh
9 Follow the prompts. If all goes well you should end up in Samsung's setup utility. If somehow you don't get there, typing linux-config in a terminal will get you there.
10 Add printer
11 Enter root pswd you created in step 7
12 Follow the promps, you're on your own here
13 When all done type: sudo passwd -l root [disables root pswd]

Your printer should be configured and available in System>Administration>Printing


9 For me linux-config doesn't work. But the Samsung Icon was on the desktop so activate it through the Icon.

line 8 It's not ./setup.sh anymore , it's ./autorun
line 11 Didn't get asked for root pswd, it just went straight ahead as if I had typed it
line 3 libgtk 1.2 was already loaded onto my system by default, but check your system.

I have come to the conclusion that the key to the installation is the creation of the shadow cups user and the temporary root user. Without these the Samsung unified driver script just cannot run properly.

Suggest you remove your current Samsung installation before you start so that you have as clean a system as possible. The Unified Driver comes with an Uninstall script, you may have to search for it in the directories.

Hope this helps.

Laidback (newbie)

---

### Post by laidback on 2006-12-27
In case this helps others viewing this thread, I have just installed Ubuntu 6.10 Edgy Eft, and it comes with many more printer drivers as standard, including Samsung ML-1610. Installation is a breeze now, as it should be. And I've got a full set of controls i.e. Tone density range from 1 to 5.

Laidback

---

### Post by foureight84 on 2007-02-07
hmm i'm still getting error after installing libgtk1.2

```

./install.sh: 1232: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted

```

---

### Post by matjazcr on 2008-01-27
To bgeek - I have the same problem.
A working 'solution' is to install the Samsung ML-2550 printer (via System/Administration/Printing) - by using the driver that is provided.
I am disappointed that the printer doesn't have the same functionality as in Windows. Eg.: it is impossible to control the 'job options' out of applications (OOo, Firefox) - scaling, multiple pages per sheet etc.

---

