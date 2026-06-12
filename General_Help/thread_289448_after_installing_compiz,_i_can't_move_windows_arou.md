---
title: "after installing compiz, i can't move windows around the screen"
date: 2006-10-31
forum: General Help
---

### Post by syxbit on 2006-10-31
i first installed the nVidia drivers through Automatix. I then heard you needed the beta driver for compiz, and followed these steps

Add these two lines in /etc/apt/sources.list

deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy .

then

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-compiz-manager compiz-freedesktop compiz-freedesktop-gnome

then add the following line in the /etc/X11/xorg.conf file under the section “Screen” :

Option "AddARGBGLXVisuals" "True"

then reboot.

if i disable GL Desktop, everything works perfectly
any ideas?

---

### Post by iamhugeinjapan on 2006-10-31
Do you mean your program windows have no title bars?

---

### Post by junior2001 on 2006-10-31
i have same problem! there are title bars but i can t move it it seems that transparency effects don't work, (shiver)  but i can do all other effects like cube etc... i have an intel video card 945GM. Please help me

---

### Post by syxbit on 2006-10-31
no, they have a title bar,
what i mean is that it all looks normal, but when i click on the title bar of a window to move it, it doesn't move
other than that, everything seems to work perfectly
any ideas ?

---

### Post by Reapman on 2006-10-31
I think I might be able to help... basically to move them around I had to add the proper plugins to load:
1) Open up gconf-editor
2) Go apps / compiz / general / allscreens / options
3) modify the active_plugins, mine includes (in this order):
gconf
dbus
decoration
wobbly
fade
minimize
cube
rotate
zoom
scale
move (thats probably the one your missing)
resize
place
switcher
water
screenshot

and volia!  Hope that helps :)

---

### Post by kaisa on 2006-11-13
thought I'd bump this back up to the top and say that Reapman's solution worked perfectly.

Thank you!

---

