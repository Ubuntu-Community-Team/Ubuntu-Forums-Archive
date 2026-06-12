---
title: "Install Oracle 9i client"
date: 2007-09-03
forum: General Help
---

### Post by Adalgiso on 2007-09-03
Hi,

i am currently trying to install Oracle 9i client on my system. I am using Edgy (6.10). I tried to install Oracle 10g client first, and it went ok with some minor manual changes, but had to find out that i need Client 9i, as Client 10g cannot connect to a Oracle 8.16 database. 

I got Oracle 9.2.0.4 for Linux, extracted it and wanted to start with ./runinstaller on Disk1 (as user not as root!). Here i get the first strange reply:

./runInstaller: 62: Syntax error: word unexpected (expecting ")")

Then i tried to run /install/linux/runinstaller and at first the installation starts, but soon interrupts with:

Initializing Java Virtual Machine from /tmp/OraInstall2007-09-03_02-12-28PM/jre/bin/java. Please wait...
Segmentation fault (core dumped)


Can anybody help me a bit further?

Thank you in advance, best regards.

---

### Post by Adalgiso on 2007-09-06
Really noone to help me in this topic???

---

### Post by marke1 on 2007-11-13
This happens due to a "stupid" runInstaller shell script that expect RedHat to be the OS. Gaaaa. 

So change directory into the install/linux subdirectory of the install dir and then run ./runInstaller from that dir. That should work for you :)

---

### Post by Adalgiso on 2007-11-14
Thank you. Will try that out. I hope it works.

Best regards.

---

### Post by Adalgiso on 2007-11-26
@marke1

I couldn't quite figure out, where to change the directory. Could you post the relevant lines?

Thank you, best regards

---

### Post by FokkerCharlie on 2007-12-03
Hi

I'm afraid I'm asking for, rather than offering help!

Could you give me a clue on how to install the 10g client, Adalgiso?

Actually, first-could you tell me if that's what I need to do? :)

At my company, we have a system called 'Blue1', that we can access from home.  We were given a URL to put into our web browsers, that installs 'JInitiator'.  After going through the installation, repeated visits to the URL get us to Blue1- the login page, and then access to the database.

All this worked fine on IE in Windows, but I haven't got very far with it on Gutsy.  In Firefox, nothing happens, I've tried it with IE under Wine, and the installation goes ahead, but then re-visiting the page results in the browser closing itself after a couple of minutes.

I am new to Linux, and most grateful for your help.

Charlie

---

### Post by Adalgiso on 2007-12-03
Hi FokkerCharlie,

installing 10g was rather easy, you download the corresponding files from Oracle, unpack them and then, in the directory where you did that, just type "./runinstaller", if i remember well. It could be, that the installer does not find some needed software or libraries, as for example JRE, but it deliberately tells you that. After that, when everything is finished, you connect to your company's database via vpn or directly, which of course i do not know in this case. It worked fine for me, but the database i wanted to connect to, did not support 10g client yet, as it was an 8i-database. For the Jinitiator ....sorry, i do not know about that, it seems to be some kind of web-interface....no idea.

Good luck!

---

### Post by FokkerCharlie on 2007-12-03
Hi Adalgiso

That's good to know.  Could you give me an idea which download I need?  They mostly seem to be aimed at developers, and I am most assuredly not one of them!

Thanks again
Charlie

---

### Post by Adalgiso on 2007-12-04
10 g client software for Linux presumeably.

Best regards

---

