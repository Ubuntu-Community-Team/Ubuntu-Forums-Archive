---
title: "seg fault in beryl, glxgears after latest updates"
date: 2006-11-08
forum: General Help
---

### Post by Basho on 2006-11-08
Hi, everyone. I'm running Kubutu Edgy, installed on a clean machine from the CD. My graphics card is an nVidia GeForce Ti 200. Beryl, 3D acceleration, etc., were all working fine for me until my last update yesterday. After updating, I can boot fine to the desktop but I get a segmentation fault running beryl-manager or glxgears from the command line.

These are the three updates that are available, and which cause the situation:

linux-restricted-modules-generic:
  2.6.17.5-12~amaranth --> 2.6.17.6-2~amaranth

linux-restricted-modules-common:
  2.6.17.5-12~amaranth --> 2.6.17.6-2~amaranth

nvidia-glx
  1.0.9625+2.6.17.5-12~amaranth --> 1.0.9629+2.6.17.6.2~amaranth

Downgrading (by manually installing the older packages from the cache) gets everything to work again.

Am I missing a step (just using Adept and then rebooting)? Anyone else seeing this? Any solutions/suggestions?

Thanks from this just-above-a-novice ...

---

### Post by aoanla on 2006-11-08
This isn't much help to you, I know, but I have the same problem. Clearly there's an issue with amaranth's latest compiles...

---

### Post by Basho on 2006-11-08
It is a help, though. At least I'm not (and you're not) the only one.

If you do end up finding a solution here or elsewhere, please post here. Otherwise, I'll wait for the next build.

---

### Post by PriceChild on 2006-11-08
I'll try and get in contact with him for you.

---

### Post by toma222 on 2006-11-08
Hi,

It's a problem with 9629 drivers and Geforce 4 serie.
See [here]("http://www.nvnews.net/vbulletin/showthread.php?t=79703").

---

### Post by PriceChild on 2006-11-08
> **toma222 said:**
> Hi,

It's a problem with 9629 drivers and Geforce 4 serie.
See [here]("http://www.nvnews.net/vbulletin/showthread.php?t=79703").Nope... just some Geforce 4 Ti's.... or more specifically some with a Nv2 chipset or something. Check out the link :)

---

### Post by amedias on 2006-11-09
excellent, so now i know what the problem is....

how do i go back to the old drivers.

I had just done a clean install on my machine and can only see the 9629 release in repositories...how do i go back to old (9626) versions!

sorry but im fairly new to this and just getting to grips with it all!

thanks

---

### Post by jonasan on 2006-11-10
> **amedias said:**
> excellent, so now i know what the problem is....

how do i go back to the old drivers.

I had just done a clean install on my machine and can only see the 9629 release in repositories...how do i go back to old (9626) versions!

sorry but im fairly new to this and just getting to grips with it all!

thanks

I have exactly the same problem. Im at work at the moment so I havent tried this, but post your findings

*A specific version of a package can be selected for installation by following the package name with an equals and the version of the package to select. This will cause that version to be located and selected for install. Alternatively a specific distribution can be selected by following the package name with a slash and the version of the distribution or the Archive name (stable, testing, unstable).*

Enjoy!

---

### Post by jonasan on 2006-11-10
I might just add that the above quote was from [http://www.die.net/doc/linux/man/man8/apt-get.8.html](http://www.die.net/doc/linux/man/man8/apt-get.8.html) and I assume you would have to use apt-get.

Good Luck!

---

### Post by Basho on 2006-11-10
> **amedias said:**
> how do i go back to the old drivers.



I just went into /var/cache/apt/archives and reinstalled the older packages. I even put copies of them in my home folder for easier access, just in case some future update proves to be a problem.

---

### Post by PriceChild on 2006-11-10
Seems from recent reading that the problem we diagnosed you with should only happen with 97**...

We've got the wrong diagnosis here.

---

