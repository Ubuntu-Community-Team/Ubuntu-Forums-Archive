---
title: "SSH to other computer on network"
date: 2006-09-25
forum: General Help
---

### Post by skale on 2006-09-25
Yes, I've searched.

My cousin was able to ssh to his computer (800 miles north), so everything works. I just don't know how to use it.  Here's what I did:

I tried "ssh 192.168.1.103" and got a "port:22 connection refused"
I tried the internet IP address, "ssh 24.99.65.244" and got the same result.

Help, anyone? I bet the syntax is way off.

---

### Post by lamego on 2006-09-25
Are you tring to connect from the internet to a intranet ?
Have you enable port porwarding for port 22 on your router ? You need to add a port forward rule on your router so that ssh traffic goes into your intranet server.

---

### Post by LotsOfPhil on 2006-09-25
Your syntax isn't wrong. 

What are you trying to ssh into? The first address (192.168.1.103) is something on the your-home side of the router (if you have one).

Does the computer you are trying to ssh into have an SSH server installed?

---

### Post by skale on 2006-09-25
Yes, everything is installed. THe other computer cannot get on to mine with the same "port 22" issue. Sorta like the "Catch 22" story. Well not really.

How do you open up the port? Also, what is porwarding? I thought it was a typo, but it googles. 

I have a linksys <somenumber> Wireless B

Update: 
I did the port forwarding thing to 192.168.1.102 for port 22
Same old.

---

### Post by Esmo2000 on 2006-09-26
Sounds very much like your request is being rejected due to lack of a SSH server.  Are you sure you installed one?

J

---

### Post by LotsOfPhil on 2006-09-26
I agree with Esmo2000. In a terminal, type 
```
sudo apt-get install ssh
```
and let us know what it says (this will see if you have the ssh server installed).

If it is installed, and your portforwarding is done correctly, I think we'll need more details to figure out the problem.

---

### Post by pyxu619 on 2006-09-26
Hey LotsOfPhil,

Do you know how to start the ssh server service when it is installed?

---

### Post by LotsOfPhil on 2006-09-26
sudo /etc/init.d/ssh restart

---

### Post by hellmet on 2006-10-11
thanks for the thread

---

