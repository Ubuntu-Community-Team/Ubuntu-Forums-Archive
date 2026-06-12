---
title: "kate editor wont start up anymore (new since this morning, without apt upgrade)"
date: 2020-06-20
forum: General Help
---

### Post by ReneVeerman on 2020-06-20
> 
root@crow:/home/rene/data1/htdocs/localhost# kate
qt.qpa.xcb: could not connect to display crow:0
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.


Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, wayland-egl, wayland, wayland-xcomposite-egl, wayland-xcomposite-glx, xcb.


Aborted (core dumped)


i did try to apt remove kate and then apt install kate again, but it resulted in exactly the same error as shown here.

please help.

can't live without my kate, lol ;)

---

### Post by ReneVeerman on 2020-06-20
ah, a full
> 
sudo apt update
sudo apt upgrade
sudo reboot


sequence fixed my problem, but my machine still won't let me start up kate the regular way (pressing the windows key on my keyboard to bring up the system search dialog, then typing in kate into that search input field).
i have to start a terminal, and start up kate from there :
> 
kate &


---

### Post by ActionParsnip on 2020-06-20
If you press ALT + F2 can you run it that way?

---

### Post by Impavidus on 2020-06-20
Running kate as the root user may be part of the problem. Even if you don't try it now, a previous attempt may have caused some damage so that it doesn't work now. Check your home directory for root-owned files and fix them. If you want to edit a root-owned text file, use sudoedit, which will run your favourite text editor as normal user and copy the files.

---

