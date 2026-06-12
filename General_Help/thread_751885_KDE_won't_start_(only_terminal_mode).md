---
title: "KDE won't start (only terminal mode)"
date: 2008-04-11
forum: General Help
---

### Post by bolwarra_ on 2008-04-11
Hi,
I have an Acer aspire series laptop running Gutsy 32 bit.
I wanted to test an external display (Samsung Syncmaster) on my machine. 

Now, although the external display is unplugged - Ubuntu only boots into a termina,l no KDE. I then plugged the external display back-in hoping to disable any secondary displays..still no go.

I have tried the startx command and get the following error

---
Fatal server error:
Required Entity already in Use!

X10: Fatal IO error 104 (Connection reset by peer)
on X server "0:0" after 0 requests
(0 known processed) with 0 events remaining.
Xauth: error in locking authority file /home/leftblacnk/.Xauthority
----

I had look in /etc/X11/Xorg.conf for any clues, but don't understand how Ubuntu, let alone linux works well enough to go changing any values.

Any help appreciated.

Cheers,
Bolwarra.

---

### Post by kesman on 2008-04-11
You could unplug your external monitor and when it boot to terminal, run command
```

sudo dpkg-reconfigure xserver-xorg

```
to Re-Configure your XORG settings. After doing this, run startx again. If this gives you graphics back, plug in your external monitor and search the KDE menus for graphics and screens or similar to graphically configure your monitors.

---

### Post by bolwarra_ on 2008-04-11
Brilliant!
All systems are go!
Thanks kesman.

---

