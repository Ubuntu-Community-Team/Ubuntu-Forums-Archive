---
title: "Alternate keyboard/mouse shortcuts"
date: 2013-04-08
forum: General Help
---

### Post by Ck.asdf on 2013-04-08
I have a laptop that does not have any media keys, so I used the keyboard shortcut GUI to make:
F8   - play/pause 
F9   - track back
F10 - track forward

However, when I plug in my external keyboard, which does have media keys, I still have to use the F8-10 keys instead of the media keys, since I had to re-assign them.

Is there a way of creating multiple shortcut possibilities for the same function?  So that F8 will be play/pause, as will the play/pause button on the external keyboard.  Additionally, I've got a Logitech VX Revolution with a zoom slider that would be cool to map to the system volume.

I'm currently on Ubuntu 12.10 with Gnome3.

Thanks!

---

### Post by Vaphell on 2013-04-08
try xdotool, it can fake keypresses

i'd try to configure Play as XF86AudioPlay (multimedia key) and F8 as a custom shortcut that runs
```
xdotool key XF86AudioPlay
```
if it works, your standard keyboard will be able to send fake multimedia signal that will be recognized by default settings.

[http://askubuntu.com/questions/235126/simulate-media-keys-in-terminal](http://askubuntu.com/questions/235126/simulate-media-keys-in-terminal)

---

### Post by Ck.asdf on 2013-04-08
Perfect!  It took me a few moments to figure out how to apply xdotool, but then I found out that I go back to the keyboard shortcuts GUI, create a custom shortcut that has the command you mentioned above invoked by F8, and it works quite nicely.  Same with F9 & F10 for skip back/forward.

I can't get it to work with my mouse zoom slider, though.  Any thoughts on that?  
Here's an image of the mouse with the zoom slider:
[http://candeiasonline.net/tray/images/logitech_vx_revolution.jpg](http://candeiasonline.net/tray/images/logitech_vx_revolution.jpg)

Anyway, thank you very much for helping me to get my keyboard to behave! :)

---

