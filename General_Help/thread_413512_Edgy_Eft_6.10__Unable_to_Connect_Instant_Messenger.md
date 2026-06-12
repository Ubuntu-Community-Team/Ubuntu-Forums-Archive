---
title: "Edgy Eft 6.10 : Unable to Connect Instant Messenger GAIM, aMSN or any other client."
date: 2007-04-19
forum: General Help
---

### Post by SFHasan on 2007-04-19
Hello All,

I searched around for my query for a while, but was amazed to find no one else having the similar setup so I decided to put it up over here for the Ubuntu Gurus to suggest a solution.

My hardware configuration is as follows ;

HP Pavillion Laptop Dv1000, Celeron 1.7 Ghz, 512MB RAM, 80GB HardDisk and the usual peripherals which are always a part of the package. I am running Edgy Eft Ubutu 6.10 and connected to the internet via LAN. My LAN setup is as follows :

My Internet Cable Service provider (which running a UTP CAT5 wire to my home) is running Microsoft ISA Server on his central proxy through which I connect to the internet. Most of you would know that FireFox support the NTLM Authorization Scheme which is de-facto for Microsoft based inter-networking products.  FireFox comes up with a dialog box where I put my user name and password (provided to me by the cable internet provider) and everything runs smoothly as far as the 'Web Browsing' portion is concerned.

Now came the hurdle number one where the 'Synaptic' and 'Update Software' options in Ubuntu were run by me and since I have given the Proxy IP Address and HTTP Port of my existing LAN Proxy sevrer, none of them worked, simply because Ubuntu inherently doest not supports the NTLM authorization that would have been requested internally by the software in order to connect and to check for program updates. 

A few minutes of searching and I landed upon a very useful software made for the similar thousands of folks stuck in a situation like mine . The NTLMaps at ([Http://ntlmaps.sourceforge.net](Http://ntlmaps.sourceforge.net)) allows you to run a local proxy on your cimputer and configure the parameters for your LAN proxy inside a configuration script (where you mention your LAN Proxy, Port, UserName, and Password for your ISA running proxy server). All of your programs which do not support NTLM can now be given a proxy address of your local machine which is 127.0.0.1 and default port 5865. In this way I was able to connect and update all the components using Synaptics and Update Manager. I had to mention this local address whereever needed in these programs. 

Thanks for bearing with me, I actually wanted to give a detailed background of what has been done till now. My problem simply is that when I run the Instant Messaging client for Ubuntu like GAIM or aMSN, and give the same local machine proxy address, none of them is able to connect. GAIM returns the message that (Unable to connect Proxy Error 502). Same is the case with aMSN. I have tried using the IP of my  LAN proxy server as well, but that doesn't work either and niether it should since any of the instant messaging software would not support NTLM. 

I just wanna know that has any of you folks out there got a similar scenario and in case can give me a working suggestion.

Thanks in advance for co-operation and taking time to read my post.

Best Regards,
S.F.Hasan.

---

### Post by zeekay on 2007-04-19
Might sound a bit "d'oh" but aren't MSN ports and addresses blocked on your proxy? I mean, by directives of access permissions. I ask that because some companies (don't know if it's your case) rather block them to avoid dispersion during work.

There is a free webclient that I think would be interesting for you to try, just to be sure they aren't blocked: [www.meebo.com](www.meebo.com) it is.

---

### Post by SFHasan on 2007-04-19
[LEFT][LEFT][CENTER][CENTER][LEFT][LEFT][LEFT][LEFT]Thank you Zeekay For your assesment, 

I would certainly used the Web-based IM Client (like meebo and others). But I know it for sure that the Instant Messaging ports are not blocked at my service providers end. Reason being is that I am using a Dual-Boot configuration and whenever I connect Yahoo or MSN Messenger from within Windows XP SP2 they just are working fine with all the extra goodies of webcam and voice chatting. Its only in Ubuntu 6.10 that the instant messaging clients are not working since I have to connect through an intermediate software (NTLMaps) which provides and adds header to each outgoing network request in order to fulfill the NTLM Authorization structure used by ISA server.

So in my opinion there is some tweaking needed someplace in the instant messaging or NTLMaps utility in order to make it work, only just that I dont know of it as yet :-) 

Best Regards,

S.F.Hasan[/LEFT][/LEFT][/LEFT][/LEFT][/CENTER][/CENTER][/LEFT][/LEFT]

---

### Post by joeally on 2007-04-25
Same here mate...

Amsn just tries logging in forever and gaim says it can't connect to the network...

arghh
having to use meebo

---

