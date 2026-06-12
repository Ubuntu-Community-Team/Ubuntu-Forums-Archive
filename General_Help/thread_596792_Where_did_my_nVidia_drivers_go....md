---
title: "Where did my nVidia drivers go..."
date: 2007-10-29
forum: General Help
---

### Post by Kaji on 2007-10-29
Hokay, I was restarting my computer earlier today, yadda yadda.

When my computer booted up, ubuntu had secretly changed itself into a "low graphical mode"  (or something to that affect.)

Well, I was a little concerned, just having my installation working perfectly.

So when the "low graphic mode" error box told me to Configure... I decided, why not? Well I open it up, and only notice one screen available (i WAS running Dual Monitors) So I changed that screen (Screen 1 I believe) to a healthy resolution and rebooted.

When I rebooted, the login screen came up VERY VERY distorted, as in, half the screen looked like the american flag, the other half looks like the Burrito Place during lunch hour. So I got onto my secondary computer, typed in some stuff, and ran

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

In Cntrl + Alt + F2 mode

I go through the reconfiguration again, changing my resolution... AGAIN, Ctrl+Alt+Dlt to reboot.

ubuntu loads up, but the monitors are mirroring eachother, which I do not want. So I diddle my way to terminal, and I command:
```
gksudo nvidia-settings
```

Only for nvidia-settings to tell me:
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 


So I run 
```
gksudo nvidia-xconfig
```

And this Just restarts my problem, so I have to go through the whole process again, but this time I knew something was wrong.

So I opened Restricted Drivers Manager, just incase the nVidia drivers were deleted... or something. Only to have Restricted Drivers Manager tell me:
> You need to install the package

  linux-restricted-modules-2.6.22-14-server

for this program to work.

So I'm like... what? Ok, I head over to my closest Synaptic, and search for linux-restricted... not finding anything ending with server here.


So In resolution... what do I do?

---

### Post by Kaji on 2007-10-30
Can anyone help at all? I am so lost, just installing ubuntu a few days ago.

Thanks in advance,
Kaji.

Edit: seems my sound drivers are whacked aswell....

---

### Post by Maestro23 on 2007-10-30
Linux Restricted is available.  Make sure the Proprietary drivers for Devices (Restricted) is checked.

System>>Admin>>Software Sources

---

### Post by Kaji on 2007-10-30
Propietary drivers for Devices (restricted) is checked currently.

Reinstalling all of the Linux Restricted packages did nothing...
Thanks,
Kaji

---

### Post by Kaji on 2007-10-30
Bumping up from last night...

Does anyone have a solution for this?

---

### Post by ChuckL on 2007-10-30
I have a similar issue. I have a Dell 2007WFP monitor and had to go through hoops to get it to work properly. I used Envy to install the nvidia drivers which allowed me to get higher and appropriate resolution but I get the message that you reported about not using the NVIDIA X driver. When I ran nvidia-xconfig and restarted I got the low res' screen. I subsequently reran Envy again which rebuilt my xorg.config file and now I have my screen back to the appropriate resolution, etc. but I still get the message when I run the Nvidia Settings app. The Advanced Desktop Settings options don't work as well. So like you if anyone has a suggestion please...!

---

### Post by Kaji on 2007-10-30
> **ChuckL said:**
> I have a similar issue. I have a Dell 2007WFP monitor and had to go through hoops to get it to work properly. I used Envy to install the nvidia drivers which allowed me to get higher and appropriate resolution but I get the message that you reported about not using the NVIDIA X driver. When I ran nvidia-xconfig and restarted I got the low res' screen. I subsequently reran Envy again which rebuilt my xorg.config file and now I have my screen back to the appropriate resolution, etc. but I still get the message when I run the Nvidia Settings app. The Advanced Desktop Settings options don't work as well. So like you if anyone has a suggestion please...!
Finally! Someone with a problem like mine, (though not exactly the same.) Just wondering, 
Weird, Xconfig actually worked for you.

Any solutions would be fabulous,

Thanks,
Kaji.

---

