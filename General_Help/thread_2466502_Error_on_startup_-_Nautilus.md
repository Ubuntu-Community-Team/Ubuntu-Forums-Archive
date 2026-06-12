---
title: "Error on startup - Nautilus"
date: 2021-08-29
forum: General Help
---

### Post by robert71 on 2021-08-29
Hi Everyone, 
     
      Im hoping that someone can assist me with resolving an issue i encountered on startup of my Ubuntu machine recently. 

Every time the desktop loads it give the following error: 

"The application files has closed unexpectedly" 

it also happens when i right click on the folders icon in the taskbar on the left and choose any entry like:
Documents
Pictures 
Etc... 


What Ive tried: 

1. re-installing nautilus :
    sudo apt-get -remove nautilus 
    sudo apt-get -install nautilus

2. Updating Ubuntu 
    sudo apt-get update and upgrade 

I dont know what else to try, I rely on my Ubuntu desktop for my work.

Will be very grateful if anyone can assist. 

Also i have attached screenshots of the errors in detail if you need any further info that can assist in troubleshooting please let me know and ill provide.

thanks

---

### Post by TheFu on 2021-08-30
The only time I've seen issues like that was when someone used sudo with a GUI program very early after a fresh install.  The settings were all owned by root, not the normal userid. Gnome hates that and didn't (doesn't?) handle the failure well.

The fix is to 
a) never use sudo with any GUI programs.
b) sudo chown -R $USER:$USER ~/

The "b" command should do no harm on any Ubuntu system. 
The "a" command is just good practice.

BTW, I can't read any of those images. Please post text-only when ever possible.

---

