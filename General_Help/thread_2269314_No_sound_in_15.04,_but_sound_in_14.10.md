---
title: "No sound in 15.04, but sound in 14.10?"
date: 2015-03-14
forum: General Help
---

### Post by amrabdi on 2015-03-14
Okay, so I just bought an Intel NUC machine with the 5th gen Broadwell i3 cpu(as an HTPC). I at first installed Ubunut 14.10(read that it supported the 5500 gpu of the i3). Everything was working well(more so after I googled how to update to the newer kernel), including sound, via HDMI. Something about the Unity interface was not for me(specially when hooked up to my tv). I installed an SSD so I can have Ubuntu on there and leave the HDD as storage for media. I noticed that if I went with any of the beta versions of 15.04, it will update to the final when it gets released. I like the idea of gnome Ubuntu. It looks like that everything installed correctly, but that doesn't seem to be the case. Sound doesn't work, shows up as dummy(?), and a lot of the settings are locked, but it won't let me unlock. Plus, when I try to do software update, via the app and terminal it fails. And, at least via the app I get a message regarding not enough access/privilege? I tried a few other things via terminal, but still no go on getting sound to work. I also reinstalled gnome Ubuntu, but no dice. Any ideas to resolve this issue(and the issue of not having enough access)?

btw: Both versions I have tired are the 64bit version. Thank you.

---

### Post by grahammechanical on 2015-03-14
First, 15.04 is still under development and will not be released until near the end of April. So, expect bugs and expect bugs to be fixed by running a daily update.

Second, 15.04 development release is in the process of switching from upstart to systemd. So, there may be problems caused by this. At the Grub menu select Advanced Options. There you will find an option to load using upstart. Does that fix things?

Upstart and SystemD are there to start and stop system processes. 

Third, we have a section of this forum called Ubuntu Development Version. There we discuss problems that we find with the development version. Sometimes someone will know of a fix. But not always. For example, there is this thread about Ubuntu Gnome and the latest Linux kernel 3.19.0-9. 

[http://ubuntuforums.org/showthread.php?t=2268961](http://ubuntuforums.org/showthread.php?t=2268961)

There are also threads about systemd. Personally, I am not impressed with systemd. It is failing to load some kernel modules and that in turn is causing Ubuntu to add 80 seconds to loading time.

I also cannot use kernel 3.19.0-9 as it will not work with the Nvidia driver that I need to use. But hey, this is what we expect when we use a version of Ubuntu that is still under development. Welcome to Ubuntu development testing.

Regards.

---

### Post by gifford on 2015-03-14
Maybe Ubuntu 14.04.2 would be a better fit for you.

---

### Post by amrabdi on 2015-03-14
Well problem with 14.04 is Intel broadwell cpu and gpu aren't supported(or well supported). 14.10 has some support, but I'm told 15.04 with updated kernel is where things work the best. I am right now on the Beta 1 version, not a snapshot. But, thank you!


Edit: I think I may just go with gnome Ubuntu 14.10(with update kernel) and upgrade to 15.04 when that comes out. I'm reading that you can update to Ubuntu in Ubuntu itself without loosing data or anything(which is amazing cause I'm use to Windows where a clean install was always recommended and OSX, which sometimes had problemwhs when upgrading, or at least I did). 
Also, what sound drivers do you recommend for HD 5.1 audio via HDMI?

---

### Post by anne.dawson on 2015-05-14
see above

---

