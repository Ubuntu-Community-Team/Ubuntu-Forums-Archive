---
title: "the lib/modules contents has bee deleted by mistake"
date: 2013-03-18
forum: General Help
---

### Post by jcs3rdma on 2013-03-18
What is the best way to recover from this mistake. 
I tried reloading the latest 3.2.0-39 everything and it kinda works, but the mouse is a big block and I cannot load the latest video driver. 
I think that Ubuntu will only run in 2d mode. 
Thank you.

---

### Post by r.stiltskin on 2013-03-19
You could completely reinstall xwindows from a terminal login (ctrl+alt+F2)
sudo apt-get remove --purge xserver-xorg
and then
sudo apt-get install xserver-xorg
and that should reconfigure your video and mouse, but you'll then also have to reinstall a whole lot more, i.e. your entire desktop environment.

Don't know if there's an easier way.

---

### Post by jcs3rdma on 2013-03-19
That is what I figured. So, I reinstalled Ubuntu.
Now if I can figure out how to fix grub!
Thank you for the reply.

---

