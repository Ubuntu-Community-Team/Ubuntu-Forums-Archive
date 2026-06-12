---
title: "Picasa problem"
date: 2007-12-25
forum: General Help
---

### Post by clueless on 2007-12-25
Hello everyone,
I have this weird problem: picasa's menus are completely blue, making it not only ugly but also difficult to work with. 
I have no idea what is causing it!
Anyone knows how to work this out?
I am running kubuntu gutsy amd64 (with 64bit picasa) and have also installed gnome (ubuntu-desktop) in order to see if playing with gnome's themes could solve the problem.
Any help would be greately appreciated.

[[IMG]http://img148.imageshack.us/img148/8820/snapshot1po6.th.jpg[/IMG]](http://img148.imageshack.us/my.php?image=snapshot1po6.jpg)

---

### Post by clueless on 2007-12-25
Ok I found the solution.

Although I am only running KDE, apparently when I initially installed picasa, I was using GNOME with a particular theme that didn't work well with picasa. The solution: wipe out the ~/.picasa directory, use a clean GNOME theme and restart picasa.

This solution is suggested here:
[http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/e5f48ede70b75f99/a7655dad3772ce4b?lnk=gst&q=menu#a7655dad3772ce4b](http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/e5f48ede70b75f99/a7655dad3772ce4b?lnk=gst&q=menu#a7655dad3772ce4b)

---

### Post by rfruth on 2007-12-25
Glad it worked out - good idea deleting .picasa

---

### Post by clueless on 2007-12-28
It wasn't my idea, but it worked, fortunately.

---

