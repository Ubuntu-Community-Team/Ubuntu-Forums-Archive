---
title: "ssh 5900 port forwarding"
date: 2007-09-14
forum: General Help
---

### Post by phillips321 on 2007-09-14
Hi guys,

Been using vnc for ages over ssh,

I use my windows pc at work to connect to my vnc ubuntu desktop at home.

How i do this is by using putty to connect to my ssh server(port 22) whilst also tunneling port 5900 over the ssh session. Once connected to the linux box i run x11vnc to start the vnc server.

Then on the windows box i open vncviewer and connect to localhost:5900.

How do i do the same but from linux-->linux?

I have tried ssh 5900:phillips321.getmyip.com:5900 but it doesnt work, any ideas?

Cheers in advance

---

### Post by MrFSL on 2007-09-15
Here is how I do it in a nutshell.

```
ssh -l <USERNAME> -L 5900:localhost:5900 <SERVER> -f 'x11vnc -localhost -forever -usepw  -display :0'
```

---

