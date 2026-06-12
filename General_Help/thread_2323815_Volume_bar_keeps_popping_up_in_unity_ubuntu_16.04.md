---
title: "Volume bar keeps popping up in unity ubuntu 16.04"
date: 2016-05-08
forum: General Help
---

### Post by wolfguy14 on 2016-05-08
Hi, I just installed ubuntu 16.04 64bit and every couple of seconds or so the volume bar that usually comes up when you change your volume via your keyboard pops up. 

It's extremely distracting and annoying. Looking online I've found two fixes, 

one is changing show-notify-osd-on-scroll to false via dconf editor, however it just does not show up at all for me. 

The other is putting in gsettings set com.canonical.indicator.sound show-notify-osd-on-scroll false into terminal but that only wields a "No such key 'show-notify-osd-on-scroll" error. 

Please help me

[INDENT]

[/INDENT]

---

### Post by wolfguy14 on 2016-05-08
I managed to "fix" the problem by replacing pulseaudio with alas

---

