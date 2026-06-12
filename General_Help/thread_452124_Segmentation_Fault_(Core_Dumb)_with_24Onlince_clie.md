---
title: "Segmentation Fault (Core Dumb) with 24Onlince client"
date: 2007-05-23
forum: General Help
---

### Post by satz13 on 2007-05-23
Hi 
I am using a Pentium dual Core Machine with an Intel Motherboard & built in LAN Card

My ISP needs me to connect with cyberoam(24onlineClient)  to get online

After various searches ,I| did come across the client for linux /unix  based 24onlineClients..However when I try to configure them ,I get a segmentation Fault error...
I have tried linc  client but that doesnt help either...Can someone help please...As I am stuck with Windows XP only due to lack o internet connectivity currently on my Ubuntu 7.04

Thanks

---

### Post by satz13 on 2007-05-23
Typo Error Core Dump ...but of course maybe I am dumb enough to overlook something basic :)

---

### Post by ne0h on 2007-07-30
Hi,

I have successfully installed Cyberoam clinet on xUbuntu 7.04. I also got that 'Segmentaion Fault' error. But I maganed to remove that.

This is what you need to do if you connect to web through your CABLE net esp. 24Online Cyberoam client:
(for everyone who is having problem installing it in Linux)

My ISP: [http://alliancekolkata.com/]("http://alliancekolkata.com/")
**[COLOR="Green"]Configure your network card before these steps, like Gateway, your IP, Submet masks.[/COLOR]**

1. Download the client from here: [http://alliancekolkata.com/CyberoamLinuxClient.tar.gz]("http://alliancekolkata.com/CyberoamLinuxClient.tar.gz")
(If you find problem in download, I have attached that in this thread, get it from there).

2. Unzip it.

3. Create a file in your home dir named "CyberClient.conf". Put these on that file:

	AskonExit       0
	AutoLogin       0
	FirstTime       1
	Password
	Port    6060
	SavePassword    0
	Server  0.0.0.0
	User    ankit
	ShowNotification        1
	LiveRequestTime 180
	AlreadyLoggedIn 0
	VersionId       1
	Version crclient1.1

Enter your DNS server name (if you don't know ask your local cable guy, they'll tell you) replacing 0.0.0.0 on that file on 'Server' field.

4. Save the file.

5. Open a terminal and browse to the localtion where you unzipped it.

6. Type ./crclient -u <your username>
    Then it will ask for your password. Enter your password.

7. Thats it! Its done. :)

Dont try to configure it with -s option, you'll get Segmentaion Fault error.

---

