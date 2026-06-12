---
title: "Disable multitouch gestures?"
date: 2014-05-22
forum: General Help
---

### Post by mattgif2 on 2014-05-22
I keep accidentally triggering 3 and 4 finger gestures. Since I never intentionally use any gestures and accidentally triggering them upsets my workflow, I'd like to disable all multitouch gestures (but keep 2 finger scrolling, if at all possible). How do I do this? I couldn't find anything in the default settings menus or within CCSM, but maybe I just missed it. If it helps, I have an Asus Zenbook with an Elantech touchpad.

---

### Post by mattgif2 on 2014-05-28
Bump? This is on the stock 14.04 build. I'm not averse to recompiling Unity from source, if that's what it takes, but I don't know what to look for.

---

### Post by adbiz on 2014-05-28
Go into System Settings>Keyboard and Mouse>Touchpad and uncheck multi gesture

---

### Post by mattgif2 on 2014-05-30
Hey adbiz, thanks for the reply, but I don't seem to have that setting in my mouse/touchpad options. Screenshot of what I see attached. 

[IMG]http://i.imgur.com/cdyBnVh.png[/IMG]

---

### Post by santq on 2014-08-14
I've wasted way too much time on trying to disable this. If you google "disable ubuntu multi-touch gesture" you can see how many people are struggling with the same problem. There REALLY needs to be an option in 14.10 to disable this.

---

### Post by abazhgin on 2014-10-26
See [http://askubuntu.com/a/198524/321521](http://askubuntu.com/a/198524/321521)

synclient ClickFinger3=2
synclient TapButton3=2

---

### Post by mattgif2 on 2014-11-18
Thanks for the reply, abazhgin. I *think* that took care of some of the irritating 3 finger gestures (window switching in particular). I still get the irritating 4 finger dash open & 4 finger launcher reveal, however.

---

### Post by Pilot6 on 2014-11-18
Multifinger gestures are disabled in Ubuntu except 2-finger scrolling. You enabled them somehow, probably by adding some startup commands.
Just remove them.

---

### Post by mattgif2 on 2014-11-24
Which version, Pilot6? 14.04 had them enabled out of the box. The only startup commands I currently have are the two synclient suggested above by abazhgin.

---

### Post by Jack Brown on 2015-03-01
I'm encountering this problem too.  When I need to click and highlight something (click and drag) on the touchpad, it sets off application switcher as well as the dash on Ubuntu-desktop's unity.  I've tried recompiling from source, both from 'apt-get source unity' and from unity's bzr to disable multitouch gestures, but after commenting out some lines in the source as outlined here: [http://askubuntu.com/questions/57586/how-can-i-disable-arbitrary-default-multitouch-gestures-in-unity/205045#205045](http://askubuntu.com/questions/57586/how-can-i-disable-arbitrary-default-multitouch-gestures-in-unity/205045#205045) both produces errors on deb file build.

Current work around:  use gnome desktop environment.
OR use a mouse in Ubuntu's unity.

I was just finding it nice to use unity for some desktops I support, but then this issue cropped up for the touchpad on this laptop, and I'm going back to gnome, at least for this laptop.

---

