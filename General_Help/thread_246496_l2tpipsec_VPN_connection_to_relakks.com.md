---
title: "l2tp/ipsec VPN connection to relakks.com"
date: 2006-08-29
forum: General Help
---

### Post by lichtgestalt on 2006-08-29
Hey guys,

I`m trying to connect to my relakks.com VPN account. Using pptp it works for about 2min, don`t know why but shortly after the connection is established and woks fine it just vanishes without any error message or what so ever.

But hey, an l2tp/ipsec connection would be even better...
The only problem is: There seems to be a complete System for this purpose - the l2tpd and racoon but no f**** manual/how-to/what-so-ever on the whole net.

Perhaps someone here is able to help me establishing my connection.
I dont`t think there`s much to say about the provider, every thing I know can be found at [www.relakks.com](www.relakks.com) and my machine is just a standard Ubuntu - nothing execetional.

I`d be gratefull for someone helping me with this Problem.

---

### Post by Explodicle on 2006-12-18
I've been trying to do the same thing. When I tried the pptp application they linked off the Relakks website, it broke the the internet on the machine I ran it on. I tried using the wizard on KVpnc for the l2tp/ipsec connection, but had no luck there either!

---

### Post by Explodicle on 2006-12-18
Ok, I fixed my internet by going to my network settings and copying everything from a computer with working internet. A few things were different and I'm not sure what fixed it, but at least I don't need to give up and reinstall Kubuntu. :-P

---

### Post by kd7swh on 2007-03-04
I am having the same problems, pptpconfig connects to relakks but says ppp0 doesn't exist. I think there is a problem with the routing or something. Can anyone help me get this pptp vpn thing working?

---

### Post by pikakilla on 2007-04-17
Good luck. Ive been searching for this information for months. No one seems to know how to properly set up a vpn on linux. Honestly, your best bet is to get a windows box if you want vpn.

---

### Post by sorenweber on 2007-04-19
> **kd7swh said:**
> I am having the same problems, pptpconfig connects to relakks but says ppp0 doesn't exist. I think there is a problem with the routing or something. Can anyone help me get this pptp vpn thing working?

There is an extensive guide in the Swedish pirate party's forum: [http://forum.piratpartiet.se/Topic64139-164-1.aspx]("http://forum.piratpartiet.se/Topic64139-164-1.aspx").

---

### Post by xinel on 2007-05-01
Send Relakks an email, I did asking for them to supply linux users with an openVPN account or ssh shell account. If enough of us do it who knows it may happen.

---

### Post by sorenweber on 2007-05-01
> **xinel said:**
> Send Relakks an email, I did asking for them to supply linux users with an openVPN account or ssh shell account. If enough of us do it who knows it may happen.

I agree there is a good chance of them doing more to get the VPN simplified for us linux users if we write them. Though they may also just point us to this guide written for Gentoo: [http://gentoo-wiki.com/Relakks]("http://gentoo-wiki.com/Relakks")

I don't see an ssh shell account ever happening (security+storage)...

---

### Post by nonsense28sal on 2007-05-15
Hi all. 

I posted a solution to connecting to [Relakks]("https://www.relakks.com/login.php?lang=en") [here]("http://ubuntuforums.org/showthread.php?p=2662749").  So far it's worked for me in Kubuntu Feisty Fawn.

---

