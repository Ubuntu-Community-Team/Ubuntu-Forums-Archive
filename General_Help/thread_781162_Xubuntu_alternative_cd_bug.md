---
title: "Xubuntu alternative cd bug"
date: 2008-05-04
forum: General Help
---

### Post by 1r0nman on 2008-05-04
i am running a VERY old laptop with a pentium II processor 32 mb of ram and a 4 gig hard drive....everything is pretty much going smoothly,ive been able to figure a few of the bugs and glitches out myself but i am stuck....

every time i load flash on firefox it crashes...its a bug that has to do with the 16 bit color depth...so ive been trying to go into /etc/x11/xorg.conf

but the problem is,anytime i try to open it and edit it i just get a blank file and cant get out of it..ive used

sudo nano /etc/x11/xorg.conf
sudo mousepad /etc/x11/xorg.conf
and thunar file manager to go and open it(when i do this i can actually read the file but when i edit it i cannot save it because i am not root)

any help would be much appreciated

---

### Post by NightwishFan on 2008-05-04
Xubuntu needs a minimum of 128mb of ram to be run with any sort of speed and it might be uncomfortable on that much. I advise you try a barebones Puppy Linux or Damn Small Linux.

[http://puppylinux.com/](http://puppylinux.com/)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Please ask if you need any help.

---

### Post by 1r0nman on 2008-05-04
no,the alternative xubuntu cd requires 32 mb and it runs perfectly...sad to say that is not the problem...

---

### Post by NightwishFan on 2008-05-04
I am disinclined to agree. 32mb of ram is too light for any modern linux. If it truly runs well, then try to run your editor as root with gksudo, then you should be able to save the file.

---

### Post by 1r0nman on 2008-05-04
thank you,and thanks for the link to DSL i am considering installing that if i start having some other severe problems

---

### Post by c4v3m4n on 2008-05-04
Xubuntu is pretty lightweight, but not that lightweight.

---

### Post by NightwishFan on 2008-05-04
No problem. I was not arguing by the way I just hope I can help getting your laptop running well. Good luck, and may the force be with you.

---

### Post by plucky on 2008-05-04
1r0nman,

Linux is case sensitive > sudo mousepad /etc/x11/xorg.conf

Try ```
sudo mousepad /etc/X11/xorg.conf
``` to edit that file, Th x needs to be X.

+1 for Puppy.

Good Luck

---

