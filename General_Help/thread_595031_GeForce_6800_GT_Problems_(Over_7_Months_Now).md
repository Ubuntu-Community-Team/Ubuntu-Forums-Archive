---
title: "GeForce 6800 GT Problems (Over 7 Months Now)"
date: 2007-10-28
forum: General Help
---

### Post by Crafty Kisses on 2007-10-28
OK, so for the past 7 months now, I can't really use my NVIDIA GeForce 6800 GT, everytime I install the drivers, it's really weird, well here's some screenshots:
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-9.png[/IMG]
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-1-4.png[/IMG]
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-8.png[/IMG]
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-2.png[/IMG]

I'll gladly paypal anyone atleast like $30 if they can solve this, I've been dealing with this for over 6 months. This is only when I install the drivers though.

AMD Athlon 1800+
NVIDIA GeForce 6800 GT
40 GB HDD
1 GB of RAM

---

### Post by Crafty Kisses on 2007-10-28
Sorry for the bump. :(

---

### Post by Sunforge on 2007-10-28
My main system is an Intel based PC with an Aopen GeForce 6800 GT PCIE running Gutsy with the Ubuntu restricted drivers. I've experienced experienced no problems, ditto that for Feisty and Edgy. 

my xorg.conf file is pretty minimal too:

Section "Device"
    Identifier    "nVidia Corporation NV41.1 [GeForce 6800]"
    Driver        "nvidia"
    Busid        "PCI:1:0:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "PLH511S"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV41.1 [GeForce 6800]"
    Monitor        "PLH511S"
    Option "ModeValidation" "NoDFPNativeResolutionCheck"
    Defaultdepth    24
    SubSection "Display"
            Modes        "1600x1200"    "1280x1024"    "1280x960"    "1152x864"    "1024x768"    "832x624"    "800x600"    "720x400"    "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
EndSection
Section "Module"
    Load        "glx"
EndSection

I can't think that any of the above is of any great help but I'm wondering if it's worth searching for 6800 problems that are specific to the manufacturer of your card.

---

### Post by Zigi15 on 2007-10-28
I don't exatly know if this will work for you, but it did for me. I just couldn't install drivers for my Nvidia GeForce 8500 GT. There were none, because they were yet unsupported by ubuntu. If you have a driver problem, this should solve it (it did for me, anyway).

Then came my saviour: ENVY. Try (on a fresh copy) installing your graphics drivers with envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download the .deb and install it. Run it from ubuntu and use "install nvidia drivers" NOT MANUALLY. This shoul automatically install the official nvidia drivers from the nvidia site.

But, have you made sure the problem isn't in the card itself?

---

### Post by Crafty Kisses on 2007-10-28
> **Zigi15 said:**
> I don't exatly know if this will work for you, but it did for me. I just couldn't install drivers for my Nvidia GeForce 8500 GT. There were none, because they were yet unsupported by ubuntu. If you have a driver problem, this should solve it (it did for me, anyway).

Then came my saviour: ENVY. Try (on a fresh copy) installing your graphics drivers with envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download the .deb and install it. Run it from ubuntu and use "install nvidia drivers" NOT MANUALLY. This shoul automatically install the official nvidia drivers from the nvidia site.

But, have you made sure the problem isn't in the card itself?

Yeah, I've tried Envy it didn't work. I think it's just Video Buffer Overflow, which sucks, that probably means I need a new Motherboard. Thank God Christmas is right around the corner. :)

---

### Post by Caffeine_Junky on 2007-10-28
This trully  needs to be resolved.  

I assume you have tried all the methods for installing the drivers?...

Envy,  Restricted manager in Ubuntu,  Command-line with the driver from nvidia web site?.

This has got me stumped, and I am sorry I have no answers for you at the time of this post, ...but I am going to google the S**t out of this!

I have an On-board GeForce 6100 (same series as yours ...6) and I have not had a problem like I see in your screen shots.

I will be keeping an eye on this thread mate, and if only to keep bumping it to keep it alive, 

In the mean time I will see what I can find out and if I have any suggestions I will keep you posted...

Good luck!

ps: I am not interested in your money,  I just want to see this fixed.

Bump!

edit:  I was a bit slow posting

---

### Post by Crafty Kisses on 2007-10-28
> **Caffeine_Junky said:**
> This trully  needs to be resolved.  

I assume you have tried all the methods for installing the drivers?...

Envy,  Restricted manager in Ubuntu,  Command-line with the driver from nvidia web site?.

This has got me stumped, and I am sorry I have no answers for you at the time of this post, ...but I am going to google the S**t out of this!

I have an On-board GeForce 6100 (same series as yours ...6) and I have not had a problem like I see in your screen shots.

I will be keeping an eye on this thread mate, and if only to keep bumping it to keep it alive, 

In the mean time I will see what I can find out and if I have any suggestions I will keep you posted...

Good luck!

ps: I am not interested in your money,  I just want to see this fixed.

Bump!
I really appreciate this man. Yeah I've tried everything, command line installation, Envy and Restricted Drivers Manager. I appreciate all the help I'm getting and I have to give you something man, if I don't I feel bad haha, but seriously I really appreciate the help, and it's people like you man that make the Ubuntu community what it is. :KS

---

### Post by CarlAdam on 2007-10-28
does the problem remain if you turn compiz off? I have a 6800 GT and do not experience this problem...

---

### Post by Crafty Kisses on 2007-10-28
> **CarlAdam said:**
> does the problem remain if you turn compiz off? I have a 6800 GT and do not experience this problem...

I don't even have any desktop effects on when this occurs.

---

### Post by CarlAdam on 2007-10-28
hmm... very strange, do you have a clean (new) installation of ubuntu (gutsy?)? or did you upgrade, i have bad expirences with distupgrading...

---

### Post by Crafty Kisses on 2007-10-28
> **CarlAdam said:**
> hmm... very strange, do you have a clean (new) installation of ubuntu (gutsy?)? or did you upgrade, i have bad expirences with distupgrading...

I have a clean installation of Feisty, but again I think it's my Motherboard. :(

---

### Post by CarlAdam on 2007-10-28
Yeah, could be...you should try too boot another distro from a usb-stick or a live-cd before wasting your money though:)

---

### Post by Crafty Kisses on 2007-10-28
> **CarlAdam said:**
> Yeah, could be...you should try too boot another distro from a usb-stick or a live-cd before wasting your money though:)

I might try booting into Gentoo or something, but Ubuntu and Mint are giving me troubles as of now.

---

### Post by Sunforge on 2007-10-28
It's been a while since I've come across a dud motherboard, although normal experience on my part are shutdown/startup or random freezes rather than a single specific fault.

If you're experiencing similar video corruption in Ubuntu as in other OS's then does your motherboard have a built in video card? If it does, is it possible to remove your GeForce 6800 and default back to the built in? If you can - do you still experience problems?

---

### Post by Crafty Kisses on 2007-10-28
> **Sunforge said:**
> It's been a while since I've come across a dud motherboard, although normal experience on my part are shutdown/startup or random freezes rather than a single specific fault.

If you're experiencing similar video corruption in Ubuntu as in other OS's then does your motherboard have a built in video card? If it does, is it possible to remove your GeForce 6800 and default back to the built in? If you can - do you still experience problems?

I'll try that.

---

