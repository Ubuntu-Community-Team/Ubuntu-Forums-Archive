---
title: "Showcase Live DVD"
date: 2005-05-19
forum: General Help
---

### Post by tread on 2005-05-19
I'm trying to make a single Live dvd which will showcase:
1. Gnome
2. KDE
3. Xfce
4. Enlightenment 17
5. Windowmaker
6. Fluxbox
7. Openbox

Besides the desktop environments, I am putting in development environments like kdevelop, anjuta, monodevelop etc. .. music players like muine, amarok .. well you get the idea. The main applications .. the most commonly used ones. The idea here is that a user can try out a lot of applications without installing .. 

Eventually,  I would really like to setup a knoppix style install now icon on the desktop, and then give the user a choice of gnome/kde/xfce etc.. 

I burned a trial dvd, it works. But the menus are messed up .. I want to create gnome-specific menus when logging into gnome, kde specific in kde etc. Any idea where I should change the menus? (This I am sure I can find out, but if anyone has done it a quick tip would be much appreciated :))

And that is another problem .. the default user directly logs into gnome .. I dont want that. I want a login screen .. to allow choosing the environment. Also, what is the default users password anyway? I tried ubuntu .. but that didn;t work. So I sudo -added a user and then experimented with that.

I still have to figure out e17 stuff .. right now my live dvd just has e16.
Any suggestions? Also, am I reinventing the wheel .. has someone already done this?

Edited to add:
I also tried resizing an hda partition with gparted using my custom live dvd, but I got the message resource busy. Is the harddrive partition mounted by default? (duh .. forgot to see mount. now musts boot off dvd again)

---

### Post by tread on 2005-05-19
I can't find out how to diable autologin .. the gdm.conf file in the live cd says no to autologin? :???: 

I guess thats my main question .. how do I make the default user login at gdm?

---

