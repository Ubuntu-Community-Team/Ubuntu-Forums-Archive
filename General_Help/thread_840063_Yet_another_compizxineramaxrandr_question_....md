---
title: "Yet another compiz/xinerama/xrandr question ..."
date: 2008-06-25
forum: General Help
---

### Post by un_dave on 2008-06-25
Hey all,

I've been a Ubuntu user for almost a year now, and I've been overwhelmingly satisfied with the choice I've made. My desktop has matured to the point where I have very few day-to-day hassles, however one thing that still bothers me is my inability to use 3d acceleration on the desktop.

First, my hardware:
I'm running 2 x Gigabyte GF 7300GS 512M PCI-E
I selected these because I figured it was the cheapest way to allow for quad monitors, and I knew I wasn't looking for any gaming prowess.

My current setup:
I have 3x 19" LCD Monitors, setup to use Xinerama in gnome. This works fine, and I have no real issue with this setup, but it annoys me that I can't take advantage of my hardware to do some basic 3d desktop stuff.

So this morning I was reading this: [http://en.wikipedia.org/wiki/Xinerama](http://en.wikipedia.org/wiki/Xinerama) and noticed this:
*As of 2008, Xinerama is deprecated by X.org in favor of XRandR [1], and it is no longer under development [2].*

Now my understanding of the xinerama/xrandr/compiz issue was that initially, xinerama disabled xrandr, which is required by compiz. Then later, the xrandr requirement was removed from compiz, but it then caused seg faults with the nvidia drivers, if xinerama was running.

However, based on what I'm reading on wikipedia, it sounds like I should be able to drop xinerama completely, and switch to using Xrandr!
Now I've been reading up on this, and I'm not sure how, or if, it would work. Could someone explain if this is possible, and if I would allow me to use compiz, that would be great!

Thanks,

Dave.


[SIZE="1"]Originally posted with no response here: [http://ubuntuforums.org/showthread.php?t=747738](http://ubuntuforums.org/showthread.php?t=747738) but I wanted to bump this to the non-archive area. If it's already there or i've done this wrong... mods please feel free to delete this post.[/SIZE]

---

### Post by un_dying on 2008-06-25
Oh I see what you're getting at now.  I would like to know an answer to this also.

---

### Post by ad_267 on 2008-06-25
> **un_dying said:**
> Yeah I have a good understanding of the situation, I'll explain further via email.

Can you explain here for others that are also interested?

---

### Post by un_dave on 2008-06-25
It doesn't look like he can. Would anyone else like to help us out?

---

### Post by un_dave on 2008-07-09
Ok, a small update. 

After trolling several different IRC channels, and asking some helpful people in the know, it seems that the primary issue here is that in the current version of X.Org (7.3) randr does not yet support rendering to discrete graphics cards. 

So it can handle rendering two screens from one graphics card, but not 3 or 4 from two separate cards. 

Does anyone know anything else? I can't seem to find any info on when the next version of X.Org is due out, or even a blog charting it's progress.

---

### Post by iSTRONG on 2008-09-06
I have the exact same problem as you OP. did you find any other solution?

Looks like X.org 7.4 comes out on Sept 10th. hopefully that will fix it.

---

### Post by iSTRONG on 2008-09-16
strange that they haven't released it yet. it said Sept 10th on their website...

---

### Post by un_dave on 2008-09-24
Well it seems they now have. 

[http://www.heise-online.co.uk/open/X-org-7-4-comes-complete-with-new-functions-new-drivers-and-new-incompatibilities--/news/111595](http://www.heise-online.co.uk/open/X-org-7-4-comes-complete-with-new-functions-new-drivers-and-new-incompatibilities--/news/111595)

Release notes are here:
[http://xorg.freedesktop.org/wiki/Releases/7.4](http://xorg.freedesktop.org/wiki/Releases/7.4)

But I can't seem to find any reference to the handling of multiple GPUs. Can anyone see that issue addressed in there?

Also, how long is this going to filter through to being updated in the ubuntu repos?

---

### Post by balance07 on 2009-01-07
i'm in the same boat: 3 LCDs on 2 GPUs, multiple x-screens with xinerama. performance sucks. i LOVE my 3 screens, but the sluggishness is getting annoying.

---

### Post by mradem on 2009-03-15
I'm in the same boat here.  2 nvidia 8800gts's, 3 monitors, xinerama.  Anyone know anything new regarding this issue?

---

### Post by un_dave on 2009-03-15
To the best of my knowledge, there's still no progress on this. 

It's pretty much my biggest frustration with ubuntu  at the moment. (linux in general, really, i know it's not ubuntu's fault)

When you compare linux multiple monitor support, via X11, to Windows and OSX, it's simply abysmal. 

I keep thinking that fixes in this area must be just around the corner, but I'm yet to see anything substantial. 

:(

---

### Post by balance07 on 2009-03-16
> **un_dave said:**
> When you compare linux multiple monitor support, via X11, to Windows and OSX, it's simply abysmal.

i think it should be noted that the issue is multiple _***GPU***_ support, not multiple monitor.

that being said, it is my biggest gripe also. i've decided to just buy a Matrox DualHead2Go and be done with it. i want my compositing.

---

### Post by MaximumOverdrive on 2009-04-09
Yes! Please! I am a Linux Newbie and I love it already! I installed it on Sunday Apr 5th and I have been killing myself trying to get my dual screen working. The worst of it is the fact that I can't rotate my second screen for portrait when XRandR is disabled. Since my studio has the monitors mounted to the wall, I really don't feel like taking the concrete screws out to rotate it. PLEASE HELP... I don't want to go back to the big M.

---

### Post by mradem on 2009-04-15
Has anyone been willing to try the beta yet to see if our problem is fixed in 9.04?

---

### Post by dex.pdx on 2009-04-27
Well I seem to be having the same problems as everyone else.
3 24" LCD's and two Nvidia 9400GT's
I can twinview two monitors or just simply run Xinerama.
I get GLX support under Xinerama but no Compositing (which means no compiz)

This is under Xorg 7.4 Ubuntu 9.04 compiz 0.8.2 (latest nVidia at time of writing).

Hopefully 7.5 of Xorg or the next release of Compiz will fix this.
There should not be a limitation here - if I can run a GLX application under Xinerama and drag it or expand it across multiple monitors (running rather well at that) there should be no reason why compositing and or compiz should not work.

---

### Post by Mogrix on 2010-05-08
I third this notion.

Running 3 monitors on two graphics cards -- wishing i had the ability to enable some compiz effects while running Xinerama.

---

### Post by un_dave on 2010-05-09
Could someone confirm that this is still in the limitation of 10.04 ?

I'd be a little concerned if they still haven't addressed this. All reports I was getting when I first posted was that this fix was 'coming soon'... 

It's now almost 2 years later, and I've shifted largely to Win7 and OSX for my main systems, so I'm unable to check this out my self. 

My only remaining Ubuntu system is a VM server, works well, but I rarely access it via anything other than SSH.

---

### Post by svtdragon on 2010-05-09
Yes, I can confirm that it's still an issue in 10.04.

Per the chat log [here]("http://http://gentoohaven.com/2010/04/13/xinerama-composite/"), from "ajax" (the guy who wrote [this]("")) there are several underlying issues, all of which I'd love to see addressed and/or help address... but I can't seem to get past the "what do I do first, and how?" phase.

---

### Post by wallpaper_thief on 2010-07-24
> **svtdragon said:**
> Yes, I can confirm that it's still an issue in 10.04.

Per the chat log [here]("http://http://gentoohaven.com/2010/04/13/xinerama-composite/"), from "ajax" (the guy who wrote [this]("")) there are several underlying issues, all of which I'd love to see addressed and/or help address... but I can't seem to get past the "what do I do first, and how?" phase.
I can confirm it is still an issue. Luckily, Kwin doesn't require compiz, but that means you'll have to switch to KDE, which I have no problem doing, but some might.

---

