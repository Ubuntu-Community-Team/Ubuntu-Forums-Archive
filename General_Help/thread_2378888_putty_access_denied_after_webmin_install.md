---
title: "putty access denied after webmin install"
date: 2017-11-28
forum: General Help
---

### Post by tjamison1 on 2017-11-28
running ubuntu 17.40 on a host vps cloud server. Installed webmin via putty/root access. Webmin is up and running fine but now I get access denied when trying to use putty to install a shopping cart. The only changes I made to webmin was to install socket6 perl and activate ssl and changed port location. No other changes made. Putty will let me sign in as root but will not accept my password.

---

### Post by dragonfly41 on 2017-11-28
[COLOR=#000000]"changed port location" .. suggests might be port conflict

I have webmin (for development) and to check such conflicts I installed zenmap and run "gksu zenmap" looking at localhost.[/COLOR]

---

### Post by tjamison1 on 2017-11-28
I only changed the webmin port, the ssh port is still 22

---

### Post by dragonfly41 on 2017-11-28
You will find threads on the topic .. did you restart webmin server .. and I would still try zenmap

[https://ubuntuforums.org/showthread.php?t=984258](https://ubuntuforums.org/showthread.php?t=984258)

[http://blog.serverbuddies.com/changing-the-webmin-port/](http://blog.serverbuddies.com/changing-the-webmin-port/)

---

### Post by tjamison1 on 2017-11-28
for anyones info I fixxed it by going into webmin/change password for root and sshd and used my original password in both then saved. now its aok.

---

