---
title: "Need away to see my external IP from Web"
date: 2007-01-01
forum: General Help
---

### Post by kent41 on 2007-01-01
Hi everybody

I have a web IP camera that I can access from the Web using a DDNS name.  As long as the ISP does not change my external IP address all is ok.

I am the only one who needs to look at this camera (security cam) It is my understanding that I must run a computer at the camera LAN location to run a client to update the DDNS name which I don't want to do. My router does not support a way to run a DDNS client in the router like some newer routers.

My question is there a way I can find out what my external IP address is from the Web side of the router so I can change the DDNS address manually?

Also is there a way to connect to my router thru the MAC address of the router from the Web side of the router then I could see my external IP address then manually change the DDNS addres

---

### Post by houstonbofh on 2007-01-02
Short answer, No.  Updating DDNS must happen from the LAN behind the IP address you want to record.  Otherwise how do you know what it chaed to to find out?  What kind of camera and router?  Many of them run Linux, and could support a client...

As to the MAC address, that is a Layer 2 function.  You will not see a MAC address beyond a physical subnet.

---

### Post by kent41 on 2007-01-02
> **houstonbofh said:**
> Short answer, No.  Updating DDNS must happen from the LAN behind the IP address you want to record.  Otherwise how do you know what it chaed to to find out?  What kind of camera and router?  Many of them run Linux, and could support a client...

As to the MAC address, that is a Layer 2 function.  You will not see a MAC address beyond a physical subnet.

Thanks for the reply, The Camera is a D-Link 900 and the router is a Actiontec GT704GW modem/router.

Sounds like I have no choice but to get a small computer and connect it to my LAN and just run a DDNS client to check and see if my IP address changed.

The reason I can't run the client on my laptop is it will not be connected to my LAN but will be somewhere away from my LAN.

It just seems such a waste to run a computer to do nothing but to run a DDNS client.

---

### Post by houstonbofh on 2007-01-05
In that case, get a small computer and run m0n0wall ( [http://www.m0n0.ch/wall/](http://www.m0n0.ch/wall/) ) on it.  It supports ddns and so much more.  Better than a Actiontec router...

---

### Post by stalker145 on 2007-01-05
> **kent41 said:**
> My question is there a way I can find out what my external IP address is from the Web side of the router so I can change the DDNS address manually?

Also is there a way to connect to my router thru the MAC address of the router from the Web side of the router then I could see my external IP address then manually change the DDNS addres

For your first question: I know in Windows you can enter ```
ping www.yourhostname.com
``` at the command line and the response will be the IP address of the host. I haven't tried it in Linux, but I assume that the response will be the same for the appropriate command. I would try that if you are unable to access your camera by your domain name.

I assume you are using something similar to [DynDNS]("https://www.dyndns.com/") for your domain name. If you are, then you *should* be able to go into your name settings and manually update your IP with the one that comes back from the ping, as you mentioned before. I know that DynDNS has this option and I can only speak from my experience.

Personal experience here shows that my ISP only changes my IP about every 45 days. I can't get a straight answer from them, but I do watch for myself.

For your second question: as mentioned previously, you cannot get to your address via MAC. It's just not recognized by DNS as an address and will error out. Try the aforementioned if you run into problems.

---

