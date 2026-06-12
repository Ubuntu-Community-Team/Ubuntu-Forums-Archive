---
title: "Enable NVIDIA Portrait Mode?"
date: 2008-06-07
forum: General Help
---

### Post by nsivin on 2008-06-07
I am using an NVIDIA GeForce 6200 TurboCache graphics card (two years old) on a desktop with an AMD 4200+ 64-bit CPU and a Samsung Syncmaster 960B LCD monitor, which I always operate in portrait mode. I previously used Ubuntu 7.10. Thanks to the Forums, I downloaded an NVIDIA driver, and set “rotate left” as an option under System, Preferences, Resolution. An alternative was the terminal command “xrandr -rotate left.”

About two weeks ago I deleted the old Ubuntu and did a fresh install of Hardy. I was prompted to download and install the proprietary NVIDIA driver, which I did. When I tried to rotate the monitor mode to portrait, there was no way to do that on the menu (now System, Preferences, Sessions). 

The xrandr command also did not work. I checked the manual, which said the command is now “xrandr --output --rotate left”. But that doesn’t do anything, nor does “xrandr --rotate left”. 

Does anyone have any idea about the new procedure for rotation?

---

### Post by nsivin on 2008-06-22
With a couple of helpful hints from other members, I finally figured it out. It is much simpler than in 7.10:

NVIDIA Drivers are automatically installed in v. 8.04.
To rotate, in System, Preferences, Screen Resolution dialog set Rotation to Left.
If the window does not offer any rotation option, do 
	Sudo gedit /etc/X11/xorg.conf
Replace “nv” with “nividia” if necessary. Then add this line to the same “Device” section
	Option	“RandRRotation” “on” (quotes needed)

---

### Post by sendtoscott on 2008-06-22
Rotation isn't working for me on my Gateway 5056.

Graphics Adapter: NVIDIA GeForce 6100
Screen Area/Colors: 1280x1024 pixels, 16 million colors
Monitor: SyncMaster 970P,SyncMaster Magic CX912P(Analog)

I have the latest driver from Nvidia

 NVIDIA-Linux-x86-173.14.05-pkg1.run

And I've attached my xorg.conf (most of which came off a site that I hope was right, but since the explanation was in Russian, I had go hope for the best).  I can't get a rotation option on my screen prefs, and xrandr gives me:

 xrandr -o left
'X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Any ideas?
Thanks.

---

### Post by nsivin on 2008-06-23
The XRANDR command doesn't work for me either. I have looked at your xorg.conf file. I see you haven't included the entry suggested above. You might want to try it.

---

### Post by sendtoscott on 2008-07-03
> **nsivin said:**
> The XRANDR command doesn't work for me either. I have looked at your xorg.conf file. I see you haven't included the entry suggested above. You might want to try it.

Did you mean RandRRotation?  It's there:

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nv"
    BoardName      "vesa"
    Screen          0
    Option "RandRRotation" "true"
    Option "Rotate" "left"
EndSection

---

### Post by nsivin on 2008-07-04
Look again at message #2. Why do you assume that "true" is the same as "on"?

---

### Post by sendtoscott on 2008-07-04
> **nsivin said:**
> Look again at message #2. Why do you assume that "true" is the same as "on"?

Because I've seen both used and have tried both at one time or another.

---

### Post by raywood on 2008-07-15
If anybody has a minute, I'm afraid I'm not fluent in Ubuntu.  I'd like to rotate my monitor and I'm not getting any option other than "Normal" in the System > Preferences > Screen Resolution dialog in 8.04.  Thanks!

---

