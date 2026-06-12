---
title: "Ubuntu 14.04 Keyboard &amp; mouse problem"
date: 2014-04-27
forum: General Help
---

### Post by dino2 on 2014-04-27
Hello guys, im encountering one problem. If i leave my laptop (Toshiba Satallite C875D-S7105) untouched for 5-10 hours and when I turn it on the keyboard and the mouse wont work. If I restart the laptop there are 50% chances that it will work. So, once i tried to edit the grub file
```
sudo nano /etc/default/grub
```

then I write some one of these commands 
```

"quiet splash i8042.reset i8042.nomux"

"nosplash i8042.reset=1 i8042.nomux=1"

"i8042.nomux=1 i8042.reset"

```
and when i type sudo update-grub it shows some commands and what I have noticed is that it mentioned something about grub timeout...



[Picture ]("http://i.imgur.com/QEWj9oG.png")
And then when I login into ubuntu I get a notification that the system found an problem and when i try to report it , it wont do that.

---

### Post by dino2 on 2014-04-28
Bumpy

---

