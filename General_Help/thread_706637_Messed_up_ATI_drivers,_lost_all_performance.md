---
title: "Messed up ATI drivers, lost all performance"
date: 2008-02-24
forum: General Help
---

### Post by banelos on 2008-02-24
I had compiz working with ati drivers I installed from some guide that I can no longer find.. I think I also had to install XGL to make desktop effects work when I did that..

Today I then tried playing some 3D games like the Quake4 demo.. I have a Radeon HD2300 so I would think that would have worked out but it kept complaining about missing texture_compression thing. So I ended up trying to reinstall the newest ATI drivers..
After that my Quake4 demo still didn't work and it also seems the performance for everything including compiz has gone completely south. I can't even play video in fullscreen without it lagging where as before I could have like 3 videos running fullscreen on each their workspace and switch between them with compiz.

Could anyone point me at a guide or help me how to completely remove the ATI drivers/settings and how to properly install ATI drivers so that compiz, fullscreen video and games work?
I'm already missing XP >.<

---

### Post by Arand on 2008-02-24
This guide has been very helpful when I've messed about with ATI drivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

Also, the newest ATI drivers (if you download from ati and not via Ubuntu-restricted-drivers) should work without XGL (using AIGLX instead) as far as I know.

And I know how it feels, I'm dual-booting at the moment, with XP for stability :shock:, and it feels so wrong!

- Arand

---

### Post by banelos on 2008-02-25
The drivers I installed that messed up any performance I had running compiz and fullscreen video was the ones I got from installing with that very guide..

Sigh I think I'll just go back to windows again.. This is the 2nd time graphics drivers and having to manually edit xorg.conf has kept me from switching to Linux... I would really recommend the devs and other people developing on Linux distros to try and simplify this process for us beginners in some way where we still can have the choice to install the newest binary drivers.

---

### Post by Nameless_one on 2008-02-25
I also installed the latest fglrx lately, and am experiencing a drop in performance. I think the latest driver is just bad, however, 3D graphics in games work now, and they didn't before. In one of the latest versions, support for compositing was added. 

When doing that, I read some things about XGL, and most were complaints. Maybe you should try AIGLX. Compiz runs fine on my computer just with the latest fglrx, I never installed XGL. I guess the performance problem should get better in the next versions. 

Personally, I dual-boot just for games. Linux is so much better for everyday stuff. I get frustrated when I reboot into WinXP to play and I have only one desktop and no terminal (one that is in any way useful, I mean).

---

### Post by danwood76 on 2008-02-25
You say you installed XGL.
This will be your problem, the new ati drivers dont require xgl (they use AIGLX now) and you you need to remove the xgl xserver first then re install the drivers.

---

### Post by banelos on 2008-02-26
I'm gonna try to uinstall the ATI drivers, the restricted drivers and the xgl-server and then try and install the latest drivers and run them in AIGLX mode..

How do I go about running the drivers in AIGLX mode? I havn't had the best experiences with manually editing the xorg.conf lately.

More specifically what should be in Section "Module", how do I set composite on/off and any other xorg.conf edits needed.

---

### Post by chalewa on 2008-02-26
you shouldn't have to manually edit the xorg file, unless you really want to. 

if you follow the 'Manual' steps in that wiki, you should be able to relatively easily install the 8.2 driver. Also, make sure you remove the xgl-server, and all other packages with reference to fglrx (as it says to in the wiki). 

After you follow these steps, you might have to reconfigure your xorg to allow the resolution that you want on your monitor...

```
sudo dpkg-reconfigure xserver-xorg
```

will give you a 'wizard' to do it. just select the resolution you want when the time comes. 

then, you should be able to use the gui tool that comes with the driver, (in xfce it is in accessories) ati catalyst config to get the resolution that you want. 


hope that helps. if not, post your xorg.

---

### Post by danwood76 on 2008-02-26
They naturally run aiglx when its needed so there no additional config required.

Follow this guide for the re install:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually)

If you follow that guide it will configure the xorg.conf for you (the aticonfig tool does it) so theres no need to edit the xorg afterwards to get anything to work.

You should be able to remove the xgl-server and fglrx (the ati driver) using synaptic.

---

### Post by banelos on 2008-02-26
Ok thanks both of you.. I think I'm gonna throw my backed up compiz settings and some other stuff on my windows drive and then reformat my linux partition and start over so I'm sure I don't have some old drivers messing it up.. Then I'll follow the guide you linked to.

---

### Post by banelos on 2008-02-26
Ah everything seems to be working perfectly this time around. I knew a lot more about what I was doing this time too.. It seemed it was simply white listing flgrx in compiz and video output not being set to X11 that I was missing.

Tip to anyone who wants to learn a lot about Linux themselves:
Use "<command> --help" or "man <command>" in the terminal to find out how to use the terminal commands instead of just following guides blindly.

---

