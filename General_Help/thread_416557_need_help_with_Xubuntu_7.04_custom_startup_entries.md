---
title: "need help with Xubuntu 7.04 custom startup entries"
date: 2007-04-21
forum: General Help
---

### Post by tomy91 on 2007-04-21
I'm using Xubuntu 7.04 32bit, and I'm hosting HLDS (half-life dedicated server) on it! And i want to do something like that when I turn on the computer, HLDS starts automatically with my custom startup properties!

Now I'm starting the server in terminal with this command:
```

./hlds_run -game cstrike +ip <my IP> +port 27015 +maxplayers 16 +map de_dust2 +exec server.cfg -debug -pingboost 2
```

I hope you understand my problem that I want that this command starts automatically on startup! I want that you can show me how to make this. Don't know much about batch scripting on linux :(

P.S. There is no possibility to add custom startup entry @ Applications -> Settings -> Sessions and Startup Settings. 

P.P.S. Sorry for my bad English + I'm newbie on linux.

---

### Post by heimo on 2007-04-21
[FONT=monospace]I assume you have fixed ip address. Put the line in /etc/rc.local before "exit 0" line.
[/FONT]

---

