---
title: "The perennial iPod question - how best to work with it"
date: 2006-08-18
forum: General Help
---

### Post by blubris on 2006-08-18
Hi, I'm pretty new to Linux, and started out primarily with Ubuntu. I currently own an iPod mini and recently bought a 30 GB iPod, and am *still* pretty stuck as to how to use them with Ubuntu. 

Now, before you reccommend anything, consider this - I've read the 'How to iPod with Ubuntu' guide. I've searched this forum lots of times to find out information on how to use Banshee, Amarok, Rhythmbox, Quod Libet, gtkpod and various other music players. 

Amarok, though lauded everywhere, didn't play well at all with my Gnome desktop, and I already like Ubuntu too much to start installing Kubuntu or the KDE desktop just so I can sort out my iPod, especially since I can't buy music through Amarok as well, which I'd have loved to do. I tried to install Banshee from CVS because that was supposedly the version that had the support for their iPod plugin, and that backfired - Banshee didn't work. Rhythmbox I really can't stand, because I can't manage my iPod properly from there, and because of the irritating lack of song order capabilities. Quod Libet and gtkpod have been the best so far, especially Quod Libet - gtkpod crashes regularly (at-the-end-of-pretty-much-every-session regularly), and is irritating to handle because of that.

So I thought 'screw this. I'll just double boot again,', but I don't really bloody *want* to double-boot, so I searched for a way around that. VMWare and Win4Lin were the solutions that kept popping up, but I can't seem to find anyone saying that you can run iTunes (my poison of choice) on WinXP on VMWare, and actually use it to manage your iPod. I don't feel like going through the arduous process of installing VMWare only to find that it *doesn't* work with iTunes and my iPod, either. If there's anyone that's put the three together and found it fine, I'd really love to know.

Bonus question: has anyone else found a way to buy music similar to that of the iTunes music store that isn't positively illegal? I've tried emusic (don't like their song selection), and am loathe to try Rhapsody because of their subscription fee, which I think sucks. I'd really rather not have to touch Windows again if I could, and it would just be nice if there was a solution to the triple-pronged problem of using my iPod...

And seriously, people, no solution is too arcane. As long as it works and keeps working, I'll do it.

---

### Post by ctaggart on 2006-08-28
I tried the various Linux programs, but still prefer iTunes.  I *really* hope Apple makes a Linux version sometime in the near future.  I just got iTunes working within VMware player which is running Windows XP.  It was not easy.

There is an issue with USB in the Linux kernel that causes VMware player problems.  To fix it you must compile a custom kernel.  Before compiling the kernel a few lines in drivers/usb/core/usb.c must be commented out.  Follow what the diff/patch says here:  [http://www.vmware.com/community/thread.jspa?messageID=295175&#295175](http://www.vmware.com/community/thread.jspa?messageID=295175&#295175)  

I took me a while to figure out how to compile the kernel on Ubuntu.  When I booted with the kernel, I found out I had to compile kernel modules for the WiFi card and run through the VMware player setup.

I would love it if the Linux kernel would be modified or Ubuntu would apply the patch for Edgy, then iTunes in Windows on VMware player would be easy!

Cameron

---

### Post by astrx on 2007-01-29
i would suggest putting rockbox on the ipod. its slower than the regular OS, but it allows you to drag and drop music right into the player and then play that music, delete it, etc.

---

### Post by soze on 2007-01-29
I'm a big fan of gtkpod, the latest version even supports album-cover artwork.

I don't download music (too much DRM insanity).
I rip CDs (using grip), download the cover art (using albumart-qt) and then sync to the ipod using gtkpod.

For local playing on my desktop, I use Quod Libet.

---

### Post by strabes on 2007-01-29
gtkpod is unstable but IMO it's the best option for linux right now. Programs in linux generally do ONE thing, not everything like windows programs do. It's kind of the nature of open source. So gtkpod ONLY syncs your ipod, rhythmbox ONLY plays music, etc. Keeps everything faster and easier too. I don't really understand your problem with rhythmbox, it's the best music library manager for linux in my opinion.

---

### Post by soze on 2007-01-29
> **strabes said:**
> gtkpod is unstable but IMO it's the best option for linux right now. Programs in linux generally do ONE thing, not everything like windows programs do. It's kind of the nature of open source. So gtkpod ONLY syncs your ipod, rhythmbox ONLY plays music, etc. Keeps everything faster and easier too. I don't really understand your problem with rhythmbox, it's the best music library manager for linux in my opinion.

I've not had stability problems with gtkpod.
What rev are you running?

---

