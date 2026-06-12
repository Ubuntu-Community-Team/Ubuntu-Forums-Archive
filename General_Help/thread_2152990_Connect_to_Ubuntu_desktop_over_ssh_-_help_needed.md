---
title: "Connect to Ubuntu desktop over ssh - help needed"
date: 2013-06-09
forum: General Help
---

### Post by cpu2007 on 2013-06-09
Hello everyone, I need some help configuring my system and will really appreciate if someone could clarify the points that I will raise in this topic.

I have configured my system,router so that now I can access it locally and from the internet using either ssh or using desktop remote access.

The problem is that I've heard desktop access through the port 5900 is unsecure so is better to tunnel through ssh and then go to desktop.

I am confused on how to do this as I can access my system using other computer,my android phone but only if I use methods separately.

What do I have to do in order to access my ubuntu desktop through ssh? and how do I know exactly that I have connected to my system securely through ssh and it's not a direct connection through 5900?

Thank you

---

### Post by ahallubuntu on 2013-06-09
~

---

### Post by markbl on 2013-06-09
It's as simple as running the following command from your client side pc:
```

ssh -L5900:localhost:5900 your-home-router-address.no-ip-biz

```
Then run the vnc client on your client pc and just connect to "localhost". If you are running windows then run PuTTY and configure the local port forward as above.

---

### Post by cpu2007 on 2013-06-10
Thank you 

I meant vnc over ssh and came across a few tutorial but a few points weren't clear to me.

The command that you are showing, I've seen it in the tutorials but can you please what exactly that command line is doing? and how do I know for sure that I am connecting to vnc over ssh as tutorial suggest using a new terminal to connect to vnc after opening an ssh connection,which to me sounds like opening two different connection on different ports.

---

### Post by markbl on 2013-06-10
The ssh command from the client end just opens a terminal session on your linux server (after the incoming connection has been redirected by a port forward I presume you have added in your home router). Adding the -L5900:localhost:5900 to the ssh command also creates a secondary tunnel via that existing ssh session. So when you start your VNC client and connect to localhost then the ssh session intercepts that local connection on port 5900, and redirects it over the ssh session connecting it to port 5900 on the remote ssh server end. The terminal session can be used normally but it is also transporting (and encrypting) the VNC tunnel "in the background". You need to leave that ssh session open while you use the VNC client. Surely Google will explain this better than I have here though ;)

---

### Post by cpu2007 on 2013-06-23
I've just realised that I can't connect to my laptop over ssh from my workplace. Probably they are blocking it as I can connect using my phone.
So I was wondering whether it is possible to connect remotely to my laptop using port 443. I am not using this port on my router so is free but I have no idea how I can use it from my work place to access my laptop. any advice?

THanks

---

