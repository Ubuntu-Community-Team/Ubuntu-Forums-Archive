---
title: "[SOLVED] How to delay asterisk's init script until network is up?"
date: 2008-02-29
forum: General Help
---

### Post by mfyahya on 2008-02-29
I have asterisk installed and configured to register with an IAX provider. The problem is when the system boots, asterisk runs but stays unregistered, until I manually issue a reload command at asterisk's console, or I run /etc/init.d/asterisk restart. Everything else works fine after that.

I'm guessing this could be due to the network not yet being up when asterisk is initialized. Is there a way to make asterisk's init script depend on the network script and wait for the interface to be up?

My system is a desktop with a single wired ethernet interface that was set up automatically since installation (gutsy). I didn't do any manual network configuration,  except for a "chattr +i /etc/resolv.conf" because some process kept overwriting that file every few minutes. 

Thanks for any suggestions.

---

### Post by harold4 on 2008-02-29
You could alter the /etc/init.d/networking script to fire off a reload.  It's a quick dirty fix until you come up with something better.

---

### Post by mfyahya on 2008-03-01
I added a `sleep 3` to asterisk's init script in the start section. It works fine now

---

