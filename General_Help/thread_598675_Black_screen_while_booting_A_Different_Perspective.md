---
title: "Black screen while booting: A Different Perspective"
date: 2007-10-31
forum: General Help
---

### Post by Orion2014 on 2007-10-31
I know its been throughly talked about, the black screen while booting, but honestly I could care less about seeing the ubuntu loading bar, I would prefer to see the UNIX text while booting, actually telling me whats going on. 

Is there anyway to have it do this by default, as in *NOT* having to hit ctrl-F1 every time it boots up?

---

### Post by Orion2014 on 2007-10-31
BuMp

---

### Post by Whiffle on 2007-10-31
Edit  /boot/grub/menu.list 

Remove
quiet splash

from the #defoptions line.

Run  sudo update-grub

---

### Post by Orion2014 on 2007-11-01
Thanks, you were close, but here's what I actually had to do to get this to work. First, I created a launcher on my desktop with the command 

gksudo nautilus


then I browsed to that file, /boot/grub/menu.lst

then, for anyone else trying to do this, DO NOT sudo update grub after editing the file, it will set it back the way it originally was. Just save and reboot, and it did exactly what I was aiming to do.

Thanks for your help

-zebulus

---

