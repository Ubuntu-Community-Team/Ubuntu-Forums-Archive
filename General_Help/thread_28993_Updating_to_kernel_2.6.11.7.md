---
title: "Updating to kernel 2.6.11.7"
date: 2005-04-22
forum: General Help
---

### Post by raid517 on 2005-04-22
Hi, due to stability issues I would like to build my own custom kernel 2.6.11.7. But I don't like it that I get so many complaints at bootup when I use vanilla kernels downloaded from Kernel .org (Basically I get about 10 messages at the start of the bootup process saying that it cannot remove xyg module, and that the system is busy. (Or words to this effect). What specific patches does Ubuntu/kubuntu use - and do the developers have any of these patches that would work with a 2.6.11.7 kernel?

GJ

---

### Post by diebels on 2005-04-22
There is a linux-patch-ubuntu-2.6.11 package, but I don't understand the description. You could just fetch it and have a look at it I guess.

---

### Post by krrh on 2005-04-22
Those patches won't apply against a vanilla kernel -- say 2.6.11.7. The information provided with that package in Synaptic claims the patches will work only against linux-source-2.6.11_2.6.11.orig.tar.gz. I've tried doing so with vanilla source, and the process fails.

I've tried the swsusp2 patch against the orig.tar.gz source, and the patch wouldn't apply. I guess it's still Ubuntu modified.

---

### Post by raid517 on 2005-04-22
That's what I mean, there seem to be some very specific Ubuntu patches in the kernel. (Not very good ones apparently either, as they seem pretty unstable). I tried the 2.6.11.1 kernel image, but that was a nightmare on my system. Lock ups and freezes galore. (It should be noted that this doesn't happen with any other distro). I'm pretty hopeful - indeed kind of confident having tried it before on another distro that the 2.6.11.7 kernel would pretty much resolve all of my problems.

What I don't get is why Ubuntu devs are still using such old ass kernels? 2.6.11.7 has been in debian unstable for a couple of weeks now. In a short while (indeed in a very short while) the 2.6.12 kernel will be released and we will still be left standing in the dust scratching out butts, having to make do with some early buggy 2.6.10 or maybe 2.6.11 point release.

I'm not bitching. I would change the kernel myself, if I had access to recent sources and some updated working patches.

GJ

---

### Post by diebels on 2005-04-24
I think you are jumping to conlusions. Not all instability is caused by the kernel version. My laptop was damn unstable before I added noapic and nolapic to the boot parameters and adjusted the harddisk with hdparm acoustic_management = 128.

Not to say that the kernel is not at fault, but you should try to isolate the problems a bit more before you blame it. If you haven't already that is.

I bet there will be newer linux images in breezy as soon as the syncronisation with debain unstable is done.

---

### Post by raid517 on 2005-04-24
[QUOTE=diebels]I think you are jumping to conlusions. Not all instability is caused by the kernel version. My laptop was damn unstable before I added noapic and nolapic to the boot parameters and adjusted the harddisk with hdparm acoustic_management = 128.

Not to say that the kernel is not at fault, but you should try to isolate the problems a bit more before you blame it. If you haven't already that is.

I bet there will be newer linux images in breezy as soon as the syncronisation with debain unstable is done.[/QUOTE]


Well I guess you can add it up for yourself. I've had later kernel versions on other distros, and they were rock solid. I just got caught up in the Ubuntu/Kubuntu hype, which is the only reason I made the switch.

Anyway having said that, this brings me to the question of breezy. Is it possible to use breezy repositories on Hoary? I mean I only want the kernel and maybe to see if I can update KDE a bit more.

If so what are the repositories?

Also you say that the developers are 'syncing' with the debian unstable source tree. Does this mean that there are plans to keep the source tree in sync permentantly from now on? Because that would be a major relif for me. I simply can't get used to how long it takes to update software atm.

GJ

---

