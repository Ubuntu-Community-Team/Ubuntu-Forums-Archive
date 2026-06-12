---
title: "[SOLVED] Login issue"
date: 2007-11-13
forum: General Help
---

### Post by airbornemist6 on 2007-11-13
I seem to have corrupted my gdmlogin and gdmgreeter by using a corrupt theme, now I want to fix them so I can log into ubuntu again, but I don't know what files to look at to reconfigure or replace, anyone know how to fix this?

---

### Post by aysiu on 2007-11-13
Can you be more specific? In what was is it corrupt? What are the symptoms?

---

### Post by airbornemist6 on 2007-11-13
I'm not actually sure what is corrupt. I just applyed the theme and upon rebooting the greeter kept crashing, and it said it was trying to fall back to a different theme, but then it doesn't, instead there is just a black screen.

---

### Post by aysiu on 2007-11-13
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post a screenshot of what appears after the last comand? ```
sudo apt-get update
sudo apt-get install xnest
gdmflexiserver --xnest &
```

---

### Post by airbornemist6 on 2007-11-13
I'll do that in just a second, I need to boot with my live cd.

EDIT:
Don't ask me what I was thinking, I just realized I won't be able to do this from live cd

Further edit:
Ok, booted from recovery mode, but it doesn't work because I have no net connection. Would it be possible for me to just boot into the live cd and overwrite the configuration files with the defaults? If so, where are they?

---

### Post by airbornemist6 on 2007-11-13
Ah ha! I fixed it! I just wiped the contents of the /etc/gdm/gdm.conf-custom file, and it reset to default. Thanks for your help Aysiu

---

### Post by Almumin on 2007-12-30
Restart the computer in (Recovery Mode). 
Type Login
Login with your username and password
Navigate to the /etc/gdm/gdm.conf-custom file through sudo and vi.

It will look like this. 

sudo vi /etc/gdm/gdm.conf-custom 

for the non-vi folks out there. Use the "j" key to go down to in the file. Move to the lines that have a listing for the login splash name. hit dd twice to delete the line. 

after you are done with this. type :wq! and then type reboot. Welcome back home!

---

