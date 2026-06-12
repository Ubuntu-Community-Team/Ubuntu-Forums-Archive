---
title: "dumb question about internet speed"
date: 2008-02-06
forum: General Help
---

### Post by elj4176 on 2008-02-06
We have a 10Mbps down 3 Mbps up cable business class connection through Armstrong cable  at work. Random speedtests with internetfrog show that we usually get ~7Mbps down and 2 Mbps up.
Is a T1 connection faster? I seem to remember that it is but a quick google shows a T1 is 1.5Mbps  and the internetfrog applet shows a T1 as slower than our current connection.
A T1 also costs a lot more than our current connection. 

What am I missing here? Am I reading something wrong???
 
thanks

---

### Post by maconga on 2008-02-06
I think T1 is like 1.5 mbps

and you have 10 mbps

---

### Post by elj4176 on 2008-02-06
so my connection is faster than a T1... a new guy at work is saying that our connection is slow and that we should get a T1.
We have gigabit switches and gigabit nics in all servers and almost all pc's.

---

### Post by Dark Hornet on 2008-02-06
The reason why  T1 is usually MUCH more expensive is because you are paying for SLA--Service Level Agreement.  In other words, if your T1 goes down, your ISP is under contract (usually) with you to get it up and running with in a certain amount of time, and if they don't, then they will actually credit your account.  I work for a major ISP, (thankfully I DON'T work with customers--I work on the Backbone) and when our T1 customers go down, (assuming it is our fault), we credit them one full day for every hour they are down.  This is the main reason why T1's are more expensive than your typical cable connection.  In addition, usually your cable connection will be shared with others in your area, so you are not guaranteed that 10mb down, etc, where as with a T1 you are have a dedicated line of 1.5 mb up and down at the same time.  I hope this answers your questions...

--Dark Hornet

---

### Post by miqie on 2008-02-07
> **Dark Hornet said:**
> The reason why  T1 is usually MUCH more expensive is because you are paying for SLA--Service Level Agreement.  In other words, if your T1 goes down, your ISP is under contract (usually) with you to get it up and running with in a certain amount of time, and if they don't, then they will actually credit your account.  I work for a major ISP, (thankfully I DON'T work with customers--I work on the Backbone) and when our T1 customers go down, (assuming it is our fault), we credit them one full day for every hour they are down.  This is the main reason why T1's are more expensive than your typical cable connection.  In addition, usually your cable connection will be shared with others in your area, so you are not guaranteed that 10mb down, etc, where as with a T1 you are have a dedicated line of 1.5 mb up and down at the same time.  I hope this answers your questions...

--Dark Hornet
Excellent explanation.  Always wondered why T1's were so expensive.

---

### Post by elj4176 on 2008-02-07
Yes it does. Thanks! I'm just going to summarize my thoughts on this below:

So the T1 is dedicated 1.5Mbps while the cable is shared 10Mbps. So whichever one is faster depends on how many users are sharing the cable connection. If there are several other companies in the area sharing the same 10 Mbps connection then a T1 *might* be faster on average. 
Makes more sense now.

---

### Post by Cadmus on 2008-02-07
I've been looking at comms stuff recently for creating a VPN. From what I can tell T1 was king when dial-up was the only real way of connecting. These days a superfast connection tends to be either T3 (44Mb/s both up and down) or Ethernet (10|100|1000Mb/s of raw internets, please refrain from licking the cable).

Though as Dark Hornet was saying, you're also paying for assurances.

Also, I may be totally wrong, I'm not US based, can anyone correct me?

---

### Post by Dark Hornet on 2008-02-07
Well, yes you do have the option of a DS3 (T3) or an Ethernet connection...but in order to have an Ethernet connection with your ISP, you need to be co-located with your ISP.  In other words, your equipment would need to be located in the same hub as the Gateway router of your ISP, as there is no real "circuit"..there is just an ethernet cable.  Your other options would be fiber circuits like OC3, OC12, etc.  However, now you are talking some serious money per month.  Actually, all of these options are pretty serious money per month...lol.

Cadmus, what are you trying to do exactly, and what kind of budget and equipment are you able to work with?

--Dark Hornet

---

### Post by Whiffle on 2008-02-07
Verizon pushing FiOS too... fiber all the way to your  computer.  Blllliiiing (assuming lives up to the hype)

---

### Post by Cadmus on 2008-02-08
> **Dark Hornet said:**
> Cadmus, what are you trying to do exactly, and what kind of budget and equipment are you able to work with?

Well, I'm not 'doing' anything at the moment, but due to the nature of my work there's a lot of waiting involved, and I use the time teaching myself about as many technologies as I can. Networking wasn't something I understood in my undergraduate work so it's one the gaps I'm trying to close.

But in my hypothetical little situation I'm trying to build a VPN supporting about 100 users for light-to-medium desktop work. So I'm trying to figure out what bandwidth that would consume and what line you'd need at the main office, and that got me looking into T3s, E3s, and Ethernet (oh my!) trying to figure out what is practical and what meets the needs.

---

### Post by elj4176 on 2008-02-08
T3 sounds like what we need here. We move a lot of large media files and have a small VPN setup for a remote warehouse to run our ERP software. The art dept is setup on the gigabit switches and I may actually create a vlan just for their traffic. My main issue right now is replacing a 24 port hub in the rack with a new gigabit dlink switch (on its way) so that should help some with our internal speed. 
External speed for our ftp is what my original question was about. The above info about our internal network is just added non-sense.:)

---

### Post by Dark Hornet on 2008-02-08
Ah...ok..got it.  I have a question though...why Dlink..is it because of price?  Do they really have a feature set that is comparable with a Cisco Switch with GBic?  Just wondering--as you can probably tell, I am a Cisco and Juniper guy...lol.  Personally though, I prefer Juniper routers ANY day of the week to a Cisco, but Cisco would come in second.

**EDIT**  And at least you are REPLACING the 24 port Hub...adding a switch will make your life SOOOO much better.

---

