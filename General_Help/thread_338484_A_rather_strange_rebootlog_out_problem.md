---
title: "A rather strange reboot/log out problem"
date: 2007-01-14
forum: General Help
---

### Post by Valinski on 2007-01-14
Im having a rather strange problem happening with my system at the moment. When ever i leave my system idle my computer will go to a black screen then log me out. It happens even if i have left something downloading. 
The same problem also occurs if i try and load GENS (the mega drive emulator). Ive tried other programs and they seem to work fine but haven't checked them all yet. 

I the only things i have changed recently is installing the ubuntu updates. Has anyone else had a problem like this? 

Thanks for any help!

---

### Post by bernied on 2007-01-14
check your screensaver settings

---

### Post by Valinski on 2007-01-14
I think we can add the screen saver program to the list of apps that make it reboot/log out. 


Thanks for your reply.

---

### Post by bernied on 2007-01-14
What I meant was, there's an option in the scrensaver settings that makes you type in your password when returning from the screensaver. It's not the same thing as logging out in kde, but I don't know what it does in gnome. Is that option set - it's just a tickbox?

---

### Post by Valinski on 2007-01-15
Sorry for the late reply. Had work! Erm i dont think its the screensaver as the problem occurs when trying to launch some apps. Plus i cant get into the screensaver menus to check as this also makes it reboot/log out/shaft me! 

thanks again for your input.

---

### Post by ikertxu on 2007-02-20
I have just the same problem, i get logged out in a few minutes. No way to solve it. Nothing to do with screensaver or power management.
Anyone can help?

---

### Post by ikester8 on 2007-04-07
I'm having the same problem. As soon as the screensaver kicks on, Ubuntu logs me out. Even previewing the screensaver does the trick.

---

### Post by ikester8 on 2007-04-07
OK, I figured out my problem. For some reason the nvidia drivers were not working properly, so anything requiring 3D acceleration (such as xscreensaver) booted me out. I uninstalled the drivers and reinstalled using tseliot's envy script and it works like a charm now. I'm not sure what upgrade did it.

---

