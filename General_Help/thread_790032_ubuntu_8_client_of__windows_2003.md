---
title: "ubuntu 8 client of  windows 2003"
date: 2008-05-11
forum: General Help
---

### Post by eng.ahmedgaber on 2008-05-11
hello everybody,:)
at first i want to see that a great forum ...
I am network administrator of a company which have more than 75 windows XP computers and windows 2003 server which act as file server,print server,mail server(POP3,SMTP),domain controller,DNS,DHCP and WINS server .
i am new on Linux environment but i want to use Ubuntu 8 in my work cause of its stability and everything work on it.
for the first step i want to use Ubuntu 8 as a client of existing windows 2003 server .can i do that? and can Ubuntu work as Windows XP ? if that possible can someone help me ?:-k i want the instruction to do that.....
by the way i use virtual PC 2007 to test Ubuntu 8 with 2003 server
can i do everything using virtual PC. 
thank you in advance ..:eek:

---

### Post by eng.ahmedgaber on 2008-05-12
could any body help me ...
if that possible or not

---

### Post by I3aH on 2008-05-12
Yes, you can use samba client to connect to the windows 2003 servers. but since your setup is virtual i'm not aware if thats the best method in what you want to achieve.

Just search the forums or google and it should help you :) 

here is the offical Ubuntu for samba [http://www.funnestra.org/ubuntu/hardy/#samba](http://www.funnestra.org/ubuntu/hardy/#samba)

Oh and i got to "Places" at the top of the screen in gnome and "Connect to server" and change it to windows. or type in a file browser smb:///(IP address)

> and can Ubuntu work as Windows XP ? if that possible can someone help me ? i want the instruction to do that.....

I don't understand that?

I'm guessing, can ubuntu share a filesystem so that windows can see it? Thats done by a samba server but i have never done this before.

Have fun ;)

---

### Post by eng.ahmedgaber on 2008-05-13
thank you my friend to your reply ..
now i install Ubuntu 8 on my laptop physically not on virtual pc....
i success to join win 2003 domain...use this link 

[http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html]("http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html")

now i want to configure local pop3 mail server and configure ubuntu to use file server sharing on windows 2003 and print server ..
i mean with this sentence is "use Ubuntu like windows XP"

can users in my company use Ubuntu instead of windows xp without any change in services above (pop3,file server,print server)?
and does the domain policy of server 2003 applied on ubuntu like prevent users from change any configuration....
thank you for you efforts.

---

### Post by eng.ahmedgaber on 2008-05-16
hello there....:confused:
any body help me.
can i replace my xp client by ubuntu 8 client with the same server .(2003 server)

---

