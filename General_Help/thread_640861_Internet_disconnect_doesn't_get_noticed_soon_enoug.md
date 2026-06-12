---
title: "Internet disconnect doesn't get noticed soon enough"
date: 2007-12-14
forum: General Help
---

### Post by csulok on 2007-12-14
Hey

I've ran into a problem I can't solve. Nowadays I'm getting lots of disconnect because of problems at my ISP, and I noticed a number of application doesn't notice the connection was lost.

These disconnects usually last less than 5 seconds and in a webbrowser I can't even see it (unless there's a stream or download running), but in X-Chat, Pidgin, Azureus there's no traffic or connection attempt after 5-10 minutes after the disconnect (and change of IP address).

The only thing I could measure so far is that in Azureus the peers start disappearing from torrents after 4 minutes which I think is some kind of default TCP timeout window. In X-Chat a disconnected notification and reconnect attempt can take as long as 20-25 minutes. In Deluge connection lost is noticed immediately so I'm guessing it doesn't use system defaults but some aggressive internal thingy.

Is there a way to modify this on a global scale so all the applications would notice the drop of connection... almost immediately?

Thanks for the help ^^

---

### Post by csulok on 2007-12-15
bump

---

### Post by csulok on 2008-01-02
shameless bump because this annoys the hell out of me

---

### Post by kendon on 2008-01-03
i have the same problem, but only for pidgin. i have utorrent running in wine, and when pidgin notices that it is offline all torrents are up and running at full speed again. just minutes ago i got a message that was sent 18 minutes before i reconnected pidgin and received it, that really sucks.

i hope there is a plugin that keeps the connection alive, even icq can do that. so far my google searches were without results, i let you know if i find something.

---

### Post by csulok on 2008-01-04
pidgin is among the list here too, and personally i don't have a problem with the connection being kept alive, my router automatically reconnects. but certain application do have a problem noticing it. 

utorrent and mirc and deluge and the webbrowsers seem to be using some very aggresive method to find the new connection ~ llike every 5 seconds it retries.

but azureus, pidgin, xchat (and i'm sure many more) misses this internal autoretry method and relies on the operating system.

---

### Post by Blindraven on 2008-01-04
For Xchat issue the following command : 
```
/set net_reconnect_delay <seconds>
```
(but I **strongy** reccomend[_ irssi _]("http://irssi.org/"))

For Pidgin, the MSNP14 code in 2.2.1 will solve this problem, however, until then you are going to have to stick it out. 

For a global scale, you would need a keep-alive ping shell script that pinged each application, routed internet connectivity from the server to the user (you) and it would only get more complicated from there, pretty much beyond the scope of this reply and my knowledge.

You just need to specify the commands in each program and run it from there.
This is why a lot of the time CLI applications and utilities are a lot more resourceful then your average G.U.I.

---

### Post by kendon on 2008-01-06
> **Blindraven said:**
> 
For Pidgin, the MSNP14 code in 2.2.1 will solve this problem, however, until then you are going to have to stick it out. 

actually i didn't take care of my pidgin version, but as you say it i use 2.1.1, because i'm too lazy too update (using feisty) and i don't like to click through two menus to show the offline budies, like it's from 2.2. stupid, i know.

as 2.3.1 is out right now i'm gonna try it.

---

### Post by csulok on 2008-01-06
> **Blindraven said:**
> For Xchat issue the following command : 
```
/set net_reconnect_delay <seconds>
```
(but I **strongy** reccomend[_ irssi _]("http://irssi.org/"))

For Pidgin, the MSNP14 code in 2.2.1 will solve this problem, however, until then you are going to have to stick it out. 

For a global scale, you would need a keep-alive ping shell script that pinged each application, routed internet connectivity from the server to the user (you) and it would only get more complicated from there, pretty much beyond the scope of this reply and my knowledge.

You just need to specify the commands in each program and run it from there.
This is why a lot of the time CLI applications and utilities are a lot more resourceful then your average G.U.I.
Thanks for the reply.

I've been using pidgin 2.3.0 ever since it was released and it doesn't notice the new connection (or the old one being dead) any faster than azureus or xchat, or the older versions of pidgin for that matter.

As for X-Chat, the net_reconnect_delay is set to the default 10 (seconds) value and it has nothing to do with the software reacting to the ever growing latency. It just says how much time it should wait between reconnect attempts, once the need for a new connection has been realised. That doesn't happen forl 15-20 MINUTES after a disconnect.

By the looks of things what I most likely need is somekind of script that kills the network connection to my router if the internet IP address changes and then immediately connects to the router. If I pull the plug (literally) all the applications notice the disconnect. I need to replicate this without a giant robot that rips out the cable every time ;)

---

### Post by kendon on 2008-01-07
so i installed pidgin 2.3.1. as far as i can tell nothing has changed about pidgin not noticing the reconnect. just tried to disconnect and reconnect which fried my router, so i had to pull the powerplug, so the time should've been long enough for pidgin to get it.

after the reconnect of the router i sent a message, reconnected pidgin and asked the recipent for the message, he didn't get it...

---

