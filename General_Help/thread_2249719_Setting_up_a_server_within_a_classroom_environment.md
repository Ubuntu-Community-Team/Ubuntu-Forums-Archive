---
title: "Setting up a server within a classroom environment"
date: 2014-10-24
forum: General Help
---

### Post by mark170 on 2014-10-24
Hi all, as a class project (me being the teacher) I was interested in setting up a web host/server for students to connect to and use as a testing server for both front and back end web development. Currently we are working within a OS X environment and I was thinking of trialling parallels to deploy a virtual server install.
Any suggestions and links to relevant walkthroughs would be greatly appreciated.

Cheers

---

### Post by JazzPotato on 2014-10-24
If you're going to teach them web development then probably the best way is to install apache on each student machine (I think "mamp" is the package you install on mac to get a local web server running)

---

### Post by mark170 on 2014-10-24
Thanks for the reply, I have previously used MAMP within class but found issues regarding the stop/start nature of the servers, also the students don't have administrator rights to the Mac's they use so starting and stopping MAMp generally required me putting in the admin password.  
I liked the thought of a central server which held all their work too, makes it easier in theory for me to quantify grades they receive.

---

### Post by JazzPotato on 2014-10-24
If you're experienced with linux and the then I would recommend in that situation using a central server with a hypervisor, and then just create instances of virtual machines for each of the students. Then they can ssh into the virtual machines and do whatever they want, if they screw up then just delete that particular vm and create a new instance (or they could go through the character-building experience of fixing it). 

Each virtual machine would have to have an ip address remember so if you have more than 10-ish students or your subnet is crowded you will have to get your network guys to help you out with creating another subnet.

Depending on how many students you have, and how brave you're feeling, using a level 2 hypervisor such as kvm is probably a better idea then using a "bare-metal" hypervisor such as xen. If you're not sure of the difference, Eli the computer guy has some good videos on youtube that introduce the conecpt, and there are some good articles on the ubuntu wiki.

I suppose the advantage of this approach is that the students get experience working with real linux servers!

---

### Post by JazzPotato on 2014-10-24
Eli the computer guy video: [https://www.youtube.com/watch?v=zLJbP6vBk2M](https://www.youtube.com/watch?v=zLJbP6vBk2M)
Ubuntu wiki kvm [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

