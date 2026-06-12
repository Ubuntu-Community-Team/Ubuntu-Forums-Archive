---
title: "Clicking Terminal results in computer restarting"
date: 2008-03-05
forum: General Help
---

### Post by Benjam on 2008-03-05
When I clicked on Terminal to open it on Xubuntu, my screen flashed to a black screen with text, which ended up logging me out and taking me back to the log-in screen.

In my system log this is what is logged whenever I click on terminal:

gdm[4581]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
NetworkManager: <info>  Updating allowed wireless network lists

I tried re-installing the xfce parts from the cd I installed using Synaptic, but that proved to no avail.

Thanks for your help.

---

### Post by kuja on 2008-03-06
It says its a problem with X.  It could be a problem with the particular version of X or perhaps the video drivers. There must be something about what that app was doing that X wasn't liking ....

---

### Post by bingoUV on 2008-03-06
read the following bug 
[https://bugs.launchpad.net/ubuntu/+s...nal/+bug/91849]("https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849")

---

