---
title: "Auto starting an application with a specific window size and location"
date: 2015-10-18
forum: General Help
---

### Post by MarissaK on 2015-10-18
Hello all, first time poster and totally new to Linux in general so bear with me. I need to open VLC upon boot but I need the window to be at a specific location and need it to be of certain size. Actually I need them to be at a specific location with a specific size is because I need to put 3 instances of VLC beside each other. Is this even possible with a script?

Thanks in advance

---

### Post by TheFu on 2015-10-18
You cannot run an end-user GUI program without a "session"*created. That happens at login.
You can startup a program just after login.  How that happens depends on the exact version of Ubuntu DE you are using.

If this is a dedicated system, perhaps something smaller and easier to manage like TinyCore Linux would be a better choice?

Also - why VLC? There are other players which have a richer option set at startup.
The available options for every program should be listed inside the manpage for the program.
**man vlc**  - I didn't see any of the standard X/Windows -geometry options. Perhaps mplayer, mpv, or some other player will handle this better?

**mplayer** does support **-geometry x[%][:y[%]] or [WxH][+x+y]** options.

Sounds like a fun project!

---

### Post by HermanAB on 2015-10-18
You can open any window exactly where you want.  How to do it, depends on the desktop system that you are using (Unity, Gnome, KDE, XFCE...).

For Unity, see this:
[https://askubuntu.com/questions/621721/script-or-software-to-open-an-application-window-on-a-specific-viewport-and-po](https://askubuntu.com/questions/621721/script-or-software-to-open-an-application-window-on-a-specific-viewport-and-po)

---

### Post by MarissaK on 2015-10-18
Thanks for the replies. I need VLC because I will be using them to pickup a video feed from a DVB-T transmitter with a USB TV tuner.

---

### Post by TheFu on 2015-10-18
[http://www.linuxtv.org/wiki/index.php/MPlayer](http://www.linuxtv.org/wiki/index.php/MPlayer) shows how to use mplayer with DVB-T tuners, but if VLC is required and unity is being used, then it seems Herman's link is a viable solution. 

From the command line, mplayer has much richer controls. Just depends on your needs.

---

### Post by MarissaK on 2015-10-18
> **HermanAB said:**
> You can open any window exactly where you want.  How to do it, depends on the desktop system that you are using (Unity, Gnome, KDE, XFCE...).

For Unity, see this:
[https://askubuntu.com/questions/621721/script-or-software-to-open-an-application-window-on-a-specific-viewport-and-po](https://askubuntu.com/questions/621721/script-or-software-to-open-an-application-window-on-a-specific-viewport-and-po)


Thanks HermanAB, I am using unity.  ^That seems to be a good approach thanks, but I need to add arguments to VLC because I open the tuner as follows:
vlc dvb-t://frequency=474000000:bandwidth=8  :dvb-adapter=0 :live-caching=300

The first script doesn't allow for arguments. 

The edited 2nd script does but I get an error with that. 

```

Traceback (most recent call last):
  File "/bin/setwindow2", line 7, in <module>
    target_vp = int(sys.argv[6])
IndexError: list index out of range



```

---

