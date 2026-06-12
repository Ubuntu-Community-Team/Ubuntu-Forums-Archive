---
title: "Booting problem"
date: 2007-12-26
forum: General Help
---

### Post by trm96 on 2007-12-26
I   get the boot screen after the progress meter gets filled the boot screen goes away then i get a little blinking line at the top right hand of the screen and it just hangs...

---

### Post by mellowd on 2007-12-26
Which os and version are you installing? what hardware have you got?

---

### Post by trm96 on 2007-12-26
oh Im sorry, I am running Ubuntu 7.10 on an HP Pavillion ZE4800 Notebook.

P.S. it's already installed it was running fine (for a few days) untill i went to reboot it today

---

### Post by mellowd on 2007-12-26
Sounds to me like the resolution may be out, can you boot into the live cd?

---

### Post by trm96 on 2007-12-26
yes.

---

### Post by trm96 on 2007-12-26
Where is Window's "last known good" when you need it... :(

Ok I figured out the problem. Like mellowd said it was indeed a resolution problem not allowing me to run xserver. So after some goolging i found the solution to the problem. If I boot to a command prompt (you can either log in using your user name or root) then type in dpkg-reconfigure xserver-xorg (make sure if you log in using your user name you use sudo).

I only include this info in the post so any other person searching the fourms can use this info...

I officially call this thread closed!

---

