---
title: "setting up port tunneling and putty on my pc"
date: 2007-11-21
forum: General Help
---

### Post by russian460 on 2007-11-21
hey  i have a problem my school block alot of proxy sites and most ports

i have set up my ubuntu machine and i can connect using vnc but the school blocks port 5500 5600 5700 5800 and 5900 pretty much all the ports 
and i also have a friend who set up his machine and gave me access my problem is that i want to run putty and connect to my own server than configure firefox so i can use the pc at home as a proxy

i do not know much about port tunneling or forwarding so help could be apreciacted 
so hos do i set up so i can connect to my home machine?

---

### Post by mellowd on 2007-11-21
What kind of router you got at home? Setting up a port forward is pretty easy. This is a good site to check for your particular router: [http://www.portforward.com/](http://www.portforward.com/)  Click on guides and look for your device

---

### Post by russian460 on 2007-11-21
iv got a linksys router now what ? i have port forwardign set up but the school blocks almost all the ports

---

### Post by mellowd on 2007-11-21
Find out which ports aren't blocked. You'll need at least 1

---

### Post by russian460 on 2007-11-21
ok i got one but for future reference how do i find out what
ports are not  blocked? how do i scan them or at least i tihnk i find that out by scanning 

but anyway i got an open port

---

### Post by mellowd on 2007-11-21
Scanning isn't a good option. The school might think you're doing something dodgy. The best thing to do is just ask.

What's the port number you got?

---

### Post by russian460 on 2007-11-21
8118 is the port 
if i cant scan and i dotn think they will tell me if i ask 
now what do i do?

and why cant i scan ?? is there another way to scan if not how do i scan?

---

### Post by mellowd on 2007-11-21
Don't bother scanning if you already have a port.

Now edit your config file on your linux box:

```
sudo vim /etc/ssh/sshd_config
```

substitute your favourite editing program instead of vim above if you don't know how to use it. Look for the port number and change it to 8118. While in this file search for PermitRootLogin and change it to no. Save and exit and then type this:

```
sudo /etc/init.d/ssh restart
```

Then configure your router to forward port 8118 to your linux box. Now you'll be able to ssh into your box using port 8118

---

### Post by russian460 on 2007-11-21
thats it? so after that i open putty at school and input the  ip and port and im connected rite??

but when im  suding my friends server i have to go to the tunnels section of putty and add a local host and another port thats where i input the 8118 port

---

### Post by mellowd on 2007-11-21
If you just want to SSH then you don't have to do anything more. Just open putty, stick in your home IP, change the port and connect.

---

### Post by russian460 on 2007-11-21
umm yea im a complete noob at this stuff whats ssh? and why do i have to input a port and localhost in the tunnel section of putty.

---

### Post by mellowd on 2007-11-21
ssh = secure shell. A secure way of connecting to your box as opposed to something like telnet. You don't have to put anything into the tunnel section if you just want to ssh into the box

---

### Post by russian460 on 2007-11-21
ok i understand so when i ssh it encrypts the data and sends it so the blocker cant catch it?
than why did i have to input the 8118 port into the tunnel section along with local host for the firefox proxy settings to work? work?

---

### Post by mellowd on 2007-11-21
I never mentioned putting anything in the tunnel section. I mentioned changing the port on the basic setup page on putty which is the first page you see.

This is essentially what's happening. First, because your server is behind a router, NAT is happening. Meaning that your server has an internal IP, something like 192.168.1.x/24 or whatever. Your router picks up an IP address from your ISP. That IP address is then shared via NAT to all the computers in your LAN (NAT = Network Address Translation) which then lets you share one public IP address fopr multiple computers. The problem with this is when you want to get in. If I send a packet to your public IP address it just goes to the router. The router doesn't know where to send that packet because it didn't originally send it, only received it. You can't send directly to your private address because it's private, hidden from view from the net.

You've now set up a port forward. You've told the router now than whenever it receives a packet with a destination port of 8118, it forwards that packet straight to your linux box without changing anything. That allows you to speak directly to your server on that port alone. If you had to ping your public address you'd ping your router, on the other hand if you had to ping port 8118 on your public IP address you'd be pinging your linux box instead.

---

### Post by mellowd on 2007-11-21
And yeah, this is what ssh does - it sets up a secure connection so that data sent between the two devices connected are encrypted as opposed to unencrypted packets. If they were sent unencrypted then anyone with a packet sniffer could extract data and possibly passwords if they get the right packets. SSH prevents that from happening

---

### Post by russian460 on 2007-11-21
ok thank you that explained everything 
but what is the tunnels section of putty used for than? because how my friends server works
is the first box i input port and his ip than i have to go to tunnels and input localhost and another port than i start firefox and input localhost and the port i put in the tunnels box 

the tunnel and ip port are different.

---

### Post by mellowd on 2007-11-21
pm

---

