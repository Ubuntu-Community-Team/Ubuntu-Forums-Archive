---
title: "2 graphics cards, 4 monitors, ubuntu 14.04 LTS, not working properly"
date: 2015-01-10
forum: General Help
---

### Post by Todd_Quillen on 2015-01-10
I'm having an issue with a recent fresh install of ubuntu on my desktop PC.  This is my first time using linux, so I apologize for my ignorance.

Anyway, I have 2 graphics cards (AMD Radeon HD 5770) and 4 monitors (all exactly the same type), but I can't get the 2 monitors that are connected to the 2nd video card to work.  The monitors stay idle, as if they were turned on without being hooked up to a computer.

I went through this thread:

[http://ubuntuforums.org/showthread.php?t=2029378](http://ubuntuforums.org/showthread.php?t=2029378)

and I followed these directions to get Catalyst Control Center working (section 2.1, installing via command line):

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

This was a fresh install of ubuntu, so I don't think I messed up anything prior to trying those methods above.

Catalyst Control Center seems to be working properly.  The first two monitors are showing up successully there, but where there would be two more icons for a third and fourth monitor... there's one icon saying "[Uknown Display] AMD Radeon HD 5700 Series."  It seems as though Catalyst control center knows the video card is there, but isn't using it for some reason.

Does anyone know what I'm doing wrong?

Thanks.

[ATTACH=CONFIG]259161[/ATTACH]

---

### Post by QIII on 2015-01-12
Hello!

Are you absolutely sure you used 

```
 sudo amdconfig --adapter=all --initial
```?

Are both cards in, for instance, 16x slots?

Switch the two monitors on one card with the two on the other.  Do the same monitors come on?

Physically switch the cards.  What happens?

---

### Post by Todd_Quillen on 2015-01-17
> **QIII said:**
> Hello!

Are you absolutely sure you used 

```
 sudo amdconfig --adapter=all --initial
```?


Yes, I'm pretty sure I did.  I can do a fresh ubuntu install and start over if necessary though.  I can keep track of every command I type in, with restarts and such, to be sure.  Let me know if you think that's necessary.

> **QIII said:**
> 
Are both cards in, for instance, 16x slots?


Yes, I believe they are.  My mothboard is an Asus Sabertooth X58.  For reference, the new egg link for it is below:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131665](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131665)

According to the specs from newegg, It seems as though they're in the "2 x PCIe 2.0 x16 (dual at x16/x16 mode)" slots.

> **QIII said:**
> 
Switch the two monitors on one card with the two on the other.  Do the same monitors come on?


No, the other two monitors come up.

> **QIII said:**
> 
Physically switch the cards.  What happens?

There is no change when switching the two cards.

I'm not sure if this is important or not (I figured it's not), but I have two SSDs in this computer... one with windows 7, and the other with ubuntu.  During boot, I select which harddrive I want to boot to.  All 4 monitors work well on windows 7.

---

### Post by QIII on 2015-01-17
Don't reinstall Ubuntu.  Just run the

```
sudo amdconfig --adapter=all --initial
```

to see if you missed it.

The worst we are going to have to do is uninstall the driver if it comes to that.  But we'll cross that bridge if we need to later.

Did you install using the AMD/ATI website or from the Ubuntu repo?

---

### Post by Todd_Quillen on 2015-01-17
> **QIII said:**
> Don't reinstall Ubuntu.  Just run the

```
sudo amdconfig --adapter=all --initial
```

to see if you missed it.


Your code above returned:

```
Found fglrx primary device section
Found fglrx primary device section
 Unable to find any supported Screen sections

```

> **QIII said:**
> 
The worst we are going to have to do is uninstall the driver if it comes to that.  But we'll cross that bridge if we need to later.

Did you install using the AMD/ATI website or from the Ubuntu repo?

