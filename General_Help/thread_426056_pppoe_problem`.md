---
title: "pppoe problem`"
date: 2007-04-28
forum: General Help
---

### Post by DerFuhrer on 2007-04-28
Hello everybody.First,I wanna say that i'm a begginer on Ubuntu,so please `judge me` as well ... I have a problem with internet connection trough pppoe.
I've read the forums first,but i didn't find any solution to my problem . After I run the command **sudo pppoeconf** and after the network card / connection are scanned,it's showing me the following error : 
"Sorry,I scaned l interface,but the Access Configuration of your provider did not respond. Please check your network and modem cables.Another reason for the scan failure may also be another pppoe process which controls the modem".
I mention that i'm using the Ubuntu 6.06.1 LTS version . Thank you in advance .

---

### Post by robbydek on 2007-04-28
> **DerFuhrer said:**
> Hello everybody.First,I wanna say that i'm a begginer on Ubuntu,so please `judge me` as well ... I have a problem with internet connection trough pppoe.
I've read the forums first,but i didn't find any solution to my problem . After I run the command **sudo pppoeconf** and after the network card / connection are scanned,it's showing me the following error : 
"Sorry,I scaned l interface,but the Access Configuration of your provider did not respond. Please check your network and modem cables.Another reason for the scan failure may also be another pppoe process which controls the modem".
I mention that i'm using the Ubuntu 6.06.1 LTS version . Thank you in advance .

I use to use 6.06 LTS, but I have since upgraded to 7.04.  How is your pppoe configured?  Is it in the router (or do you have a modem) or do you have to configure it from your computer?  I have a pppoe internet provider that provided me a D-Link DI-624 and it works perfectly alright, since it is configured through the router.  If it's through the computer you may want to look at getting a router that can support pppoe so it will work for you.

---

### Post by DerFuhrer on 2007-04-28
I am in a network (same ip) , which receive internet from a external city provider . We don't use routers,just switches . I mention that on other distributions,the pppoe-setup had worked fine . The ip is given automatically by the network / internet .

---

### Post by zvacet on 2007-04-28
You can try this

[http://ubuntuforums.org/showthread.php?t=426196]("http://ubuntuforums.org/showthread.php?t=426196")

---

### Post by DerFuhrer on 2007-04-29
I've tried that and still it's giving me that error ... :(

---

### Post by googlebytes on 2007-04-29
I was trying to set up a Zoom ADSL modem on my 6.10 Edgy machine, and had a problem with PPPOE too. After struggling with it over the course of a day, I decided just to load the ZOOM software on my XP machine, and I was online in about 5 minutes. Then I went back to my Ubuntu machine, and lo and behold I was online! I don't know what happened - but if you have a windows machine you might try connecting with that first. By the way my ZOOM documentation said I had to have some secret code in one of my Ubuntu files - mine already had it, but 6.06 may not have the code you need already.

---

