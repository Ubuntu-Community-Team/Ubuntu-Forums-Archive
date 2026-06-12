---
title: "Touchscreen on Laptop (wrong forum?)"
date: 2016-10-16
forum: General Help
---

### Post by schutnik on 2016-10-16
I'm having trouble calibrating my touchscreen on my laptop.  I didn't know if this would count as a "tablet" problem or a "normal" problem.

I've tried following instructions from several web sites using xinput_calibration tool and saving the settings in the /etc/share/X11/xorg.conf.d path, but I cannot seem to get anything to make any difference.  i'm hoping someone can point me the right direction to some logs or something to see what I'm doing wrong.

The machine is a HP tx2520er machine (HP Pavilion tx 2000) labelled.

I apologize if this is the wrong forum - if so, feel free to move my post or tell me where I should post it ;)

Thanks!

---

### Post by mily2 on 2016-10-16
Hi Schutnik,

This is Ubuntu Touch forum: [URL="https://www.ubuntu.com/phone"]https://www.ubuntu.com/phone

[/URL]Perhaps you should ask the question in [General Help]("https://ubuntuforums.org/forumdisplay.php?f=331") forum.

---

### Post by schutnik on 2016-10-17
I figured it out... Now waiting for rights to edit the Wiki so I can describe what I had to do on wiki ([https://wiki.ubuntu.com/Touchscreen](https://wiki.ubuntu.com/Touchscreen)).

Basic idea - used the information here: [http://linuxwacom.sourceforge.net/wiki/index.php/Calibration](http://linuxwacom.sourceforge.net/wiki/index.php/Calibration)
Then set up Xsession.d file with (one for each device in question): 
```

xsetwacom set "<devicename>" Area <xmin> <ymin> <xmax> <ymax>

```

I found the name(s) of the devices I needed to fix using xinput list (in my case, they were "Wacom ISDv4 93 Pen stylus").

Thanks

---

### Post by howefield on 2016-10-17
Thread moved to the "*General Help*" forum.

> **schutnik said:**
> I figured it out...

Congrats :)

---

