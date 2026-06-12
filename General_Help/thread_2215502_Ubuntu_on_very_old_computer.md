---
title: "Ubuntu on very old computer"
date: 2014-04-07
forum: General Help
---

### Post by 3d4tPNm on 2014-04-07
I installed Ubuntu on a very old desktop, in which windows XP runs like its 1993 (terrible)

495.8 mb Ram
Intel Pentium (R) 4 CPU 1.70 GHz
video card: nv11x86/mmx/SSE2 (no idea what that is about)

Ubuntu doesn't run so hot either, the dock never loads, and it is VERY slow, I was able to access the file systems and some system features by right clicking on desktop and creating a "new folder", as well as accessing [COLOR=#000000]system info from the change appearances section. Aside from being too buggy to load the dock, it lags just like it did on XP. Icons are also very buggy, and do not render properly. ttyl terminal works flawlessly, without issue.

Now, I think this is caused by the decade old hardware on the machine? What are the reasons why the dock would never load?

So I am looking at Lubuntu and Xubuntu and they seem pretty good, would that be a good way to make this computer usable? What is everyone's experiences running Ubuntu on ultra slow computers? I will mainly use to for viewing YouTube, and need to run flash.

On a unrelated note, is it possible to extract the HDMI port/system from a laptop (broken processor)?[/COLOR]

---

### Post by mörgæs on 2014-04-07
Yes, Lubuntu is a good choice.
More advice in the link in my signature.

---

### Post by sudodus on 2014-04-07
> **mörgæs said:**
> Yes, Lubuntu is a good choice.
More advice in the link in my signature.

+1

Lubuntu can bring [old hardware]("http://ubuntuforums.org/showthread.php?t=2130640") back to life :-)

---

### Post by mastablasta on 2014-04-07
Ubuntu is not for old hardware. it's a modern OS with last iteration made in Autumn last year. it needs enough ram and good 3d acceleration to run well. so Lubuntu/xubuntu is a better choice for that old maschine. both are modern, but they do not need high ram or 3D acceleration to draw windows etc.

---

### Post by pfeiffep on 2014-04-07
> **mastablasta said:**
> Ubuntu is not for old hardware. it's a modern OS with last iteration made in Autumn last year. it needs enough ram and good 3d acceleration to run well. so Lubuntu/xubuntu is a better choice for that old maschine. both are modern, but they do not need high ram or 3D acceleration to draw windows etc.

For those folks who have middle of the road hardware I found that it was relatively inexpensive ($30) to increase the ram on my laptop to it's 2 GB maximum.
 Unity seemed to be out of reach for this middle aged Dell so I installed gnome fall back.
These 2 actions brought it back to life.

---

### Post by ralph-beeby on 2014-04-07
One thing you may have to watch out for is your laptop not having Physical Address Extensions...though I think if it's a Pentium 4 you should be safe. I gather recent versions of Lubuntu won't cope with pre-PAE machines (not sure about Xubuntu). Another possibility I found with a similarly old laptop was that it would run Ubuntu 10.04 considerably faster if you had a quick tinker with the desktop to minimise the animations and graphical effects!

---

### Post by SeijiSensei on 2014-04-07
Boot up the machine, then run "top" from the command prompt.  How much swap is being used?  With <512 MB of RAM, the machine should be swapping a lot of the time.  Buy some more memory, and your performance will improve markedly on both platforms.  An upgrade to 1 GB should cost less than $50, probably more like $25-30 depending on the type of memory the machine uses.

---

### Post by ibjsb4 on 2014-04-07
> 495.8 mb Ram
Intel Pentium (R) 4 CPU 1.70 GHz

I have a 2002 (same spec) machine and find Lubuntu to be very fast on it.  If you wish a ultra-lite build of Lubuntu, there is LXDE.  But this takes more work to install as it is very bare bones and software needs to be added.

[http://lxde.org/](http://lxde.org/)

---

### Post by sudodus on 2014-04-07
> **ralph-beeby said:**
> One thing you may have to watch out for is your laptop not having Physical Address Extensions...though I think if it's a Pentium 4 you should be safe. I gather recent versions of Lubuntu won't cope with pre-PAE machines (not sure about Xubuntu). Another possibility I found with a similarly old laptop was that it would run Ubuntu 10.04 considerably faster if you had a quick tinker with the desktop to minimise the animations and graphical effects!

The PAE problem with Pentium M and Celeron M processors will be solved easily with the boot option ***forcepae*** in the next version, Trusty Tahr, to become Lubuntu and Xubuntu 14.04 LTS.

---

### Post by 3d4tPNm on 2014-04-07
Thanks guys, I have installed lubuntu on that computer, and it seems to work great, however Flash runs extremely slowly, apparently my computer does not quite reach the system requirements (weird since I remember running Flash games on ancient Windows 98's a decade and a half ago). Is there a way to speed up Flash? (Yes, Flash sucks)

A second problem is that I currently receive no sound what so ever, what should I do to fix this issue?

Also, is there a good fast lightweight browser that you guys can recommend, I would prefer if it can run Flash.

---

### Post by sudodus on 2014-04-08
Flash has grown during this decade, and needs much more horsepower now. Maybe you can change the settings to run in low resolution mode.

I usually install pulseaudio and pavucontrol into Lubuntu. Using pavucontrol you can tweak your audio system much more thoroughly and should be able to find a setting that works.

```
sudo apt-get install pulseaudio
sudo apt-get install pavucontrol
```

You can try the web browsers Midori or Xombrero.

---

