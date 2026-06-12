---
title: "Display Settings Lost On Restart"
date: 2015-12-03
forum: General Help
---

### Post by re1d on 2015-12-03
Hi! Have used Ubuntu on System76 computers & other hardware for about 10 years - at first with Gnome, then later (for the past few years) with Unity. My present System76 box is a 15" Pangolin: i7, 8GB RAM, Samsung 840 SSD. I also run an Acer 22" monitor as a second display using an HDMI hookup.

I used to like Gnome, so I thought I'd try the latest Gnome again in the form of UbuntuGnome 14.04 LTS. I installed it alongside my existing work installation of standard vanilla Ubuntu 14.04, which has been working great in every respect. My idea was that I'd run UbuntuGnome for a few months alongside my working install to see how I liked it. If I liked it well enough, I might go for UbuntuGnome, instead of plain vanilla Ubuntu, when the next LTS comes out.

I installed UbuntuGnome and everything went fine, as expected. But I've run into one glitch I can't figure out. It's the Display Settings - I have **the laptop physically located to the RIGHT of the big display**, using the laptop as the primary display. The default Display setting is the other way round, with the laptop screen in the Display dialogue shown to the left of the second display. 

In Unity, no problem - I re-arranged the screens in Display Settings and applied it, and it was set forevermore. *But in Gnome, when I re-arrange the screens and apply the setting, the setup only lasts during the current session.* If I shut down, the settings revert to the default, which is to have the laptop screen to the LEFT of the larger display. So every time I start, I have to go to the Display Settings and correct it. Pain in the ass - a minor one, admittedly, but still a pain.

So: **Does anyone know how to make the display settings "stick" between starts?**

Thanks! :)

---

### Post by jim_deadlock on 2015-12-03
I had the exact same problem (with native Ubuntu Gnome), I wanted a mirrored display for my TV, solved it by putting an xrandr line in my startup apps:

```
xrandr --output HDMI-0 --pos 0x0
```

---

### Post by re1d on 2015-12-05
> **jim_deadlock said:**
> I had the exact same problem (with native Ubuntu Gnome), I wanted a mirrored display for my TV, solved it by putting an xrandr line in my startup apps:

```
xrandr --output HDMI-0 --pos 0x0
```

Thanks, Jim! Appreciate the response.

Just to be certain what we are talking about: will the command you quoted *reverse* the order or position of the two monitors - or will that command result in the 22" monitor *mirroring* the primary (laptop) monitor? I don't want mirroring - I'm using the big display for additional desktop real estate. I just want to reverse the two monitors' left-right relationship, and have it stay that way between starts. 

Cheers!

---

### Post by jim_deadlock on 2015-12-05
First you would need to find out the IDs of your active displays:

```
xrandr
```

Then:

```
xrandr --output RIGHT-SCREEN-ID --right-of LEFT-SCREEN-ID
```

Put that in your startup apps and you're all set.

Don't forget to mark thread as solved.

---

### Post by re1d on 2015-12-05
Thanks Jim! Much appreciated.

---

