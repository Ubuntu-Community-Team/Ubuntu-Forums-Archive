---
title: "Cursor size, theme fix"
date: 2018-11-04
forum: General Help
---

### Post by cmcanulty on 2018-11-04
I have been battling the inconsistent cursor size and color since ubuntu 5.04. Always I couldn't get a consistent size and color cursor across the board for all apps, especially for the non admin users. I think I finally have it and it is dead simple, at least for cursors that are already in the distro. I prefer DMZ-Black size 48. So for example I put this text in 

```
/home/usernamehere/.Xresources

Xcursor.size: 48
Xcursor.theme: DMZ-Black

```

if the .Xresources file doen't exist, create it for each user and just put the above text in it, changing the username and size and theme of cursor as desired

so far it survives reboots and stays set for all users. You can check for available icons in 
/usr/shar/icons also many more can be downloaded. A while ago I had an easy fix using dconf-editor and /etc fix I don't remember but they never worked for all users, yea, 13 years of this bugging me!

---

### Post by Dennis N on 2018-11-04
Also, the cursor theme has to be resizable for the size setting line to have any effect. Not all cursor themes are.

---

