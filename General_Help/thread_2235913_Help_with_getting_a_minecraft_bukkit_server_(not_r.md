---
title: "Help with getting a minecraft bukkit server (not related to the actual game/program)"
date: 2014-07-23
forum: General Help
---

### Post by Lauri_Tuumi on 2014-07-23
Hello Ubuntu forums. 

For a while I've had public minecraft server running on a mac mini late 2012 model. At first I ran the server in Mac os X because that's what the mac had installed already, but then what happened is that Mac os X began to chrash after the server running for long enough (the OS gave a report of the problem and so on so I don't think it's anything related to overheating or such). Because of this I decided that I'd install Ubuntu on the server mac mini so I'd have a good fresh OS to run the server on-

after installation I started tinkering with the server (which if you didn't know is a java .jar file you have to run from the terminal). and I was succesfully able to start the server and so on. But the problems I have are considering the automation of the server startup in case of a system chrash or a thunderstorm causing a power outage. I've been able to make Ubuntu run the server through running the startup script  (which you execute when you'd normally start the server through the console) of the server on reboot through rcon, but the problem is that there's no console to monitor the server or issue commands. 

So basiacly the main question  is if I can automate a terminal window window to open and run exec /path/to/the/server/server.jar or somehow have other kind of access to the command line of the server (I think there might be some programs or something that make you be able to remotely or locally control the terminal/command line of the Java server). 

All help will be grately appreciated :)

---

### Post by slooksterpsv on 2014-07-23
You can do an ssh server; I believe this is still relevant - [https://help.ubuntu.com/10.04/serverguide/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/openssh-server.html)

---

### Post by Lauri_Tuumi on 2014-07-23
But if I had the server already started up without the terminal would I still be able to access the command line of it through ssh??

---

### Post by slooksterpsv on 2014-07-24
Yes, ssh creates its own terminal session (tty) for you to use. So you can remote in and be at a terminal so if you need to reboot it, restart minecraft, run updates, or anything else via the CLI you can.

---

### Post by Lauri_Tuumi on 2014-07-25
> **slooksterpsv said:**
> Yes, ssh creates its own terminal session (tty) for you to use. So you can remote in and be at a terminal so if you need to reboot it, restart minecraft, run updates, or anything else via the CLI you can.

So you're saying if I had the server running as it normally would and suddenly there was a power outage, the server computer would automatically reboot after the power outage and I had the server script running on bootup through cron, I could still connect through SSH to somehow use the command line of the server even though it wasn't started through 
terminal or has a visible command line in the desktop?

---

### Post by slooksterpsv on 2014-07-25
SSH is a service on the system, so yes whenever you reboot it should start automatically. If you're away from home and have it as receiving a public IP or have port forwarding, you can still connect to it via ssh.

---

