---
title: "open ports / security"
date: 2007-09-26
forum: General Help
---

### Post by conehead77 on 2007-09-26
Im using Ubuntu for some months now and today i read sthg about security/firewalls etc.

So i scanned my ports with "sudo netstat -tulpen" and this was the result:

```
Aktive Internetverbindungen (Nur Server)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       Benutzer   Inode      PID/Program name   
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     0          22093      6773/hpiod          
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     0          21984      6713/cupsd          
tcp        0      0 0.0.0.0:15000           0.0.0.0:*               LISTEN     65534      22562      6999/wesnothd       
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     108        22184      6802/python         
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          105        21207      6410/avahi-daemon:  
udp        0      0 0.0.0.0:68              0.0.0.0:*                          100        27271      7520/dhclient       
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          105        21206      6410/avahi-daemon:  
```

I know avahi and dhclient arent an issue for security. Also the daemons(?) listening to localhost 127.0.0.1.

But i dont know about the wesnothd stuff.
I played "Battle Of Wesnoth" today, but it isnt running anymore. From what i read this could be a security issue, because it is set to LISTEN. Am i right?

If yes, let me know how i can prevent stuff like this. Do i need a firewall now?

---

### Post by pointone on 2007-09-26
For whatever reason, when Battle for Wesnoth installs, it includes a script that starts the Wesnoth server daemon on boot. Simplest solution is use update-rc.d to remove the symlinks to /etc/init.d/wesnothd.

---

### Post by conehead77 on 2007-09-27
Thx for the reply. I ran sudo apt-get autoremove meanwhile and this also removed the server program for wesnoth.
Looks still strange to me...

---

