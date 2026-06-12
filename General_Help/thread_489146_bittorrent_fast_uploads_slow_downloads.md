---
title: "bittorrent: fast uploads slow downloads"
date: 2007-07-01
forum: General Help
---

### Post by d_xtremw on 2007-07-01
i got a problem with my bittorrent. my download speeds are slow as hell and my uploads speeds are high. when i uncap my upload speeds after downloading it does up to 140kbps. but my downloads top out at about 20kbps. can anyone tell me how to fix this problem. considering im using a cable connection thats dead slow

---

### Post by Computer-Geek on 2007-07-01
I would suggest u to use aMule on Linux and eMule on Windows. They r Fast.

Thanks!!

---

### Post by orasis on 2007-07-01
> **d_xtremw said:**
> i got a problem with my bittorrent. my download speeds are slow as hell and my uploads speeds are high. when i uncap my upload speeds after downloading it does up to 140kbps. but my downloads top out at about 20kbps. can anyone tell me how to fix this problem. considering im using a cable connection thats dead slow

You cannot download any faster than what the seeders are allowing from their clients, many times a torrent will say it has "60" or "100" seeds, but since sites update periodically it is not (usually) a true reflection of the amount of seeders or the actual speed you will receive from them. 

1. If you have a router make sure you have your "DMZ" set to on for maximum speed, the option which allows you to have full connections to 1 PC on your network, or make sure that you have forwarded your ports to the proper settings - if you have not, you may find that most seeders cannot connect to your client, hence slow downloads - fast uploads. 

2. This is torrent related and has nothing to do with the OS you are using. 

3. Emule and AMule, are slow :D

---

### Post by Dean92 on 2007-07-01
What client are you using?, since this could be the problem. (as CG and orasis said)
In my case for example, Utorrent is slow as hell, but when I download the same with Azureus, it's downloading really fast all of a sudden.

You could give Azureus a try if you want:
[Clickme!]("http://azureus.sourceforge.net/")

Dean.

---

### Post by d_xtremw on 2007-07-01
1. If you have a router make sure you have your "DMZ" set to on for maximum speed, the option which allows you to have full connections to 1 PC on your network, or make sure that you have forwarded your ports to the proper settings - if you have not, you may find that most seeders cannot connect to your client, hence slow downloads - fast uploads.

how exactly do i go about doing that??

and im usint bittorrent. the version that came pre-installed on ubuntu

thanx

---

### Post by Dean92 on 2007-07-01
@Pre-installed ubuntu package:

Yep, all pre-installed once were slow for me.
You could try Azureus and see if that solves it,

Dean.

---

### Post by d_xtremw on 2007-07-01
lol now im downloading at bps instead of kbps. wen i used limewire on xp i was downloading at about 50kbps.  now its asking me to make sure that i have some port open if im using a router/firewall (im using a router by the way) and it says that decntralised tracking requires this

---

### Post by splintercellguy on 2007-07-01
You have to port forward the BT port specified in your client else peers and seeds cannot connect to you, which equals slow d/ling.

---

### Post by d_xtremw on 2007-07-01
umm whattt?:S:S... lol aight i think i understood wat u said. i hafta upload and/or download thru the port specified in my azureus otherwise peers and seeders wont be able to connect to me. if i'm right, how do i go about doing this.

and of course if im wrong, what did you mean? :-$

---

### Post by splintercellguy on 2007-07-01
Check your BitTorrent options and find what port your client is using. Using a guide from this site: [http://portforward.com/](http://portforward.com/), port forward the port in your router configuration so that outside connections can go to your computer.

---

### Post by d_xtremw on 2007-07-01
i switched to azureus because it has an actual user interface. with bittorrent all it did was open a file manager window, ask me to navigate to the .torrent file and that was it. no menu or place for options or anything. azureus is givin me a similar problem though. quick uploads and slow downloads. my downloads top out at about 5kbps

---

### Post by d_xtremw on 2007-07-01
the error message for azureus keeps popping up. in th main window it says
"There appears to be a problem with the distirbuted database's UDP port mapping (NAT/Firewall)

can anyone translate or tell me what that means in relation to my problem??

---

### Post by splintercellguy on 2007-07-01
For the error message, it means Azureus was unable to create a UPnP entry for the UDP DHT port. This can be ignored. As I said, you need to port forward if you haven't done so already. The torrent health also counts too. If you have not many peers or leechers outnumbers seeds you have a problem.

---

### Post by d_xtremw on 2007-07-01
thanx for the site. but i guess im not as computer literate as i thought cuz alot of that was still confusing. are there any good simple HOWTO: 's on this site for port forwarding

---

### Post by d_xtremw on 2007-07-03
aight i got my friend to help me portforward all my UDP packets to the same port that azureus uses. with the exception of bad health torrents everything seems to be roughly okay. hope this thread helps ppl in the future.

---

