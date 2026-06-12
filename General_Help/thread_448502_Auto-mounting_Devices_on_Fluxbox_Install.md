---
title: "Auto-mounting Devices on Fluxbox Install"
date: 2007-05-19
forum: General Help
---

### Post by matt_risi on 2007-05-19
Hey guys, probably a quick and simple solution here, but it's been bugging me for a long time. I'm getting into minimal installs, usually involving me installing a command-line system from the ubuntu alternate install cd and then installing a window manager of choice (most always fluxbox and openbox). However one thing that is seriously hindering the overall usability of these systems is that they do not automatically mount

- CD's
- USB storage devices

Is there a package I'm to download for this to happen? I know that I can manually mount them, but that's a pain in the butt. Any ideas? 

Thanks guys.

---

### Post by Cene on 2007-05-19
I use gnome-volume-manager in Openbox for automounting. Try that.

---

### Post by matt_risi on 2007-05-19
I tried installing gnome-volume-manager and there was nothing to install, seems I already have it. Also just to be sure I tried putting in a music CD to see if it'd mount, but nothing. I checked /media/cdrom/ as well.

---

### Post by aysiu on 2007-05-19
Try adding *gnome-volume-manager* to the list of startup applications.

---

### Post by dolphin_oracle on 2007-05-19
i've used ivman to automount usb drives.  google ivman for info,  i think its in the repositories.

---

### Post by RedSquirrel on 2007-05-19
> **matt_risi said:**
> I tried installing gnome-volume-manager and there was nothing to install, seems I already have it. Also just to be sure I tried putting in a music CD to see if it'd mount, but nothing. I checked /media/cdrom/ as well.


If you already have it installed, add it to ~/.fluxbox/startup

```
gnome-volume-manager &
```

---

### Post by matt_risi on 2007-05-20
Well, that got me further than I've been before to achieving convenience with devices. USB drives mount automatically and show up in PCManFM, which is awesome. Any way to eject them easily, again preferably a GUI method. PCManFM has an eject button when you right-click on the device but error messages saying that it couldn't eject come up when you try to do so.

CD's still aren't mounting.

Also, is there an all-purpose manager for .deb files, like how in GNOME you can double-click on the .deb file and it will extract and compile the program for you? I recall something along the lines of GDebi, but not sure.

Thanks for your continued support!

---

### Post by Cene on 2007-05-20
I don't know if there is any GUI method to umount drives without nautilus, konqueror or so.. I might be wrong too, since i have never used many GUI programs, i prefer command line. :)
The normal command to umount a drive is umount /mnt/device or umount /media/device whereas device is the item you want to umount (usually cdrom0 for CD's and the name of the device for usb devices).
The gnome-volume-manager has always mounted cd's for me too... Do you have permissions to mount cd's without root access at /etc/fstab? gnome-volume-manager cannot do something it is not permitted to do.

The program to install .debs with a GUI is gDebi, but as far as i know, it requires some other gnome components to run. Again, don't keep my word as an absolete truth.

---

### Post by dolphin_oracle on 2007-05-20
the thunar file manager has a unmount option in its right click menu.  you might try that out.

---

### Post by RedSquirrel on 2007-05-20
> **matt_risi said:**
> Well, that got me further than I've been before to achieving convenience with devices. USB drives mount automatically and show up in PCManFM, which is awesome. Any way to eject them easily, again preferably a GUI method. PCManFM has an eject button when you right-click on the device but error messages saying that it couldn't eject come up when you try to do so.

CD's still aren't mounting.

Is this data CDs or music CDs? Data CDs should mount. You can't mount a music CD; the media is accessed directly, so a music CD probably wouldn't show up in pcmanfm. I haven't used nautilus in a long time, but I seem to recall that it would show music CDs when you inserted them. However, that doesn't mean they were "mounted"; it just means that nautilus could show the tracks the same way that xmms does. It is quite likely that pcmanfm doesn't have that full functionality.

I like to manually mount so I haven't played around with automounting all that much.

---

### Post by matt_risi on 2007-05-20
It was a music CD, data CD's are mounting okay. Any idea how I'd get a music CD to be accessible by audacious? Also, is there any simple way to change the background in Fluxbox? Any more feedback on the ejecting issue? Thunar's a little too heavy for my needs, I don't wanna have to switch file managers.

Thanks so much for the correspondence, you guys are the best resource a new light-weight user could ask for.

---

### Post by RedSquirrel on 2007-05-20
> **matt_risi said:**
> It was a music CD, data CD's are mounting okay. Any idea how I'd get a music CD to be accessible by audacious? 

I don't use audacious, but I would guess you just have to give it the device file, such as /dev/cdrom or /dev/hdc (or whatever it is on your system). I was using crip this morning and it didn't like /dev/cdrom, so I gave it /dev/hdc and it was fine with that. (I just checked now and /dev/cdrom is pointing to /dev/hdd. I'll have to fix that!)

I'll address the other things a little later.... someone here is tugging at my arm, if you know what I mean. Back ASAP.

---

### Post by RedSquirrel on 2007-05-20
OK. I installed audacious to check it out and playing a music CD worked fine for me. You just have to make sure that the CD Audio Plugin is setup correctly:

Preferences -> Plugins -> CD Audio Plugin -> Preferences Button

Then make sure you have something like:

Device: /dev/hdc
Directory: /mnt

You can check whether audacious likes your setting with the "Check drive..." button.

> **matt_risi said:**
> Also, is there any simple way to change the background in Fluxbox? 

Yes.

Check to make sure you have a program to set the background:

```
fbsetbg -i
```It should report: "<program_name> is a nice wallpapersetter. You won't have any problems."

If not, install feh:

```
sudo apt-get install feh
```Now, add this to your ~/.fluxbox/menu file (wherever you want it to appear):

```
 [submenu] (Backgrounds)
 [wallpapers] (~/.fluxbox/backgrounds) 
 [wallpapers] (~/path_to_more_backgrounds) 
[end]

```Then open your ~/.fluxbox/init file and find the line that looks like this

```
session.screen0.rootCommand:
```and change it to this

```
session.screen0.rootCommand:    fbsetbg -l
```Restart Fluxbox from the menu: Fluxbox menu -> Restart.

Screenshot below.





> **matt_risi said:**
> Any more feedback on the ejecting issue? Thunar's a little too heavy for my needs, I don't wanna have to switch file managers.

I don't use automounting and I prefer the command line for my file manager, so there's not much I can say. Just out of curiosity, what does the ejecting error say?


> **matt_risi said:**
> Thanks so much for the correspondence, you guys are the best resource a new light-weight user could ask for.

:D

---

### Post by matt_risi on 2007-05-25
Wow thank you very much for the awesome reply. I've yet to try it as I've been busy working full time (I'm a student, not used to that) haha. I'll try it as soon as I can get to my little eMachine.

---

