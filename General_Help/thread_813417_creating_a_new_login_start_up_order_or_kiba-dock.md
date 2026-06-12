---
title: "creating a new login start up order or kiba-dock"
date: 2008-05-30
forum: General Help
---

### Post by armandli on 2008-05-30
I have been trying to start kiba-dock at login in gnome, and somehow, when kiba-dock is started at login, all the gnome applets that started after kiba-dock will automatically go into the dock instead of my gnome panel, which causes some problem that i don't have. 

so I wanted to make kiba-dock launch after all other start up at login programs launch, is there anyway to do that? I've tried entering "sleep 5; kiba-dock" in sessions, under Startup programs. but somehow kiba-dock does not launch if i do that. any ideas?

---

### Post by EXCiD3 on 2008-05-31
I dont think it parses that command correctly to run both the sleep and kiba-dock separately. You can create a script to do this for you however that should fix your problem.

Create a file in your home directory:```
gedit .kibadock_start.sh
```
Put this in and save it:```
#!/bin/bash
sleep 10 && kiba-dock;
```

Make sure the script is executable:```
chmod a+x .kibadock_start.sh
```

and then use that script in your Sessions instead of kiba-dock (location: /home/<username>/.kibadock_start.sh)

---

### Post by armandli on 2008-06-05
apparently it doesn't work. somehow the nm-applet's socket is blocked and cannot even start, which is the initial reason i cannot start kiba-dock on start up

---

