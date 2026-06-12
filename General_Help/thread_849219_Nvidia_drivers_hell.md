---
title: "Nvidia drivers hell"
date: 2008-07-04
forum: General Help
---

### Post by dchurch24 on 2008-07-04
Hi,

I had my system up and running just fine, and then I saw a youtube video of someone with a really nice skin and widgets.

I installed Emerald, changed Compiz to look at Emerald, made some changes and all was fine.

This morning I installed VirtualBox - it didn't work at first and told me to install some libraries. This I did.

Then I received notification that I needed a system restart. 

I restarted.

Since then, I have both my screens in 800x640 mode - and the Nvidia drivers are now missing from the restricted driver management screen.

I'm sure that if I can just get them listed in there once again I can sort this out.

I am running Hardy 64 with a nVidia GeForce 7600 GS.

Like I say, I know this is fine as it was working perfectly before this morning's reboot.

I uninstalled nVidia-GLX-New completely, and then reinstalled, rebooted, and still they are not listed.

Any ideas on how to get the nVidia drivers listed in the restricted drivers manager once again.

---

### Post by Tomatz on 2008-07-04
Try this:

```
sudo apt-get remove --purge nvidia-glx-new && sudo apt-get install nvidia-glx-new
```


**Reboot**


Hope that helps ;)

---

### Post by dchurch24 on 2008-07-04
Have done - but remotely using Putty from work - I won't know the results until I get home!

Thank you for the incredibly quick reply!

I only have 5 hours to wait to see if it worked ;-)

---

### Post by Tomatz on 2008-07-04
> **dchurch24 said:**
> Have done - but remotely using Putty from work - I won't know the results until I get home!

Thank you for the incredibly quick reply!

I only have 5 hours to wait to see if it worked ;-)

Cool ;)

I will make sure i check back later.

---

### Post by dchurch24 on 2008-07-04
Here's my xorg.conf file:

```


Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection


```

---

### Post by Kevbert on 2008-07-04
This is my device driver info (xorg.conf) on Gutsy:
```
Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:5:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
```
Hopefully this is of some use.

---

### Post by dchurch24 on 2008-07-04
Excellent - thank you. I will add that into the conf file, and see what happens when I get home!

---

### Post by overdrank on 2008-07-04
> **dchurch24 said:**
> Excellent - thank you. I will add that into the conf file, and see what happens when I get home!

HI and you may try and add that but most likely it will not help. More than likely you installed something for the kernel for VB and this conflicted with the nvidia drivers. Do you know what exactly you installed for VB because this may have removed something for the restricted drivers. This happened to me once.

---

### Post by Tomatz on 2008-07-04
> **overdrank said:**
> HI and you may try and add that but most likely it will not help. More than likely you installed something for the kernel for VB and this conflicted with the nvidia drivers. Do you know what exactly you installed for VB because this may have removed something for the restricted drivers. This happened to me once.

Also have you done any kernel upgrades recently? The kernel may have been auto upgraded for the vbox kernel modules.

Either way purging and reinstalling the drivers should fix the issue ;)

---

### Post by dchurch24 on 2008-07-04
Actually, this machine very, very rarely gets switched off. I think the last time it was switched off was when we moved house about 3 months ago.

I do remember doing an apt-get update - it could have been a week or just a couple of days ago.

I installed VB through Synaptic - and all the associated libs.

I'm may even have done an update since then, although I can't think why I would have done this.

I did purge and reinstall the drivers this morning - the only difference being that I uninstalled them using apt-get remove --purge and reinstalled them using Synaptic.

That didn't work sadly, so I renamed my xconf file and then I got a decent resolution in only the right-hand monitor. I checked to see if the drivers were present in the restricted driver manager and they were still not there, so I removed and added again using Synaptic - rebooted, and then went straight back to 640x480 (or whatever the bare minimum was/is).

---

### Post by Tomatz on 2008-07-04
> **dchurch24 said:**
> Actually, this machine very, very rarely gets switched off. I think the last time it was switched off was when we moved house about 3 months ago.

I do remember doing an apt-get update - it could have been a week or just a couple of days ago.

I installed VB through Synaptic - and all the associated libs.

I'm may even have done an update since then, although I can't think why I would have done this.

I did purge and reinstall the drivers this morning - the only difference being that I uninstalled them using apt-get remove --purge and reinstalled them using Synaptic.

That didn't work sadly, so I renamed my xconf file and then I got a decent resolution in only the right-hand monitor. I checked to see if the drivers were present in the restricted driver manager and they were still not there, so I removed and added again using Synaptic - rebooted, and then went straight back to 640x480 (or whatever the bare minimum was/is).

Open a terminal and run:

```
gksu nvidia-settings
```

Select the appropriate screen resolution then let nvidia-settings rewrite your xorg.conf.

Reboot

Hopefully xorg will be configured correctly now ;)

---

### Post by dchurch24 on 2008-07-04
Will do - thank you (again!)

