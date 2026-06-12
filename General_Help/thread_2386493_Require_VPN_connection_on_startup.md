---
title: "Require VPN connection on startup"
date: 2018-03-06
forum: General Help
---

### Post by tantalizingbanana on 2018-03-06
So I have Ubuntu 16.04 installed on a machine that is on a local area network but i want that machine alone to always connect it to a VPN on startup and if that connection with the VPN is interrupted then the connection to the internet in general is disconnected as if the cable as been pulled out. How can I set this up properly?

---

### Post by #&amp;thj^% on 2018-03-06
Easy Peesey, Have a look here: [https://askubuntu.com/questions/328823/vpn-autoconnect](https://askubuntu.com/questions/328823/vpn-autoconnect)

This is assuming you have set your VPN up prior to setting this. (Plain english your VPN must be working before hand)
If you read everything carefully on the link you will get it sorted out it's pretty straight forward. 
BTW Welcome to the Forum.

---

### Post by tantalizingbanana on 2018-03-06
> **1fallen said:**
> Easy Peesey, Have a look here: [https://askubuntu.com/questions/328823/vpn-autoconnect](https://askubuntu.com/questions/328823/vpn-autoconnect)
What about entering the VPN server login credentials?

---

### Post by #&amp;thj^% on 2018-03-06
This is assuming you have set your VPN up prior to setting this. (Plain english your VPN must be working before hand)
If you read everything carefully on the link you will get it sorted out it's pretty straight forward.

---

### Post by tantalizingbanana on 2018-03-06
> **1fallen said:**
> This is assuming you have set your VPN up prior to setting this. (Plain english your VPN must be working before hand)
If you read everything carefully on the link you will get it sorted out it's pretty straight forward.
It isn't my VPN, it is FrootVPN but nonetheless, I am not sure where to input the credentials

---

### Post by #&amp;thj^% on 2018-03-06
> **tantalizingbanana said:**
> It isn't my VPN, it is FrootVPN but nonetheless, I am not sure where to input the credentials
Your VPN currently works now right? (As in before adding it to automatically adding it)
No matter what VPN it just has to be pre-setup  mine is PIA. and use that drop down box to add it and DONE! (Or the Server location you wish to use)
Screenshot included

---

### Post by tantalizingbanana on 2018-03-08
> **1fallen said:**
> Your VPN currently works now right? (As in before adding it to automatically adding it)
No matter what VPN it just has to be pre-setup  mine is PIA. and use that drop down box to add it and DONE! (Or the Server location you wish to use)
Screenshot included
It gets interrupted from time to time randomly. Which is the concern here.

---

### Post by #&amp;thj^% on 2018-03-08
> **tantalizingbanana said:**
> It gets interrupted from time to time randomly. Which is the concern here.
In that case, I would most certainly open a support ticket with your VPN provider. 
After all they claim:
> 99.99% Uptime Guarantee
FrootVPN offers only the best industry standard for our server uptime. Experience no run-down or interruption in our servers, therefore you can be assured of continuous access on all of our services, 24/7 reliable customer support, among others.

Good Luck :)

---

### Post by tantalizingbanana on 2018-03-13
> **1fallen said:**
> In that case, I would most certainly open a support ticket with your VPN provider. 
After all they claim:


Good Luck :)
The question here is really my connection disconnecting and reconnecting, how can I have it that should this occur that the VPN connection is reconnect automatically?

---

### Post by #&amp;thj^% on 2018-03-13
> **tantalizingbanana said:**
> The question here is really my connection disconnecting and reconnecting, how can I have it that should this occur that the VPN connection is reconnect automatically?

Again this question should be asked of your VPN Provider this is not a fault of Ubuntu or OpenVpn but rather in their ("FrootVPN") coding ".configs"
Mine PIA dose just that. Or if there is a problem down the pipe it just disconnects period.> I have no experience with "FrootVPN" or how they do things. "**Connect on start-up **was the original support question"
Now morphing into trouble shooting "FrootVPN"
Sorry but that's best  advice I can offer you here.
Please direct your very Valid Question to them for the best results. ;)
And Again Good Luck! :)

---

### Post by linuxpenguin on 2018-12-15
> **tantalizingbanana said:**
> So I have Ubuntu 16.04 installed on a machine that is on a local area network but i want that machine alone to always connect it to a VPN on startup and **if that connection with the VPN is interrupted then the connection to the internet in general is disconnected** as if the cable as been pulled out. How can I set this up properly?
I think the response to this contains a misunderstanding of what was being requested...

There are several reasons you could lose connectivity that do not involve any fault of the VPN provider, especially if we're talking wifi. You can be at a coffee shop in an area with a weak signal, you can be on a wifi hotspot and have the battery die...

From what I've found although there are many ways to do this if you're an advanced user or a sysadmin, but maybe no easy way through the GUI or that will automatically do this for you on any network you connect to.

I too would be interested in the answer to this question.

---

