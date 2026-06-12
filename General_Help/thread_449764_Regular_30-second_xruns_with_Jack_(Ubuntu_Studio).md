---
title: "Regular 30-second xruns with Jack (Ubuntu Studio)"
date: 2007-05-20
forum: General Help
---

### Post by alatham on 2007-05-20
Hi everyone.

I'll post my system and usage specs at the bottom.

I've recently switched over from Mandriva due to general difficulties getting my audio programs running correctly.  Ubuntu Studio has fixed most of these, but I'm still having trouble with Jack.  I'm using QTJackctrl to start jack, but I get the problem even if I just start jack from the command line.

I get an xrun at exactly 30-second intervals.  I won't necessarily get one every 30 seconds, but it happens about 90% of the time.  So I can't go more than 1 minute without hearing a glitch in the output.  The problem occurs in all three modes (duplex, playback, and capture).

Here is a sample of QTjackctrl's running commentary:
delay of 18363.000 usecs exceeds estimated spare time of 2858.000; restart ...
15:14:51.712 XRUN callback (1).
delay of 18608.000 usecs exceeds estimated spare time of 2881.000; restart ...
15:15:21.712 XRUN callback (2).

Obviously something is halting my soundcard for 20 ms once every 30 seconds.

I found someone with a similar problem, but he was running on a laptop and fixed it by turning ACPI off.  I'm running a desktop and can't even turn that on.  See his post here:
[http://www.music.columbia.edu/pipermail/linux-audio-user/2006-September/038384.html](http://www.music.columbia.edu/pipermail/linux-audio-user/2006-September/038384.html)

What I've done so far:
Stopped every process except Jack and QTjackctrl using the System Monitor.  Didn't help.
Changed back to the basic video driver (I was using the NVidia drivers).  I have since switched back to NVidia with no changes.

I can set the latency up to 20+ ms while running Jack and suffer no problems.  That was obvious once I started looking at the error messages QTjackctrl was spitting out.  But I'm a musician and that's just not acceptable for the kind of multi-track recording I do.  I really would like it down to 5 ms or lower.  I can do this just fine running XP home.  I think it's set to 2.4 ms there.

Here is the line that jack starts with:
jackd -R -P80 -p128 -dalsa -dhw:0 -r44100 -p64 -n3

I have tried running in non-realtime mode (many more xruns), lower priority (no change), and different rates (no change).

My guess is that there is some other piece of hardware with a higher priority that is running something every 20 seconds.  USB / FireWire?  Does anyone know how to find out what the priorities are set to for each piece of hardware.  I know my soundcard is on interrupt 22, but I doubt that's useful to know.

Please note that I'm Linux semi-literate.  Thanks everyone, this is a great distro.

System:
Boring stuff:
Gateway 552GE.  Pentium 4 - 3.2GHz.  1G RAM.  450 Gigs on 2x 7200 RPM hard drives.
NVidia 6800 XT.  USB keyboard and mouse.  2 DVD-ROM drives.  Multi card reader.  unoccupied FireWire port.

Soundcard:  M-Audio Delta 1010LT.  Works flawlessly in Windows.

Ubuntu Install:
I'm running the low-latency kernel.  I'm trying to use Audacity and Ardour (I'll learn some other programs later).  The xruns happen no matter what I'm doing at the moment, even if I'm just sitting there watching QTjackctrl.

---

### Post by ricrac on 2007-05-20
CD autodetect maybe?

If you struggling to see the difference between winxp an linux and know how to multiboot, try 64studio (debian based), jacklab (rpm based, can use CCRMA apps/tips) or dynebolic(streaming, livedj, livevj).  These have been around longer and kernel, jack config, arts/esd, cd autodetect, etc. have already been dealt with.
I use all three, each one does some things well.

Ubuntu moves very fast and should catch up in no time...

---

### Post by alatham on 2007-05-21
I think I was able to shut off CD Autodetect, but I'm not positive if I did it correctly.  I went to a menu called Removeable Media, or something like that (I can't remember exactly, I'm at work now).  Any thoughts on how exactly to go about doing it, assuming I did it wrong earlier?

I also did some more hunting and found out that my computer does use ACPI, I thought it was specific to laptop hardware, but I was wrong.  So I went and added "acpi=off noacpi" to the end of the Kernel line in my /boot/grub/menu.lst file.  That seemed to shut off ACPI (as it didn't show up in "cat /proc/interrupts"), but the problem remained.

So I still need to figure out what process is running for about 20 ms once every 30 seconds.  And why does it have higher priority than Jack.  Note that sounds play just fine when I'm not running Jack (i.e. Amarok and movie players work perfectly just using ALSA).

---

### Post by alatham on 2007-05-22
I've discovered that if I stop dbus from running, the xruns go away completely.  The only problem is dbus is required for lots of things.

Any idea's on how I can get dbus to stop communicating for so long every 30 seconds?  I tried lowering it's nice value to 20, and raising Jackd to -20 (those values are counterintuitive, if you ask me) but that doesn't help.

I noticed there are 2 dbus processes, dbus-daemon and dbus-launch.  Is it possible that I could stop one of these and not run into problems?  I'll try out a few more things tomorrow night.

---

### Post by neurator on 2007-05-22
I definitely anticipate hearing about your experiences, as I'm getting the same problem!

---

### Post by alatham on 2007-05-23
Then anticipate no more.  I've found the problem.

I don't know how much help it will be to others, but I have indeed found my problem.

It's my Logitech LX7 wireless mouse.

There was a rather convoluted series of events before I narrowed it down, but I eventually discovered that if I unplug my mouse from the USB port, the xruns stopped.

My guess at the ultimate culprit is it's battery detection circuit.  I'm assuming it's transmitting once every 30 seconds with info about the battery.  And it takes about 20 milliseconds to transmit that data.

I, of course, have zero evidence for this, especially in light of the fact that that's a long time to take to transmit two bytes of data.  But that's what I think it is.

So, do other people who have mouses with battery detection as a feature have any sort of similar problem, or is it simply a specific driver issue?

One important thing to note is that the driver that Ubuntu Studio auto-installed was for a Logitech MX1000.  I know the mice are related, but should I be looking for a more specific driver?  Does one even exist?

So, I either have a driver problem, or I need a new mouse.

Now please, poke holes in my theory.

---

### Post by neurator on 2007-05-23
I have an MX1000 lasermouse, and have confirmed the same problem.  I think a workaround might be just to change the mouse driver to a more generic option and go with that... I don't use any of the special buttons on my mouse anyhow.   I'll try that... this might be something we should communicate to whatever group wrote the drivers for the MX1000 mouse, it could be a simple bugfix.

Thanks for your work on this!

-R

---

### Post by alatham on 2007-05-23
Hey, no problem.

Do you happen to know how to go about forcing Ubuntu to use a generic driver?  I also only ever use the 2 buttons and scroll wheel, I'm sure those are well supported under generic drivers.  I've looked around, but I haven't found out how to manually change drivers like that.

---

### Post by euchrid on 2007-06-07
Thanks for this. I haven't seen this mentioned anywhere else. It looks like my Logitech Cordless Trackball might be doing similar things (but not providing so many/frequent xruns). Might go back to my Wacom tablet full time.

There seem to be a few problems with JACK/Alsa set up in Feisty. Hopefully, someone can find out what is at the root of it all (there seems to be a lot of interconnected isses with sound and recording).

---

