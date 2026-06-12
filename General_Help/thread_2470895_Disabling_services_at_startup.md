---
title: "Disabling services at startup"
date: 2022-01-15
forum: General Help
---

### Post by sniper8752 on 2022-01-15
I am trying to figure out how to disable services on startup.  I know about 'systemctl disable <service-name>'.  
In this particular instance, I see KMail is enabled.  It shows up in my notification tray bar.  I tried disabling using the method above, but it does not work.  I also used the following method to check if it is enabled here:
sudo systemctl --all list-unit-files --type=service | grep -i kmail   
But that did not return anything.
How do I control which processes run at system startup?

---

### Post by deadflowr on 2022-01-15
kmail is a client so systemctl most likely will have no affect since that deals in services.
I'd look in the system settings startup listings.

---

### Post by dragonfly41 on 2022-01-15
A GUI I suggest for this is Stacer. Then look at Startup Apps window.
Of course you can use commands or System Settings, but in my view Stacer makes the task easier.

---

