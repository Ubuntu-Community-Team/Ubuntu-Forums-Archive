---
title: "Can't install anything..."
date: 2007-08-22
forum: General Help
---

### Post by icehammer on 2007-08-22
I'm using Feisty, which i downloaded yesterday.. After finally getting through the screen resolution issue..  But there's a list of more problems i came across:

I used Automatix to download Google Earth.. It installs successfully. but when i try to run it.. The splash screen comes, and then everything blacks out.. the console shows up with a list of stuff.. The GUI comes up again for 2 seconds, and all of a sudden i'm logged out.., and i have to login again..

The same happens when i try to install wine...

How do i correct this problem?

---

### Post by g2g591 on 2007-08-22
I'm sorry but automatix isn't supported see [here]("http://ubuntuforums.org/announcement.php?f=13"),and [here]("https://help.ubuntu.com/community/Automatix").(please read both)   I recommend you uninstall it. You can just download and reinstall google earth from google's site. Here's a howto install google earth [here]("https://help.ubuntu.com/community/GoogleEarth")

---

### Post by forrestcupp on 2007-08-22
It's probably not an Automatix problem.

Do you have Compiz or Beryl running?  Sometimes opengl apps don't work well with those running, especially Compiz/Fusion.  Try ```
metacity --replace
``` then try running it.

---

### Post by sumguy231 on 2007-08-22
> It's probably not an Automatix problem.
Probably not, but it's still good advice to avoid it.

---

### Post by icehammer on 2007-08-23
I uninstalled Automatix, and also tried installing google earth directly from the google site.. but still no go..

Should i reinstall ubuntu again?

---

### Post by sumguy231 on 2007-08-23
I don't think the problem lies with Google Earth, I would guess it's a video driver thing or something. Try running 'glxgears' and see if the same thing happens.

---

### Post by icehammer on 2007-08-23
Yup.. running 'glxgears' does the same thing..
what does this mean??

---

### Post by sumguy231 on 2007-08-23
It's got to be some problem with X, and I'm guessing it has to do with video drivers.

What kind of video card do you have, and are you using proprietary drivers for it? Could you look at the /etc/X11/xorg.conf file and find what's listed under the line that says "Driver"?

---

### Post by icehammer on 2007-08-24
Well, i couldn't find anything which says "Driver".. but this what i think may meet the requirements:

```
Section "Device"
	Identifier	"3Dfx Interactive, Inc. Voodoo 3"
	Driver		"tdfx"
	BusID		"PCI:1:0:0"
EndSection

```

Lemme knw if u need the complete xorg.conf file...
Thanks..

---

### Post by sumguy231 on 2007-08-24
Yeah, that's what I meant. I assume that is the correct info for your video card, right? I've never dealt with Voodoo cards or older cards like that, so I don't think I can help much there. 

By the way, you can probably find out what the actual error it's throwing is if you look at /var/log/Xorg.0.log.

---

### Post by john8791 on 2007-08-24
> **sumguy231 said:**
> Probably not, but it's still good advice to avoid it.

I disagree.  I have used Automatix to install Google Earth, Picasa, ntfs-3g driver with great success.  The problem is probably a video driver or X11 configuration problem.

---

### Post by GSF1200S on 2007-08-24
Try going into Synaptic and searching for Nvidia. Your looking for video drivers that are called glx something. Its not glx or glx-new.. its like glx-classic or something. Install that, and do a reboot. 

Your screen goes screwy because you dont have 3d acceleration. You just need to use synaptic to get the drivers and then google earth should work fine..

Maybe someone else can tell you what the drivers are called- I cant remember and Im on windows (trying to get a nice lean kde core install going).

Good luck! :)

---

### Post by john8791 on 2007-08-24
> **GSF1200S said:**
> Try going into Synaptic and searching for Nvidia. Your looking for video drivers that are called glx something. Its not glx or glx-new.. its like glx-classic or something. Install that, and do a reboot. 

Your screen goes screwy because you dont have 3d acceleration. You just need to use synaptic to get the drivers and then google earth should work fine..

Maybe someone else can tell you what the drivers are called- I cant remember and Im on windows (trying to get a nice lean kde core install going).

Good luck! :)

I have had great luck using "Envy" to install Nvidia drivers on a couple different computers.  It was absolutely painless.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by sumguy231 on 2007-08-25
> **GSF1200S said:**
> Try going into Synaptic and searching for Nvidia. Your looking for video drivers that are called glx something. Its not glx or glx-new.. its like glx-classic or something. Install that, and do a reboot. 
If that person's Xorg.conf file is right, they're using a Voodoo card meaning the Nvidia drivers wouldn't help much.

> Your screen goes screwy because you dont have 3d acceleration. You just need to use synaptic to get the drivers and then google earth should work fine..
Actually, in my experience if glx is not loaded or if the card doesn't support it apps which need to use it just refuse to load. I've never seen it crash X.

> I disagree. I have used Automatix to install Google Earth, Picasa, ntfs-3g driver with great success. The problem is probably a video driver or X11 configuration problem.
I have no doubt that it worked ok for you. But a member of the Ubuntu technical board recently released a report showing various haphazard things Automatix did that *could* lead to problems later on or in certain conditions. Read all about it:
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

