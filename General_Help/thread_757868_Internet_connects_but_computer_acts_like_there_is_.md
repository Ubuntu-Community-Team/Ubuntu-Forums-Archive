---
title: "Internet connects but computer acts like there is no connection."
date: 2008-04-17
forum: General Help
---

### Post by Tienshinan8 on 2008-04-17
I installed my modem driver and Ubuntu knows it's there and can use it but when I connect to the internet, I can hear the noise on the phone line so I know its doing something but when I open Firefox and try to visit a site, it instantly says that it cannot connect to the server as if I am not connected.

Mind you, I don't have GnomePPP or pom but instead I initiate the connection by checking off the modem connection box in the manager thing.

What am I doing wrong?

---

### Post by Tienshinan8 on 2008-04-17
Why the hell does nobody reply?:mad:

---

### Post by Tienshinan8 on 2008-04-17
They say "if you have a problem, post it at the forums and you'll get assistance". Well I posted 2 other topics as well and nobody gave a **** enough to help out and now its happening again and I'm starting to get pretty ****** pissed off!

This isn't a good way to get me to use Ubuntu when I can't use it to connect to the internet and nobody wants to help.

---

### Post by hariprs on 2008-04-17
Are you getting connected?
Did you check PPP interface?
1) After connecting give $ifconfig from the terminal and see whether you are connected to internet.

---

### Post by Tienshinan8 on 2008-04-17
Thank you for replying.  It is too late now, I will check tomorrow.

---

### Post by Tienshinan8 on 2008-04-19
Well I ran ifconfig before starting the connection and I saw a "eth0" group and a "lo" group.

When I ran it after I connected a "ppp0" group was added:

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:216.209.7.146  P-t-P:216.209.7.241  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:1 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3669 (3.5 KiB)  TX bytes:4466 (4.3 KiB)

Also, now when I tried to go to a site, Firefox actually took time before saying "cannot connect to server" as if now the computer knows I'm connected but still won't transfer information.

Now what?

---

### Post by Iowan on 2008-04-19
One possibility is IPv6.  Ny signature has a link for a How-to (but it's a version or two old).

---

### Post by Tienshinan8 on 2008-04-20
I created the bad_list file but it won't let me place it into /etc/modprobe.d because I don't have sufficient permission. 
How can I place it into the folder? Do I have to use sudo in the terminal? If so I need to know how to use the copy or move command in the terminal.

---

### Post by Whiffle on 2008-04-20
sudo mv file destination


Also, could you post the contents of /etc/resolv.conf when its connected?  Its sounds like a DNS issue to me.

---

### Post by Tienshinan8 on 2008-04-20
I moved the file and I'll try it right now but if it is a DNS issue, what will resolv.conf show?

---

### Post by Tienshinan8 on 2008-04-20
I moved the file into the /tec/modprobe.d and then I ran

ip a | grep inet6

and got back

inet6 ::1/128 scope host

so I'm not sure if it actually disabled IPv6 and Firefox is still not getting anywhere.

---

### Post by Tienshinan8 on 2008-04-20
Oh and it might help if I note that before when I was using Kubuntu, KPPP said I was successfully connected but Konqueror couldn't connect to anything.

---

### Post by mikey.duhhh on 2008-04-20
> **Tienshinan8 said:**
> I created the bad_list file but it won't let me place it into /etc/modprobe.d because I don't have sufficient permission. 
How can I place it into the folder? Do I have to use sudo in the terminal? If so I need to know how to use the copy or move command in the terminal.

Yes.  Open a terminal and type   
sudo gedit /etc/modprobe.d/blacklist
                                              ^^^^^
                                               or whatever filename you are using.
It will ask you for your password.

When you are done, just save it.

---

### Post by Tienshinan8 on 2008-04-20
Bump!!!!!!!!!!!!!

---

### Post by Tienshinan8 on 2008-04-21
for **** sakes BUMP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Tienshinan8 on 2008-04-22
god damn ****** hell BUMP!

---

### Post by Tienshinan8 on 2008-04-22
I guess nobody gives a **** anymore........
XP was never this hard.

---

### Post by Tienshinan8 on 2008-04-23
...

---

