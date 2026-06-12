---
title: "How to turn X Server off and on in command line!?"
date: 2007-05-25
forum: General Help
---

### Post by JuicedJuice on 2007-05-25
I'm new to linux and am trying to install the nvidia driver for my nvidia video card in the newest 64-bit Ubuntu (7.04). When I run "sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run" I get the message that an X server is already running and can't be on if I'm to install the drivers. I know I have to press cntrl + alt + F1 and then somehow kill the X server but I have no idea how and can't find up to date info on how to do this. I'll also need to know how to turn the X server back on. Wish I didn't have to go through this to install a dang video driver hah. Anyhow, thanks for any help.

---

### Post by sebbouckaert on 2007-05-25
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

follow the 2nd method

---

### Post by amphet on 2007-05-25
try pressing ctrl+alt+f1

then if you use gnome

sudo /etc/init.d/gdm stop

to start it again

sudo /etc/init.d/gdm start

if you use kde replace gdm with kdm

---

### Post by knallkopf on 2007-05-25
No good tip :)

---

### Post by JuicedJuice on 2007-05-25
Ah cool. Thanks. Everything worked out fine although now I need to one more thing (install the libc library or whatever).

---

