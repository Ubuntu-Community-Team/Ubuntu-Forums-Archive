---
title: "Internet connection on uBuntu"
date: 2007-04-06
forum: General Help
---

### Post by warlock_handler on 2007-04-06
Hi guys,
I have some doubts about my internet connection, on WinXP i do the following procedure before i connected the first time:
[LIST=1]
[*]Goto my network places
[*]add new connection (the new connection wizard appears)
[*]In the connection type screen select "Connect to the Internet"
[*]Then select "Setup my connection manually"
[*]Then select "Connect using broadband connection that requires user name and password" (Your ISP may refer to this type of connection as PPPoE)
[*]Enter ISP name
[*]Type the ISP user name and password (And its done)
[/LIST]

I was wondering how do i setup this connection on uBuntu, if thats not possible then how can i setup my wireless router so both my winXP machine and uBuntu machine can access the net...

thank you
Warlock handleR

---

### Post by wislon on 2007-04-06
There's a number of ways of doing this, depending on your requirements (e.g. internet connection sharing/publicly accessible server). I suggest having a look around this site

[http://www.howtoforge.com/taxonomy_menu/1/1/50](http://www.howtoforge.com/taxonomy_menu/1/1/50)

They seem to have most topics nailed down! :)
Good luck with it :)

---

### Post by warlock_handler on 2007-04-06
> **wislon said:**
> There's a number of ways of doing this, depending on your requirements (e.g. internet connection sharing/publicly accessible server). I suggest having a look around this site

[http://www.howtoforge.com/taxonomy_menu/1/1/50](http://www.howtoforge.com/taxonomy_menu/1/1/50)

They seem to have most topics nailed down! :)
Good luck with it :)


Can you point me to one specific topic... cause i cant find what i need...

---

### Post by lynxus on 2007-04-06
One of the best things for you to do is find out what your current XP config is.

IE: 
- whats your IP
- what DNS servers are you using
- whats your default gateway
- whats your subnet mask

That is really all the info you will need, However!! and its a big one. I fyou use some form of ADSL modem that requires software to run or dial out then you will need to hunt around the forums ofr answers.

One of the best ways and best performance ways is to get a modem that assigns your pc a dynamic IP via DHCP then you administer the internetconnection's settings on the modem/router directly.

---

### Post by warlock_handler on 2007-04-06
> **lynxus said:**
> One of the best things for you to do is find out what your current XP config is.

IE: 
- whats your IP
- what DNS servers are you using
- whats your default gateway
- whats your subnet mask

That is really all the info you will need, However!! and its a big one. I fyou use some form of ADSL modem that requires software to run or dial out then you will need to hunt around the forums ofr answers.

One of the best ways and best performance ways is to get a modem that assigns your pc a dynamic IP via DHCP then you administer the internetconnection's settings on the modem/router directly.

I dont use any dialers or other softwares to conenct
I guess I will setup my DNS servers || gateway and subnet mask... ya i know how to do that... 

thnx

---

### Post by warlock_handler on 2007-04-08
guys,
This is the file that my internet guy gave me for linux 
[http://202.63.173.82/client/linux-1.1-1.i386.rpm](http://202.63.173.82/client/linux-1.1-1.i386.rpm)

I converted it into a *.deb using alien and installed it... and i tried to connect before which i had to setup the connectionso at the terminal i had to run

sudo adsl-setup [then is asked for my username password then server info which i entered correctly, then it told me run adsl-start to connect]
sudo adsl-start [and it says connection timed out... please help]


](*,)

---

### Post by hikaricore on 2007-04-08
If you're using dsl where you have to authenticate, you're probably better off having a router
to do this instead of your computer.  I'm guessing you have an older modem as most newer
dsl modems are modem/router combos that authenticate for you.

---

### Post by loveshocked on 2007-04-08
I didn't set up connection in my ubuntu, it is connected to the internet automatically. When i tried to set up the proxy, (system-> preferences-> network proxy) I don't know what happens, but I can't even connect to gaim instant messenger. So I just leave it that way.. I am using a private IP, n I need not to set it tu (dhcp)

---

### Post by warlock_handler on 2007-04-09
> **hikaricore said:**
> If you're using dsl where you have to authenticate, you're probably better off having a router
to do this instead of your computer.  I'm guessing you have an older modem as most newer
dsl modems are modem/router combos that authenticate for you.

dude.. i have a linksys router,.. and i was waiting to know how do i connect through my router?? i have plugged my cable in the router..  cant figure out how to connect.. and authenticate using my username and pwd... pls pls pls help...

---

### Post by warlock_handler on 2007-04-09
> **loveshocked said:**
> I didn't set up connection in my ubuntu, it is connected to the internet automatically. When i tried to set up the proxy, (system-> preferences-> network proxy) I don't know what happens, but I can't even connect to gaim instant messenger. So I just leave it that way.. I am using a private IP, n I need not to set it tu (dhcp)

@ loveshocked > hi thats the problem u have a private live IP ... well in my case i dont have one.. and my DHCP gives me an IP everything i authenticate and registers my comp on the network...

---

