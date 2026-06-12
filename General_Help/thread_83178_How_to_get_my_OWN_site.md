---
title: "How to get my OWN site"
date: 2005-10-28
forum: General Help
---

### Post by kirillrdy on 2005-10-28
Hey, i am running my own webserver, and I have a static IP,
I can access my Site by [http://232.232.32.32/](http://232.232.32.32/) (ip is not important). anyways, I was woundering how can i get my own host name like [http://myname.net/](http://myname.net/) . I know i can pay some company etc, but can I do it bymyself somehow? 
sorry for a dumn question if it is, I am just really have bad understanding of how it works

---

### Post by funkenstein on 2005-10-28
No, you can't, is the short answer.

The DNS (Domain Name Servers) system essentially maps a name (ubuntuforums.org) to an IP address (kind of like a telephone number for computers. In the case above, that's 64.21.33.9) Thing is, if your webserver is on a computer at home, you're probably going to be on a dynamic IP address- every time you reboot your router you'll get a new IP address... On top of that, everytime you change an IP address for your TLD (Top Level Domain - ubuntuforums.org <- note the lack of www. That's intentional), it takes about 24-48 hours to filter through to all the DNS servers across the globe. Finally, you have to be what's called a Domain Name Registrar to be able to assign these names, and be registered with RIPE and a whole bunch of other things. So - yes, you *could* in theory become a registrar and DIY it, but that'll be a VERY big (and increadibly interesting in an Ubergeek sort of way) hassle.

The easiest solution is to go to a site like [www.dyndns.org](www.dyndns.org) and register with them. The bad news is that everytime your IP address changes, you'll need to log back in to dyndns.org and change your details. There's plenty of ways to automate this, but that's even further out of topic for these forums. Just google up "dynamic dns ip address TLD" or something like that to find sites other than dyndns that provide this service. 

Note that if you're not on a dynamic IP then you just need to find a Domain Name Registrar, pay them ~$10 per annum for your own name (sorry to report that myname.net is already taken :() and you're laughing.

Anyway, you can get plenty more info on this type of this from the big wide internet thing that we're on.... Hope that helps :p

---

### Post by kirillrdy on 2005-10-28
Haha... Thanks a lot mate :).. i like the laughing part,
anyways, I am on static IP, it will not change even after i reboot my modem, anyways, i would have though that I'd have to pay,
too bad myname.net is taken... such a nice adress :)

---

### Post by N6546R on 2005-10-28
[QUOTE=kirillrdy]Haha... Thanks a lot mate :).. i like the laughing part,
anyways, I am on static IP, it will not change even after i reboot my modem, anyways, i would have though that I'd have to pay,
too bad myname.net is taken... such a nice adress :)[/QUOTE]

Try the .name domain. Most of the commons names have been purchased, but that still leaves a lot of names that aren't Smith or Jones.

Perry

---

### Post by jeffreyvergara.NET on 2005-10-28
if you really your own website, check my Sig for hosting plans, I got my domain name for $4/yr from Netfirms

---

### Post by matthewv on 2005-10-28
I think dyndns.org also supports static ip, if you need that. The big downside is your name will look somethin like [http://myname.dyndns.org/](http://myname.dyndns.org/) or something like that

---

### Post by kirillrdy on 2005-10-28
ok guys :). thanks alot,,, I will get onto that straight after i finish my exams ( i did 2 today) 5 more left  :)
I think i'll just pay, $5 p/y is not that bad actually

---

### Post by Kyral on 2005-10-28
dyndns.org DOES have Static IP DNS Mappings, and you can even choose the .xxx.org part from a list. I mapped my IP to ******.boldlygoingnowhere.org (You didn't think I was gonna give it out that easy did you? :P) so I didn't have to remember my IP when SSHing :D

---

### Post by peterbrowne on 2005-10-28
I use [www.godaddy.com](www.godaddy.com) for my domain name and for DNS use [www.zoneedit.com](www.zoneedit.com)

---

