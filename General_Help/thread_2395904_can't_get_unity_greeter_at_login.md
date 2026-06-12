---
title: "can't get unity greeter at login"
date: 2018-07-08
forum: General Help
---

### Post by sebastien4 on 2018-07-08
I can't seem to get unity greeter at login. I checked settings and autologin is set to off (I can even turn it on for some reason). There is a pull down near the login button that gives me the Ubuntu in Wayland option that does nothing but try to start and takes me right back to the login screen after displaying the desktop for a second.

---

### Post by #&amp;thj^% on 2018-07-08
What version of Ubuntu are you using? (16.04 or 18.04)
If you have a Nvidia card with the driver installed that will cause the login loop on wayland.
More information is needed to help here.

---

### Post by sebastien4 on 2018-07-09
looked up spec online without having computer in front of me, seems like it is a NVIDIA GeForce 610M / Intel HD Graphics 4000. 

Running 18.04. I need to read up on wayland a bit more. 

So is that drop down the Unity Greeter? and is the Ubuntu option Gnome?

---

### Post by #&amp;thj^% on 2018-07-09
> **sebastien4 said:**
> looked up spec online without having computer in front of me, seems like it is a NVIDIA GeForce 610M / Intel HD Graphics 4000. 

Running 18.04. I need to read up on wayland a bit more. 

So is that drop down the Unity Greeter? and is the Ubuntu option Gnome?

First let me try to clear this up>>"Unity Greeter" is for Unity>> Gnome uses GDM. :)
Now I need to know at the login window can you select X11 option and get to a working session?
By default Gnome is using the X11 session unless you are trying to login with the gnome-wayland option.

---

