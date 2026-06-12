---
title: "[SOLVED] start up script"
date: 2008-03-28
forum: General Help
---

### Post by nvysel24 on 2008-03-28
ok here is my delima i need (well i dont need to but it would b nice) to create a start up script so everytime i plug in my linksys usb 54g v4 it doesnt go to eth1 but instead go to rausb0 w/ my cracked drivers for packet injection.
problem 1 
    where do i put the start up script once i make it
problem 2 
   how do i make a script ( i have basic knowledge of programming but im a fair nub when it comes to linux)
problem 3 
   i tried making a script but when i start it...it uses sudo and still asks me for my password. i want to get around that i tried w/o sudo but then it doesnt work it give me an error. 

so far this is what i need to do or part of my code
     sudo modprobe rt2570
(enter pass)
then bam its done its simple yet i dont know how to implement it

---

### Post by nick_h on 2008-03-28
You can put your startup script in /etc/rc.local and it will run as root - no need for sudo.

If you just want to load a module then add it to /etc/modules instead.

---

### Post by nvysel24 on 2008-03-28
so what do i do open up the rc.local and put it at the end of the file?

i did try somthing like that but in a different file system and it said i couldnt save it cuz i didnt have permissions how do i change that

---

### Post by nick_h on 2008-03-28
Type:
```
gksudo gedit /etc/rc.local
```

---

