---
title: "Run applications through SSH"
date: 2008-05-08
forum: General Help
---

### Post by jmasgalas on 2008-05-08
My main desktop is PCLinuxOS 2007. I can ssh to a server and run an app. This brings up an X shell where I can see the gui of the app. For example I ssh to a redhat server and type up2date I get the gui of up2date through my ssh session.

On my Ubuntu 8.04 laptop I cannot get this to work. The X shell never starts. I run a lot of apps remotely through SSH on my servers. How do I get this working in Ubuntu?

---

### Post by tamoneya on 2008-05-08
what command are you using.  I am not familiar with ssh in PClinuxOS but in ubuntu you need to enable X11 explicitly. e.g:```
ssh -X user@server.com
```

---

### Post by eldragon on 2008-05-08
and if you wish to save some bw (or have some speed)
ssh -C -X username@server

---

### Post by Whiffle on 2008-05-08
You first need to install ssh-server, and then edit /etc/ssh/sshd_config and turn on X11_Forwarding, then restart the ssh server.

---

### Post by jmasgalas on 2008-05-09
ssh -X worked. Thanks for your help guys;) I am slowly favoring Ubuntu more and more;)

---

