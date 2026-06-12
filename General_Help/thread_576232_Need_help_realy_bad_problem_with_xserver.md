---
title: "Need help realy bad problem with xserver"
date: 2007-10-15
forum: General Help
---

### Post by Foresthello on 2007-10-15
ok what happend is I installed xserver something in synaptic maniger I realy messed up my computer when i restarted it later it said something like a xserver error :

"faild to start the x server (your grapgical interface). It is likely that it is not set up correctly. would you like to view the x server output to diagnose this problem"
" 
then i get these errors: "failed to load module "fg1rx" (module does not exist, 0)"   and this other error "no drivers availble." 

Then i get "the x server is now disabled. Restart GDM when it is configured correctly."  

Im a compleate noob when it comes to stuff like this so i can access the terminal tho i wonder if i need to reinstall ubuntu but i realy dont want to do that i was wondering if i could uninstall the x server thing that i installed.

---

### Post by yabbadabbadont on 2007-10-15
Reboot and take the option for recovery mode.  If ubuntu is the only OS on the machine, you may have to hit the escape key when you see the grub prompt to get the menu.  Once it has booted into recovery mode, you will be at a text prompt.  Run the following:
```
sudo dpkg-reconfigure -p high xserver-xorg
```
If you know the correct driver for your video card, then select it.  If you don't know, or it still doesn't work, then try selecting the vesa driver.  After you have done that, just type "reboot" (without the quotes) and hit enter to restart the machine.

---

### Post by Foresthello on 2007-10-15
ok i will try

---

### Post by Foresthello on 2007-10-15
you do not know how greatfull i am
 thank you so much

---

### Post by yabbadabbadont on 2007-10-15
You are welcome.  I'm glad it helped.

You would be surprised at how often I have to post that tidbit.  :D

---

