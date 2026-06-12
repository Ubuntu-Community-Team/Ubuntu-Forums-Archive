---
title: "nvidia driver help!!"
date: 2007-08-28
forum: General Help
---

### Post by nickkov89 on 2007-08-28
ok well i was trying to install compiz and to tell the truth i had no idea what i was doing and i ended up uninstalling the nvidia drivers so when i start up ubuntu i get some crazy error message filled with weird symbols saying something like:

Failed to start the x server(your graphical interface)

and something like

failed to load module "nvidia" (module does not exist)
there was a lot more to it but these are the main errors

now my terminal loads, but thats it, i guess i have to install my nvidia drivers onto it again but i dont know how using the terminal, maybe thats not the problem, i dont know, please help thanks a lot

---

### Post by confused57 on 2007-08-29
> **nickkov89 said:**
> ok well i was trying to install compiz and to tell the truth i had no idea what i was doing and i ended up uninstalling the nvidia drivers so when i start up ubuntu i get some crazy error message filled with weird symbols saying something like:

Failed to start the x server(your graphical interface)

and something like

failed to load module "nvidia" (module does not exist)
there was a lot more to it but these are the main errors

now my terminal loads, but thats it, i guess i have to install my nvidia drivers onto it again but i dont know how using the terminal, maybe thats not the problem, i dont know, please help thanks a lot
You might try using the "vesa" or "nv" drivers to get to a gui, then you can try reinstalling the "nvidia" drivers.  From the console, enter:
```
sudo dpkg-reconfigure xserver-xorg
```
You can probably go with the defaults for most of the setup, but choose "vesa" for the video driver(or "nv", if you have an older Nvidia card).  Once you're finished configuring:
```
startx
```

You may want to try Envy to install the Nvidia driver:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

