---
title: "[SOLVED] School Is Stupid"
date: 2007-09-01
forum: General Help
---

### Post by Garrulousbrevity on 2007-09-01
So, I just got to school for the first time.  The IT department at myschool is.. very mainstream.  

Anyway, they want me to have a firewall.  So, I reinstalled XP on my desktop, and set up the firewall that comes with XP and it's happy for this computer.   However, I would kind of like to be able to use Ubuntu on my laptop and on my desktop again.  

Though it seems I need an internet connection to get a firewall going on both of them.  An internet connection I don't have.  

So.. can someone help me, or give me a deb package for the firewall program or something? 

Thanks.

---

### Post by -SpaZ on 2007-09-01
Ubuntu automatically runs a firewall in the background.  You can use [Firestarter]("http://www.fs-security.com/") to manage it.

---

### Post by Seisen on 2007-09-01
Basically firestarter is the gui for iptables which is installed by default in Ubuntu. To install firestarter 

```
sudo apt-get install firestarter
```

---

### Post by expatCM on 2007-09-01
and if you want to test your firewall, you may want to have a look on this site 
[http://www.grc.com/default.htm](http://www.grc.com/default.htm)
for the Shields Up tests ......

---

### Post by cwaldbieser on 2007-09-02
> **Garrulousbrevity said:**
> 
Though it seems I need an internet connection to get a firewall going on both of them.  An internet connection I don't have.  

So.. can someone help me, or give me a deb package for the firewall program or something? 
Thanks.
As others recommended, Firestarter is a good GUI front end for the built-in firewall.  However, you may need to be connected to the internet to download the package.

What exactly prevents you from connecting to the Internet with Ubuntu?  If it is just some sort of staff policy, you can tell them that Ubuntu has iptables built-in.  If it is more like your school uses some sort of software that communicates with a specific firewall program on WinXP, you will need to provide more details.

---

### Post by por100pre1 on 2007-09-02
> **Garrulousbrevity said:**
> So, I just got to school for the first time.  The IT department at myschool is.. very mainstream.

Those IT guys... :rolleyes: No wonder why every time a Windows vulnerability is discovered they start running scared! They should know better! ;)

---

### Post by RedSquirrel on 2007-09-02
> **Garrulousbrevity said:**
> Anyway, they want me to have a firewall.

[HOWTO: Set a custom firewall (iptables) and Tips]("http://ubuntuforums.org/showthread.php?t=159661")

---

### Post by swisscow on 2007-09-02
> **por100pre1 said:**
> Those IT guys... :rolleyes: No wonder why every time a Windows vulnerability is discovered they start running scared! They should know better! ;)

To be fair to IT guys in schools running windows they have to be scared. The school I worked in contracted a virus, swept through the network onto 300 PCs. Network down for ten days. They got it working, only thing was, got another virus and it happened again! Changed their virus checker policy after that!

---

### Post by Old *ix Geek on 2007-09-02
> **swisscow said:**
> To be fair to IT guys in schools running windows they have to be scared. The school I worked in contracted a virus, swept through the network onto 300 PCs. Network down for ten days. They got it working, only thing was, got another virus and it happened again! Changed their virus checker policy after that!Just think of the downtime, man-hours, and inconvenience that could have been avoided if those PCs were running Linux.  Seems like IT guys would know better.

---

### Post by -SpaZ on 2007-09-02
> **Old *ix Geek said:**
> Just think of the downtime, man-hours, and inconvenience that could have been avoided if those PCs were running Linux.  Seems like IT guys would know better.

Most IT guys know better, but some of the local colleges are like that.

---

### Post by swisscow on 2007-09-03
> **Old *ix Geek said:**
> Just think of the downtime, man-hours, and inconvenience that could have been avoided if those PCs were running Linux.  Seems like IT guys would know better.

BUT - AND I STRESS I DON'T AGREE WITH THIS - many schools have to run windows on their PCs  if they wish to be seen as giving students skills for the future which they can use in business. The students have windows at home, the parents have windows at home, so they wish to use windows in schools. 

Also an awful lot of software for schools is designed for, guess what........windows, so sometimes there isn't so much of a choice. So in reality, many times the IT guys would love to run something different than Windows, it's just the demand won't let them.

Think of all the IT guys in schools around the world who's head is saying '*we must have vista to keep up with the masses*' and the IT guys are going to have to install that piece of sh*t.

---

### Post by -SpaZ on 2007-09-03
> **swisscow said:**
> BUT - AND I STRESS I DON'T AGREE WITH THIS - many schools have to run windows on their PCs  if they wish to be seen as giving students skills for the future which they can use in business. The students have windows at home, the parents have windows at home, so they wish to use windows in schools. 

Also an awful lot of software for schools is designed for, guess what........windows, so sometimes there isn't so much of a choice. So in reality, many times the IT guys would love to run something different than Windows, it's just the demand won't let them.

Think of all the IT guys in schools around the world who's head is saying '*we must have vista to keep up with the masses*' and the IT guys are going to have to install that piece of sh*t.

If the IT guys at most schools are as knowledgeable as you say they are, then the ones at Garrulousbrevity's school would have realized that iptables runs automatically in the background.

---

### Post by strabes on 2007-09-03
All of the university-owned computers at my school (Wheaton College, IL) run debian linux and VMWare XP fullscreen. They're unbearably slow but really easy to maintain. There are several "guest" computers in the library which just run debian with gnome, which I prefer. They fly when compared to the virtualized windows installs on the surrounding boxes. 

All the computers also have Openoffice installed along with MS Office. When I found that out I was really happy.

---

### Post by -SpaZ on 2007-09-03
> **strabes said:**
> All of the university-owned computers at my school (Wheaton College, IL) run debian linux and VMWare XP fullscreen. They're unbearably slow but really easy to maintain. There are several "guest" computers in the library which just run debian with gnome, which I prefer. They fly when compared to the virtualized windows installs on the surrounding boxes. 

All the computers also have Openoffice installed along with MS Office. When I found that out I was really happy.

Wow, your school sounds like they have a good IT team.

---

### Post by por100pre1 on 2007-09-03
> **swisscow said:**
> BUT - AND I STRESS I DON'T AGREE WITH THIS - many schools have to run windows on their PCs  if they wish to be seen as giving students skills for the future which they can use in business. The students have windows at home, the parents have windows at home, so they wish to use windows in schools. 

Also an awful lot of software for schools is designed for, guess what........windows, so sometimes there isn't so much of a choice. So in reality, many times the IT guys would love to run something different than Windows, it's just the demand won't let them.

Think of all the IT guys in schools around the world who's head is saying '*we must have vista to keep up with the masses*' and the IT guys are going to have to install that piece of sh*t.

I have to admit that it is true on many schools. I even know one where IT personnel is not consulted at all when the school buys software and hardware.

---

### Post by -SpaZ on 2007-09-03
> **por100pre1 said:**
> I have to admit that it is true on many schools. I even know one where IT personnel is not consulted at all when the school buys software and hardware.

Sadly, a lot of people think that IT guys are only useful when something goes wrong, when in fact, they can prevent a lot of things from going wrong in the first place.

---

### Post by Garrulousbrevity on 2007-09-08
Hey, sorry I haven't responded.  

The guide on how to set firewall settings through the terminal helped me futz around with what it was they wanted me to check. 

They're... a little... silly about it though.  They only check your firewall once.  Then your MAC address is "okay" and they don't check you again. But it works because I messed up while trying to get the firewall settings to save.  

What have you. 

Thanks a lot.

---

