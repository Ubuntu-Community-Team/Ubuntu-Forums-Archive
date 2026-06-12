---
title: "ubuntu not responding on ssh request"
date: 2007-09-10
forum: General Help
---

### Post by qtrader on 2007-09-10
Please bear me with my English.  I try to ssh back home to the ubuntu machine, but the machine  does not respond at all.   The ssh port is open on ubuntu firewall and forwarded to that machine from the router.   ssh login was tested good from another pc in the home network by using IPs from both inside and outside.   I think the network card on that ubuntu machine might be powered down automatically, or other problems beyond my level?  I wonder how to check/change power management for NIC and make the system wake up on network request?   Any help will be greatly appreciated!

---

### Post by insane_alien on 2007-09-10
can you ping the ssh server from the client machine? are you sure you got the IP right? are you using DynDNS or similar?

---

### Post by qtrader on 2007-09-10
Thanks for replying.  The IP is right for sure, because I have ssh working on a suse 10.0 server at home now (using a different port forwarding on the router).    

It seems that "ping" does not work for either server.  I tried "ping myip -p porttoubuntu" and "ping myip -p porttosuse" , but no package through.  

> **insane_alien said:**
> can you ping the ssh server from the client machine? are you sure you got the IP right? are you using DynDNS or similar?

---

### Post by qtrader on 2007-09-10
After some trying, I found out this: 
1. I can only use putty to ssh back to the suse server.   ssh from the console  does not work.  The suse server responded and asked for the paraphrase key, but didn't recognize it.  

2. With putty, after ssh login to suse server, I can ssh onto the ubuntu machine.    Both the internal ip and the external ip worked by this way. 

3.  Either putty or ssh commandline worked on ssh to the ubuntu server.  

How could this happen?  I am really confused.  



> **qtrader said:**
> Thanks for replying.  The IP is right for sure, because I have ssh working on a suse 10.0 server at home now (using a different port forwarding on the router).    

It seems that "ping" does not work for either server.  I tried "ping myip -p porttoubuntu" and "ping myip -p porttosuse" , but no package through.

---

### Post by Alex1770 on 2007-09-10
Just checking: did you install the openssh-server package? You need this if you want to ssh into your Ubuntu machine.

If this isn't the problem then you can check some things:
```
ps auwwx|grep sshd
```
to check the sshd is running
```
ifconfig
```
to check your IP address is what you think it is
```
ssh localhost
```
to check to see if you can log in to yourself

If all these tests pass, then it might be a firewall problem. Or it might be something else :-). Try looking at /var/log/auth.log (which should record ssh attempts), and maybe the other log files.

---

### Post by Alex1770 on 2007-09-10
> **qtrader said:**
> After some trying, I found out this: 
1. I can only use putty to ssh back to the suse server.   ssh from the console  does not work.  The suse server responded and asked for the paraphrase key, but didn't recognize it.  

2. With putty, after ssh login to suse server, I can ssh onto the ubuntu machine.    Both the internal ip and the external ip worked by this way. 

3.  Either putty or ssh commandline worked on ssh to the ubuntu server.  

How could this happen?  I am really confused.

Sorry, when I replied I hadn't seen your last two replies (I think they were somehow delayed), so my above suggestions are mostly redundant. I'm a bit confused as to what you mean. Are you saying you have two ssh clients on both machines ("ssh commandline" and "putty")? Your (2) and (3) above appear to be saying that you can ssh into your Ubuntu machine, which is what I thought the problem was, so I'm sorry for not understanding you.

In any case, you can still check some things.

```
tcpdump -i eth0
```
(replacing eth0 with the correct interface as shown by ifconfig) to check network traffic during ping and ssh attempts.

Look at the log files: /var/log/auth.log to see ssh attempts, 

Look at the little lights where the network cables are plugged in to the network cards to see if traffic is getting through.

Check the firewall on your router (as well as your machines) and maybe check how ports are forwarded on your router.

---

### Post by deadowl on 2007-09-13
Okay, I have the same problem. I used WireShark to try to figure out what the communications looked like, without it, it just seems like every machine trying to connect to mine is hanging.

1. Can receive TCP packets for ssh.
2. Can connect to ssh from same machine.

However, my computer isn't sending anything to machines that are trying to connect. My friend's computer had the same problem, so it doesn't seem Ubuntu-specific, but more like a problem with a firewall or configuration.

---

