---
title: "how do the live disks manage to support all sorts of hardware?"
date: 2015-07-15
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2015-07-15
I want to make a usb external hd based system able to work with a wide variety of machines. My systems now only seem to completely work with the machines they were built on. Specifically when I boot a laptop from them they can't access the internet, even though the connection is the same ethernet cable used on the machine they were built on. I'd like to be able to carry this drive anywhere and boot and use most machines with it. Any suggestions on packages I need?

---

### Post by oldfred on 2015-07-15
Is usually is video drivers. Sometimes wireless drivers.
And now live install is both UEFI & BIOS compatible.

The live installer uses the open source drivers which work with most video, but some systems need the proprietary drivers to work well. Sometime then boot parameters can also help set defaults to allow system to boot. With live installer & first boot after install I have always needed nomodeset boot parameter.

Not all wireless work, but most Ethernet hard wired connections do work. They assume DHCP and will connect to local network.

---

### Post by mastablasta on 2015-07-16
only devices that have opensource drivers available work out of the box and well in live session (well some GPU's have fallback drivers). in any case drivers in Linux are part of kernel. 

how are you creating your systems?

---

### Post by Dreamer Fithp Apprentice on 2015-07-16
Thank you both, gents. Funny,  I could have sworn I replied last night. I guess I previewed instead.

Anyway, all the systems in question were made by installing from a CD burned from a 14.04 mini iso and then using apt to install xorg, openbox, lightdm, lightdm-gtk-greeter, thunar, synaptic, firefox, xscreensaver, wmctrl, fbreader, mirage, vlc, etc. When I first started making ultralight systems I started with Lubuntu and subtracted stuff until I broke it and started over, keeping records. This way works a lot better and is a lot faster. You wouldn't believe how hard it is to find all the weird ways LXDE and Lubuntu on top of that modify the quite adequate Openbox environment so that you can't figure out whose manual to follow. Building from the mini up I get it done faster, get a lighter system, and get a system that is, usually, easier to troubleshoot, repair, and understand.

The video works fine on all systems, despite the fact that the monitors are sufficiently different to have different resolutions. The only problem I've run into is internet access, despite the fact the same ethernet cable to the same router is employed. While I do want a general solution to this CLASS of problems, that's really the only thing that isn't working with the hardware to hand. There is a command to output a list of installed packages with brief descriptions (I'll have to look it up - I forget what it is). I was thinking of doing that on one of the systems that doesn't work and again for the one that does, then generating a list of packages on the latter not on the former, ideally by clever bash commands, but manually if necessary. Then I could check the descriptions to see what might have something to do with the internet. That's assuming it is the LACK of a package that is the problem. Of course, it is conceivable it could be a config file, or even the PRESENCE of a package. That sounds like a week long project for a tinkerer like me that only sort of half-way knows what they are doing. So I was hoping y'all might have a more elegant approach or thoughts on how I might find one.

---

### Post by oldfred on 2015-07-16
If it is Ethernet hard wired, not wireless, then it may be a configuration file. 
Best to review threads on Internet connection, and if good info not found, post a new thread with details of your hardware & configuration.

I do not know if this old thread is still valid or not (export using dpkg is still what I use). I created my own python/sqlite compare program.
But you probably can just export the lists of installed apps and use Meld Diff compare tool or similar just to compare two files.
       HowTo: Create a list of installed packages
Compare two lists: kdford post #70
[http://ubuntuforums.org/archive/index.php/t-261366.html](http://ubuntuforums.org/archive/index.php/t-261366.html)

---

### Post by Dreamer Fithp Apprentice on 2015-07-18
Thanks Oldfred. Usually, in threads like this I post back when I've made progress or exhausted the possibilities discussed, but this looks like it may take some time, so - an interim report:

I used a script employing deborphan to generate lists of packages installed deliberately (as opposed to dependencies) on the working and the most similar non-working systems and compared the lists with the tools described in the thread you linked to. There were only a couple of packages on the working system, not on the crippled one.

One is nautilus-data and the other is browser-plugin-lightspark ( with browser-plugin-gnash instead on the non-working system).  Those don't look likely to be involved.

But the deborphan script is known to miss packages with circular dependencies so I'll try that again later with complete lists. For that matter, it isn't impossible that I might have different libraries installed as dependencies - I can think of ways that might happen - so I need to do it with f ull lists anyway.

I've tried to address the config question by using debs to install nictools-pci (which I succeeded in installing, but I haven't managed to get it to do anything yet) and network-manager-gnome. The latter I have not yet been able to install because of an "irresolvable" dependency, though I may try resolving it by replacing one library with an older version if I don't reach success by some other path first. 

I'm going through the networking forum looking for things that might be relevant. If nothing else, maybe I can at least find the names of some possibly relevant config files to compare.

I'll post back when I've made some more concrete progress or exhausted these approaches. That may take a few days.

---

### Post by sudodus on 2015-07-18
In order to make the network portable in systems created from the Ubuntu mini.iso (to work in several computers without tweaking), I use the tips in the following link

[Unmanaged Wired Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)

If network manager and nm-applet are installed, it also helps making wifi connections easy too.

---

### Post by Dreamer Fithp Apprentice on 2015-07-18
Thank you, Sudodus.

That page appears to be extremely relevant.  I got some studying to do. Thank God for coffee.

---

### Post by sudodus on 2015-07-18
You are welcome and good luck :-)

---