I can't do that until I get to the machine (obviously) - and I've just been told my lift home has let me down too! :-( Could be bloody days before I can use this machine again!

I'll give that a go when I get in.

I wonder what caused it to do this? I have installed so much since the last reboot that it could literally be anything.

---

### Post by dchurch on 2008-07-04
Hi guys,

tried all of that, but no go.

Still sitting here with massive resolution with no Nvidia drivers listed.

Completely lost now. I was hoping to get away without a complete reinstall.

My GF is now on my case about installing Windows, and to be honest, I just don't think I can bear doing that. I've just got used to thing working without having to struggle.

---

### Post by dchurch on 2008-07-05
This is really odd.

I ran the above command, and something opens too quick for me to see what it is - the closes again.

...but, now the Restricted Driver Manager has gone from my System menu.

Looking at it, it seems that VB installed a load of kernal updates - I have uninstalled VB and assoc. libs, but still I can't install nVidia drivers.

Help!! Please! I'm lost!

---

### Post by dchurch on 2008-07-05
Hmmmm...

If I do a modprobe I get this:

```

modprobe nvidia
FATAL: Error running install command for nvidia

```

So, presumably the drivers are not installed. When checking Synaptic, they are marked as if they are installed. After a remove and reinstall, I get the same results.

---

### Post by tenmoi on 2008-07-05
Post your /var/log/xorg.0.log and nvidia-installer.log and xorg.conf

but first of all your should do this:

sudo apt-get update && upgrade

reboot

sudo dpkg-reconfigure --phigh xserver-xorg ## this is to get back your original xorg.conf.

sudo apt-get remove --purge nvidia-* linux-restricted-modules*

sudo apt-get install nvidia-* linux-restricted-modules*

log out then log in to see if it works.

IF NOT,

Download the nvidia driver consistent with your video card and linux architecture (32 or 64 bit)

sudo apt-get remove --purge nvidia-* linux-restricted-modules*
sudo apt-get install build-essential libxft-dev.

3. Ctrl + ALt + F1

4. sudo /etc/init.d/gdm stop

5. sudo sh /path to your file .run

6. ok/accept.

7. sudo /etc/init.d/gdm restart.

That's all there is to it.

---

### Post by Tomatz on 2008-07-05
You could try using envyng to automatically download and install the latest nvidia drivers:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It's a strange problem :confused:




**@tenmoi**
[B]
sudo dpkg-reconfigure --phigh xserver-xorg[/B] is defunct as of hardy (for graphics anyway). You now have to use the screens and graphics app ***gksu displayconfig-gtk***.

---

### Post by dchurch on 2008-07-05
Hi guys,

Thanks for the replies (again! ;-) )

I did this:

I renamed the xorg.conf file to .bak (just in case), then:

I installed the Restricted Driver Management (RDM) prog through Add/Remove programes.

Then:

sudo rm -f /lib/linux-restricted-modules/.nvidia_new_installed

sudo apt-get install nvidia-kernel-common

sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx

Then the drivers appeared in the RDM, I clicked to enable the nVidia drivers, and then it downloaded the "-new" nVidia drivers and replaced the glx ones.

I then rebooted, and hey presto! I had a decent resolution and the nVidia drivers were being used - only on one screen though.

No problem, : sudo apt-get install nvidia-settings

Ran the nvidia config prog, and then set up the second screen - all worked fine! 

..apart from I can only get it to span across both screens - I can live with that, but I used to have it against 2 screens but when you maximised a window it would only maximise to the screen I was in, now it maximises again both, which is a little annoying.

Also, after enabling Compiz the cube is across both screens wheras before it was a seperate (cloned) cube in each.

Hey ho! I can live with that, and will slowly get to grips with Compiz and work out why the cube zoom is so slow!

Thanks for your help guys - you really are diamonds!

---

### Post by Tomatz on 2008-07-05
> **dchurch said:**
> Hi guys,

Thanks for the replies (again! ;-) )

I did this:

I renamed the xorg.conf file to .bak (just in case), then:

I installed the Restricted Driver Management (RDM) prog through Add/Remove programes.

Then:

sudo rm -f /lib/linux-restricted-modules/.nvidia_new_installed

sudo apt-get install nvidia-kernel-common

sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx

Then the drivers appeared in the RDM, I clicked to enable the nVidia drivers, and then it downloaded the "-new" nVidia drivers and replaced the glx ones.

I then rebooted, and hey presto! I had a decent resolution and the nVidia drivers were being used - only on one screen though.

No problem, : sudo apt-get install nvidia-settings

Ran the nvidia config prog, and then set up the second screen - all worked fine! 

..apart from I can only get it to span across both screens - I can live with that, but I used to have it against 2 screens but when you maximised a window it would only maximise to the screen I was in, now it maximises again both, which is a little annoying.

Also, after enabling Compiz the cube is across both screens wheras before it was a seperate (cloned) cube in each.

Hey ho! I can live with that, and will slowly get to grips with Compiz and work out why the cube zoom is so slow!

Thanks for your help guys - you really are diamonds!

Sounds like you fixed the issue yourself, which is great! :)

If you mark the thread as solved others will benefit from your solution.

---

### Post by dchurch on 2008-07-05
I will do - I just have to wait until I get back to work - numbnuts here forgot his password for the dchurch24 account which is the one I started the thread with. On my work machine it has the password saved, so I can log in!

Thanks again for your help - I'm just playing around with it now to see if I can get it back to 2 screens instead of one huge one across both monitors.

I'm really chuffed I got this working; my GF was going on about reinstalling Windows ("we didn't have these problems in Windows you know, blah, blah" - no, we had a lot more problems!), and I really don't think I could stomach going backwards - I've got too used to things just working as they ought to to do that.

---

### Post by Tomatz on 2008-07-05
> **dchurch said:**
> I will do - I just have to wait until I get back to work - numbnuts here forgot his password for the dchurch24 account which is the one I started the thread with. On my work machine it has the password saved, so I can log in!

Thanks again for your help - I'm just playing around with it now to see if I can get it back to 2 screens instead of one huge one across both monitors.

I'm really chuffed I got this working; my GF was going on about reinstalling Windows ("we didn't have these problems in Windows you know, blah, blah" - no, we had a lot more problems!), and I really don't think I could stomach going backwards - I've got too used to things just working as they ought to to do that.

Yeah my gf was like that but now she wont even go near windows :) Create your gf an account with a pink theme and a wallpaper with a kitten on it. Women are suckers for kittens and pink things.

:lolflag:

---

