---
title: "Cant see anything"
date: 2007-09-30
forum: General Help
---

### Post by chomama1 on 2007-09-30
ok my main problem is that when i login to ubuntu my screen is all messed up. its really hard to describe what it looks like but ill try anyway.  there are like black,green,red,blue lines when i highlight something. i cannot see anything at all. everything seems to be distorted some how.

ive had ubuntu for a few months and had beryl working with no problems.  Recently i installed warcraft 3 and it was running really slow so i tried to fix this by changing some stuff but i dont remember exactly what i did but this is when the problem occurred.  i believe i did something involving my video card but i cant remember what it was. i also removed beryl thinking this was the problem but nothing changed

also id really rather not have to reinstall. any suggestions would be appreciated greatly.

thanks in advance.

---

### Post by ajgreeny on 2007-09-30
Sounds like your video driver is giving the problem.  Pity you can't remember what you actually did as that would be a good starting point to get things back to where they were.

Try ```
sudo dpkg-reconfigure xserver-xorg
``` in a terminal and if you know what your video card is chose the appropriate driver when you get to that part; for the rest just accept what is default.  If you don't know your video card chose vesa at that point and hopefully you will at least get a gui you can use to sort things in more detail later.

---

### Post by chomama1 on 2007-09-30
ok thanks i tried that but after i finished and rebooted it said that xserver was missing and it was disabled. 

i did this to fix that

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=xv

and now im back to the same problem.

oh and i just realized that i forgot to mention that im using an ati mobility x1400 video card

---

### Post by ajgreeny on 2007-10-01
Just to get things going try the sudo dpkg-reconfigure xserver-xorg again but chose ati at the video card part to see if that works.  I know from experience that th fglrx driver can be a beast to get working, and you may be better off with the open source ati driver if it works.

---