### Post by ge5239 on 2007-10-30
..and one more with the problem here.. 
installed myself with betadriver from nvidia.com, latest stable from nvidia.com, via envy, via apitude. 
it just doesnt help and nvidia-settings wont work! 
poor us, atleast you got yourself a little bump :)

---

### Post by Kaji on 2007-10-30
Ok, I got half of this working.

I went into Synaptic and downloaded the nvidia-settings repository, It doesn't sa> 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

When I run gksudo nvidia-settings.. but it does say this (outcome in terminal)
```
(gksudo:6012): Gtk-WARNING **: Theme file for OSX_Cursors_v0.2 has no directories


** (gksudo:6012): WARNING **: Invalid borders specified for theme pixmap:
        /home/kaji/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image
ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.
```

Could this be leading onto something?

I still get the "i need to install the repository that doesn't exist" error when I try and run restricted drivers.

---

### Post by brunocf on 2007-10-30
Same problem for me. After a simple reboot the same problem happened and the same package is asked for. And I couldn´t find such file.

linux-restricted-modules-2.6.22-14-server

---

### Post by Kaji on 2007-10-30
Is there no solution to this?

---

### Post by Kaji on 2007-10-30
I really liked ubuntu, after switching to it from Vista. But this is just frustrating me, but I am trying to keep my cool. nVidia and sound drivers are not working. Is my only option to reinstall ubuntu? Please someone, just say "Lol ur screwed reinstall" or something, just so I can be certain there is no fix.

---

### Post by Kaji on 2007-10-30
Well, if no one knows a solution, I really hope some solution can fix this bug, sometime in the near future. Im off to reinstall.

---

### Post by tj111 on 2007-10-30
I'm having a similar problem.  After selecting nvidia-glx in the restricted drivers manager, I get a "failed to load glx" error.  I have to go into the xorg .conf, change the driver to "vesa", then reboot again.  I've reinstalled xserver and the driver, but still have no luck.

---

### Post by sliPrix on 2007-10-31
I am having the exact same problem! Every time I reboot my system, the Low-Resolution prompt comes up asking me to configure it.  I have reinstalled the NVidia driver straight from their site a few times, all resulting in the same set of problems. Has anybody found anything to solve this, or a workaround yet?  Thanks in advance.

---

### Post by sliPrix on 2007-10-31
Last night I finally got everything installed, and working after a reboot.  I found that the new version of "Envy" supports Gusty.  I installed Envy with errors regarding dependencies.  Sorry I didn't record what the errors were exactly, at that point I wasn't thinking anything would work and just wanted to get my drivers installed.  Anyways, I ran envy, however while starting that Synaptic came up with a message stating "You have a broken package" or something along those lines.  I ignored this and switched to the Envy window.  It prompted me to download the missing files, to which I accepted.  After a few minutes, I was able to select "Install Nvidia drivers."  The program ran fine, I rebooted when it was done, lo and behold, my Nvidia drivers were working!  Synaptic also no longer says that Envy is broken.  I hope this helps, and that your Envy install goes more smoothly than mine.  Good luck!

---

### Post by xanthmode on 2007-11-01
I ran into the exact same problem today.  Couldn't find the package linux-restricted-modules-2.6.22-14-server anywhere.  I installed linux-restricted-modules-2.6.22-14-generic instead and did 

```
sudo dpkg-reconfigure xserver-xorg
```

Ran through the whole configuration and now it was detecting my nvidia hardware.  Restarted X afterwards and everything works now.  Still can't get into the Restricted Drivers Manager though.

---

### Post by shellex on 2007-11-01
Alright, I had the same problem, but solved it. Don't think I know what I'm talking about in the following.
I must have installed a package which had the Linux Kernel server-edition as a dependency. So it got installed and messed with the generic kernel.
Go into the package manager of your choice and remove linux-image-2.6.22-14-server and reinstall linux-image-2.6.22-14-generic. It's going to override your boot settings and stuff, but everything will be normal after that.
The restricted driver manager obviously took the ending of the kernel module ("server") and looked for an appropriate package, which does not exist.
I hope this solved the problem for you all.

Greetz.

---

