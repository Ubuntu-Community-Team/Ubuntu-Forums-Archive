---
title: "HELP! Gnome freezes at Startup"
date: 2006-11-06
forum: General Help
---

### Post by oracle5 on 2006-11-06
It comes up with this error:

> There was an error starting the Gnome settings daemon.

Somethings such as theme, sounds, or background settings may not work correctly.
 
The last error message was:

Unabel to determin the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

Gnome will still try to restart the Settings Daemon next time you log in.

Then the screen freezes and I can't do anything.

I'm completely lost on what to do. Please Help.

---

### Post by oracle5 on 2006-11-06
bump

---

### Post by David Corrales on 2006-11-06
Did you recently install or uninstall stuff? I've seen some people mistakenly remove their d-bus which completely kills everything lol.

---

### Post by oracle5 on 2006-11-06
No but I logged into the failsafe terminal and started x. It worked fine there. Then I logged into my account through a nested window and found that having my bottom panel transparent was the problem. Some reason it worked in the nested login. Seems odd but I guess I can get by without transparency for now.

---

### Post by zorkerz on 2006-11-15
I have a similar error.  Sometimes Gnome takes an extremely long time to start up after login when it does the theme dose not work properly and I get this error.

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Sometime however gnome starts without any problems.
anyone know what this last paragraph is talking about, thank you.
elias

---

### Post by zorkerz on 2006-11-15
Ok this [thread]("http://www.ubuntuforums.org/showthread.php?t=291116&highlight=there+was+an+error+starting+the+gnome+settings+daemon") seams to be more relevant to my error.

---

