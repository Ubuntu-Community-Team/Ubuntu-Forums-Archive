---
title: "Poor Performance: Where do I start"
date: 2014-01-26
forum: General Help
---

### Post by backfour94 on 2014-01-26
I am experiencing general poor performance but don't know enough about Ubuntu to know where to start.

When I first installed it performance was fine, now it even takes a while for the 'systems settings' window and the unity search pane to start up or display.  I get frequent greying of windows for several seconds often enough to make using the system a pain. I did have backup running daily and stopping that made a difference but not to the point that I didn't feel I needed to dig much more.  I can't track it to a particular update of Ubuntu.

I am running a Toshiba Satelite Pro Laptop: Genuine Intel® CPU T1600 @ 1.66GHz × 2.  Graphics: i Mobile Intel® GM45 Express Chipset x86/MMX/SSE2

Ububtu 13.10.

System Monitor shows less than 40% cpu utilisation, 60% memory usage of 935.1 MiB, Swap usage of 40% of 2.9 GiB.  Network history bubbles along at near 0%.  Which all look fine to me.

I just want to know where to look to try to identify what is wrong.

Thanks for any help.

---

### Post by sudodus on 2014-01-26
With such hardware I would switch to a lighter desktop environment, Xubuntu or Lubuntu. You can do that within your current installation (the only draw-back being some doublets of utilities) or make a fresh installation. Xubuntu is medium light and Lubuntu is ultra-light.

```
sudo apt-get install xubuntu-desktop
sudo apt-get install lubuntu-desktop

```
After installing one or two of these desktop environments, you switch session at the log in screen. Click on the round symbol (see that attachment).

It is also possible to install only the corresponding desktop environments

```
sudo apt-get install xfce4
sudo apt-get install lxde
```

---

### Post by backfour94 on 2014-01-26
Thanks for this.  Have install Lubuntu and will give it a go; looks like windows though :--(

---

### Post by sudodus on 2014-01-26
Xubuntu might be better for you, try them all before you settle down with what is best for you :-)

---

### Post by backfour94 on 2014-02-09
Yep Xbuntu seems to be it; thanks for you help.

Just for reference is there something particular that I could upgrade that would make running the full Ubuntu and option?

---

### Post by The Cog on 2014-02-09
> **backfour94 said:**
> Yep Xbuntu seems to be it; thanks for you help.

Just for reference is there something particular that I could upgrade that would make running the full Ubuntu and option?

Yes.
```
sudo apt-get install ubuntu-desktop
```
will do it. But that will leave you with both Ubuntu and Xubuntu bits installed.

---

### Post by sudodus on 2014-02-10
It will run better with standard Ubuntu and the Unity desktop, if you increase the RAM to at least 2 GB.

---

### Post by mastablasta on 2014-02-10
> **sudodus said:**
> It will run better with standard Ubuntu and the Unity desktop, if you increase the RAM to at least 2 GB.

ram is not so much the issue here. Ubutnu should run on 1GB just fine (the desktop memory usage is not that high!). however you would need a good GPU. sicne it's a laptop that is the problematic part to upgrade. in desktop you would just throw in a cheapest new GPU card and it will work well. Unity desktop interface found in Ubuntu is 3D accelerated and is utilising the power of the GPU.

if you used 12.04 you would find Unity 2D that might work well on your config.

also you can make XFCE to look like unity ;-) well aside for dash search and lenses...

---

