---
title: "How to change text scaling factor via terminal"
date: 2014-02-13
forum: General Help
---

### Post by CaptainMark on 2014-02-13
Long story short, my computer room has become a nursery, so the computer got relegated to the lounge hooked up to the main TV. Sometimes when sitting in different seats it's more or less difficult to see any text. Is the there a terminal command that can change the option (usually found in tools like ubuntu-tweak and gnome-tweak-tool) for text scaling factor, it would be really useful to alter it quickly without going through menus.

Regards
Mark

---

### Post by deadflowr on 2014-02-13
Would this work
```
gsettings set org.gnome.desktop.interface text-scaling-factor <newnumberhere>
```
The default is 1.0.
The range is 0.5 to 3.0.
(0.5 being tinny, and 3.0 being huge.)

Edit: I'm guessing the room becoming a nursery means congratulations.

---

### Post by CaptainMark on 2014-02-13
That works great thanks, I just a series of scaling short cuts from 1.1 to 1.9 + 1.0 on my numbers across the top of this infernal wireless keyboard. 

And yes thats exactly what it means, I'll have to wait until 18.04 is released until I get a bigger house and get my desktop back, until then, I've actually found a use for Unity, for all my ranting about how I'd never use it again, I never thought my TV would be my main monitor :P

 Last problem to sort out is the HDMI sound volume, it's way too loud :(

Thanks

---

