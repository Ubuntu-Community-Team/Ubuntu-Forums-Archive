---
title: "permission issue"
date: 2015-06-16
forum: General Help
---

### Post by shishini on 2015-06-16
Greetings, 

suddenly i started to face some permissions issues
- i can no longer install updated from apper, unless apper or muon updater or whatever tool is started with root permissions using sudo (note apper doesnt prompt me anymore for my password as it used to and it give me an authorization error type of message)
- usb sticks and the like no longer load, unless i start the file manager (dolphin in my case) using sudo
- i cant connect to wifi (i have no idea how to do this as using sudo) (i get an error message not authorized to control network)

so for the more general problem what went wrong, what happened, 
and as a quick fix, since i can no longer connect to wifi and i am currently in a place where i just cant pluggin a physical cable 
how can i sudo myself into wifi

thank you

---

### Post by TheFu on 2015-06-17
Running some GUI programs with sudo can lead to issues like you've described. It is best to **never** use sudo with any GUI program. This is because files created that way will be owned by root:root and your userid can't do anything about it later.

It is best to learn about file and directly permissions so this doesn't happen again. There are tutors easily found with a quick search - "linux permissions tutor"

Now for corrective action - which has some risks too.  Run **sudo chown -R $USER:$USER $HOME** but the current situation is much worse that what that command can harm.

Now logout and login again.  All fixed?

---

