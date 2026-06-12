---
title: "[SOLVED] Domain name strangeness"
date: 2008-04-14
forum: General Help
---

### Post by ashdezign on 2008-04-14
Here is a mystery I hope someone can help me solve.

I run a webdesign company and we do some of the design work on windows and some on linux (specifically ubuntu and kubuntu).

Recently we booked a domain jlcrecruit.com which we have hosted on one of our dedicated servers.

Our windows boxes are able to resolve the domain and load the webpage when typed into the browser using firefox or IE.

Our linux boxes however say unknown host when we try to load the page.

All the pc's are sharing the same internet connection through a router.

The error extends to ftp as well.

The error happens even when i try to load the page from my home pc using linux so its not location specific.

I am at wits end. Been on to the webhost and they say its definitely not the server (which is a linux server as well). They even tried loading the site on one of their linux boxes (a gentoo box) and it loaded with no problem. 

So it seems this weirdness is ubuntu/kubuntu specific. And only happens with this one domain name: jlcrecruit.com. We have several domains hosted on the same server and all the rest work fine.

Tested on puppy linux: also fails

Ping on linux for jlcrecruit.com: returns unknown host but on windows works fine

nslookup on linux returns:

[B];; Got SERVFAIL reply from 124.104.135.67, trying next server
;; Got SERVFAIL reply from 124.104.135.67, trying next server
Server:         124.104.135.68
Address:        124.104.135.68#53

** server can't find jlcrecruit.com: SERVFAIL[/B]

ns lookup on windows returns:
[B]
nslookup [www.jlcrecruit.com](www.jlcrecruit.com) 
Server:  ns1.i-gate.net
Address:  58.69.254.3
 
Non-authoritative answer:
Name:    jlcrecruit.com
Address:  69.64.71.120
Aliases:  [www.jlcrecruit.com](www.jlcrecruit.com)[/B]


Any help at solving this mystery would be appreciated!

---

### Post by wormser on 2008-04-14
Sounds like it is a DNS issue since it is not resolving.  Try putting the IP address in the browser.  Do you guys have a DNS server or just a router?  Is it a home style router?  You could just add the names to the [/etc/hosts]("http://www.faqs.org/docs/securing/chap9sec95.html") file.

Update:

I miss understood you and thought this was in a local network.  Try [OpenDNS]("https://www.opendns.com/start/ubuntu.php").

>  nslookup jlcrecruit.com

Non-authoritative answer:
Name:   jlcrecruit.com
Address: 69.64.71.120

Also. the dig command is suppose to be better than nslookup.  
```
dig example.com
```

---

### Post by ashdezign on 2008-04-14
did a dig: 

[B]$ dig jlcrecruit.com

; <<>> DiG 9.4.1-P1 <<>> jlcrecruit.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 59684
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;jlcrecruit.com.                        IN      A

;; Query time: 125 msec
;; SERVER: 124.104.135.67#53(124.104.135.67)
;; WHEN: Mon Apr 14 15:11:28 2008
;; MSG SIZE  rcvd: 32[/B]


We are using an ordinary router

I am willing to try using opendns but that doesnt solve the larger issue: what of other linux users who may want to visit my clients website?

---

### Post by wormser on 2008-04-14
> **ashdezign said:**
> I am willing to try using opendns but that doesnt solve the larger issue: what of other linux users who may want to visit my clients website?

Does your site just say "test page"?  That is what I got when I went to jlcrecruit.com and I am on Ubuntu.

---

### Post by ashdezign on 2008-04-14
Yes, right now it only says test page. I take it you are able to see it on your ubuntu box though so maybe the problem is specific to my linux boxes?

---

### Post by wormser on 2008-04-14
It has something to do with your ISP's DNS set up and your local router.  I am not sure where the problem lies but the solution is to use OpenDNS.  So, this is only happening on your local network.

---

### Post by ashdezign on 2008-04-14
But why should it affect the linux boxes but not the windows boxes? They are all accessing the same isp through the same router

---

### Post by wormser on 2008-04-14
Sorry, I do not know.  It must be something in Ubuntu and the way it handles DNS.  I suspect that has something to do with your router and the way it hands it off to Ubuntu.

---

### Post by ashdezign on 2008-04-14
Thanks for your help. I am gonna give it a couple of days to see if it resolves itself (which I doubt it will) then switch over to open dns

---

### Post by wormser on 2008-04-14
Post the results when you do.  If it does work mark the thread as Solved and click the Star in the lower right hand corner on the post that helped.  Those 2 things make the forums easier to search for a solution.

---

### Post by ashdezign on 2008-04-14
I am going to try opendns on one of my computers running kubuntu. the **$ sudo network-admin** command given on the opendns site does not seem to work on kubuntu.

Also I want to configure it on the computer, but not on the router. If I change to open dns on the computer but the router specifies its own dns will that cause a problem?

Edit: OpenDNS works a charm. problem solved

---

