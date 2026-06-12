---
title: "DVI/HDMI hot-swapping... wait, it works on Ubuntu, but not Windows?"
date: 2008-06-16
forum: General Help
---

### Post by AndrewZorn on 2008-06-16
Short story: I am recently the victim of copyright protection affecting the legal consumer.  Replaced my Dell 2405fpw without HDCP for an HP w2408h, which only has a single digital input (HDMI).

Using my HDMI switch is quite a pain.  When I'm in Windows, I'm running my PS3's optical out into my computer, and 'monitoring' it through the speakers.  When I switch to my PS3, it's fine.  But when I try to switch back to my computer, the monitor goes to sleep.  I need to restart my computer to see what's on the screen again, which makes playing my PS3 an ordeal.

Apparently, this is a big issue.  The video card *needs* the EDID information sent to it constantly, or the output port will be disabled.  To fix this, everyone says I *need* something called a DVI Detective, which basically holds this EDID information in between the computer and monitor.  It's $70, and there's *no* software/firmware solution, it's simply *impossible*.

So says the internet.  I put everything in italics because after accidentally restarting in Ubuntu, I noticed the switch works **perfectly fine**.  NO delay, no redetecting (as in, the monitor does not display the resolution and color settings again) etc.  Just like I HOPED the switch would work.

So now we get to the point of the post.  The world seems to think this DVI/HDMI problem is a problem with all video hardware, and is unfixable without some sort of trickery device.  However, Ubuntu handles it fine, and typically has sub-sub-par drivers for stuff like video cards.  I have an Nvidia 8800gt.  From doing all this, I now KNOW there is a software solution possible.  I was wondering if any of the gurus here knew what was going on in Ubuntu that lets this work, and if there's anything I can do (as in, DISABLE) in Windows to get this to work how I want.

I'm very surprised at all of this.  So why not just leave it in Ubuntu?  Well, skipping over the whole "I'm not that good in Linux and none of my games work in it either" part, I cannot get the sound from my Razer Barracuda AC-1 working in Linux.  Even if I could, I'm not sure that I'd be able to get the optical in working and all.  Any advice for this would be great though, then I'd just restart to play games.  On my laptop, which features near-fully functional hardware, I don't even have Windows installed, and get by 99% of the time (sans-gaming).

Thanks!

---

### Post by Zorael on 2008-06-16
On a small tangent, to increase my lubberly post count since I'm a shallow person, I note that the Razer Barracuda AC-1 is based on the C-Media CMI8788 chipset. ALSA doesn't support this yet, but OSSv4 does!

From [http://www.phoronix.com/scan.php?page=article&item=590&num=2:](http://www.phoronix.com/scan.php?page=article&item=590&num=2:)
> When it came to the ALSA support the C-Media device was listed in system-config-soundcard, but the Barracuda AC-1 failed to play any audio. The CMI8338, CMI8738, and CMI8768 are supported by ALSA, but the CMI8788 has yet to be supported. However, in OSS v4.0 Beta rc2-build 178 the audio controller support has been added.

From [http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html):
> ...
C-Media 2/4/6/8ch USB audio adapter (BETA)
C-Media CM8338A
C-Media USB audio adapter - model1
C-Media USB audio adapter - model2
CMedia CM8338B
CMedia CM8738/CM8768
**CMedia CMI8788**
...

An OSSv4 installation guide for Ubuntu can be found [here.](http://tinyurl.com/5c6luu) I can't promise anything about the optical ins-and-out, though, but there's a [proper OSS forum](http://www.4front-tech.com/forum/index.php) which may be able to help if it doesn't work straight off the bat.



That is all. Carry on.

---

### Post by damis648 on 2008-06-16
> **AndrewZorn said:**
> However, Ubuntu handles it fine, and typically has sub-sub-par drivers for stuff like video cards.

I would just like to point out these drivers are not sub-sub-par. They are basically the same drivers from the nvidia website (modified to automatically configure). Back on the point of your problem... maybe you could (re?)-download the official drivers from the nvidia website and reinstall them in Windows?

---

### Post by Zorael on 2008-06-16
> **damis648 said:**
> I would just like to point out these drivers are not sub-sub-par. They are basically the same drivers from the nvidia website (modified to automatically configure). Back on the point of your problem... maybe you could (re?)-download the official drivers from the nvidia website and reinstall them in Windows?

I believe his point was that Nvidia puts more effort and manpower into optimizing and fixing their Windows drivers than their Linux drivers, which I think we can all agree on.

---

### Post by damis648 on 2008-06-16
> **Zorael said:**
> I believe his point was that Nvidia puts more effort and manpower into optimizing and fixing their Windows drivers than their Linux drivers, which I think we can all agree on.

Sure, they do. Just pointing out that the drivers in Ubuntu are still the official drivers.

EDIT: At least they MAKE drivers for linux... ((hello Broadcom?!))

---

### Post by AndrewZorn on 2008-06-19
> **damis648 said:**
> I would just like to point out these drivers are not sub-sub-par. They are basically the same drivers from the nvidia website (modified to automatically configure). Back on the point of your problem... maybe you could (re?)-download the official drivers from the nvidia website and reinstall them in Windows?
There's no *problem* I'm having in Windows, per se.  It's a known issue with the DVI switching.  It's just everyone out there thinks it's a hardware issue, and not a simple software thing.  It's something that Ubuntu is or is not doing that would be really nice for Windows to copy somehow.

---

### Post by AndrewZorn on 2008-06-30
**For NVIDIA cards on XP, disable the NVIDIA Display Driver Service.**  Totally fixes it.  Incredible, people making a living just working around stupid driver crap that should have never started.

---

