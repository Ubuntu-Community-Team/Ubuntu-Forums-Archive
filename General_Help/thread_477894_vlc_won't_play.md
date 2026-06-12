---
title: "vlc won't play"
date: 2007-06-18
forum: General Help
---

### Post by tronica on 2007-06-18
I just got done installing ubuntu on my laptop and then installed vlc, when i try to open a video with it, vlc opens for a split second then closes. so i ran it from the terminal and here what i got

```
tronica@laptop:~$ vlc diggnation--0102--2007-06-14--large.xvid.avi 
VLC media player 0.8.6 Janus

(.:8568): Gtk-WARNING **: Theme directory 22X22/actions of theme areo-linux has no size field


(.:8568): Gtk-WARNING **: Theme directory 24X24/stock/generic of theme areo-linux has no size field

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83
tronica@laptop:~$ 

```

any ideas

nevermind, i closed beryl, and the problem went away. now my question is why would beryl cause such as this?

---

### Post by Kodfish on 2007-06-18
Try using mplayer. See if that helps.

---

### Post by tronica on 2007-06-18
i tried that and i get a pop with an error on it

"Error opening/initializing the selected video_out (-vo) device"

---

