---
title: "usplash doesn't appear on startup or shutdown"
date: 2008-07-01
forum: General Help
---

### Post by theshadowwithanmp5n on 2008-07-01
my usplash won't appear on start-up or shutdown 

i tried changing the resolution and running sudo dpkg-reconfigure usplash
but when i rebooted, nothing happened.

however, when i run sudo usplash from terminal, the resolution on the virtual terminal is fixed.

to kill two birds in one stone, can someone tell me how to fix the resolution of my virtual terminals so the text doesn't go flying off the screen.

any help would be appreciated.

---

### Post by stats on 2008-07-03
do this.
```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```
do you see on entry for u splash?
it should be check on runlevels 2,3,4,5

also check /boot/grub/menu.lst
the kernel line should have the word splash somewhere in it(near the end of the line usually)
add it if it's not there

---

### Post by theshadowwithanmp5n on 2008-07-03
there's no usplash entry in sysv
what do i do

---

### Post by pferpaddy on 2008-07-03
download startup manager from synaptic and select show bootsplash if that dosnt work  reinstall the usplash using synaptic

---

### Post by theshadowwithanmp5n on 2008-07-03
none of those worked

---

