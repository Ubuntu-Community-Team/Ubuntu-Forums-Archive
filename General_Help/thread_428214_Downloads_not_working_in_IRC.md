---
title: "Downloads not working in IRC"
date: 2007-04-30
forum: General Help
---

### Post by foug on 2007-04-30
My downloads in IRC are not working. I'm pretty sure my torrents don't work either. Downloading things through my browser or synaptic are fine though. Turning Firestarter off doesn't help either.

---

### Post by g8m on 2007-04-30
Strange. But a port problem somehow. synaptic and firefox all use port 80 (http) or 20 (ftp) to download. IRC uses different ports, mostly high up (60,000 or so). So this is either a firewall problem or a router problem. Maybe even a provider problem.

---

### Post by willskills on 2007-04-30
If you are using a router, make sure you are forwarding the correct ports, if you want to DCC.

---

### Post by foug on 2007-04-30
How would I go about forwarding the correct ports? I don't know much about networking or internet problems. I set up my router and that's about it for me. IRC and torrent downloads worked fine in windows so I think both of you are right when you say it's a port problem.

---

### Post by g8m on 2007-04-30
Theoretically you should be able to download dcc or torrent, even if you are behind a router. Only if you want to seed or dcc-send you need to set the correct ports to forward on your router. Does your router have a dmz (demilitairized zone) setting. In dmz all ports are forwarded to the ip you set the dmz for and sending and receiving should work. I still think it's a firewall problem.

---

### Post by psusi on 2007-04-30
Yes, you will need to configure your router to forward the ports to your computer for dcc and bittorrent.  BT will work without it, but not as well, since others won't be able to connect to you.  Your BT and IRC clients should have options for what ports to use.  You need to set it up so that the router forwards whichever ports they use to your IP address.

---

### Post by foug on 2007-04-30
i'm not sure how to do that. Like I said, I don't know much aobut routers and port forwarding etc. Thanks for the help.

---

### Post by foug on 2007-05-03
bump

---

### Post by psusi on 2007-05-04
You will need to consult the manual that came with your router, but it usually involves opening [http://192.168.1.1](http://192.168.1.1) or similar in your web browser, logging in with the default password, and using the web page to set up the forwarding rules.

---

### Post by foug on 2007-05-05
Ok i've tried adding ports and nothing happens, after I click save nothing shows up. Am I naming the application wrong or what? I found [this]("http://forum.xchat.org/viewtopic.php?t=3398") but the IP address it wants me to enter does not fit in the box.

---

### Post by foug on 2007-05-11
bump

---

