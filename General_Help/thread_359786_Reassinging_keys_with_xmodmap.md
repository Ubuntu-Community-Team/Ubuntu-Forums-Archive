---
title: "Reassinging keys with xmodmap"
date: 2007-02-12
forum: General Help
---

### Post by sammydee on 2007-02-12
Hi.

I installed beryl recently on my thinkpad, but it has no windows key. I'd like to use the function key instead of the windows key. Beryl will not recognise this key, but xev will and gives me a keycode of 227.

Is there any way I can remap this so that the function key acts like a windows key, but still works  in the normal way with the function buttons to suspend/blank screen/etc ?

Sam

---

### Post by nereid on 2007-02-12
You could change the key, but I don't know that it will still be used as the function key.

Create a file (for example) .Xmodmap in your home folder

```

keycode 227 = XYZ

```

and replace XYZ with the wanted key. Then you have to load this file with xmodmap everytime you start the Xserver.

---

### Post by sammydee on 2007-02-12
What do I need to replace XYZ with to make it act as the windows key?

Sam

---

### Post by nereid on 2007-02-13
xev says that my left windows key is bound to the key "Super_L". But I don't know if this is the right key, as it acts as a modifier key in my case (like CTRL).

---

### Post by sammydee on 2007-02-14
tried to xmodmap -e 'keycode 227=Super_L' and got:

xmodmap:  commandline:1:  bad keysym name 'Super' in keysym list
xmodmap:  1 error encountered, aborting.

I'm giving up, I'll just use ctrl-shift instead of the super key, its a rarely used combo anyway.

Sam

---

