---
title: "Where is this lock screen coming from?"
date: 2015-08-17
forum: General Help
---

### Post by CantankRus on 2015-08-17
Where is this lock screen coming from? 
Can't work out what installed this lock screen which has replaced my unity lockscreen.
The unity greeter is ok just the lock screen has been replaced.

---

### Post by kerry_s on 2015-08-17
go into synaptic-> status-> installed & type "lock" in the search, see whats there.

---

### Post by CantankRus on 2015-08-17
Nothing stands out.
I have gnome-shell installed but "sudo dpkg-reconfigure lightdm" is set to lightdm not gdm.
I don't have any other greeters installed besides unity-greeter.
What config determines the lock screen?
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] ls /usr/share/lightdm/lightdm.conf.d**
50-greeter-wrapper.conf  50-ubuntu.conf         50-xserver-command.conf
50-guest-wrapper.conf    50-unity-greeter.conf  90-nvidia.conf
```

[COLOR="#FF0000"]Edit[/COLOR]: Odd thing is, I see the normal lockscreen in another user account that I leave as default??

---

### Post by CantankRus on 2015-08-17
Couldn't work it out.
Removing **~/.config/dconf/user** restored the normal lock screen.
Had to redo all my customizations stored in dconf though.

---

