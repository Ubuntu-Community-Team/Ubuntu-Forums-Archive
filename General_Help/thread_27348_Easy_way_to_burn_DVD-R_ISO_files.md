---
title: "Easy way to burn DVD-R ISO files?"
date: 2005-04-15
forum: General Help
---

### Post by Dromio on 2005-04-15
I have a 3.1G DVD-R ISO file I need to burn.  Nautilus says it's invalid.  I open it in k3b and the "start" button to actually burn it is disabled.  I got gnomebaker from apt, but it won't burn it because I need some sore of ProDVD version of cdrecord, which requires you to request a license key and all sorts of other bother.

Is there an easy way to do this, or must I chase down ProDVD?

---

### Post by ron1n1 on 2005-04-16
Have you been able to burn any .iso files?  What type of DVD burner is it?

It sounds like either the .iso IS bad or your DVD burner isn't recognised.

Some troubleshoooting steps:

mount the .iso--> sudo modprobe loop, mount -o loop <name>.iso <some folder>
If the image is good you should be able to browse the folder and access the files.

burn through gnome --> insert a blank disc; does the burn:// window pop up? if so, right click the file in nautilus and select 'write to disk'

Some programs use links such as /dev/dvd /devcdrom etc.  make sure the programs are configured and pointed to the correct device and mount point.

---

### Post by Dracontopes on 2005-04-16
Well, I have several problems with Gnomebaker etc, so I thought hey let's give NeroLINUX a try -> work!

Easy way to burn ISO :) Only you must have a legal copy of Nero (for Windows LOL) to download it...

---

### Post by Dromio on 2005-04-16
[QUOTE=ron1n1]Have you been able to burn any .iso files?  What type of DVD burner is it?

It sounds like either the .iso IS bad or your DVD burner isn't recognised.

Some troubleshoooting steps:

mount the .iso--> sudo modprobe loop, mount -o loop <name>.iso <some folder>
If the image is good you should be able to browse the folder and access the files.

burn through gnome --> insert a blank disc; does the burn:// window pop up? if so, right click the file in nautilus and select 'write to disk'

Some programs use links such as /dev/dvd /devcdrom etc.  make sure the programs are configured and pointed to the correct device and mount point.[/QUOTE]
 It's an xiso, an iso for the xbox.  I found dvdrecord in the dvdrtools package which allowed me to burn it, but it's a CLI program.  I was sure hoping for a nice GUI method to handle this.

And Nero is very nice, but I think I'd rather use the CLI than spend that amount of money on a utility.

---

### Post by vassie on 2005-04-27
Did it work?
Burning xiso's is the only thing holding me back from removing Windows :(
Ben

[QUOTE=Dromio]It's an xiso, an iso for the xbox.  I found dvdrecord in the dvdrtools package which allowed me to burn it, but it's a CLI program.  I was sure hoping for a nice GUI method to handle this.

And Nero is very nice, but I think I'd rather use the CLI than spend that amount of money on a utility.[/QUOTE]

---

### Post by Fab on 2005-04-27
[QUOTE=vassie]Did it work?
Burning xiso's is the only thing holding me back from removing Windows :(
Ben[/QUOTE]

he said it allowed him to burn it, i guess it did work then ;P

---

### Post by rothbart on 2005-04-28
[QUOTE=vassie]Did it work?
Burning xiso's is the only thing holding me back from removing Windows :(
Ben[/QUOTE]

That's a journey I'm on myself.  For me, it's finding a good replacement for AutoGK (tried AcidRip, dvd::rip, and Thoggen) and NewsLeecher (tried Pan).  Right now I'm running those two (surprisingly well) with VMware Workstation.  I'd love to lose the overhead of the virtual Windows system...

The tip about dvdrecord is handy to know about.

You know about XBGM# v0.8, right?  It's a lesser, but still very usable Linux program similar to Qwix.  Check it out [here](http://www.xbox-scene.com/xbox1data/sep/EEEukAFFylMGxwcYFs.php).

---

