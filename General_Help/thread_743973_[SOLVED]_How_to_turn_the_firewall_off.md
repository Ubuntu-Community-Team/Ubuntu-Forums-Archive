---
title: "[SOLVED] How to turn the firewall off ???"
date: 2008-04-03
forum: General Help
---

### Post by LinuX-M@n1@k on 2008-04-03
When I run "nmap localhost", it says that the server is down... I think it's a firewall issue, but I'm not sure because I installed Firestarter and stopped it.
```
boris@linux:~$ nmap localhost

Starting Nmap 4.20 ( http://insecure.org ) at 2008-04-03 13:04 EEST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 4.007 seconds
boris@linux:~$
```

It's the same thing with root privileges too:
```
boris@linux:~$ sudo su
root@linux:/home/boris# nmap localhost

Starting Nmap 4.20 ( http://insecure.org ) at 2008-04-03 13:09 EEST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 4.036 seconds
root@linux:/home/boris#
```

What do I do ?

Edit: With "nmap -P0 localhost" I wait about 5-10 minutes and nothing happens...
```
root@linux:/home/boris# nmap -P0 localhost

Starting Nmap 4.20 ( http://insecure.org ) at 2008-04-03 13:11 EEST
```

---

### Post by sekinto on 2008-04-03
Firestarter isn't really a firewall, it is a tool that monitors connections and allows you to configure iptables (which is a firewall kind of), iptables is active no matter what the state of Firestarter is.

---

### Post by LinuX-M@n1@k on 2008-04-03
Okay... any ideas what's happening ? What's blocking those ping probes ?

---

### Post by njparton on 2008-04-03
I've had similar problems in the past and have resorted to installing webmin and using that to configure iptables.
 
I've never quite figured out firestarter or iptables...
 
Give webmin a try?

---

### Post by LinuX-M@n1@k on 2008-04-03
I'll try it and post back. Thanks

---

### Post by LinuX-M@n1@k on 2008-04-03
I've managed to stop the firewall using [this]("https://help.ubuntu.com/community/IptablesHowTo") and [this]("http://ubuntuforums.org/showthread.php?t=159661"), but I still get the same error :( Please help me !

Edit: Oops, sorry for the double post, I should edit the last one...

---

### Post by cdenley on 2008-04-03
To remove firestarter
```

sudo dpkg -P firestarter

```

To clear firewall rules
```

sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -F

```

If you still can't connect to the server, then we will need more information about the server.

---

### Post by LinuX-M@n1@k on 2008-04-03
The "server" is my computer, and nmap says that it's not running and that I should try with nmap -P0 localhost... o_O
I still get that error with nmap localhost
I'm not trying to run any server application, I just can't run nmap localhost ( There were no problems before... )
I'm using Ubuntu Desktop 7.10

Edit: I meant that the host is down, not the server, my bad .. :(

****EDIT: Fixed ! localhost was down**
```
ifconfig lo 127.0.0.1 netmask 255.255.255.255
```

---

