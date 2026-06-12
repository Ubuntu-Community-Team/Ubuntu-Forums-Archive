---
title: "Strange internet connectivity with ubuntu and firefox..."
date: 2007-01-01
forum: General Help
---

### Post by skelooth on 2007-01-01
Sometimes (actually quite frequently) when I'm surfing websites the internet connection "goes dead". IE, the loading animation just spins it's wheels and I can not access any other webpages. The odd thing is that things already running such as gaim are unaffected. I am not able to visit any webpages or start any internet connections until after I get a 404 from the website.

I used to think that this was the fault of my ISP, but after spending a good deal of time on windowsXP to play video games, I noticed the problem does NOT exist there at all.

Can anyone give me a clue as to why this would happen? Now that I know it doesn't happen in windows, I feel like it's unbearable.

---

### Post by mkent91 on 2007-01-01
Yeah I'm having the same problems...i really dont want to go back to windows other than to play games.....its quite confusing.:(

---

### Post by skelooth on 2007-01-01
the sad thing is, I've dealt with this for years and always just ASSUMED it was the ISP's fault.

---

### Post by gfgodoy on 2007-01-01
I'm dealing with this also!!


sudo poff dsl-provider
sudo pon dsl-provider 


seem to do the job for me...


Is there a way of making this a script or something??


Here's my log:

(daemon.log)

Dec 17 23:05:24 Hal-9000 dhclient: DHCPREQUEST on eth0 to 10.0.0.138 port 67
Dec 17 23:05:24 Hal-9000 dhclient: DHCPACK from 10.0.0.138
Dec 17 23:05:25 Hal-9000 dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Dec 17 23:05:25 Hal-9000 dhclient: bound to 10.0.0.1 -- renewal in 3366 seconds.


Thanks in advance

---

### Post by skelooth on 2007-01-01
> **gfgodoy said:**
> I'm dealing with this also!!


sudo poff dsl-provider
sudo pon dsl-provider 


seem to do the job for me...



When do you run that? WHILE it's happening?  Wouldn't that break off any other connections I have going though?

This is a most disturbing problem. It should really be addressed.

---

### Post by moshuptrail on 2007-01-01
Have you read the posts about IPV6?

I was having the same problem and disabling IPV6 seems to help a lot.
Search on "disable IPV6".  (I can't remember all the steps, there's a few)

Evidently IPV6 has been enabled through one of the updates.  The problem is, if your router doesn't support it, you will experience pauses and the like.

---

