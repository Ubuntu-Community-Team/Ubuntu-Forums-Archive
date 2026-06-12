---
title: "Open SMTP Port, Can't close"
date: 2008-06-09
forum: General Help
---

### Post by ShinHadoken on 2008-06-09
Ok, here's the output of "nmap localhost":

```

Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-09 14:39 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1711 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
25/tcp  open  smtp
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.142 seconds


```

The only port that *I've opened* is the SSH port. I have no idea why ports 25 and 631 are open. I'm sharing a printer on my Windows XP desktop (this is my laptop). Is that why 631's open? 

lsof -i revealed that port 631 is being used by cupsd, and that port 25 is being used by exim4.. 

So, here's the question: what do "cupsd" and "exim4" do, do I need them, and if not, how do I turn them off?

Thanks a MILLION BILLION in advance,

SH

---

### Post by SpaceTeddy on 2008-06-09
```
sudo /etc/init.d/exim4 stop
```
will stop your running exim. You cannot install it, as exim is afaik an essential part of the system. what you can do tho is bind it to the internal network card only. A 
```
sudo dpkg-reconfigure exim4-config
```
should take you through a menu driven setup of exim where you can choose what devices to listen on... i think

As for cups - the 631 is the webpage for manageing printers. This, also, should only be bound to 127.0.0.1. You can change that via /etc/cups/cupsd.conf.
just bind the interface to 127.0.0.1:631 and nobody can access it anymore. 

hope it helps :)

---

### Post by brian_p on 2008-06-09
> **ShinHadoken said:**
> So, here's the question: what do "cupsd" and "exim4" do, do I need them, and if not, how do I turn them off?

Thanks a MILLION BILLION in advance,

I do not think exim4 is not part of a default Ubuntu install so if it is on your system you must have thought you needed it so you installed it. How it is configured depends on what you did in answer to the debconf questions. Just because the port is open (exim4 is listening) does not mean it will necessarily accept mail from anywhere.

Should you have no use for it - remove it from the machine. Otherwise reconfigure it as advised by SpaceTeddy.

Cups comes with a default install. It is set up to only print to a printer attached to the computer. It listens but will not respond to requests from the network. That can be changed, of course.

---

### Post by ShinHadoken on 2008-06-09
I've installed [OSSEC-HIDS]("http://www.ossec.net/") and it's configured to email me upon alerts. Is that why exim is running?

---

### Post by brian_p on 2008-06-09
> **ShinHadoken said:**
> I've installed [OSSEC-HIDS]("http://www.ossec.net/") and it's configured to email me upon alerts. Is that why exim is running?

Possibly. If so, I'd expect it to be set up for local mail delivery only, but if you want to make sure use dpkg-reconfigure to set it that way. Port 25 will show as open but that's no problem.

---

### Post by ShinHadoken on 2008-06-09
ok, cool thanks. I'll ty that. I guess it's not that important because I'm behind a router anyway, but it *is *a laptop.
 
SH

---

### Post by brian_p on 2008-06-10
> **ShinHadoken said:**
> ok, cool thanks. I'll ty that. I guess it's not that important because I'm behind a router anyway, but it *is *a laptop.
 
SH

Even if it is a laptop moving between networks it makes no difference. Either exim4 relays mail or it doesn't. Yours will be set up not to.

---

