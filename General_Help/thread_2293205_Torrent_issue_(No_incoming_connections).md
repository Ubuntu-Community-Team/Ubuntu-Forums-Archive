---
title: "Torrent issue (No incoming connections)"
date: 2015-09-03
forum: General Help
---

### Post by M1n1M3 on 2015-09-03
Hi all, my first thread.
To start with I'm new to ubuntu, it's a bit different from Windows.

My ubuntu is 14.04 LTS, installed 3 weeks ago. No modification from my side, straight out of the disc. My internet comes from a fiber connection (100/100) straight to the computer, no router. From a user friendly ISP, Bahnhof.

My current problem is this. I started to use Deluge 1.3.6. I can download without problems, while I download I upload porly 1-2 peers with 10-40kB/s. When download finish, the seeding stops. I get the red warning '!' no incoming connection.

I delete deluge, try transmission the same issue, and don't like the look of that app. So I install qBittorrent, and get the same issue there, the yellow warning in the bottom.

I google, and look in here for solution. I check the firewall that is by default closed of in ubuntu. It is off, I turn it on and create a rule to open port 49995 on all. I go to terminal and use sudo ufw status, and it is all allowed.

so recap.
qBittorrent with port 49995
firewall off or on with rule for port 49995 open.
No router
Torrents with 20+ peers. (you can see 1-2 popup in the peerlist, but dosnt download anything and disappear.

Any ideas?
or any more info you need.

Cheers
Nic

---

### Post by angrymoose on 2015-09-04
If I understand correctly you are connected directly to the internet via a modem. First thought is that you'r port is closed. To check if your port is open go to ```
http://www.canyouseeme.org/
``` and pop in your port and tell us if it responds as open or closed.I believe despite your attempts your port is actually closed. So if after checking that site your port is reported as closed try the following listed below.

Open terminal

Become Root.

```
sudo su -
```

Iptables rules to allow traffic in.

```
iptables -P INPUT ACCEPTiptables -F
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp --dport 49995 -j ACCEPT
iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -L -v

```

To Save Iptables Rules On Reboot. While the code posted below will work quite well there is probably a better way to do it now.

```

iptables-save > /etc/iptables.up.rules

nano /etc/network/if-pre-up.d/iptables
```

Insert into file opened with nano

```

#!/bin/bash
/sbin/iptables-restore < /etc/iptables.up.rules

```

Chmod the file to execute on boot.
```
chmod +x /etc/network/if-pre-up.d/iptables

```

---

### Post by M1n1M3 on 2015-09-09
Sorry for the delay, had a back injury, but I'm back on my feet again :D

> **angrymoose said:**
> If I understand correctly you are connected directly to the internet via a modem. First thought is that you'r port is closed. To check if your port is open go to ```
http://www.canyouseeme.org/
``` and pop in your port and tell us if it responds as open or closed.I believe despite your attempts your port is actually closed. So if after checking that site your port is reported as closed try the following listed below.

That's correct. After checking this canyouseeme.org, All ports are closed (49995, 80, 53 etc..). I get this error:

Error: I could not see your service on [my IP] on port 49995
Reason: Network is unreachable

> **angrymoose said:**
> 
Open terminal

Become Root.

```
sudo su -
```

Iptables rules to allow traffic in.

```
iptables -P INPUT ACCEPTiptables -F
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp --dport 49995 -j ACCEPT
iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -L -v

```


I get to:
iptables -P INPUT ACCEPTiptables -F

Then it gives me this error:
iptables v1.4.21: cannot use -F with -P
Try 'iptables -h' or 'iptables --help' for more information.

I will show how technical I'm with this statement:
I pressed [enter] after the first line, didn't find a way to switch line so couldn't write the whole section. 

I can't find the link now, but I tried something someone here wrote about testing ports, I did like they wrote and there it said my ports was open. I will try to find that post again.

EDIT: found it.
sudo ufw status

status: active
TO         Active    From
49995/tcp         ALLOWED     Anywhere
49995/udp         ALLOWED     Anywhere
49995/tcp (v6)   ALLOWED     Anywhere
49995/udp (v6)  ALLOWED     Anywhere

49995/tcp         ALLOWED OUT    Anywhere
49995/udp         ALLOWED OUT    Anywhere
49995/tcp (v6)   ALLOWED OUT    Anywhere
49995/udp (v6)  ALLOWED OUT    Anywhere

What will I do with this iptables error?

---

