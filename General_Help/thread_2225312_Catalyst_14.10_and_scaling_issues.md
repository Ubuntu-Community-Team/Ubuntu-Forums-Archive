---
title: "Catalyst 14.10 and scaling issues"
date: 2014-05-20
forum: General Help
---

### Post by Mazate on 2014-05-20
I just did an install of the catalyst 14.10 driver and all is working fine.  As is the case after installing an amd driver, the screen has a black border around it... it's not going the size of my screen.  Normally I open the catalyst control center and adjust it out to full screen and we're ready to go.  Unfortunately this version of the catalyst control center doesn't have any adjustment for this. It has a selection for automatic scaling to the size of the screen but it doesn't do it.  [ATTACH=CONFIG]253330[/ATTACH] If anyone knows how I can get this open to full screen, I would appreciate the info.

---

### Post by Yellow Pasque on 2014-05-21
So you have tried tweaking the overscan settings?

---

### Post by Elfy on 2014-05-21
*Thread moved to **Ubuntu Development Version**.*

---

### Post by Mazate on 2014-05-21
This should not have been moved to this forum.  I'm using catalyst 14.10, not Ubuntu 14.10.  I'm using Ubuntu 14.04.  As for the question of having tweaked the overscan settings, such settings appear not to exist.  If you look at the screenshot on my previous post, you'll see that there really are no settings to tweak.

---

### Post by Elfy on 2014-05-21
oops - pesky numbers

---

### Post by Yellow Pasque on 2014-05-21
The screenshot only shows one particular page of CCC. Try clicking the different tabs and the '+' signs for each category. I know they're in there...

---

### Post by SingingBush on 2014-05-21
forget the trying to fix this using Catalyst Control Center, it's been broken for ages. Disable the overscan with:

[B]sudo amdconfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0


[/B]You will need to reboot

---

### Post by Mazate on 2014-05-21
This is what I get:

```
desktop:~$ sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again.
aticonfig: parsing the command-line failed.
```

---

### Post by QIII on 2014-05-21
Herein lies a part of the problem.

After installing the ATI driver, it is not supposed to be necessary any longer to run amdconfig.  However, what is supposed to be the case does not appear to be the case.

Ubuntu, by default, does not need an /etc/X11/xorg.conf file to run. A basic one is created when you install the driver. However, some values required by the driver and Catalyst are stored there only if amdconfig is used.  CCC is *not *broken.  This little known necessity is not well-published.

So, run 

```
sudo amdconfig --initial
```

and then reboot.

See if Catalyst will then allow you to correct the underscan by allowing ATI to use the monitor for scaling (I'm not at home, so I can't tell you exactly where that is.)  If that doesn't work, use the setting as described above.  In the wiki link in my signature, I have commented both about amdconfig and correcting underscan via the terminal.

Cheers.

---

### Post by Mazate on 2014-05-21
I tried what you said and it didn't do anything unfortunately.  The catalyst control center doesn't have much in the way of scaling options in this particular driver version which is strange.  I went to the wiki in your link and it had the same info that you gave me here.  I'm stuck...  Thanks for helping me on this, by the way.

---

### Post by QIII on 2014-05-21
Did you try "Use display for scaling"?

Is this actually Catalyst 14.10?

---

### Post by Mazate on 2014-05-21
Ok, so I'm a little embarrassed.  This is 14.4, not 14.10.

Yes, I tried "use display for scaling" and it did absolutely nothing.  The screen went black for about two seconds while it made the change and when it came back up everything was the same.  I'm using a Radeon 7770 if it means anything.  There used to be a sliding scale on the adjustments screen that I would slide over to make the picture fit the screen but this version of the CCC doesn't have it.

---

### Post by Mazate on 2014-05-21
Ok, I just noticed that the CCC is not allowing me to set it to "Use display for scaling".  It stays on the option to use the graphics processor for scaling option.

---

### Post by QIII on 2014-05-21
OK.

Did you install from the ATi website by directly running the .run, creating a .deb or from the Ubuntu repository?

By the way, I'm using Kubuntu 14.04 with the most current driver right at the moment.

---

### Post by Mazate on 2014-05-21
I installed the driver from AMD's website using the guide on this page:  [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide)

I have two good images here to show you my problem.  Here's the normal CCC setting for scaling.  [ATTACH=CONFIG]253353[/ATTACH]  As you can see there is a horizontal scroll bar for my settings that normally fixes this.  Here's what I see now.  [ATTACH=CONFIG]253355[/ATTACH]  No scroll bar here.

---

### Post by QIII on 2014-05-22
OK.  I'm going to make a suggestion as a troubleshooting measure.

When you install via the instructions on the website, there is an uninstall script in the installation directory.  Run that.  Also rename /etc/X11/xorg.conf to something like /etc/X11/xorg.conf.bak.  Reboot.

You should fall back to the default driver.

Then install the driver (which is the same version if you are using Trusty 14.04) from the repo:

```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates xvba-va-driver
```

```
sudo amdconfig --initial
```

Reboot.

I am running the driver from the Trusty repo (the xx.04 and xx.10 versions of Ubuntu have traditionally included the April and October versions of the fglrx driver in the repo at release time).

Right now, I don't think ATi has released 14.5, so you should get the latest driver.

Let us know if that gets you to where you can adjust the underscan either through CCC or via the command line.

---

### Post by Mazate on 2014-05-22
Well, installing from the repo... would that mean that I'm still getting 14.4 if I use the "additional drivers" app?

---

### Post by Yellow Pasque on 2014-05-22
They Trusty repo's version is actually based off 14-3 beta from what I can tell, but don't take that as gospel. AMD's dual numbering (a date version and an arbitrary version) is confusing enough, but then Ubuntu often makes a custom version of their own.

---

### Post by QIII on 2014-05-22
Actually, I think you are right.  There was some confusion with getting 14.4 ready by the time Trusty came out, so it got out of phase.  Usually ATi gets the .4 and .10 versions up to snuff by the Ubuntu releases - even if the drivers are not released to the public and only to Canonical.  This usually leads to a snide article from Phoronix about ATi and Canonical being in cahoots.

---

### Post by Mazate on 2014-05-22
Ok, I uninstalled 14.4 and then reinstalled it and it works perfectly.  It rebooted with the picture fitting the monitor.  So, we're good.  Thanks you guys very much for the help.

---

