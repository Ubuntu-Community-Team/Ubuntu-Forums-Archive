---
title: "My weekly video card post"
date: 2007-11-13
forum: General Help
---

### Post by TheOrangePeanut on 2007-11-13
I have an Ati 9500 Pro and use fglrx drivers from the repos.  It is stable when I do every day tasks, but it flat out freezes my system anytime I start a 3d application (say, Neverball, Planet Penguin Racer, Open Arena, etc).  I'd use the open source "ati" driver, but it freezes at the Ubuntu login screen so that's not even an option.

Any idea what I could do to diagnose or fix the problem?  I get good 3d performance in Windows, so I'm fairly certain it isn't a problem with the actual hardware.

---

### Post by TheOrangePeanut on 2007-11-15
Would turning off agp fastwrite in the BIOS help?  I know Nvidia had issues with agp fastwrite a few years ago.

---

### Post by hardyn on 2007-11-15
desktop or notebook?

if desktop, go find a 50$ used nvidia 66/6800 on ebay.

---

### Post by TheOrangePeanut on 2007-11-15
It's a desktop, but that kind of defeat the purpose of Linux being free (as in beer) :)

---

### Post by strabes on 2007-11-15
You're not going to have any luck with ATI until they start getting serious about linux. Their newest driver release, 8.42, does include compositing support but is so buggy and pathetic that it's not worth it. Buy an nvidia card.

---

### Post by hardyn on 2007-11-15
> **TheOrangePeanut said:**
> It's a desktop, but that kind of defeat the purpose of Linux being free (as in beer) :)

linux was never about free as in beer, it was about free as in libre; ubuntu just happens to be free as in beer.  and you do have a free linux system, you just don't have a graphics card that works very well with it.

---

### Post by Colro on 2007-11-15
Try the driver Envy installs, it works great for me:

```
sudo apt-get install envy
```

Then go to Applications -> System tools -> Envy -> click "Install ATI driver" -> Click apply and let it do its thing.

As I said, it works great for me. I've got a Radeon 9600 Pro.

---

