---
title: "VMware Causes Mouse Cursor To Disappear!"
date: 2007-03-17
forum: General Help
---

### Post by jacc1234 on 2007-03-17
Hello, I am having a problem with vmware that is driving me crazy. When I boot a virtual machine my screen flashes and my mouse pointer in Ubuntu disappears. There is also some artifacting on the top right of my ubuntu desktop. My mouse is still functioning but I cant see where it is on the screen. When I was in my windows xp vertual machine and the mouse was functioning in software I could see it, but once I installed vmware tools i lost the mouse in the virtual machine as well. I have looked all over and cant see to fine an answer to this problem so any help would be great.

I am running Ubuntu 6.10 with kernel 2.6.20.1. My mouse is USB and I am using an integrated Nvidia 6200 video card. 

Thanks,
jacc1234

---

### Post by jacc1234 on 2007-03-17
Solved: Finally figure it out. It was a framebuffer issue. I added vga=795 on the end of my default kernel in menu.lst and all is well.

---

