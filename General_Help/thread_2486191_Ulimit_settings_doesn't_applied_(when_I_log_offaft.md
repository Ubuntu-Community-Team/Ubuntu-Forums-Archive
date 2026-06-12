---
title: "Ulimit settings doesn't applied (when I log off/after a while)"
date: 2023-04-22
forum: General Help
---

### Post by eyupp on 2023-04-22
Hello, I am developing a new module for my IPv6 Proxy Generation project. The name of the module is "rotating" and it changes the IPv6 addresses on the proxies every n minutes. This allows you to constantly use a new IPv6 address on the same port. However, I am encountering an error with high amounts of proxies (e.g. 2000). When I log out of the server after waiting for a period of time or after installing, the proxies stop working. If I restart the proxies through the script, there is no problem, but this defeats the purpose of using the module. I have tried using crontab, running it in the background with the sleep command, and using systemd, but none of these solutions have worked. I also tried using the disown command, but it did not work either. I have tried many solutions, but none have helped. Please help me..

---

### Post by TheFu on 2023-04-23
ulimit is a shell built-in for the soft limits.  

Typically, if a script/program needs a specific ulimit setting, I'd have the script that starts the program set it at the top. These values would be inherited by all child processes.
If a specific setting is required for a specific user, I'd set it in the ~/.profile which gets run at login.

I would expect the system default to be retained after a reboot.  This is a common "UNIX" thing.  Don't change settings system-wide, unless absolutely necessary. Prefer to change major settings only for the smallest possible impact.

Or am I missing something?

---

