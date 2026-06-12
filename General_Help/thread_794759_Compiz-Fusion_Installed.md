---
title: "Compiz-Fusion Installed?"
date: 2008-05-14
forum: General Help
---

### Post by Winsbreaker on 2008-05-14
I have an IBM T42 Laptop with 1.7 Ghz, 1G RAM, 80GB HDD and have Hardy installed with the proprietary ATI driver, working, see below:

> paul@paul-laptop:~$ glxgears
13749 frames in 5.0 seconds = 2749.780 FPS
14155 frames in 5.0 seconds = 2830.926 FPS

paul@paul-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.1.7412 Release

paul@paul-laptop:~$
 

I believe I have Compiz-Fusion installed and running, I followed the guide posted here: [http://howtoforge.com/compiz-fusion-ubuntu-8.04-ati-mobility-radeon-9200](http://howtoforge.com/compiz-fusion-ubuntu-8.04-ati-mobility-radeon-9200) 

and everything appears happy, yet I can't get any of the affects to work such as the cube wobble...etc. It has disabled my normal desktop and window effects and not enabled any of the Compiz-Fusion effects. Help please.

---

### Post by jcollins on 2008-05-14
what is the output when you run compiz at a terminal?

---

### Post by Winsbreaker on 2008-05-14
This is what I get:

> 
paul@paul-laptop:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e50 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: not present.
aborting and using fallback: /usr/bin/metacity

paul@paul-laptop:~$


---

### Post by tommyhakinen on 2008-05-14
Check this

> [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

Your ATI Graphics Card might be blacklisted.

Good luck.

---

### Post by Winsbreaker on 2008-05-15
Okay, so if my card (ATI Radeon Mobility 9600) is blacklisted and I can forgo using Compiz-Fusion, how do I recover my desktop effects and workspace switching effects to normal?

---

### Post by tommyhakinen on 2008-05-15
press Alt + F2, then enter
> metacity --replace
it will switch off all the visual effects

or you can install Fusion-Icon for ease of use
> sudo apt-get install fusion-icon

Access it from System Tools > Compiz Fusion Icon
On the Notification Area, right click on the Compiz Fusion Icon and switch the Windows Manager to Metacity (No visual effect)

---

### Post by RAOF on 2008-05-15
Hah!  There's the winner:
```

...
Checking for Composite extension: not present.
...

```

It is likely that your xorg.conf has a section explicitly disabling Composite.  This was needed in the past to enable 3D acceleration with fglrx (since it didn't support 3D + Composite), but now fglrx supports 3D + Composite, and it is needed to use Compiz.

Either remove the
```

Section "Extensions"
        Option "Composite" "0"
EndSection

```
part of your /etc/X11/xorg.conf file, or post your whole /etc/X11/xorg.conf file and I'll show you precisely what to remove.

Alternatively, this might be because your fglrx driver is too old to support Compiz.  I'm not familiar with ATi's versioning, but the version string from your fglrxinfo looks suspicious to me :).

---

