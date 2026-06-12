---
title: "Overnight meltdown"
date: 2018-12-04
forum: General Help
---

### Post by nickj01 on 2018-12-04
I'm running Ubuntu creative studio. Last night everything was working great. This morning however I am faced with a litany of issues.

1. Firefox tabs keep crashing
2. Can't shut down or log off except with terminal
3. All favorites from start menu gone
4. Can't save writer documents odt
5. Can't launch chrome

I have no idea what is going on. Has anyone any ideas? Do I have a virus? Am I being hacked? Has some update taken place over night that's destroyed my system?
Or am I doing something stupid that's making my life miserable?

I'm not really getting any error messages or system feedback. So I can't really post any extra information to assist troubleshooting. Any insight at this point is welcome.

---

### Post by TheFu on 2018-12-04
Check the system logs.  There is a log viewer ... or use any of the built-in CLI text tools.  Logs are in /var/log/

I suspect hardware is failing, guessing the storage is most likely.

Make daily backups going forward if you don't see anything in the logs.

---

### Post by HermanAB on 2018-12-05
It is not necessary to wonder what is going on.  Run top and df.  

See whether the disk is full of junk and whether there are zombie processes and memory leaks.

---

