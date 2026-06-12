---
title: "Amule-daemon in the sturtup"
date: 2005-08-31
forum: General Help
---

### Post by Eleka on 2005-08-31
Hello!!!

First, excuse me for my english, it's really bad.

I've installed amuled (amule-daemon) to have a amule running without login in my PC. It works very fine, and I can acces it with amuleweb, but I want to run it without login, because now I run the amuled on a terminal, and if I close my session, it will be closed.

I think that I have to add a script in my /etc/init.d and in the /etc/rcN.d, but I don't konw very well how can I do this

Can anybody help me?

---

### Post by makhand on 2006-01-23
You dont need to do all of that. You can just use the 'screen' utility to accomplish your task. All you would have to do is login through a shell, type 'screen', then you might have to press enter, then start your amuled, then you can pressy 'Ctrl-d' to 'detatch' from your screen. At this point you can logout and in as you wish, your application will keep running. To reconnect to the screen session, login and type 'screen -r'. You will then see yourself back where you started your amuled. here you can stop it or do whatever you wish. 

now, if you could just tell me how to get amuled?

---

