---
title: "Firestarter doesn't start during startup"
date: 2007-09-24
forum: General Help
---

### Post by milt on 2007-09-24
I have Ubuntu 7.04. I've seen similar problems in these forums but don't have what I need yet. Firestarter does not start during the Ubuntu start up routine. When I start Firestarter manually it asks for my password which I've already given before system startup. How can I get Firestarter to start during the start routine? I'm a newbie with Linux so please be specific. Thanks.

---

### Post by fedira on 2007-09-24
Hm... Try this:
Go to System > Preferences > Sessions
In the Startup Programs tab, click "New." 
Call it "Firestarter" (or whatever), and in the "Command" line, type:
```
sudo /usr/sbin/firestarter --start-hidden
```
Close the "Sessions" dialog and restart -- Firestarter should start up automatically. 

If someone could corroborate this before you try this, that might be good, since I haven't actually done this myself. ;)

This has some more involved instructions if the above doesn't work:
[http://www.howtoadvice.com/AutoFirestarter/](http://www.howtoadvice.com/AutoFirestarter/)

Also worth noting is that your firewall (iptables) is automatically on -- Firestarter is just a tool for modifying iptables, it's not the firewall itself. 
(see: [http://ubuntuforums.org/archive/index.php/t-457254.html](http://ubuntuforums.org/archive/index.php/t-457254.html))

---

### Post by por100pre1 on 2007-09-24
There's a way to do so, but instead I recommend you to disable that Firestarter startup. It is unnecessary (iptables is the actual firewall and it loads at startup), and it is a security breach (it uses superuser privileges to run).

---

### Post by p_quarles on 2007-09-24
> **por100pre1 said:**
> There's a way to do so, but instead I recommend you to disable that Firestarter startup. It is unnecessary (iptables is the actual firewall and it loads at startup), and it is a security breach (it uses superuser privileges to run).
I agree with por100pre1.

If you want the firewall to that firestarter created to be persistent, you can simply run it once, configure it, and then open a terminal and type:
```
sudo sh -c "iptables-save > /etc/iptables.up.rules"
```
Following that, run
```
gksudo gedit /etc/network/interfaces[/codes]
Following the line that lists your ethernet interface (usually eth0), add this:
[code]pre-up iptables-restore < /etc/iptables.up.rules
```
Save the file, and then your firewall will automatically load before the NIC connects to the network.

---

