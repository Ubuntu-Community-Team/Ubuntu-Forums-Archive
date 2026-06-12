---
title: "xgl compiz"
date: 2006-08-02
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-08-02
How do I get xgl/compiz running? I've tried two guides, both of which didn't work. I log-in anfd then the screen goes black.

AMD 64 proc though i'm running 32-bit. ATI 

radeon express 200

It's my tenth attempt, and it's getting really annoying.

---

### Post by siplus on 2006-08-02
I haven't run XGL on ATI hardware yet, so I can't help with any specific problems, but you have installed ATI's proprietary driver, or are you using the default driver?

I googled for some XGL hardware compatability lists, found these two links:

[http://en.opensuse.org/Xgl#Hardware_Advisory](http://en.opensuse.org/Xgl#Hardware_Advisory)
[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#ATI_Cards](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#ATI_Cards)

Neither of them are from the ubuntu project, but hardware is hardware :)

Hope this helps

---

### Post by distroman on 2006-08-02
Did you try a HowTo from [http://www.compiz.net/index.php](http://www.compiz.net/index.php) I just did and it's up and running.
I use Nvidia, but maybe the top one for you? (ati 32 bit)?

---

### Post by tubo on 2006-08-03
On black screen problems: make sure when running ATI that the Device section of /etc/X11/xorg.conf includes the (undocuemnted) KernelModule line -- mine looks like this:
```

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "KernelModuleParm" "agplock=0"

EndSection
```

best
tubo

---

### Post by 23meg on 2006-08-03
Try Automatix Bleeder.

---

