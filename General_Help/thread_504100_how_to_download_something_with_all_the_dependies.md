---
title: "how to download something with all the dependies?"
date: 2007-07-18
forum: General Help
---

### Post by bone2006 on 2007-07-18
I have a system that has internet and one that doesn't.  I want to install VLC on the system that doesn't have internet, is there an easy way to install it with all the dependencies?

I used the synaptic package manager and clicked download only, but thats' only the main program since it's already installed it doesn't seem to download again the dependences in the /var/cache/apt/archives directory

When I right click on VLC in the synaptic package manager and look at decencies it's annoying to search and download each when there's probably at least 10.  Seems like there should be an easier way to get VLC on another computer with the dependencies when there's no internet on that system?

---

### Post by AlexenderReez on 2007-07-18
try to use aptoncd --->

> [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)


to install

> sudo aptitude install aptoncd

read the instruction given with the package...

---

### Post by overdrank on 2007-07-18
> **bone2006 said:**
> I have a system that has internet and one that doesn't.  I want to install VLC on the system that doesn't have internet, is there an easy way to install it with all the dependencies?

I used the synaptic package manager and clicked download only, but thats' only the main program since it's already installed it doesn't seem to download again the dependences in the /var/cache/apt/archives directory

When I right click on VLC in the synaptic package manager and look at decencies it's annoying to search and download each when there's probably at least 10.  Seems like there should be an easier way to get VLC on another computer with the dependencies when there's no internet on that system?

Hi maybe this link will help!
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Happy_Man on 2007-07-18
....nope. Always, when you are dealing with a problem b/t unresolved dependencies and an internet issue, get the internet issue resolved first. It's by far more important than anything else. 

Having said that..... what's up with your internet?

---

### Post by bone2006 on 2007-07-23
Honestly the internet is frustrating on this system.  I had to use ndiswrapper and find the windows drivers and spent hours and hours getting it to work with an older version of ubuntu, then the new version broke it.  I had to go to ndiswrapper's website and get the latest version for my drivers to work.  it's just really a pain, since I do format often.  Well I think this time the hardware device might have gone out, I can't even get the lights to turn on.

I'm considering just looking for something that works out of the box.  Something that I can get the liveCD to work without messing around with ndiswrapper.   The wifi one I was using is a usb key, so I'm not sure if there are any linux compatible ones of this nature.  But I really want something that just works out of the box and something that isn't going to break with each release.

---

### Post by stchman on 2007-07-23
> **bone2006 said:**
> I have a system that has internet and one that doesn't.  I want to install VLC on the system that doesn't have internet, is there an easy way to install it with all the dependencies?

I used the synaptic package manager and clicked download only, but thats' only the main program since it's already installed it doesn't seem to download again the dependences in the /var/cache/apt/archives directory

When I right click on VLC in the synaptic package manager and look at decencies it's annoying to search and download each when there's probably at least 10.  Seems like there should be an easier way to get VLC on another computer with the dependencies when there's no internet on that system?

[http://packages.ubuntu.com/feisty/graphics/vlc](http://packages.ubuntu.com/feisty/graphics/vlc)

This lists all the dependencies of VLC.  Download all the packages and then do a:

sudo dpkg -i *.deb

---

### Post by hessiess on 2007-07-23
if your internet aint working, get new hardwere that dus, it will save you alot of time, outherwise you may never get it to work

---

### Post by bone2006 on 2007-07-24
Any recommendation on hardware?  I'm just looking for something cheap
I have a buffalo router with dd-wrt firmware on it that's an 802.11g.  I'd prefer a USB device, but I have plenty of PCI slots to use.

Kind of wish there was an installer that I could download or one single package.  Wish ubuntu or linux had something that I could get an entire package with all the required dependices as required.

I mean I only want to install one program and I have to search download and install a few hundred others to get it to work, doesn't seem practical.  I understand that with the internet it's not a problem, but some people have labs in which they don't have access to the internet in labs for security reasons.

---

### Post by -random on 2008-06-16
I know this is an ooold thread, but I also have the same problem, except imagine the off-line pc doesn't have a lan card and is in the middle of the desert.

I need to get vlc for a buddy of mine, but APTonCD doesn't show VLC to be in /var/cache/apt/archives/. any help plz?

thankxs:popcorn:

---

### Post by Happy_Man on 2008-06-16
> **-random said:**
> I know this is an ooold thread, but I also have the same problem, except imagine the off-line pc doesn't have a lan card and is in the middle of the desert.

I need to get vlc for a buddy of mine, but APTonCD doesn't show VLC to be in /var/cache/apt/archives/. any help plz?

thankxs:popcorn:
Well, you could download VLC, and then use APTonCD to get it to your buddy.

---

### Post by -random on 2008-06-16
got it! thnankxz

i had the prob:

> **-random said:**
>  but APTonCD doesn't show VLC to be in /var/cache/apt/archives/.

and the terminal showd:

```

2512
Note: there are some packages installed that are not available in cache

<PackageModel object at 0x84e8b44 (GtkListStore at 0x88d49e0)>
<PackageModel object at 0x84e8b44 (GtkListStore at 0x88d49e0)>
<PackageModel object at 0x84e8b44 (GtkListStore at 0x88d49e0)>
<PackageModel object at 0x84e8b44 (GtkListStore at 0x88d49e0)>
<PackageModel object at 0x84e8b44 (GtkListStore at 0x88d49e0)>
<PackageModel object at 0x84e8b44 (GtkListStore at 0x88d49e0)>
<PackageModel object at 0x84e8b44 (GtkListStore at 0x88d49e0)>
<PackageModel object at 0x84e8b44 (GtkListStore at 0x88d49e0)>
```

so in synaptic I re-installed vlc, and used aptoncd. weo weo..

do i need to worry about those pagagemodel.... terminal messages?

aslo, how do i get my hands on non-cached-packages other than re-installing them? (prob solved, im just curious here)

---

