---
title: "vncserver problems"
date: 2008-04-04
forum: General Help
---

### Post by taliosfalcon on 2008-04-04
I installed vncserver via apt-get, when i start it with vncserver it seems to work fine, prompting me for a password, saying its running as whatever:1, whatever:2 etc. However I can't actually connect to it. When I do a ps -ef | grep vnc the only result is that command which means vncserver isn't even running afaik. This problem has persisted through 3 OS reformats (various reasons, mostly doing install testing for a business rollout) Anyone have any suggestions as to how to go about fixing it?

---

### Post by cdenley on 2008-04-04
What does your ~/.vnc/xstartup look like? Anything listening on port 5901 (netstat -l)? You can try vnc4server.

---

### Post by taliosfalcon on 2008-04-04
There is no xtstartup in .vnc, just a bunch of (empty) log files for various instances i've tried to start and .pid files. And no, nothing listening on port 5901
edit: just tried vnc4server and it seems to work fine. Ideally I would still like to get vncserver working though as it's what the users are used to, and they will not stop complaining if they need to type "vnc4server" instead of "vncserver" it's just how they are =/

---

### Post by cdenley on 2008-04-04
I can't really help you with the old vncserver since it does not seem to be available for hardy. Maybe this command lets you switch which version is the default.
```

sudo update-alternatives --config vncserver

```
If not, you can remove the vncserver package, then create a link
```

sudo apt-get remove vncserver
sudo ln -s vnc4server /usr/bin/vncserver

```

---

