---
title: "Extremely weird problem, Firefox 3b5, Hardy"
date: 2008-05-02
forum: General Help
---

### Post by daehenoc on 2008-05-02
Hi all,

I upgraded this Dell Latitude D630 (AU) from Gutsy to Heron a few days ago.  It's working great, solved some wireless instability (fingers crossed) but the one problem I have found is this:

Browsing to the recent discussion about Pidgin ([http://developer.pidgin.im/ticket/4986](http://developer.pidgin.im/ticket/4986)), I get the page in Firefox successfully, but as soon as I try to scroll down the page (using either the page down or arrow keys, or the mouse scroll wheel!) X bombs out and restarts?!

Any idea why that would be?

Thanks,
G

---

### Post by daehenoc on 2008-05-02
OK, I just did it (caused X to restart) and had a look in /var/log/Xorg.0.log.old:

```
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f07420]

Fatal server error:
Caught signal 11.  Server aborting
```

Does anyone have any tips? :)

---

### Post by lemming465 on 2008-05-02
Commiserations; you found a bug in the X server.  Signal 11 is an addressing violation; it went off looking for memory it didn't own.  If you are comfortable with troubleshooting, reporting this in launchpad would improve the odds that it gets fixed.

As a workaround, try using a different web browser on that page, such as konqueror.

---

### Post by daehenoc on 2008-05-02
Woot, go me!  I thought about it a bit more and disabled the restricted driver for the Nvidia video card (nvidia-glx-new module), rebooted and could browse that web page successfully!

Warning: silly question coming up.

What and where is launchpad?

---

### Post by daehenoc on 2008-05-02
OK is the launchpad you refer to here: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) ?

Also, I've install epiphany-browser and the same problem happened in that browser.

---

### Post by daehenoc on 2008-05-02
I love replying to myself.  I have logged this bug in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/225988](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/225988)

---

### Post by greengrocer on 2008-05-03
> Woot, go me! I thought about it a bit more and disabled the restricted driver for the Nvidia video card (nvidia-glx-new module), rebooted and could browse that web page successfully!

.. Yes, but at the expense of leveraging the advanced features of your graphics card.

---

### Post by daehenoc on 2008-05-03
> **greengrocer said:**
> .. Yes, but at the expense of leveraging the advanced features of your graphics card.Yes, I knew that I would loose the advanced features, but since this laptop is being used by a Director of a French Cultural center, he's not too fussed about the Visual Effects available.  He does web browsing, email and some document editing and that's about it!

---

