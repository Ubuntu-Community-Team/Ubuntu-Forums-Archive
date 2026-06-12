---
title: "Xserver will not start"
date: 2018-02-15
forum: General Help
---

### Post by Donnut on 2018-02-15
I can not get into Ubuntu desktop. It was working just fine until today. When I boot it just boots me into the terminal(shell?). When I hit startx, all I get is this and then a blank screen.
[IMG]http://i255.photobucket.com/albums/hh147/romcrazy/IMG_0515.jpg[/IMG]

---

### Post by Donnut on 2018-02-17
Can anyone help me with this? Or do I just need to re-install? Has anyone else had this?

---

### Post by Donnut on 2018-02-17
Ok, so I seem to have fixed it. I ran ```
sudo apt-get install ubuntu-desktop
``` it installed 9mb worth of stuff, mostly lib packages, I rebooted, and it logged right in! Odd.

---

