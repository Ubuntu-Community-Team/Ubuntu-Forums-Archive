---
title: "VNC Breezy XFCE"
date: 2005-10-27
forum: General Help
---

### Post by citrusfizz on 2005-10-27
hi all
i just got done making a fileserver that i can ssh into (the server is in my closet now with no monitor)
anyways i installed xfce on the server. and i am looking to start xfce with startx or something similer so i don't have to use  gdm/kdm/xdm  and i need to vnc into it so that i can do some remote gui operations..   
can someone help with 
1. start xfce with startx (orsomething similer)
2. help me set up a vnc server that i can connect to it from windows

tyvm

oh and keep in mind i can't do anything local with the server  just remote but ssh works fine..  i can pull the computer out if i have to

---

### Post by stuporglue on 2005-10-27
> 1. start xfce with startx (orsomething similer)

You'll need to ssh in with the -X option. 

ssh -X username@hostorIPnumber

X11 programs will now start from the CLI. If you want the Xfce menu bar, you can probably just type "xfce" and hit tab a couple times to see your options. 

Doing it like this won't actually forward your entire desktop to your client desktop, it will only forward the programs you're using.

---

