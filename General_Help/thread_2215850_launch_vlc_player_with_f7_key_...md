---
title: "launch vlc player with f7 key .. ?"
date: 2014-04-08
forum: General Help
---

### Post by roiikkata on 2014-04-08
hi,

   i tried searching for it everywhere and even tried the commands from xotools or whatever its called

can somebody let me know how to launch vlc player in ubuntu 13.10 with the f7 key .. ?

i tried typing in "vlc" and "vlc media player" in the shortcut command in the keyboard shortcuts "custom" hotkey menu for the f7 key, "vlc media player" just crashes the computer and the command "vlc" just does nothing.

ive been trying to figure this out forever. sorry if this is a simple answer to this but im still kind of new to the operating system, so ..  thanks ..

---

### Post by ajgreeny on 2014-04-08
What happens if you use the command **vlc** in terminal?
Does it crash the computer?
Does vlc start?
Does nothing happen?

---

### Post by roiikkata on 2014-04-08
vlc starts but if i put it into the command section of the hotkey manager custom shortcut window it doesnt do the same thing. my cpu doesnt even go up or run faster like its launching something if i run the hotkey from it ..
but, in the terminal it works with no errors
its confusing me . .

---

### Post by roiikkata on 2014-04-08
vlc 2.0.8 "twoflower"

---

### Post by Bucky Ball on 2014-04-08
*Thread moved to **General Help**.*

---

### Post by mc4man on 2014-04-08
The command would be just
vlc
It's probable in 13.10 that custom shortcuts don't take effect until you log out/in after setting
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1243532](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1243532)

(- fixed in 14.04 at least in an ubuntu session, ie. unity-settings-daemon

---

### Post by roiikkata on 2014-04-08
bingo. thank you.

---

