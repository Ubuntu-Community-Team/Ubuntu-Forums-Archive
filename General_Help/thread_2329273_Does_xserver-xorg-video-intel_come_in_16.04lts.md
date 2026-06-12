---
title: "Does xserver-xorg-video-intel come in 16.04lts?"
date: 2016-06-29
forum: General Help
---

### Post by ronnie4 on 2016-06-29
I got lubuntu to correctly boot after installing the intel video drivers, but real vnc only shows a black screen when the computer itself goes to the lock screen. This is because when the computer locks, the graphics glitch and goes to that seem black screen I used to get on boot, but then the gui quickly comes back. This momentary abscence of video I believe messes up the realvnc connection and you can only log in at the computer itself. Does regular Ubuntu not have this problem with the graphics?

Thanks.

---

### Post by sudodus on 2016-06-29
If you are running an installed system it is easy to install it into Lubuntu.

```
sudo apt-get install xserver-xorg-video-intel
```

But if you want it in a live drive (and the iso file), *yes*, this package comes with Ubuntu 16.04 LTS (and I think Xubuntu 16.04 LTS too).

---

### Post by ronnie4 on 2016-06-29
Thanks for the help. yes I got it working in lubuntu but it is still buggy so I want to try regular ubuntu again.

-Ron

---

### Post by sudodus on 2016-06-30
If you tell us about the computer, particularly the

- *brand name and model* of the computer itself or the motherboard if home-built
- CPU (brand name and model)
- graphics chip/card (brand name and model)
- wifi chip/card (brand name and model)
- RAM (size in MB or GB)

it will be easier to give more detailed advice.

---

### Post by ronnie4 on 2016-06-30
It's a Dell optiplex 755 small form factor
intel core2 duo 2.4ghz
4gb ddr2 ram
intel integrated graphics (believe chipset is q35 not 100% sure)
onboard gigabit ethernet

---

### Post by sudodus on 2016-06-30
That computer should work with any of the Ubuntu flavours (including standard Ubuntu), but it might play video better, if you install one of the ultra light (Lubuntu) or medium light flavours (Xubuntu and Ubuntu MATE). So I suggest that you try them live and then settle with the flavour that you like best. One advantage with standard Ubuntu is that the LTS versions have 5 years of support, while the other flavours have only 3 years of LTS.

So there are still 3 years to go with ***Ubuntu 14.04.1 LTS*** (if that would play better with your computer hardware than any of the 16.04 LTS flavours).

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by ronnie4 on 2016-06-30
Thanks for the info, yeah Lubuntu was really buggy for me, I ended up going with regular ubuntu 16.04 lts, I was running 14.04 before which was rock solid, but after upgrading some hardware, figured I'd give the new version a shot. So far so good, everything working smoothly.

---

