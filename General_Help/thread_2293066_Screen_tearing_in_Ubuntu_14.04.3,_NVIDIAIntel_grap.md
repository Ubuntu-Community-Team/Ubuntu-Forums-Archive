---
title: "Screen tearing in Ubuntu 14.04.3, NVIDIA/Intel graphics"
date: 2015-09-02
forum: General Help
---

### Post by kyle55 on 2015-09-02
I really hope someone here can help, because I'm very close to giving up and moving back to Windows. I have an MSI GT70 Dominator ([http://www.amazon.com/gp/product/B00PR1F2YQ](http://www.amazon.com/gp/product/B00PR1F2YQ)) with an i7-4710MQ 2.5 GHz, Intel HD 4000 (I'm pretty sure) integrated graphics card, and a GeForce GTX 970M/PCle/SSE2 dedicated graphics card. I started with a stock install of Ubuntu 14.04.3, and there is terrible screen tearing in every program I've tried, from Chrome to Minecraft to L4D2. I'm using the proprietary Nvidia drivers (version 346.82 from nvidia-346) because I've heard they get the best performance.


[LIST]
[*]I've tried going to Nvidia X Server Settings to turn on "Sync to VBlank", but the problem persists.
[*]I tried installing Bumblebee as well, but when using the optirun command to open a browser and going to a Youtube video, the screen tearing is still there.
[*]I've also tried going to usr/share/lightdm/lightdm.conf.d and editing the 5-xserver-command.conf to have the -bs option.
[*]After some advice from reddit, I upgraded to 15.04, but that didn't work.
[*]I tried setting my Nvidia power settings to high, no luck.
[*]I've tried Compton and Compiz, neither did squat.
[*]I've tried [https://wiki.archlinux.org/index.php/NVIDIA#Avoid_tearing_with_GeForce_500.2F600.2F700.2F900_series_cards](https://wiki.archlinux.org/index.php/NVIDIA#Avoid_tearing_with_GeForce_500.2F600.2F700.2F900_series_cards), nada.
[/LIST]

I've rebooted after every attempted fix. I really want to use Ubuntu, but if this screen tearing persists, I might just have to go back to Windows, it's horribly distracting. Please, please, please help me. Tonight, I'm going to a brand new install of Ubuntu 14.04.3, and any help anyone can give will be greatly appreciated, thanks!  I am open to other distributions and other DE's, anything to fix the tearing.

---

### Post by ptn107 on 2015-09-02
What about nvidia-355?

---

### Post by kyle55 on 2015-09-02
Tried.  Still has tearing.  I think part of the issue is that fact that in the X Server Display Configuration in nvidia-settings, there is no screen displayed in "Layout", X Screen 0 is the only thing selectable in "Model", and whenever I try to Save to X Configuration File, it says "Failed to generate X config file!"  I meant to put this in the OP, but it slipped my mind, apologies.

---

### Post by v3.xx on 2015-09-02
I do not run it, but have seen good reviews on MateMint and newer graphic cards.  It may be a easy way out, can't say for sure, just a thought.

---

### Post by kyle55 on 2015-09-02
That's the second recommendation I've gotten for trying out Linux Mint.  I'm going to do my fresh install of Ubuntu, try a few more things.  If that doesn't work, I'll give Mint a try.  I have no particular preference for one over the other, I've just used Ubuntu for a little while now (six months or so) and have really enjoyed it so far- until I got this laptop, that is.  My old one was ATI instead of Nvidia, and for all its horribleness, it didn't tear.  Thanks.

---

### Post by v3.xx on 2015-09-02
Its based on ubuntu as far as I know.

Good luck :)

---

### Post by mc4man on 2015-09-02
I've tried for some time regarding nvidia mobile with optimus & compositing WM/DE. There is no solution as nvidia-prime can't yet provide  vsync & while some claim different,  bumblebee seems not to work well or consistently with video playback.

Here then I've only used the Intel gpu for linux(Ubuntu), maybe look for a non compositing distro. 
(there are some claims that the lack of vsync in nvidia-prime will be addressed at some point or maybe wayland will be a solution some day.

Otherwise I've looked for a laptop with nvidia only (no optimus), that has proved difficult as most Intel mobile cpu's with nvidia mobile gpu's include optimus. The alternative of getting a laptop with a desktop cpu hasn't worked out yet as the one I tried ran way too hot to be useful so was returned. Whether there are any laptops with desktop cpu's & excellent cooling I'm not sure, certainly none for less than 2k & everytime I buy & return costs me about $100 in shipping costs/deductions so for the moment have given up..

[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1260128](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1260128)
from email to/from maintainer - 
```
On 19-08-15 18:56:20, mc4man wrote:
> More a question, Is there any hope of getting vsync with nvidia-prime?
>

That is not something I can add. It depends on upstream kernel work. I
think Maarten Lankhorst (at Intel) was working on it.
```

---

### Post by kyle55 on 2015-09-02
Okay, so basically, it's just a problem that's not going away, no matter what I try?  So long as I have a hybrid graphics setup, the screen will tear, regardless of distribution or DE because the problem is with Linux itself?

---

### Post by kyle55 on 2015-09-03
Solved.  Freshly installed Ubuntu 14.04.3, installed the ppa from [http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action), then added Option "TearFree" "True" to the Intel device section of xorg.conf.

---

### Post by v3.xx on 2015-09-03
Congratulations and nice find.  I have bookmarked that :)

---

### Post by mc4man on 2015-09-03
Can confirm that the xorg option does reduce tearing, most effective here with the 355 drivers. It eliminates about 98% of tearing, I've one test vid that still shows some really minor occasional tearing.
So at least with recent nvidia mobile cpu's one  can get a usable Ubuntu
(- and will make the search for my next laptop much easier, can justify paying for the nvivia gpu
Thanks for pursuing...

---

### Post by mc4man on 2015-09-03
Just to note - 
If using nvidia-prime to switch to intel gpe then xorg.conf is moved to xorg.conf.xxxxxxx. When switching back to nvidia gpu the old xorg.conf is not reused, instead a new one is created which will not have the tear line.
No way around that unless whichever source creates that xorg.conf can be altered to include that line by default.

---

### Post by jgor on 2015-09-06
> **kyle55 said:**
> Solved.  Freshly installed Ubuntu 14.04.3, installed the ppa from [http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action), then added Option "TearFree" "True" to the Intel device section of xorg.conf.

Thank you so much for finally finding a fix for me! I've been dealing with this problem for many days and have tried so many different things. I am on xubuntu 14.04.3 with a nvidia 940m and core i5 intel processor (MSI Notebook GP70 2QE-491CA). The above is the only thing that fixes the tearing for me, and it doesn't even require display composting to be enabled!

---

### Post by jermann-matjaz on 2016-03-09
> **kyle55 said:**
> Solved.  Freshly installed Ubuntu 14.04.3, installed the ppa from [http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action), then added Option "TearFree" "True" to the Intel device section of xorg.conf.

But this results in lag and latency of input and display :S

---

