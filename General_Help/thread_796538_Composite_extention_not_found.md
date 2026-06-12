---
title: "Composite extention not found?"
date: 2008-05-16
forum: General Help
---

### Post by justgrant2009 on 2008-05-16
I just installed ubuntu 8.04 on my desktop (first time ubuntu for this machine) and durring my routine customizations for my machines, it's reporting to me that it cannot find the composite extention when i turn visual effects to "normal". same with "extra".  I've tried to go reinstall all of the compiz files too in the synaptic and it installs all but compiz-fusion-bcop (for some reason it has trouble moving one of it's files).  Consequently, I can't use any eye-candy, and where's the fun it that #-o

---

### Post by bill516 on 2008-05-16
Same situation here except that I upgraded from 7.10 where the various compiz effects did work.  In 8.04 they do not and I get the "composite extension is not available" message.  My graphics card on this laptop is by ATI and the ATI driver has been enabled and it is working.

Perhaps someone will respond and help both of us.  Let's hope.

---

### Post by xtreme- on 2008-05-20
Hi guys,
Maybe you have already tried this, but have a look at [http://ubuntuforums.org/showthread.php?t=436110](http://ubuntuforums.org/showthread.php?t=436110)

Try the tip by TMulder (post #5) and cifrancgx (post #17).

justgrant2009: Have you installed the proprietary drivers for your graphics card? If not, you could try that. Go to System->Administration->Restricted Drivers Manager and check the "Enabled" box by the graphics driver.

Sorry if this did not help, but I decided to post since you haven't got any answers yet.

If it doesn't work, maybe you should post more detailed info on you graphics hardware (output from "lspci" in a terminal) and your xorg.conf-file (fond at /etc/X11/xorg.conf).

Good luck!

---

### Post by Forlong on 2008-05-21
> **justgrant2009 said:**
> I just installed ubuntu 8.04 on my desktop (first time ubuntu for this machine) and durring my routine customizations for my machines, it's reporting to me that it cannot find the composite extention when i turn visual effects to "normal". same with "extra".
Try [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
> **justgrant2009 said:**
> I've tried to go reinstall all of the compiz files too in the synaptic
This is not Windows. ;)
Reinstalling will only help if you installed something from outside the Ubuntu repositories.
> **justgrant2009 said:**
> it installs all but compiz-fusion-bcop (for some reason it has trouble moving one of it's files).
You do not need compiz-bcop.
Only install the **compiz** metapackage, that will take care of everything for you.

Still it's odd that you can't install bcop, what's the exact output of
```
sudo apt-get install compiz-bcop
```

---

### Post by mr_boo1711 on 2008-06-02
Ok - It looks like i'm another one who cant get the eye-candy working.  I decided to remove my linux and reinstall completely - you know, tidy up my hard drives and start fresh :) (I've been playing with ubuntu now for 2 years and I've got files and stuff EVERYWHERE in this damn PC!) lol

Anyways - did the fresh install and installed the nvidia beta drivers.  I'm running two 19" monitors, and i've setup it up xinerama.  All good so far.  Tried to run the custom display settings to take advantage of compiz... and that's where it 'fell down'..

Here's the output from compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

stephen@stephen-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0295 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 


...As you can see I ran 'comiz' out of curiosity to see what happened. Needless to say nowt happened. lol

Any ideas peeps?? :confused::confused:

---

### Post by Forlong on 2008-06-02
> **mr_boo1711 said:**
> I'm running two 19" monitors, and i've setup it up xinerama.  All good so far.
No, that's exactly where the problem lies.
Xinerama disables your composite extenstion. You have to switch to TwinView.

This may be of help: [https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo) (I know it says Xinerama how to but there's a guide for TwinView as well ;))

---

### Post by mr_boo1711 on 2008-06-02
> **Forlong said:**
> No, that's exactly where the problem lies.
Xinerama disables your composite extenstion. You have to switch to TwinView.

This may be of help: [https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo) (I know it says Xinerama how to but there's a guide for TwinView as well ;))

Ah - ok.  So would it not be easier for me to use nvidia-settings and just switch off xinerama?  Incidently - it doesnt look half as good without xinerama switched on... :(

I tried the link you sent to give it a read over, and followed the link to the 'Teinview' page - but it says..

"This page does not exist yet. You can create a new empty page, or use one of the page templates. Before creating the page, please check if a similar page already exists."

The strange thing is that it was working fine after I upgraded to 8.04 BEFORE I wiped it and reinstalled everything from scratch...  why cant I just leave things alone.:(

Damn it.... lol

---

### Post by Forlong on 2008-06-02
> **mr_boo1711 said:**
> I tried the link you sent to give it a read over, and followed the link to the 'Teinview' page - but it says..
That's not supposed to be a link, that's the wiki software (moinmoin) parsing CamelCases.
Just follow the steps below. :)
> **mr_boo1711 said:**
> The strange thing is that it was working fine after I upgraded to 8.04 BEFORE I wiped it and reinstalled everything from scratch...
But not with Xinerama, was it? Because AFAIK, it's simply not possible.

---

### Post by mr_boo1711 on 2008-06-02
Ah - I knew that, I was just testing.... ;)

Well it definitely did work - I promise you. lol.  I was using older drivers and I had messed about with my config that much over the past two years that I maybe did something and didn't realise it. :confused:

---

