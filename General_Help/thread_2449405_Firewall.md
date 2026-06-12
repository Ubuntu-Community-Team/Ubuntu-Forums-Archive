---
title: "Firewall"
date: 2020-08-26
forum: General Help
---

### Post by candylovergirl on 2020-08-26
Hello

I was reading this wiki 
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

> 3. enable the firewall (sudo ufw enable) without further tweaks;

But I installed Gufw Firewall v20.04.01

Should I uninstall Gufw and type only the terminal commands?

Thanks

Camelia

---

### Post by mastablasta on 2020-08-26
you don't need firewall because all outgoing connections are disabled. you might need it if you are setting up a server. (maybe game server?)

gufw is front end for ufw, which i think is front end for iptables.

if you installed gufw then it means you have firewall installed. 
now you need to setup the rules for applications.[URL="https://help.ubuntu.com/community/Gufw"]
https://help.ubuntu.com/community/Gufw[/URL]

---

### Post by poorguy on 2020-08-26
GUFW is a GUI which allows the user to enable the UFW and make changes without going into the terminal.

I've found the default settings to work very well.

Since you have installed GUFW I'd go ahead and leave it installed as it easy to see the status of the firewall.


To enable firewall in terminal enter this command 

[B]sudo ufw enable
[/B]
press enter and then enter password and press enter.


If you want to check the the status of the UFW in the terminal enter this command

**sudo ufw status verbose**

press enter then enter password and press enter again.


Output should look like this.

```


thomas@hp-compaq:~$ sudo ufw status verbose
[sudo] password for thomas: 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
thomas@hp-compaq:~$ 


```

---

