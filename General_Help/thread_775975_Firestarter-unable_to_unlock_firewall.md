---
title: "Firestarter-unable to unlock firewall"
date: 2008-04-30
forum: General Help
---

### Post by whovian777 on 2008-04-30
If I lock firestarter it crashes when I attempt to unlock it. The lock is still active after firestarer is shut down. I can remove it if I restart the connection. Worse still if I lock the firewall and turn on the screen saver after I come back NOTHING works. Can't even shut things down! This all happened when I installed Hardy heron. It was a clean install.

---

### Post by whovian777 on 2008-05-01
Hey, am I going to get any help from anybody? Maybe this is why linux is so unpopular!

---

### Post by 45acp on 2008-05-01
I have the same problem. I can't unlock the firewall after it has been locked with firestarter. I have to kill firestarter and then reboot to get internet access back. Know idea as to a fix.

---

### Post by nowshining on 2008-05-01
be calm, also u don't need firestarter for the firewall, as it's a GUI for the built in Iptables. If you can manage I suggest arno-iptables-firewall in the repos - it's a script for iptables and in /etc/arno-iptables-firewall/custom-rules you can insert your own custom rules but easier is to read and use firewall.conf.

Or you can try guraddog which is another one.

there are many scripts/gui's for iptables or you can create your own. :)

for the firestarter problem my only suggestion is switch.

---

### Post by whovian777 on 2008-05-02
Arno doesn't install correctly. Yeah, I know it's a front end iptables. How about this, instead of suggesting something else how about someone find a way to fix this problem. Firestarter is popular and I'm bet other people are having this problem as well!

---

### Post by nowshining on 2008-05-03
arno should install fine, there is no specific point & click GUI for it, it's all txt files however u'll need sudo privs by default to edit the rules, config, and even restart the firewall after making such changes...

I had problems with firestarter myself on earlier versions of ubuntu as the last time I used it it was too old to work properly so that's why I suggested a switch.

either switch or wait for a reply on a fix if you do get any or have you tried searching the web for your problem with keywords, etc... on a search engine?

---

### Post by ramjet_1953 on 2008-05-03
The question begging to be asked here, is why are you using Firestarter in the first place?

Are you aware that Firestarter is only a GUI for iptables and is NOT a firewall.

Unless you need to do port forwarding, there is no need to use firestarter, as iptables is configured to close all ports and your system is secure.

What do they say about trying to fix something that isn't broken?

Regards,
Roger :cool:

---

### Post by jocko on 2008-05-03
> **ramjet_1953 said:**
> Unless you need to do port forwarding, there is no need to use firestarter, as[COLOR=Red] iptables is configured to close all ports and your system is secure[/COLOR].

Actually by default iptables is not configured at all, which mean ubuntu by default have no firewall.

You can check this by:
```
sudo iptables --list

```
Which reports this, unless you have configured iptables yourself:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

### Post by Paris Heng on 2008-05-03
> **jocko said:**
> Actually by default iptables is not configured at all, which mean ubuntu by default have no firewall.

You can check this by:
```
sudo iptables --list

```
Which reports this, unless you have configured iptables yourself:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

This i am looking for, thanx

---

### Post by friendofpugs on 2008-05-13
I just had the same problem. As a test, I locked the firewall down in Firestarter and it went dead on me. Even after I killed it, it was still locked. It also wouldn't restart; only a reboot got me going again. Very unnerving. I'm still getting over the Windows-mindset where I have to have a firewall up at all times, but I didn't know iptables was already running under the surface. Just as long as I'm stealthy, I feel okay. Somebody should check into that Firestarter glitch though.

---

### Post by Gotit on 2008-05-22
I have the same problem:
New Hardy install
Firestarter v1.0.3 from Add/Remove
Firestarter > lock
Firestarter > unlock and it dies (turns gray)
Must reboot to get internet access

I need to open a port to share my printer on my desktop and used Firestarter in Gutsy.

> **friendofpugs said:**
>  Just as long as I'm stealthy, I feel okay. 

To check this go [here]("http://www.grc.com/default.htm") and select "ShieldsUp" to run a scan (it's under Hot Spots).

---

### Post by Philip41987 on 2008-05-24
I have the same problem - Have to re-boot to unlock. 

ALSO Firestarter seems to have a problem when booting. On boot up the system starts Firestarter then closes it and the closing fails. This requires a drive inspection, a start failure (drive inspection) and restart- failure and finally continues to boot without Firestarter. Makes the boot time two or three minutes longer. 

There is an error message: UFW not enabled. 

What does this mean and How do I fix this?

---

