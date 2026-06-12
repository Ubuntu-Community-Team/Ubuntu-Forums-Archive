---
title: "Envy forked up my display driver..."
date: 2007-05-19
forum: General Help
---

### Post by TotalRetard on 2007-05-19
I've been going through the ATI driver rumba, as any Ubuntu user has to...

So I found Envy, the neat program that installs the driver automatically.
I install the driver, everything is good, and then I reboot.

Okay, there is no sound anymore. The computer says that the sound is fine, but it's not coming out of my speakers anymore. So from the Envy menu I choose "Uninstall Ati Driver" and then I reinstall the Ati-Driver.

Again, reboot...

.... and X-server fails to start. I still log in, and try to uninstall the Ati driver. It goes as planned, but when I reboot the X-server fails to start, yet again. 

Then I attempt to re install the Ati-driver. It works, but there is no sound anymore. And besides, when I test the whole thing with Cedega, it says that OpenGl driver and the 3D driver both don't work (still says that the sound works).

Any suggestions?

I'd like to start by installing the default Ubuntu display drivers, but I can't find anywhere how I would do that. After that I would like to make a clean install of the Ati drivers again with Envy, without all this hassle.

So, what do you think I should do, and how do I return to the default screen driver? 

P.S. I use Ubuntu 7.04, and the sound cables are still hooked, I can hear the thump from my speakers when the computer shuts down / starts up.

---

### Post by MoLE on 2007-05-28
If you can give us some more specific information, we may be able to advise you better.
Things that would be useful:
- output of the /var/log/Xorg.0.log when you try to start X.
- what model of ATI card are you using?  Some of the older ATI cards are no longer supported by the proprietary driver.

If you boot into 'recovery mode' - from the Grub boot menu, and run the following command:

```

$ sudo dpkg-reconfigure xserver-xorg

```
This will enable you to generate a new xorg.conf file, hopefully with the default display drivers.

I'm not sure about the sound issue - that is unlikely to be directly related - but run through the [comprehensive sound troubleshooting guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide").  This may give you some clues as to where the problems lie.

---

