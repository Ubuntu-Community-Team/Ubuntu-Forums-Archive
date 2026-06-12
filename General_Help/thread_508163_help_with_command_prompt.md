---
title: "help with command prompt"
date: 2007-07-23
forum: General Help
---

### Post by jmlock on 2007-07-23
can someone tell me how to remove the nvidia restricted driver and re-install the generic (original) from the command prompt. as soon as i get into the desktop i lose all mouse and keyboard function. according to uname-r im running 386i have tried "sudo apt-get-purge remove nvidia-glx" i get bad command.

thanks for any help.

there is btw no way for me to do this from the gui

---

### Post by Shazaam on 2007-07-23
At the prompt=

sudo dpkg-reconfigure xserver-xorg


This will give you a way to reset your video with an interactive setup.

---

### Post by moffa on 2007-07-23
instead of "sudo apt-get-purge remove nvidia-glx"

it should be "sudo apt-get remove --purge nvidia-glx"  you need a space after the apt-get part

---

### Post by jmlock on 2007-07-23
thnk yo both 

i did the 1st suggestion the reconfigure one... when i got to the end it went back to prompt i tried startx but said already running. then (dunno why) i did something  and it tried to connect to xorg. i forgot to reconnect ethernet cable (2 computers 1 connection) it failed. now i get fatal error code of some sort. now im lost!!!!!

---

