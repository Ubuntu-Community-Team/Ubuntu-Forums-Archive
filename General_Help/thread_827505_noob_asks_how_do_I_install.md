---
title: "noob asks how do I install?"
date: 2008-06-12
forum: General Help
---

### Post by loudtoys on 2008-06-12
Hey

 I am new to Linux and so far love it. Ubuntu 8.04 installed and ran with little effort.
I have a Dell Vostro 1500 laptop with an Ubuntu/XP dual boot install.
I am impressed by the vast amount of free software out there and wonder now why Windows is used as much as it is?
Now I have a problem. How do I install things I want to add on?
One example. I installed Nexuiz from Synaptic Package Manager without a problem.
I set up drivers for my vid card and wireless networking card.
Upgraded to "The Cube" and installed fire starter. Things were good.
I then tried to install aircrack with SPM. No shortcut appeared under Applications->Internet->.
No shortcut anywhere. SPM says it is installed. I tried complete removal->reboot->reinstall with no luck.
I then tried Kismet. Same deal no shortcut dont know how to launch it. How do I install and use a program that does not have a shortcut to it?
Am I installing these programs wrong? Do I need to install anything else first?
[FONT="Arial Black"]Is there a step by step tutorial on how to install aircrack for noobs you could lead me to?[/FONT]

Thanks in advance from a happy new linux user.

---

### Post by Joeb454 on 2008-06-12
I think you may need to install a frontend to aircrack.

May I ask why you want aircrack installed?

---

### Post by MaxNorris on 2008-06-12
> **Joeb454 said:**
> May I ask why you want aircrack installed?

Somebody's being naughty heh..  that aside, it's mostly console apps.  Google up their wiki for how to use it.

---

### Post by Ender305 on 2008-06-12
its his business what he wants to install, but some apps(most without a graphical frontend) dont have an icon in the programs menu, so you just have to type the right command into a terminal and they should work, I don't remember whether aircrack has a frontend, so you may have to learn to use a terminal

---

### Post by isaiddurazoo on 2008-06-13
HI I HAVE A CHANNEL ON YOUTUBE FOR BEGGINERS ITS PRETTY DESCENT IF YOU WANT CHECK IT OUT [http://www.youtube.com/user/sold13r45](http://www.youtube.com/user/sold13r45)

---

### Post by loudtoys on 2008-06-13
You may ask what I want with aircrack.
I want to find wireless access points to connect to the net.
After google found the wiki and I read it and I think the program is more than I wanted.
I am just looking for a program to find networks that are open not "crack them".
Anyway thanks for the advice guys.

---

### Post by re98001 on 2008-09-10
If you simply want to find wireless access points to connect to the net run in terminal:

iwlist scan

If you'd like more info on how to use iwlist, run in terminal:

man iwlist

---

### Post by kokkus on 2008-09-10
For the future, executable files are under /bin directories.
So u can find out the right command for a program by simply go to SPM, search for the program/package again, click properties, and under installed files you will see the full log if the package is installed.
E.g /usr/bin/programname.

I Hope this helps. And welcome to Ubuntu btw :)

---

