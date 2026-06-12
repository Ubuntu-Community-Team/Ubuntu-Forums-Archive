---
title: "Connecting to the Internet through DHCP"
date: 2007-04-26
forum: General Help
---

### Post by dery on 2007-04-26
Last week my Internet provider changed my connection from a manual (i.e. I set the IP, the DNS, etc) to DHCP. That is, they gave me a username and a password which I am supposed to enter to connect to the Internet. While I can easily do this in Windows from "Network Connections", in Ubuntu I don`t know how. I can get into "Network Configuration", but I can`t set the username and password. Does anybody know how to do that? :(

---

### Post by Hendrixski on 2007-04-26
My best guess would be that when you go to System --> administration -->network  you type in the user name and password there.

Have you called tech support?  If enough people call and say "I use Linux, you need to support Linux or else you're going to lose my business, you will lose money" then some guy in a suite will say "oh crap, start supporting this linux thing" because they only understand the language of money.  And then life will be easier for all of us.

---

### Post by dery on 2007-04-26
> when you go to System --> administration -->network you type in the user name and password there.

That`s what I tried from the start, but it doesn`t work. It doesn`t work because there is no "*there*" to type in the user name and password. If I select "automatically (DHCP)", I don`t get no property boxes where to set these values. 
The interesting thing is that the ISP`s network (through which, in theory, I should connect to the Internet) is listed, which means that if I didn`t have to put in the username and pass, the Internet would have worked. 

 > Have you called tech support? 
Yeah, I called them before asking help on this forum. A young lady answered and with the typical sweet-talk, she said I should "get the opinion of an expert". I was like wtf?!?!?  :confused:  I thought she was supposed to be the expert... ](*,)

---

### Post by zvacet on 2007-04-26
system>administration<network settings>select your modem>properties>choose your type of connection(dhcp).If you use Feisty leave upper left box uncheked,and if you use some other version chek it>close.In DNS tab replace existing address with your nameserver>close.programs>accessories>terminal

```
sudo pppoeconf
```

---

### Post by dery on 2007-04-26
> **zvacet said:**
> system>administration<network settings>select your modem>properties>choose your type of connection(dhcp).If you use Feisty leave upper left box uncheked,and if you use some other version chek it>close.In DNS tab replace existing address with your nameserver>close.programs>accessories>terminal

```
sudo pppoeconf
```

Doesn`t work. Firstly, why do I have to choose "modem" if I have optic-fiber??? Anyway, I choosed "modem" and clicked "properties", but still no I couldn`t go further, as nothing you said appears to me. Moreover, in the terminal, running the [COLOR="DarkRed"]sudo pppoeconf[/COLOR] command gives me a "command not found" error...

---

### Post by dreadlord_chris on 2007-04-26
> **dery said:**
> Doesn`t work. Firstly, why do I have to choose "modem" if I have optic-fiber??? Anyway, I choosed "modem" and clicked "properties", but still no I couldn`t go further, as nothing you said appears to me. Moreover, in the terminal, running the [COLOR="DarkRed"]sudo pppoeconf[/COLOR] command gives me a "command not found" error...

Because there still has to be a "modem' in the mix, the signal that travels over fiber is **not** the same as what flows over Ethernet lines. It's the box that you (probably) got from your ISP. The Internet line, coming from outside, plugs into the WAN port of it. And your comuter or router (if you have on) would plug into the Ethernet port.

Any way, you must have that all connected properly - or you would never have been able to get onto the 'Net. It really sounds like it's the Modem that needs to be set up - how you do this will depend on the what kind of modem it is.

For example: My DSL modem is a Speedstream 4100. To configure it I open a browser to [http://192.168.0.1](http://192.168.0.1)
This brings up my modem configuration/status page. From there I had to enter my username & password for my DSL to connect.

So, you need to find out what kind of modem you are using.

---

### Post by dreadlord_chris on 2007-04-26
> **dery said:**
> That`s what I tried from the start, but it doesn`t work. It doesn`t work because there is no "*there*" to type in the user name and password. If I select "automatically (DHCP)", I don`t get no property boxes where to set these values. 
The interesting thing is that the ISP`s network (through which, in theory, I should connect to the Internet) is listed, which means that if I didn`t have to put in the username and pass, the Internet would have worked. 

 
Yeah, I called them before asking help on this forum. A young lady answered and with the typical sweet-talk, she said I should "get the opinion of an expert". I was like wtf?!?!?  :confused:  I thought she was supposed to be the expert... ](*,)

lol..... front line ISP tech support are **never** experts at *anything* except passing the buck. You should have told her to bump you up to a higher level of support. Also, I have found it very useful with my ISP to **never** mention I run *nix - 9/10 times their immediate response is "Oh, sorry, we don't support Linux". At which point I have to spend 20 minutes explaining why it doens't matter what OS I happen to be running (2 times the modem had gone *pfffft*, and once it was crossed wires at the pole) - so now, I just don't tell them, if they ask I say it's XP :roll: saves **alot** of time and frustration.

---

