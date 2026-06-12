---
title: "x won't start!"
date: 2008-02-18
forum: General Help
---

### Post by vizitorq on 2008-02-18
so i didn't do anything, but for some reason, x won't finish loading properly, and then exits back to the terminal every time i boot. i really have no idea what the deal is. but i boot up, everything seems fine. then i type in my terminal, startx... and x starts to load, then all of a sudden it brings up this small window that says

"X session warning: Unable to write to /tmp; X session may exit with an error"

and that's it. i click 'okay' and then it takes me back to the terminal. i have never encountered this before. maybe i just need to open some space up on my /tmp partition? something like that? please help i can't use ubuntu!!! =(

---

### Post by SpaceTeddy on 2008-02-18
interesting that you acctually type something in a terminal to start the xserver... i always thought ubuntu starts gdm/kdm by default... 

your error should be pretty self-explainatory... check the rights in your /tmp (with *ls -la /tmp*) folder. it should be owned by root and have drwxrwxrwx permissions, i.e. everybody is allowed to do anything it.

if that is the case, check if your hd is full (*df -h*). if your drive is full, then i would first suggest a "sudo apt-get clean" to delete some temporary, not needed files anymore...

running out of ideas :)

---

