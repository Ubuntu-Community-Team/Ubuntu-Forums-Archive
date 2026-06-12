---
title: "Make network tunnel form school to home"
date: 2006-10-08
forum: General Help
---

### Post by Muffe on 2006-10-08
I have access to a wireless network at school. The only problem is that as far as I know, only port 80 and 21 is opend for outgoing traffic. That's a fairly big problem for me, because I can't even use Thunderbird to check my IMAP mail account.

At home I have a server running 24/7. At the moment, it's running ClarkConnect, but I will switch to Ubuntu 6.06 LTS next week. I will also upgrade my laptop to Edgy (perhaps already today).

At the server, I have a web server, so port 80 is already in use, but I don't have anything at port 21. My question is:

Is it possible to make a tunnel from my laptop to my server at home, through port 21, and route all traffic except port 80 through that tunnel? I don't want to route port 80 through that tunnel, because the speed will be limited to 360 kbps (the upload speed of my ADSL line), and the speed of the wireless network at school is between 10 and 15 Mbps.

Please assume that I'm running Ubuntu at my server. Is it possible to make a tunnel like this, and how do I do it?

Thanks in advance.

---

### Post by btdown on 2006-10-08
If I were you, I would install NoMachines NX server (its what FreeNX was based on). I assume you have openssh-server installed so you can ssh into the box at home with putty or another client.

There are instructions on how to install the NX server here:
[I][http://ubuntuforums.org/showthread.php?p=1190037#post1190037](http://ubuntuforums.org/showthread.php?p=1190037#post1190037)

and here:
[http://ubuntuforums.org/showthread.php?t=251651&highlight=nomachine](http://ubuntuforums.org/showthread.php?t=251651&highlight=nomachine)



Then just goto the nomachine.com site and download an nx client to log in with.

BT


[/I]

---

### Post by Muffe on 2006-10-08
Is NoMachines open source? Because I guess it's possible to do this with open source tools, I would prefer that... Closed source programs is an emergency-only solution.

---

### Post by sprucegum on 2006-10-09
On your server at home, 
sudo apt-get install ssh
sudo vi /etc/ssh/sshd_config
sudo /etc/init.d/ssh restart  

Sorry, i forgot to tell you to restart ssh after making the change in the configuration.

change
# What ports, IPs and protocols we listen for
Port 22

to port 21

Then from school, ssh in like
ssh -L 7777:localhost:143 [email]user@yourserver.com[/email]:21

That will connect you to your server through ssh.  It will tunnel port 143 to your machine as port 7777
to connect  to this port you use localhost:7777 as your address

I know you wanted to know how to forward a range of ports, but I dont know how to do that.  I hope this helps... and works :P

---

### Post by Muffe on 2006-10-09
What about some VPN solutions (PPTP, OpenVPN etc), is that an option? What do I need on the server and client side to set up that? And will it be possible to set up routing so that port 80 is not routed through that VPN, but directly to the internet?

---