Hmm, I think I originally tried via the AMD website, but was having issues (the file wouldn't excecute because of something with fglrx, I think I hadn't installed it yet).  I wasn't sure if I had broken anything, so I did a fresh install of ubuntu and started straight from section 2.1 of this link:

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Now that I see that again, I think ONLY did section 2.1.  Are the other sections applicable?

For reference, this command:

```
fglrxinfo
```

outputs:

```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 5700 Series
OpenGL version string: 4.3.12798 Compatibility Profile Context 13.35.1005

```

---

### Post by QIII on 2015-01-18
Hey!  Haven't forgotten about you.  I'm on the road and sometimes am limited to my cell phone.  If someone else pops in, there are a lot of very knowledgeable people here.

Try enabling Xinerama.  You might only be able to do an extended desktop between the pair of monitors on each card -- that is you would have two distinct desktops and can't drag windows to the desktop on the other card, but we'd get things going that way.

Cheers.

---

### Post by Todd_Quillen on 2015-01-18
Hey, no problem!  I'll take the help whenever I can get it.

Something I just thought of... I'm second guessing myself whether or not my graphics cards would be considered AMD or ATI.  Would it make a difference if I had picked the wrong one?  The fact that there are two commands:

[FONT=arial]```
[COLOR=#333333]sudo aticonfig [/COLOR][COLOR=#333333]--adapter=all --initial[/COLOR]
```
```
[COLOR=#333333]sudo amdconfig --adapter=all --initial[/COLOR]
```[/FONT]

Makes me think there might be.

Anyway, the reason why I'm second guessing myself is because when I boot into windows (where all four monitors work properly), the device manager actually labels them as "ATI Radeon HS 5700 Series."  During my ubuntu setup, I think I used the amdconfig command, not the aticonfig.

I've attached a screen shot of the windows properties of the video card for reference.

[ATTACH=CONFIG]259346[/ATTACH]

---

### Post by QIII on 2015-01-19
AMD bought ATI.  The aticonfig command has been deprecated, so amdconfig is the one now.

A thought:  could you post the contents of etc/X11/xorg.conf?

It doesn't exist by default, but should be created when you install the fglrx driver.

---

### Post by Todd_Quillen on 2015-01-20
ect/X11/xorg.conf:

```
Section "Device"
    Identifier "Default Card 0"
    Driver "fglrx"
    BusID "PCI:3@0:0:0"
EndSection

Section "Device"
    Identifier "Default Card 1"
    Driver "fglrx"
    BusID "PCI:4@0:0:0"
EndSection


```

QIII, I really can't thank you enough for helping me with this.

---

### Post by QIII on 2015-01-20
Hmmm...

Is that all there is?

---

### Post by Todd_Quillen on 2015-01-20
Yeah... that's all there is.  Did I do something wrong during my setup to cause such a minimalist xorg?

---

### Post by Todd_Quillen on 2015-01-20
For reference, I have a couple of other xorg.conf files that I assumed were back ups (different names) when I was trying to setup everything based on that tutorial (obviously, I may have done something wrong).

Anyway, those other xorg.conf files are:

xorg.conf.01102015:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:3:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

xorg.conf.original-0:

```
# NOXORGCONFEXISTED: No X.org configuration file existed when this backup was created.


```

---

### Post by QIII on 2015-01-22
Still mulling this and doing some research.

With any luck, someone else will be along before it takes me too long.  :)

Another thought:  Do you have the cards linked with a Crossfire cable?

---

### Post by Todd_Quillen on 2015-01-22
No problem, I just really appreciate the effort.  No, the cards are not connected with the crossfire cable.

---

### Post by Todd_Quillen on 2015-01-24
So I spent a few hours on this today uninstalling the drivers, installing new ones directly from AMD, and trying a ton of different xorg.conf configurations... to no avail.  I've got three monitors working with the default ubuntu drivers, so I'll stick with that for now.  The fourth monitor is showing up in the settings, but it stays black for reason.

Anyway, thanks for the time you put into this QIII.

---

