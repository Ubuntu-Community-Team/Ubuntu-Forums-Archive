---
title: "UT2004 on Ubuntu"
date: 2004-11-12
forum: General Help
---

### Post by puzzledm on 2004-11-12
Okay so I have installed the Nvidia Glx drivers through the very easy how-to on the wiki site and I have downloaded the UT2004 demo.  And then I try to install the demo - which is when the problems start.

If I install the demo without 'sudo' it can't write to anything it needs to and therefore crashes.  But if install the demo with sudo I can't run the game unless I open a terminal and run 'sudo ut2004' which is a pain especially seen as an icon appears in my games list in my applications button (but It won't load without sudo)

So if you have any suggestions that would be great as I would like to get this sorted before I buy the full game.  :(

---

### Post by zenwhen on 2004-11-12
Remove the game and install it to a directory that your user has full read/write access to.

---

### Post by allen on 2004-11-12
when it asks for an install path choose /opt/ut2004/

---

### Post by puzzledm on 2004-11-12
Will I have full read/write access to /opt/?

---

### Post by stodge on 2004-11-12
Probably not. You could install it to /home/username/opt and just create that directory. As it's in your home directory you will automatically have permission to install there.

---

### Post by jdong on 2004-11-12
Install it into /usr/local/, the default... You should have read access to that location. You may want to run **chmod -R 755 /usr/local/ut2004(demo)** to make sure of that!

That's what I did, and I'm happily playing the demo.

---

