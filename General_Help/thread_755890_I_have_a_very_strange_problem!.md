---
title: "I have a very strange problem!"
date: 2008-04-15
forum: General Help
---

### Post by Malvazar on 2008-04-15
I reasontly aquired a compact desktop and intalled Ubuntu on it. The installation went off without any problems. The only complaints that I have is that when I get to the login screen about five or six distorting lines appear on the sreen. These line do not appear untill after the login screen has fully loaded how ever! The next problem is that my update manager will not find any updates. I know that there ae at least 150 updates to be had because I have ubuntu on my laptop and there was about 200 updates that it downloaded and installed when I first installed unbuntu on it. If it helps any I am running on Ubuntu 7.10. Could really use some help!

---

### Post by Tews on 2008-04-15
```
sudo apt-get update
```

---

### Post by SnakeHips on 2008-04-15
System / preferences / Software sources for your updates. 

would you check the "universe" and "multiverse" are enabled

---

### Post by Malvazar on 2008-04-15
No the universe and multiverse were not turned on, but they are now and that triger the update manager to start downloading some updates! I still don't know about this distortion in the screen still thoe. I know it isn't my monitor because it wasn't doing this untill after I intalled Ubuntu!

---

### Post by dstew on 2008-04-15
Take a look at the Gnome configuration editor. Maybe you can change a setting for the login screen, like resolution, to get rid of the annoying bars. See this: [http://www.maximumpc.com/article/customize_gnome_with_configuration_editor](http://www.maximumpc.com/article/customize_gnome_with_configuration_editor)

---

### Post by SnakeHips on 2008-04-16
what graphics card / drivers are you using? and does changing the screen resolution (reboot) give the same symptoms?

backup your xorg.conf just incase ;-)
in terminal
```
cd /etc/X11
```
then 
```
sudo cp xorg.conf xorg.backup
```

---

### Post by Malvazar on 2008-04-17
> **SnakeHips said:**
> what graphics card / drivers are you using? and does changing the screen resolution (reboot) give the same symptoms?


Umm... Do you think you could tell me how do look up my graphics drivers? I don't really recall how you go about doing that! 

Also I tryed changing the graphics display from the view sonic monitor display thing that Ubuntu setup for me to use with my monitor to the plug in play option but that really mest every thing up to the point of static like you would see on a TV so I reset it back to the veiw sonic option and it still has the distorting lines! (Gerrr!:mad:) 

I haven't tryed the resolution deal yet thoe, but it will have to wait a few hours because I am at school:(!

---

### Post by Malvazar on 2008-04-17
> **dstew said:**
> Take a look at the Gnome configuration editor. Maybe you can change a setting for the login screen, like resolution, to get rid of the annoying bars. See this: [http://www.maximumpc.com/article/customize_gnome_with_configuration_editor](http://www.maximumpc.com/article/customize_gnome_with_configuration_editor)

This one didn't work:(.

---

### Post by SnakeHips on 2008-04-17
What do you have in /sytem/administration/hardware devices (from the top menu) are any restricted drivers enabled ?

---

### Post by forrestcupp on 2008-04-17
open a terminal and type
```
lspci | grep VGA
```post the output to show us what kind of video card you have.  Then type

```
glxinfo | grep direct
```And tell us if direct rendering says yes or no.

---

### Post by Malvazar on 2008-04-17
> **Malvazar said:**
> Umm... Do you think you could tell me how do look up my graphics drivers? I don't really recall how you go about doing that! 

Also I tryed changing the graphics display from the view sonic monitor display thing that Ubuntu setup for me to use with my monitor to the plug in play option but that really mest every thing up to the point of static like you would see on a TV so I reset it back to the veiw sonic option and it still has the distorting lines! (Gerrr!:mad:) 

I haven't tryed the resolution deal yet thoe, but it will have to wait a few hours because I am at school:(!

Okay I am home now and I just change my resolution and that seemed to have fixed it:)! There is still a little left here and there but it is no were what it used to be! Thanks for all you help the computer is running much better now!

---

### Post by lespaul_rentals on 2008-04-17
Please marked your thread as solved in Thread Tools at the top right of the thread.

Glad you got your problem fixed.

---

