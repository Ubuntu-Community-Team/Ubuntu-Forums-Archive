---
title: "nvidia/xorg problems"
date: 2006-11-24
forum: General Help
---

### Post by stealth_kid on 2006-11-24
hi, i'm new to ubuntu and i have some problems that i do not know how to solve. to put it in one sentence: nvidia drivers makes xorg freeze. first i tryed with ubuntu 6.06 and all of the methods described on this forum (apt-get/synaptic, a script called envy, compiling the drivers from nvidia web site). then i did a fresh install of 6.10 and tryed again to install the drivers. no matter which way i do it, when i tell the system to use nvidia drivers instead of the default nv xorg freezes. these are the hardware specs: an old soltek motherboard with via chipset and agp 4x support (i do not remember the exact model but i can look it up if necessary), athlon xp 1700+ CPU, nvidia geforce fx 5700 agp 8x. i'm using ubuntu 6.10 with the default kernel. the only drivers that do not make the computer freeze are the 9629 which i installe followinh [these]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29") steps. but i cannot run any application that uses hw acceleration. if i open a console and run "glxgears" i get a black window (only once in a while i see the spinning gears) that stays open for a few seconds and then closes without any error. the only thing that i see in the console is the word "aborted" without any more explanations. same goes for other apps: google earth, blender, maya, wings3d. they all open, wait a bit then close themselves. if anyone can help, please do because i ran out of patience :-? .

---

### Post by catanzag on 2006-11-24
did you noticed some errors or warnings (lines starting with (EE) or (WW) respectively) in /var/log/Xorg.0.log file? if you post here, somebody could help you finding what is wrong

regards

---

### Post by stealth_kid on 2006-11-24
there are some errors... i'm new to linux so i'm not sure what they mean and how they can be fixed. should have thought by myself to post them, silly me. i post as attachments the log file and the xorg.conf. thanks for the reply.

---

### Post by catanzag on 2006-11-24
the only errors in the log are referred to the non existence of /dev/wacom device; you can either comment out the lines in xorg.conf of the three InputDevice sections with the wacom device, something like this

```

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    #Identifier     "stylus"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "stylus"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    #Identifier     "eraser"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "eraser"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    #Identifier     "cursor"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "cursor"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

```

or regenerate the file with

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

by the way, please note that 9629 (the log is referred to it) has some documented bugs with some old card (see [http://www.nvnews.net](http://www.nvnews.net)) maybe this is not your case, but probably is better to test nvida driver first with released Ubuntu package (8776 I suppose)

hope this can help you

---

### Post by stealth_kid on 2006-11-25
i know 9629 drivers are buggy but so far it's the only version that does not make xorg freeze. i tryed other versions, even the legacy drivers and when gdm starts i have just enough time to enter the username and half of the password before the system freezes. 
anyway, i tryed comenting those lines in xorg.conf as you sugested and when i restart gdm i get an error like *Data incomplete in /etc/X11/xorg.conf. Undefined InputDevice "stylus" referenced by ServerLayout "Default Layout"*. i also ran the command *dpkg-reconfigure -phigh xserver-xorg* and it creates the same lines reffering to a wacom tablet. and i don't have one. i have a usb mouse. could that be the cause of all these troubles?
thanks for taking the time to help me. i installed ubuntu about 10 days ago thinking to give up windows and the only problem so far is the video drivers.

---

### Post by depu on 2006-11-25
dpkg-reconfigure -phigh xserver-xorg creates all those lines by default u use them or not.
what i think catanzag meant was that you should comment out all the lines that refer to the wacom device.
so comment out the following lines in ServerLayout and or default layout

    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"

Hope that this helps
ps: no its not the mouse

---

### Post by catanzag on 2006-11-25
Yes, depu, thank you for the correction, sorry stealth_kid for the mistake, I was in hurry before going out and forgot to point out that all the referring lines should be commented out too.

I've a usb mouse and I've no problem; but BTW, first time I installed Ubuntu I got problem with nvidia driver due a slight incompatibility, I mean, I took all the files from installation DVD and 8774 didn't work with default 386 kernel, but legacy worked, while with 686 kernel 8774 works fine: do you have some misalignment of packages? You could try another kernel or update everything with

```

apt-get update
apt-get upgrade
```

before trying again to solve video problems.

---

### Post by InsomniacUK on 2006-11-25
I seem to get told off when I suggest this, but it worked for me. Boot into recovery mode, edit xorg.conf using nano. Change the video driver to say VESA. Reboot, and start as normal. Install Automatix2. Tell it to install the nVIDIA drivers. Reboot.

It worked for me. Worth a try maybe.

---

### Post by fragos on 2006-11-25
Use Synaptic to install nvidia-glx from the Ubuntu repositories.  It will give you 8776 which works fine with my FX5200.  I'm not sure newer versions make any difference with an older but still supported card like the FX5200.  My first choice for installs is Synaptic and I stick to Ubuntu repositories.  I don't have any of the problems that some seem to find.

---

### Post by stealth_kid on 2006-11-27
the first time i installed nvidia drivers was through apt-get. isn't it the same thing as with synaptic? it installed 8776 which made x server freeze instantly. i also tryed legacy drivers which worked a bit better, i mean it took approx 45 seconds untill it froze solid :mrgreen: . the only thing i did not try is 686 kernel... how do i install it and will it work with my athlon xp (isn't that for intel processors?)?

---

### Post by catanzag on 2006-11-27
As far as I know, aptitude, synaptic, adept and so on are all interfaces to apt-get command, so if no warning/error arise with one of them it's ok, it is the same to use any of the other ones.

I installed 686 versione as I have a Pentium 4M; of course it doesn't work with an AMD XP processor, which architecture should be k7.

---

### Post by fragos on 2006-11-27
I don't have a good answer on wheather apt-get and Synaptic yield the same results.  I have seen discusions on differences between apt-get and aptitude.   There is definately a difference between repositories and deb packages.  I believe that the best chance of getting a result consistent with the distrobution developers expectations is by using the tools and process they prefer.  Reading the posts of indiviuals with installation problems consistantly call the use the use of apt-get and frequently the use of different repositories.  I think this is particularly important during upgrades.  Perhaps not scientific but while favoring Synaptic, Ubuntu repositories and the "Ubuntu" recommended processes I have consistently successful outcomes.

---

