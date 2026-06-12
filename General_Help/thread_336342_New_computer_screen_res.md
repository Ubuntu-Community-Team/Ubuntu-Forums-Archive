---
title: "New computer screen res?"
date: 2007-01-11
forum: General Help
---

### Post by haxer on 2007-01-11
Hello ive got my new computer today... when i was installing ubuntu 6.06 ive got a chance to choise wich screen resolutions i wanted ive just pressed "enter" so ive messed up something becuse now i cant go to screen resolution and choice the one i want 1280x1024 :( anything i can do to make it go to 1280x1024 btw i have 7300gt MSI nvidia and ive got the right drivers! ;) :-k

---

### Post by taurus on 2007-01-11
You can edit /etc/X11/xorg.conf and add that screen resolution to it, "1280x1024".

Applications -> Accessorries -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```
Save it and restart X with <Ctrl><Alt>Backspace.

---

### Post by rioghal on 2007-01-11
If you want to add new screen resolutions to xorg, you can do that with this command:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Then restart xorg with CTRL+ALT+Backspace

---

### Post by haxer on 2007-01-11
Thanks both worked fine :)

---

