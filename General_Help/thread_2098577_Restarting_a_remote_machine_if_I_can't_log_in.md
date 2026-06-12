---
title: "Restarting a remote machine if I can't log in"
date: 2012-12-27
forum: General Help
---

### Post by irsmart on 2012-12-27
I'm the administrator of a web server running Ubuntu. (It's virtualized but I don't have access to the physical machine and that administrator isn't available.)

Somewhere along the line (between apache and wordpress) I think a fork bomb exploded, exhausting all system resources. (I got an error message saying bash couldn't fork to run ls then was forced to log out.)

The only fix for this that I know of is to restart the machine. However, since I don't have access to the physical machine and I can't log into the virtual server via ssh (gives me this error)

```
ssh_exchange_identification: Connection closed by remote host
```

I do have access to other machines on the local network. Other than just trying repeatedly to log in via ssh is there any way to restart the server? Thanks!

---

### Post by chadk5utc on 2012-12-27
> **irsmart said:**
> I'm the administrator of a web server running Ubuntu. (It's virtualized but I don't have access to the physical machine and that administrator isn't available.)

Somewhere along the line (between apache and wordpress) I think a fork bomb exploded, exhausting all system resources. (I got an error message saying bash couldn't fork to run ls then was forced to log out.)

The only fix for this that I know of is to restart the machine. However, since I don't have access to the physical machine and I can't log into the virtual server via ssh (gives me this error)

```
ssh_exchange_identification: Connection closed by remote host
```

I do have access to other machines on the local network. Other than just trying repeatedly to log in via ssh is there any way to restart the server? Thanks!

If you are unable to connect and have no physical access I am unaware of any method of remote restart/reboot..

---

### Post by irsmart on 2012-12-27
That was my guess. I was hoping there'd be some type of signal I hadn't heard of to send to the machine over a local network similar to Wake-On-LAN but rather Reboot-On-LAN. Thanks though.

---

### Post by rnerwein on 2012-12-27
> **irsmart said:**
> That was my guess. I was hoping there'd be some type of signal I hadn't heard of to send to the machine over a local network similar to Wake-On-LAN but rather Reboot-On-LAN. Thanks though.
hi
i don't know how important this server is. but may be it's a solution, for former times, to
have a low coast PC which is connected via a serial line to the server and on the other side
to the network. then it shold be possible to bring the server save down. nearly all companies i worked they got this solution ( on pc you can more server to it). mostely they uses an embeted linux box.
mostely people have to learn about errors.
cheers

for future tell them there are a couple of tuning parameters in the system ( i don't understand that there is by default mostely per user no limit set) to restrict those situations. on security discussions they make a mouse to an elefant but that any normal user can bring down a huge server by just exhause those limits i can't understand. by the side - tuning is my professional. first watch the server to figure out what's normal then race up these conditions but let always a trap for the root user.
have fun

---

