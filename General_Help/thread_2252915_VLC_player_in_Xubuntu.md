---
title: "VLC player in Xubuntu"
date: 2014-11-15
forum: General Help
---

### Post by neilajarn on 2014-11-15
Is it possible to tweak the VLC player so that there is an option to "play with VLC" when right clicking on a folder or "add to VLC play list".

---

### Post by nerdtron on 2014-11-15
Not sure for folders but I think you can Open VLC and then drag the folder?

---

### Post by mc4man on 2014-11-15
Don't use xubuntu or thunar but seems that one  way could be - 
In thunar > Edit > Configure custom actions..
So like in screens or fool about for what you want, like.  (- Name & Description can be whatever you wish, ect.

---

### Post by coldcritter64 on 2014-11-16
> **mc4man said:**
> Don't use xubuntu or thunar but seems that one  way could be - 
In thunar > Edit > Configure custom actions..
So like in screens or fool about for what you want, like.  (- Name & Description can be whatever you wish, ect.

Just tested on xfce 4.8 on Debian; good tip this (including the screenshots with vlc "settings"), it works well here. I open directories with vlc all the time from a context menu in Nautilus. Finally, an easy way for me to do so in Thunar now as well. Many thanks.

@OP, mc4man has included all the settings for it to work, as you described in the opening post, in the screenshots. Cheers.

---

### Post by nerdtron on 2014-11-16
Hhhmmm thanks for the tip. Been using Xubuntu for a while and haven't touched custom actions yet.

---

### Post by neilajarn on 2014-11-16
Nice one, that works well thanks. Any ideas on how to get "add to vlc playlist" working on folders and audio files ?

---

### Post by mc4man on 2014-11-16
> **neilajarn said:**
> Nice one, that works well thanks. Any ideas on how to get "add to vlc playlist" working on folders and audio files ?
What are you looking for?
For ex.
1. enqueue  to an already open vlc's playlist  but stay on current track
2. enqueue to an already open vlc & start playing the new track

vlc has some gui settings regarding this, screen  > playlist and instances

For individual tracks vlc should show up in your context menu so if you set as in scr. then 1. above should happen.  For 2. don't enable the enqueue option
Adding a folder via the custom actions would be treated the same.

If you leave those option(s) in scr. disabled then you'd need to use command options to achieve whatever you want, see
 vlc -H 
and search enqueue

---

### Post by neilajarn on 2014-11-19
> **mc4man said:**
> What are you looking for?
For ex.
1. enqueue  to an already open vlc's playlist  but stay on current track
2. enqueue to an already open vlc & start playing the new track

vlc has some gui settings regarding this, screen  > playlist and instances

For individual tracks vlc should show up in your context menu so if you set as in scr. then 1. above should happen.  For 2. don't enable the enqueue option
Adding a folder via the custom actions would be treated the same.

If you leave those option(s) in scr. disabled then you'd need to use command options to achieve whatever you want, see
 vlc -H 
and search enqueue

Many thanks, that works well.

---

