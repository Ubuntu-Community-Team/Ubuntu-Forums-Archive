---
title: "I need help with a server. Please don't hurt me."
date: 2006-10-23
forum: General Help
---

### Post by BillMajelo on 2006-10-23
You, who are programmers, administrators, users... please help my dad. Wrote his first program in 1972 and has programmed consistently, is currently a consultant for Target and Northwest Capital. He's a smart guy and knows enough about computers that he has written an independent program for high-end database management, tracking performance management in company databases. He knows his stuff. He's given me a list of qualifications for things he needs, which only means a little to me. Trying to keep track of stuff he uses is absolutely infuriating. 

Summary Part the One because it's easier to type out then what's really going on: Our Windows licenses are running out. We've got a huge network in our house. Three servers, a computer in all but the bathrooms and dining room. Downstairs, there are at least seven computers. He's pissed off because he doesn't want to renew any licenses, will not pirate, and needs to work for his business. We can't afford new hardware unless we absolutely desperately need it.

His server requirements. That I could quantify, anyway.

Needs to be a file server for Linux and Windows clients. This is a requirement and priority.
Needs to be a DNS server for the local domain.
Needs to be a DHCP server.
Needs to be a VPN server. Can NOT be the firewall server due to server conflicts already within the house.
Needs to run ORACLE. 
Needs an application server for running JSP.
Needs to be able to run a small LAN, supporting an approximate 25 node network.

Might need to be a WINS server.

Don't need Windows Domain Name Services.

And worse, it needs to be a non-annual fee as minimal as humanly possible. 

He's been trying to determine which Linux distributions are best for this type of implementation, and thusfar, has been frustrated as anything. I'm not looking for reccomendations, myself. My current issue right now is that he is the go-to guy on forums he frequents. What I need are IRC rooms, good programmers and people who know their stuff. He's not used to the network of information available to him, and I decided to find out how to access that network of people. If those of you in the know could point me in that direction, talk to me on my AIM or MSN, I'd appreciate it because I don't know where to go.

Summary Part the Two: I need people who know their computer stuff to help me locate a place that could help my dad with his unique requirements. Point me in the right direction.

I have been told that this particular operating system could help me. Which would be incredible. I'm asking if this system is the correct one, (And considering it's a nongraphical interface... at least from what my dad said just now) and if not, could someone point me to the right one? A guy they know on AIM who would know, a site that could help, anything you've got. 

I am not a programmer. Please do not yell at me for knowing nothing, for possibly posting in the wrong forum, for being utterly unknowing about these things. I'm so very sorry.

Sorry this is long and boring. Thank you for reading.

My AIM is BillMajelo and my MSN in [email]pokemaniacbill@hotmail.com[/email] if you need to contact me. And again, I am so sorry.

---

### Post by Arisna on 2006-10-23
Okay, a few things.  First, no worries--you've given a good problem report and in the right place, and the people here are friendly. :)

There is, as you mentioned, a server version of Ubuntu available that is command-line only.  It is free to download and use for any purpose, just like the desktop versions, which have GUIs.  As to your concerns about choosing the right distribution, many distributions are suitable for making servers, but Ubuntu is often viewed as a good choice for people new to GNU/Linux.

Running a file server should be no problem.  You can be a file server for machines with Unix-like operating systems using NFS, and Samba will let you make a file server for Windows machines.  Samba can also be used to make an Ubuntu machine a WINS server.

On the networking stuff--DNS, DHCP, VPN, and running a LAN--we're getting out of my area of expertise, but I know that these things can be done well with a GNU/Linux server.

Oracle is commercial software that Ubuntu's software repositories will not provide, so you'll have to obtain a copy yourself and install it manually.  Same thing with the JSP stuff, I believe.  The good news is, I think both will run on GNU/Linux, but check with Oracle and Sun to make sure.

---

### Post by marianom on 2006-10-23
Installing Oracle on Ubuntu server should be pretty easy.
On the otn.oracle.com you would find lot of docs about how to do it.
I would start here:
[http://www.oracle.com/technology/tech/linux/install/index.html](http://www.oracle.com/technology/tech/linux/install/index.html)
and specifically here:
[http://www.oracle.com/technology/tech/linux/install/files/oracle-database-10gr2-kubuntu-dapper.txt](http://www.oracle.com/technology/tech/linux/install/files/oracle-database-10gr2-kubuntu-dapper.txt)

If you encounter any error please let us know and we'll see if we can help.

You mention a VPN server: I recommend the one I'm currently using: 
[http://openvpn.net/](http://openvpn.net/) (I'm using it in a server with oracle installed)
Check that out and seek for others recommendations and make your decision.

---

### Post by BillMajelo on 2006-10-23
I appreciate your posts... I'll relay the information to him. I really wish I could be of more assistance in asking this and in helping him, but I am simply not a programmer or administrator of any decent amount of skill. That is to say none.

He has copies of all the developmental software he needs to use, but... the lack of a graphical interface is really an issue for him. Especially with the developmental piece, because his program is definitely based in visuals. I'm simply not sure what I can tell him to make a decision, because while I can get a computer to do most anything you need in Windows (For those who ask. The people who know more then me absolutely don't need to ask), or find a program that can give you the alarm clock you want, but Linux thusfar has given me an awful headache. It just doesn't make sense to me at all. Again, thank you for your help and I am so sorry I don't know more then I do.

---

### Post by beerorkid on 2006-10-23
you can install X on top of server no problem, so you have the server power and a GUI.

---

### Post by BillMajelo on 2006-10-23
beerorkid... um, I'm sorry, but I don't really know what you just said. Could you please elaborate?

---

### Post by wolf202 on 2006-10-23
He means that you can install a GUI (Graphical User Interface) on top of the server very easily.  I haven't done this since I worked with debian but it took like 2 mins

-wolf

---

### Post by BillMajelo on 2006-10-23
Forgive me for asking but what exactly does a GUI do? My dad simplified it for me originally by saying "GUI = Easy, Not GUI = Hard". What would it mean if a GUI was installed over it?

---

### Post by CatKiller on 2006-10-23
> **BillMajelo said:**
> Forgive me for asking but what exactly does a GUI do? My dad simplified it for me originally by saying "GUI = Easy, Not GUI = Hard". What would it mean if a GUI was installed over it?

**G**raphical **U**ser **I**nterface - pretty pictures that you click on with the mouse rather than obscure and arcane commands that you type in whilst muttering to yourself :D

---

### Post by beerorkid on 2006-10-23
yeah a simple ```
sudo apt-get install kde
``` will install the KDE desktop manager.

I am not sure of the name of the gnome desktop since that is what i always install.

---

### Post by BillMajelo on 2006-10-23
Thank you. I appreciate the help. I'll relay this stuff to my dad... I can't say for certain but I'm guessing this stuff will really help.

---

