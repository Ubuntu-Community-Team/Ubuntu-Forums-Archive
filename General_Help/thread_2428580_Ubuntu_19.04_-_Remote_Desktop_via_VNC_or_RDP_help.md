---
title: "Ubuntu 19.04 - Remote Desktop via VNC or RDP help"
date: 2019-10-05
forum: General Help
---

### Post by Vince N on 2019-10-05
Good Afternoon All,

I'm coming back to Ubuntu after a very long time away. I think the last time I regularly used it was back with Lucid if that tells you anything.

I've installed 19.04 on my HP Pavilion laptop and for the most part it works great with a couple of minor glitches i'm still sorting through. However one thing I do like to do is remote access my laptop from my main PC. I've typically done this with RDP on Windows based systems but thats obviously not the best solution for a Linux System

I've read a number of different posts on getting VNC working, but I honestly have not had much luck nor can I find a guide that seems straightforward to the version of Ubuntu I have loaded.
The closest I have found is to go to the "Sharing" tab in settings but the "Share my Screen" option is missing. Supposedly this is because i'm on Wayland instead of X-Org but I just have standard "Ubuntu" and not "Ubuntu with Wayland" selected on my login screen.

Has anyone had any luck making this work in a simple process or who would be willing to assist with some troubleshooting?

---

### Post by Vince N on 2019-10-05
Just an asside, I've also tried using xRDP which honestly would be a good solution since I'm trying to remote from a Windows PC, however while I can get it to take my user ID and password, The session closes immediately after.

I am currently using teamviewer as a solution but I would prefer RDP or VNC.

---

### Post by Skaperen on 2019-10-05
you could run a totally separate XVNC server without doing screen sharing.  then run a VNC client when using the laptop to connect to itself.

---

### Post by HermanAB on 2019-10-06
Well, you have to build the tower of Piza up from the bottom - you cannot start in the middle or at the top...

Check that Xorg is running - if you have Wayland then draft a nice message to the Ubuntu team (don't send it though...) and reinstall the whole thing.
Check that the network connections work.
Consider using SSH instead, since it is less hassle and works better for most use cases.

The diff between VNC and SSH is that VNC overloads your local desktop with a slow remote desktop.  With SSH, you simply run the remote application transparently on your local desktop.

Overwriting your local desktop with a slow remote desktop is useless if your local machine is already running a perfectly good UNIX desktop.  So VNC is mostly a Windows thing.

---

