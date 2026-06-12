---
title: "Slow performance with Intel i3-540"
date: 2015-02-21
forum: General Help
---

### Post by deadwolfbones on 2015-02-21
Hi all,

I've been away from Ubuntu for a while—was running Openelec for years but recently switched to Plex and am now using Ubuntu to run Plex Media Server. My HTPC, which I'm using for the server, was plenty fast for Openelec and previous versions of Ubuntu, but it's really crawling on 14.10. Its specs:

Intel i3-540
Integrated GPU
4GB RAM

What I'm seeing is huge lag when I click on anything, lag when typing, lag when scrolling in browser. In particular, when opening the "home lens" search bar, I get huge lag (2-3sec). Same when clicking the power button in the upper right (1-2sec). There's half-second or so typing lag in either Chromium or Firefox; gedit is better but not perfect. Dragging windows around the screen is pretty quick but if I snap them to full-screen I get pretty bad lag while the window redraws.

All of this smells like a GPU/driver problem to me, but I checked and I appear to be running the correct driver. Does 14.10 just not like integrated Intel graphics?

---

### Post by deadwolfbones on 2015-02-21
Here's my GPU info, if it helps:

xxxxxxxxxxx@linuxbitch:~$ apt-cache policy xserver-xorg-video-intel
xserver-xorg-video-intel:
  Installed: 2:2.99.914-1~exp1ubuntu4.2
  Candidate: 2:2.99.914-1~exp1ubuntu4.2
  Version table:
 *** 2:2.99.914-1~exp1ubuntu4.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2:2.99.914-1~exp1ubuntu4 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages

---

### Post by mc4man on 2015-02-21
check this, if it reports gallium & lvmpipe then you'd want to find out why (should return something concerning Mesa Dri/ Intel. You probably will need to install mesa-utils package to run command
```
glxinfo |grep "OpenGL renderer string"
```
(ex. here on i7 - 
$ glxinfo |grep "OpenGL renderer string"
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile

---

### Post by deadwolfbones on 2015-02-21
Thanks. Did that and got what I assume is the correct response:

$ glxinfo |grep "OpenGL renderer string"
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Desktop

---

### Post by deadwolfbones on 2015-02-21
Oh, one other really weird thing I noticed that's probably not related in any way: the character "x" doesn't show up in the desktop search thing (there's just a blank space), though it does appear in gedit. Weird, huh?

---

