---
title: "[SOLVED] How do I replace a screwed up X11/xorg.conf with a X11/xorg.conf.backup?"
date: 2007-06-11
forum: General Help
---

### Post by proxima estacion on 2007-06-11
Was trying to get my screen resolution up a bit. Now Beryl doesnt work and screen is very 'sticky'.
everything was working then I did this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then did this:

sudo dpkg-reconfigure -phigh xserver-xorg

Then changed the settings from what I think was Vesa to fglrx
and then this did this and blocked out all monitors over about 1280x1024 then did this:

sudo dpkg-reconfigure -phigh xserver-xorg

If I am right I have a backup X11/xorg.conf, can I just replace the curretn with the backup? how do i get it back to how it was??? thanks all!!

EDIT: ATI Radeon x1300 512mb

---

### Post by rscott5 on 2007-06-11
> **proxima estacion said:**
> Was trying to get my screen resolution up a bit. Now Beryl doesnt work and screen is very 'sticky'.
everything was working then I did this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then did this:

sudo dpkg-reconfigure -phigh xserver-xorg

Then changed the settings from what I think was Vesa to fglrx
and then this did this and blocked out all monitors over about 1280x1024 then did this:

sudo dpkg-reconfigure -phigh xserver-xorg

If I am right I have a backup X11/xorg.conf, can I just replace the curretn with the backup? how do i get it back to how it was??? thanks all!!

EDIT: ATI Radeon x1300 512mb

Typing the following will replace the edited xorg.conf with the xorg.conf.backup that you made.

```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

I don't really know anything about X though, so I'm not saying that that will set everything back to the way it was, that will just replace the edited .conf file with the original.

---

### Post by RedSquirrel on 2007-06-11
Using mv in this case _renames_ the xorg.conf.backup file to xorg.conf. If you want to keep that xorg.conf.backup for later use, use cp instead of mv:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf 
```cp is the copy command.

```
cp SOURCE DESTINATION
```Have a look at the man pages for more information:

```
man cp
``````
man mv
```

---

### Post by proxima estacion on 2007-06-13
Thanks RScott5 & RedSquirrel It worked a treat first time!!! thank you!:popcorn:

---

### Post by proxima estacion on 2007-06-13
;);)

---

