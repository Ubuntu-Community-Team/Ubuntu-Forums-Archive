---
title: "I did something stupid I think..."
date: 2007-10-28
forum: General Help
---

### Post by grEnAlEins on 2007-10-28
I was messing around, and I changed the driver for the video card.  Now I cannot boot up.  Is there anything that I can do besides complete re-install?  I really do not want to do that as I will not have a working computer for days due to the fact that I cannot connect to the internet without Java, and cannot download Java without connecting to the internet](*,).  I can give more info as it is needed.

Thanks,

Nick

---

### Post by kellemes on 2007-10-28
Well, what's your videocard? And how have you tried to install the driver you need for it?

---

### Post by grEnAlEins on 2007-10-28
Intel® Graphics Media Accelerator 950.

I did it through a GUI through the menu up top.

---

### Post by Ehtetur on 2007-10-28
> **grEnAlEins said:**
> I was messing around, and I changed the driver for the video card.  Now I cannot boot up.  Is there anything that I can do besides complete re-install?  I really do not want to do that as I will not have a working computer for days due to the fact that I cannot connect to the internet without Java, and cannot download Java without connecting to the internet](*,).  I can give more info as it is needed.

Thanks,

Nick

hrmmm... I never heard of needing java to connect to the internet.

Couple things you can try..
Since you can't boot up normally, you'll need to boot using the recovery mode option.
[LIST=1]
[*]Change the driver listed in xorg.conf to the one that worked.
Look at the Driver listed under Section "Device" Is it the one you want?
> less /etc/X11/xorg.conf
It may be as simple as changing the driver to the one you want to load.
Before you edit it, make a backup
    > sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
]sudo gedit /etc/X11/xorg.conf

[*]OR.. Check for a backup xorg,conf file dated prior to the driver change.

> ls -al /etc/X11/xorg.conf*
Check the dates of the files listed. The one that is dated before you made changes is the one you will use.
    > sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
   sudo cp /etc/X11/**Name of earlier xorg.conf file**  /etc/X11/xorg.conf


[*]OR.. if all else fails, reconfigure:
> sudo dpkg-reconfigure xserver-xorg
[/LIST]

Good luck!!

---

### Post by ericartman on 2007-10-28
During startup isn't there a safe video option you can choose? I'm supposing this doesn't appear or work?

Cart

---

### Post by grEnAlEins on 2007-10-28
> **Ehtetur said:**
> hrmmm... I never heard of needing java to connect to the internet.

Couple things you can try..
Since you can't boot up normally, you'll need to boot using the recovery mode option.
[LIST=1]
[*]Change the driver listed in xorg.conf to the one that worked.
Look at the Driver listed under Section "Device" Is it the one you want?

It may be as simple as changing the driver to the one you want to load.
Before you edit it, make a backup
    

[*]OR.. Check for a backup xorg,conf file dated prior to the driver change.


Check the dates of the files listed. The one that is dated before you made changes is the one you will use.
    


[*]OR.. if all else fails, reconfigure:

[/LIST]

Good luck!!

I do not need java to connect to the internet in general, only the network for the dorms I stay in.  We need to use the Java applet that corresponds to Cisco Clean Access Agent.  I need Java to run the applet, and to connect to download the JRE or the firefox plugin.  Our network administrator is a *jerk* and will not give use temporary access to DL java.  He gives 15min temp access to windows users to DL Cisco CCA and the required antivirus (Symantec Corporate).  But no temp access for linux kids... what a tool, huh?

I will give that a try,  Thanks for the input.

EDIT:  option 2 FTW!!!  Thanks so much!:guitar:

Cheers,

Nick

---

### Post by grEnAlEins on 2007-10-28
> **ericartman said:**
> During startup isn't there a safe video option you can choose? I'm supposing this doesn't appear or work?

Cart
No sir, that did not work, if you mean the thing on the cd... not sure if that was what you meant, but I tried that with no luck.  It was my first thought too.

Thanks,

Nick

---

### Post by Ehtetur on 2007-10-29
> **ericartman said:**
> During startup isn't there a safe video option you can choose? I'm supposing this doesn't appear or work?

Cart

Right before the Ubuntu splash screen, you should see a brief message about pressing **ESC** to access the boot options...
Press the escape key then and you'll get 3 boot options. Choose the **(recovery mode)**.

---

