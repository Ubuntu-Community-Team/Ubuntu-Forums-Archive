---
title: "Running &quot;wireless.sh&quot; at Startup"
date: 2006-11-17
forum: General Help
---

### Post by bitninja on 2006-11-17
Hi guys, I'm using Ubuntu Edgy 6.10, and I need some help getting a script to run at startup. I have tried placing it in init.d, and running update-rc.d placing it in runlevels 2, 3, 4 and 5. The exact command I used was "update-rc.d -f wireless.sh start 99 2 3 4 5 ." and I didn't get any errors or things of the like. It just worked. I rebooted and still nothing happened. I'm starting to get annoyed, as I manually have to run my wireless script every time I start my system. (It's just a basic "iwconfig wlan0 essid blah key restricted blah" thing.) I tried adding the commands to /etc/rc.local, also to no avail. It seems that the script is getting executed too early, if at all. Am I doing things wrong? Is init doing things wrong? Am I just too stupid to comprehend what I'm doing?:-D If you've got answers or suggestions, let me hear 'em.

The fairly old (old as in started using it 3 years ago), but slightly incompetent linux user,
Cody

---

### Post by highneko on 2006-11-17
If you want a delayed execution add "sleep 10" to a script, and move your script to one of the bin places. For a list of the bin things you can type "echo $PATH". In Gnome goto Main Menu -> System -> Preferences -> Sessions -> Startup Programs, and add the name of your script.

---

### Post by bitninja on 2006-11-17
I tried using the session manager in Gnome too, but it seems that every time I close the manager after adding the commands I want, it isn't saved. I type in the command, close the session manager, and go right back to it, and my command isn't there anymore.

---

