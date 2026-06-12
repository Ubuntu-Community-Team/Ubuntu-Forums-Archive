---
title: "linksys wusb54gs (speedbooster)"
date: 2006-08-08
forum: General Help
---

### Post by brobbo on 2006-08-08
hi i have followed the ndiswrapper method 1 on tehre website and found the 2 .sys files 
to tell the truth i just started using ubuntu linux yesterday and i am in the total deepend lol
i want to learn the code of linux and how to use it so here gos

could someone be extremly kind and give me an idea on how to use ndiswrapper becasue i have no idea how to install in on ubuntu and im havving problems

cheers guys brad

---

### Post by x64Jimbo on 2006-08-08
You need the sys files AND the inf files. Once you have found them all, put them in a directory in your system, and run this:
ifconfig -a 
(this will tell you what interfaces you currently have)
sudo ndiswrapper -i <inffile>.inf
(installing the inf file. sys files must be in same directory)
sudo modprobe ndiswrapper
(plugging the ndiswrapper module into your kernel)
ifconfig -a
(check interfaces again and look for new one. that should be it.)

---

### Post by coldstatue on 2006-12-06
See how quick that guy gave up? I don't think he knew that he should be typing in a console. I think Linux veterans forget what it's like to be a newbie.

---

