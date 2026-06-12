---
title: "Access PM2 process?"
date: 2020-09-06
forum: General Help
---

### Post by Andrew_Benjamin on 2020-09-06
I set up a server for my son on a cloud VPS.  Among other startup actions, it starts up a minecraft server via pm2.
specifically, it runs a .sh file which reads:

sudo screen -S "Minecraft"
cd /minecraft
sudo java -Xmx1024M -Xms1024M -jar server.jar nogui


It works fine.

pm2 list shows it as id 2 with everything as one would expect; watching is 'disabled' - I don't even know what that means, if it is pertinent.

issuing 'screen -ls' tells me no sockets found.
'screen -r' tells me there is no screen to be resumed.


Is there a way to access the "Minecraft" screen is he wants to make live changes?  I can stop Minecraft and make edits to the world properties file and restart, but that seems rather awkward.

Solutions?

Andrew

---

### Post by Holger_Gehrke on 2020-09-06
Unless you misquoted that script, screen runs a shell as root and has nothing whatsoever to do with the actual Minecraft server, which gets started afterwards and outside of screen. If you wanted to run the server as root inside screen it should be something like:
```

cd /minecraft
sudo screen -S "Minecraft"  java -Xmx1024M -Xms1024M -jar server.jar nogui

```
Since screen keeps sessions separate per user, you'd have to run 'sudo screen -ls' to see the session and 'sudo screen -r' to attach to it.

As far as I know a server started with 'nogui' does not have an interactive console (and it's kind of problematic to have a GUI on a remote server; not impossible, but problematic). You might see some status messages and (non-fatal) errors, but that's it. To control the server remotely you need to enable rcon (remote console) in server.properties (and set a password for it) and connect to that using one of the rcon-clients for minecraft like [mcrcon]("https://github.com/Tiiffi/mcrcon").

Holger

---

### Post by Andrew_Benjamin on 2020-09-07
Thanks for the insight; now I have somewhere to start.

Andrew

---

