---
title: "[SOLVED] How to connect to SSH from the internet"
date: 2008-02-17
forum: General Help
---

### Post by Ge64 on 2008-02-17
Hi,

I set up a small ubuntu 7.10 machine that is connected to the internet via a router. I can connect to it from my macbook easily with ssh -l username hostname, and that works fine. I'd like to set it up so that I can also access it via ssh from school, over the internet and not the local network. I assume I have to open port 22 in the router, but is there anything else I need to do to make it work? Also, how safe is it to do this (assuming my password for ssh is safe) and can I set a seperate password for any ssh connection so I can leave the accounts' passwords as they are? For example, type in password a (which is very long safe and annoying) and then just login to ssh like normal?

Also, how will I test if it works from the internet from within the network? Will I have to ask a friend or is there a better way?

---

### Post by anliveyak on 2008-02-17
as long as you are connected to the internet and you know your ip address it will not be any different to ssh to your computer. obviously your computer will need to be turned on and the firewall on the ssh port turned off. juswt go to the terminal of the computer at school or where ever you wish, and type "ssh *username*@*ip address*" and hit enter. it will ask you for your password. having the ssh port on your computer open all of the time is a somewhat dangerous thing to do, so just turn it on when you need it and restrict the privlages of it. if you ever feel that your connection has been comprimised you can also monitor the traffic on that connection.

---

### Post by &amp;)ky#)^ on 2008-02-17
Here's some recommended reading:
[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

Try the community help wiki.  There's some pretty decent articles in there.

---

### Post by Ge64 on 2008-02-17
Is there a firewall set up on a fresh ubuntu install? If so, how do I open a port? I don't think I would be randomly hacked because the machine never does anything so nobody knows of it.

---

### Post by &amp;)ky#)^ on 2008-02-17
The only firewall that ships with Ubuntu is iptables.  To see the current rules for iptables run this command:
sudo iptables -L

For more info on iptables, see the following:
[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

---

### Post by trippinnik on 2008-02-17
you must be behind some kind of router though right? you 'll need to forward the port that you have your ssh server running on to the PC that is running the ssh server from the router.  Also if you're using DSL/cable or some other high speed internet your IP address will probably keep changing. you may need to setup a domain (there are some free ones like dyndns).

---

### Post by Ge64 on 2008-02-17
Thanks for all your help. I opened the port on nat and iptables and it seems to work fine :) I have one completely unrelated question but I don't want to open a whole thread for it: If I set up an apache server on one machine, and a mysql server on another machine on the lan, does the mysql server have to be able to be accessed from the internet for it to work? Because when you use PHP, isn't it fine as long as the webserver can reach the mysql server?

---

### Post by bernied on 2008-02-17
> **Ge64 said:**
> ... I have one completely unrelated question but I don't want to open a whole thread for it: If I set up an apache server on one machine, and a mysql server on another machine on the lan, does the mysql server have to be able to be accessed from the internet for it to work? Because when you use PHP, isn't it fine as long as the webserver can reach the mysql server?
What you say is correct. The web server machine needs to be accessible (port 80 - and others if you're doing https - forwarded), but the mysql server machine does not need to be open to the internet, just to the machines that want to access it.

---

