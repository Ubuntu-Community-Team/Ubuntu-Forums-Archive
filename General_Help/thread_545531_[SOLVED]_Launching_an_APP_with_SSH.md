---
title: "[SOLVED] Launching an APP with SSH"
date: 2007-09-07
forum: General Help
---

### Post by phibit on 2007-09-07
Is there a way to launch an application on an SSH server? 

For example, I have an ssh server running on my home desktop. Say I was on my laptop at school, and I SSHed into my desktop computer. Could I launch Amarok to run ON MY DESKTOP (the ssh server)?

I've tried ssh with the -X parameter (ssh -X nnn.nnn.nnn.nnn) but that just launches Amarok onto  the client... :(

---

### Post by phibit on 2007-09-08
Alright I solved this with a bit of research so I figured I'd share. Apparently it has to do with the $DISPLAY variable the X-Server uses. The trick is to set it after you connect to the ssh server.

On the server, run: 
```
echo $DISPLAY
```

For me this was just  ":0.0" . Remember it.

Then, connect to your ssh server from a remote computer, and enter the following, using the variable you picked up before.

```
export DISPLAY=:0.0
```

That will run any X-Server GUI programs you run in your ssh session on the remote hosts computer.

---

