---
title: "My DNS?"
date: 2008-06-28
forum: General Help
---

### Post by AmpersUK on 2008-06-28
I have a **weblog** *(see below)* and have this set up within my **Google Analytic**s account so that I can check numbers of visitors to my site.

I want to omit my own visits from my website as I log in a few times a day.

Google Analytics allow this but want a DNS address instead of my url. Something along the lines of **123.45.678.9** *or whatever.*

Can someone tell me how I can find this? I use **Ubuntu Hardy Heron** which is always up to date.

Ampers

---

### Post by Gunman1982 on 2008-06-28
There is some mor information needed, is your computer directly connected to the modem or are you using a router? Do you have a fixed internet ip or just normal dsl with random ip?

---

### Post by fahadsadah on 2008-06-28
The DNS address of ampers.blogspot.com is 72.14.207.191.
How I found this out:
```
dig ampers.blogspot.com NS
```
This shows that the server is blogspot.l.google.com (a CNAME).
I resolved this CNAME into 72.14.207.191 using ```
dig blogspot.l.google.com
```

---

### Post by AmpersUK on 2008-06-28
*> **Gunman1982 said:**
> There is some mor information needed, is your computer directly connected to the modem or are you using a router? Do you have a fixed internet ip or just normal dsl with random ip?*

Thank you for your reply.

My computer is connected, with my wife's computer, to a **router** - via ethernet - and the router is connected **directly** to the telephone socket.

Not sure about the other but we have a **business account with** **BT** *(ISTR it is "Business 500")* - does that help? If not can you suggest where I can locate the other information? I would hazard a guess that it is just a normal DSL with random IP?

Ampers

---

### Post by AmpersUK on 2008-06-28
> **fahadsadah said:**
> The DNS address of ampers.blogspot.com is 72.14.207.191.
How I found this out:
```
dig ampers.blogspot.com NS
```This shows that the server is blogspot.l.google.com (a CNAME).
I resolved this CNAME into 72.14.207.191 using ```
dig blogspot.l.google.com
```

Thanks but that is not what I am looking for.

I need to know the number of the PC I am using at home to connect to blogspot.

Andrew

---

### Post by fahadsadah on 2008-06-28
Some routers support Dynamic DNS. This will give you a fixed address such as yourname.dyndns.com.

Please register at [http://www.dyndns.com/services/dns/dyndns/]("http://www.dyndns.com/services/dns/dyndns/"), and post the make and model of your router here.

---

### Post by Gunman1982 on 2008-06-28
The easiest way to find out your ip is to access this site [http://whatismyipaddress.com/]("http://whatismyipaddress.com/")

If you don't have a fixed ip than this ip will probably change in 24 hours or earlier. In this case you can use a service like dyndns where your changing ip is hidden behind a static dns name which you tell google analytics to use. But for such a service either your router has to support it or you have to install a small program on your computer.

---

### Post by wormser on 2008-06-28
> **AmpersUK said:**
> I want to omit my own visits from my website as I log in a few times a day.

Google Analytics allow this but want a DNS address instead of my url. Something along the lines of **123.45.678.9** *or whatever.*

I think you are looking for your IP address so Google Analytics can exclude your address from the reports.  This link will give show you your IP address.

[http://www.whatismyip.com](http://www.whatismyip.com)

---

### Post by AmpersUK on 2008-06-28
> **fahadsadah said:**
> Some routers support Dynamic DNS. This will give you a fixed address such as yourname.dyndns.com.

Please register at [http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/), and post the make and model of your router here.

Thanks. I went to this website and opened an account as I think it may prove useful once I understand the subject more.

Alas there was nowhere I could find to enter the make and model of my router. Am I missing something here?

Ampers

---

### Post by AmpersUK on 2008-06-28
> **wormser said:**
> I think you are looking for your IP address so Google Analytics can exclude your address from the reports.  This link will give show you your IP address.

[http://www.whatismyip.com](http://www.whatismyip.com)

**Perfect**, this is exactly what I am looking for.

[FONT=Arial][SIZE=4]Thanks very much.[/SIZE][/FONT]

---

### Post by wormser on 2008-06-28
You need to go to [http://www.whatismyip.com]("http://www.whatismyip.com/") and get your IP address.  Then in your DynDNS account add your IP number and create a domain name for it.  Every month you will get an email asking you to update your account and to make sure the IP address is correct.  If you want to have your IP address automatically update in your DynDNS account you can install ddclient on your Ubuntu box.
> 
apt-cache show ddclient
 Update IP addresses at dynamic DNS services
 A perl based client to update your dynamic IP address at DynDNS.com
 (or other dynamic DNS services such as Hammernode, Zoneedit or
 EasyDNS), thus allowing you and others to use a fixed hostname
 (myhost.dyndns.org) to access your machine. This client supports both
 the dynamic and (near) static services, MX setting, and alternative
 host. It caches the address, and only attempts the update if the
 address actually changes.

---

