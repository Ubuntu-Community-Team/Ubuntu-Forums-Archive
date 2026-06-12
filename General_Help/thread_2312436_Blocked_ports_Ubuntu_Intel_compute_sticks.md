---
title: "Blocked ports Ubuntu Intel compute sticks?"
date: 2016-02-04
forum: General Help
---

### Post by Puls8 on 2016-02-04
Hi all,

Since a few days I have the Intel compute stick (1 GB RAM version) to play with. Replacing the desktop with Lubuntu makes it a really neat pocket gadget ;)

Now I want SSH into the stick, but I can't get it to work eventhough I have setup ssh on earlier occasions, but not on this device. First, I installed dropbear but I couldn't reach the stick by ssh from my laptop. (checked IP address). Removed dropbear and installed openssh-server. No luck and rebooted and checked IP address again. Set a static address, still no luck. Then I did a networkscan; all my devices showed up, but not the stick. So I thought maybe a strict firewall is running, but ufw reports 'inactive'. When I ssh to in the terminal to its own IP address, it says "couldn't resolve hostname". Finally I installed ngrok and it worked!

I am totally without a clue; I just want a simple ssh login...

TIA

(Tried even this morning to setup a new ssh connection between two PC's at work: worked within 5 minutes without a flaw.)

---

### Post by sandyd on 2016-02-04
Hi, does sshd show that it is listening when you run
```

sudo lsof -Pni :22

```

Is there any traffic if you install TCPDump on the stick and run
```

sudo tcpdump -i eth0 'port 22'
```?

---

### Post by Puls8 on 2016-02-04
Hi Sandyd,

Thanks for your help.

As I have set sshd port to 2222 (maybe port 22 was blocked), I adapted your commands accordingly:

```
[FONT=arial]sudo lsof -Pni :2222[/FONT]
[FONT=arial]COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME[/FONT]
[FONT=arial]sshd    1179 root    3u  IPv4  14546      0t0  TCP *:2222 (LISTEN)[/FONT]
[FONT=arial]sshd    1179 root    4u  IPv6  14548      0t0  TCP *:2222 (LISTEN)[/FONT]

```
The stick has only a wireless adapter...
```
[FONT=arial]tcpdump -i wlan0 'port 2222'[/FONT]
[FONT=arial]tcpdump: wlan0: You don't have permission to capture on that device[/FONT]
[FONT=arial](socket: Operation not permitted)[/FONT]


``` 
This last one doesn't look good. What does it mean?

---

### Post by sandyd on 2016-02-04
Forgot a sudo in the second command - fixed

---

