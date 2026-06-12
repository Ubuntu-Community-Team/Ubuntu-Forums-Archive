---
title: "Ubuntu Not Loading"
date: 2007-01-02
forum: General Help
---

### Post by Tumpster on 2007-01-02
So I've been running Ubuntu for a few weeks now and was finally getting the hang of it but I've run into problems.  Last time I was on I updated as ubuntu signed that I had a bunch of updates for it and I let it download em and install em, I also split my hard drive so I have a 100gb FAT32 so i can see it on windows and linux. Now it goes through loading and everything but then it just goes to the desktop and all i see if the red background and nothing else loads. Nothing, I have the red background and the white cursor, thats it. Can anyone help me?? Thanks!!

---

### Post by ajgreeny on 2007-01-02
When you get to the red screen hit Ctrl+Alt+F1 to hopefully get a terminal screen.  Login and then type startx.  You may get a desktop to start, but if not type:-
suao dpkg-reconfigure xserver-xorg
and go through the screens one by one.  If you are not sure about things just accept the default, you can change details later in the desktop you are more used to.  If you know what make of graphic card you have chose that driver when it shows in the list and hopefully you may end up with a desktop after trying startx again.

---

### Post by bulldog on 2007-01-02
> **Tumpster said:**
> So I've been running Ubuntu for a few weeks now and was finally getting the hang of it but I've run into problems.  Last time I was on I updated as ubuntu signed that I had a bunch of updates for it and I let it download em and install em, I also split my hard drive so I have a 100gb FAT32 so i can see it on windows and linux. Now it goes through loading and everything but then it just goes to the desktop and all i see if the red background and nothing else loads. Nothing, I have the red background and the white cursor, thats it. Can anyone help me?? Thanks!!

The splitting thing,did you do that after you installed ubuntu?
If so you have to take a look at your menu.lst and your fstab as well,to see if things are listed as they should be.

---

### Post by Tumpster on 2007-01-03
Disregard, after a few resets it began working and now works. Strange, but thank you for the help!! :-)

---

