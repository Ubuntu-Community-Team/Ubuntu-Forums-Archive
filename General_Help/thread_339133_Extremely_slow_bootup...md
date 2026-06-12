---
title: "Extremely slow bootup.."
date: 2007-01-15
forum: General Help
---

### Post by Nevermore on 2007-01-15
hi everyone
i have edgy installed on my laptop, a panasonic CF73, centrino 1.4Ghz, 512ram, 40gb hdd.
It worked fine until 3 days ago, i had some speed tweaks, like those:
```

    # defoptions=rootflags=data=writeback elevator=cfq
    # altoptions=(recovery mode) single rootflags=data=writeback elevator=cfq

```
prelink and preload packages installed.
Until then, i had used only with wireless, now i need to connect by the ethernet port, i went in bios, activated the ethernet, then added the configs in network to make it connect, and was fine.
However, when i boot up, it take a good 5 mins to load the desktop, it hangs at the gnome splashscreen, and the whole desktop loads VERY slowly, even if the processor stays at the lowest speed, it takes around 2 mins to see the first stuff on the desktop, another 1 to see all the icon, another 1 to load compiz and all the eyecandy, and 1 more to be able to open a terminal or any program that request sudo privileges..
even sudo mc hangs there until 5 minutes have passed..
what can i do? i tried to remove prelink, but no effect, tried to disable wifi, with good effect but is just a workaround, i deleted .metacity and .nautilus on my home dir, it does speed up things, but just for a couple reboots..
can someone tell me where i should look?
until i turned on ethernet everything was SO SWIFT, now everything is DEAD..
btw ethernet doesn't want to retain the dns settings...
Thanks alot ](*,)

PS i deleted prelink from /etc/cron.daily
no effect, but now how do i recreate it???
sudo /etc/cron.d/prelink doesn't work anymore!

---

