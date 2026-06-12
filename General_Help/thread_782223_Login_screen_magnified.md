---
title: "Login screen magnified"
date: 2008-05-04
forum: General Help
---

### Post by johnel on 2008-05-04
I am brand new to ubuntu I have the latest version downloaded and running the only problem I have so far is the login screen has been magnified to the point that its login page is off screen. Once I login everything is back to normal. How do I change the first page "Login Screeen" to the correct size

---

### Post by evertmantel on 2008-05-06
Had the same problem.

[http://ubuntuforums.org/showthread.php?t=767042&highlight=login+screen+size&page=2]](http://ubuntuforums.org/showthread.php?t=767042&highlight=login+screen+size&page=2])

Did the trick for me. See mail #15 from Zorael

Also the trick of setting the Administration> Login Window> Logo > Style > Plain    worked for me, but I think that is a work around, not a solution.

---

### Post by Leesh on 2008-05-06
> **johnel said:**
> I am brand new to ubuntu I have the latest version downloaded and running the only problem I have so far is the login screen has been magnified to the point that its login page is off screen. Once I login everything is back to normal. How do I change the first page "Login Screeen" to the correct size
There is something with the resolution. For example, my login screen has a much bigger resolution, than I use (I use 1024x768 ). But it is not a problem for me.

---

### Post by k_dv700 on 2008-05-12
I got it solved by a hint of Max Schukin:
First log on (blind if necessary: user name <enter> then password <enter>)

Press Alt+F2 and enter:
gksudo gedit /etc/X11/xorg.conf
(you are prompted for the root password now)
Scroll down to the Screen section and add the following lines:
        SubSection "Display"
             Depth 24
             Virtual 1024 768
        EndSubSection

Change 1024 768 to your resolution.  
In my case the lines were already present, but for some reason it said 1600 1200

---

