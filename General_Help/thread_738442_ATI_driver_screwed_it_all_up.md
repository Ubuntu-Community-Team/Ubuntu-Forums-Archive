---
title: "ATI driver screwed it all up"
date: 2008-03-28
forum: General Help
---

### Post by lilalmond on 2008-03-28
Hey

I recently switched to ubuntu gutsy on my laptop and i got it to work properly.
I run compiz fusion and Awn without problems (maybe slow but what to expect from a dinausaurus  :)  )
I made couple of installations via terminal and it went ok.
i had problem with xgl at once but solved it.
And today i tried to install drivers for ATI Radeon and something went wrong with fglrx.
When i rebooted the puter i couldnt get to the login window, i spent several hours trying to fix it  :mad:
When i thought i had fixed the problem i came to the login window and i couldnt type my user name (letters) but i could type numbers (and the letters ö,ä   swedish keyboard layout)
I finally modified the xorg.conf as it was earlier and i could get to the login window and type my user name and password.
Now it seems to run as it used before.
Im just curious about what happened and if it happened to someone else :confused:
Im a noob so take it easy  ;)

---

### Post by lilalmond on 2008-03-30
Hey again,

In my previous post i explained what happened when i tried to install drivers for ATI Radeon, and i 'd like to understand why both xgl and fglrx screwed up my computer.
Im actually trying to fix the graphics because everything is so slow...
For example when im on youtube, the video buffered all the way, no problem with the connection but the video is very slow and is lagging.
When i go in system>administration>graphics it says my graphic card is ATI Radeon (fglrx) and drivers is ATI - ATI Mach 8 Mach 32 Mach 64..
For the drivers i can choose mutiple model like Radeon fglrx, Radeon vesa, Radeon fbdev...
I'd like to know which drivers im supposed to select to make it work better.
Please any help would be welcome...

---

### Post by danwood76 on 2008-03-30
fglrx will work best with accelerated graphics.
XGL is not needed and will slow down yur machine if you have the xgl xserver installed as its more buggy and slower than the standard Xorg xserver.

the best thing to do is to run the following command:
```

sudo aticonfig -f --initial

```
this will setup fglrx properly in your xorg.conf.

---

### Post by lilalmond on 2008-03-30
First thx for replying

I did run the command "sudo aticonfig -f --initial" but it said  command not found
Anyway, 2 days ago when i downloaded the drivers for ATI Radeon everything screwed up and i edited the xorg.conf file as it was before the screw up so i could start ubuntu again.
I did run "sudo aticonfig --initial-f" to get my original configuration back at the same time i reconfigure my xorg.conf file but this doesnt solve my problem...

In my previous post i asked which drivers im supposed to choose because in system>admin>screen and graphic it says my graphic card is ATI Radeon (fglrx) but in my xorg.conf files  ( i have several of them  xorg.conf.1  xorg.conf2 ...)it says in section device that my driver is vesa then in the xorg.conf.1 it says its ATI and in the xorg.conf.2 it says its fglrx   so im confused...

I do not have xgl xserver installed because from previous "**** up" i had to uninstall it.

Also when i run "lspci -n | grep 0300" in terminal this is the output
   0000:01:05.0 0300: 1002:4337
And when i run "lspci | grep VGA" the output is
   0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

Dont know if that helps

Any help is more than welcome

Thx

---

### Post by strabes on 2008-03-30
You should uninstall everything related to fglrx and then install it using the restricted drivers manager under System -> Administration.

---

### Post by danwood76 on 2008-03-31
> **lilalmond said:**
> 
I did run the command "sudo aticonfig -f --initial" but it said  command not found


If it says command not found that means you havent installed the ati driver properly.
Install the drivers using this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually)

---

### Post by lilalmond on 2008-03-31
> **danwood76 said:**
> If it says command not found that means you havent installed the ati driver properly.
Install the drivers using this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually)

My problems came from that installation...
I downloaded "ati-driver-installer-8-3-x86.x86_64.run" and followed the instructions until i rebooted and couldnt get into the system anymore.
My graphic card does not support fglrx so i cant install this driver.

---

### Post by danwood76 on 2008-04-01
Right, if your card isnt supported by the latest release of fglrx then you wont be able to nativly run compiz due to the drivers available not using AIGLX.
Install the drivers from the restricted drivers manager, if you really want compiz and so on you will need to instal the xgl-xserver but as I said before this is slow and buggy.

I would just go without compiz or get a better gfx card.

---

### Post by lilalmond on 2008-04-01
> **danwood76 said:**
> Right, if your card isnt supported by the latest release of fglrx then you wont be able to nativly run compiz due to the drivers available not using AIGLX.
Install the drivers from the restricted drivers manager, if you really want compiz and so on you will need to instal the xgl-xserver but as I said before this is slow and buggy.

I would just go without compiz or get a better gfx card.

I have compiz fusion and AWN up and running
Like i said in my previous posts i installed xgl before and it also screwed up my laptop so i uninstalled it.
Everything is working but its very slow, thats why i thought it was some graphic problems but obviously theres not much to do.
I guess my graphic card is old and crappy but good enough to have compiz fusion and AWN to work.I also have the 3D desktop plugin and the snow plugin working so i think i cant complain.
Im gonna put more RAM see if it gets better...
Oh and about the restricted drivers manager when i click on it, it says "your hardware does not need any restricted drivers"
Thx for ur help anyway

---

