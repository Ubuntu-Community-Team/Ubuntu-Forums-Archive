---
title: "Samba Access"
date: 2007-07-15
forum: General Help
---

### Post by maxehhh on 2007-07-15
Well, i'd installed Samba in a server from Home... i've got the server here in my home network and i want my father to access through it from his office... but the problem is that i have a router, and i don't know how to setup the ports, how do i know wich port is Samba using? I left a draw with what i have :P

[[IMG]http://img294.imageshack.us/img294/3986/picjo1.th.jpg[/IMG]](http://img294.imageshack.us/my.php?image=picjo1.jpg)

Well, that's what i have

---

### Post by maxehhh on 2007-07-15
anyone plz?

---

### Post by JohnnySkidmark on 2007-07-15
Hmmm, looks like port 139:
```
# netstat -at
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
[snip]

# grep netbios-ssn /etc/services
netbios-ssn     139/tcp                         # NETBIOS session service
netbios-ssn     139/udp
```

I don't think Samba is especially well-suited for internet access, though, and I'm not sure if what you're trying to do would even work.  Something like FTP might work better, or even setting up a VPN connection so his office computer can access the Samba server as if it were on the same network.

---

### Post by maxehhh on 2007-07-16
ok i guess i will have to take the pc to the office... and then share the ssh for internet and can manage the server from here... thx

---

