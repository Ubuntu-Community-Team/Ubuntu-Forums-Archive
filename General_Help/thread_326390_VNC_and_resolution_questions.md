---
title: "VNC and resolution questions"
date: 2006-12-27
forum: General Help
---

### Post by cmspaz on 2006-12-27
I'm running Edgy on my server, which doesn't get a dedicated monitor unless I'm doing a lot work on it, so I generally use VNC and/or SSH to work with it. However, if the box boots without a monitor attached, the maximum resolution I can get over VNC is 800x600, with the only other option being 640x480.

So, first question, how can I set it so that I get a higher resolution (1280x720) over VNC?

Now, I also would like to be able to log into the machine after a reboot through VNC, however Ubuntu VNC doesn't start until after the Xserver has been started... which happens after you log in.

Second question, how can I get the Ubuntu VNC to start before the Xserver at the login screen?

---

### Post by KenSentMe on 2006-12-27
About your first question: i think you can add a higher resolution to your /etc/X11/xorg.conf file. Or delete the 800x640 and smaller and only make a higher resolution available.

---

### Post by cmspaz on 2006-12-27
The only display modes listed in the xorg.conf are listed for the monitor I've been using. 

```
Identifier     "Default Screen"
Device     "ATI Technologies, Inc. Rage 128 RF/SG AGP"
Monitor     "BenQ T701"
<display modes here>
```

There is no generic section. Those modes will only be available when the monitor is plugged in.

---

### Post by alexport2 on 2006-12-29
I have the same problem. I tried to connect through vnc4server but no luck. I also tried the tutorial for vnc4server but no luck either. Do I have to shut down vino in order to connect through vnc4server? 

The answer for your second question my friend is to enable automatic login at /system/administration/security tab.

(I 'm a newb too so be gentle...)

---

