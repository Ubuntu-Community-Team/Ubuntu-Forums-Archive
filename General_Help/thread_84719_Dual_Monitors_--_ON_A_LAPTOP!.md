---
title: "Dual Monitors -- ON A LAPTOP!"
date: 2005-10-31
forum: General Help
---

### Post by jimmygoon on 2005-10-31
Ok! Well I've got a Toshiba laptop with a newly installed copy of Linux on it and I would like to know what I need to do to extend my desktop onto a second monitor (just plugged in the back of the laptop).

please edumacate me ;) (yes I've looked but all instructions seem to be for people with desktop PC's and dual grafix cards)

thanks

---

### Post by Whatthehello on 2005-10-31
the port on the vga port on the back of the laptop will  output the same thing as the current display on your laptop. im using the port to replace my broken laptop lcd with an external one

---

### Post by jimmygoon on 2005-10-31
in windows I can extend my desktop onto my other monitor. Is this a possibilty in linux?

---

### Post by Whatthehello on 2005-10-31
did you extend windows desktop on a laptop?

---

### Post by jonny on 2005-10-31
This isn't for the faint hearted under linux, I'm afraid.  You need to research xinerama, and be prepared for some heavy editing of your /etc/X11/xorg.conf file.  If it goes wrong, you might need to be able to resurrect your machine with just a command line.

IMHO this is the single biggest weakness of the Gnome desktop environment.  In business, a laptop without dual monitor output is next to useless.  The average business laptop user will never use linux until this matter is addressed by someone far cleverer than me.

---

### Post by jimmygoon on 2005-10-31
I'm fine with editing and a command prompt. I'm a fast learner with a bit of guidance.  I will do some research and some more google work. thanks

---

### Post by banadushi on 2005-11-01
You might wanna check out [http://www.granneman.com/techinfo/linux/installation/dualheadhowto.htm](http://www.granneman.com/techinfo/linux/installation/dualheadhowto.htm).  Shows howto configure for Radeon Mobility 9000 (M7 LW).

Have a good one.

Jason

---

