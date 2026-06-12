---
title: "Evolution 2.12.0 Segmentation fault when connecting to Exchange"
date: 2007-10-19
forum: General Help
---

### Post by 1tiger1 on 2007-10-19
Afternoon all, 

I have recently installed Gutsy, and am trying to use Evolution 2.12.0 to connect to our exchange server. I have googled this a bit, and have found that people have trouble connecting to Exchange 2007, but we are running Exchange 2003. 

I fill out the information, Select "Microsoft Exchange" as the email server, put in the server name and my login, it asks for a password, then BAM! - Seg Fault. 

(minor) details here:

tony@tony-laptop:~$ evolution
CalDAV Eplugin starting up ...
Loading Spamassasin as the default junk plugin

(evolution:7395): libsoup-CRITICAL **: soup_message_set_request: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution:7395): libsoup-CRITICAL **: soup_message_set_flags: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution:7395): libsoup-CRITICAL **: soup_session_send_message: assertion `SOUP_IS_MESSAGE (msg)' failed
Segmentation fault (core dumped)
tony@tony-laptop:~$

Anybody know what a brother can do? I need to use the shared calendar features that evolution supports (or supported) in Exchange since I have meetings and stuff. 

Help!!!

-Tony

---

### Post by repawn on 2007-10-20
are you using the version of Evolution in Gutsy? It now works off of your exchange web access address. I connect to exchange 2003 both at work and from home - it might be worth checking to see if your IT people are using RPC over HTTP on the the server. This seems to make Evolution work much better when offsite. Let me know if you have any questions - I manage our exchange server so I have a bit of insight into how it interacts with Evolution.

---

### Post by joelmeans on 2007-10-23
I am getting the exact same error as the op.  Anyone have any insight into this?
Thanks,
Joel

---

### Post by pagingmrherman on 2007-10-23
I get the same thing.  It started happening right after we installed a certificate for sql2005.  It's fubar

---

### Post by bodybuzz on 2007-10-25
Same problem here.   I am running Fiesty and mine was working fine until I got a new laptop and tried to set it up again.   I know I have set it up the same...   I get the following:


```
CalDAV Eplugin starting up ...

(evolution-2.10:12446): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:12446): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
GET /exchange/darren.fuller HTTP/1.1
E2k-Debug: 0x823b808 @ 1193329501
Host: webmail.exchange.bell.ca
Accept-Language: en-CA, en
Authorization: NTLM TlRMTVNTUAABAAAABoIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMAAAAAAAAAAwAAAA
User-Agent: Evolution/1.10.1

302 Moved Temporarily
E2k-Debug: 0x823b808 @ 1193329501
Set-Cookie: sessionid=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: cadata=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
Location: https://webmail.exchange.bell.ca/exchweb/bin/auth/owalogon.asp?url=https://webmail.exchange.bell.ca/exchange/darren.fuller&reason=0&replaceCurrent=1
Connection: close
Content-Length: 0

GET /exchange/darren.fuller HTTP/1.1
E2k-Debug: 0x823b868 @ 1193329501
Host: webmail.exchange.bell.ca
Authorization: NTLM TlRMTVNTUAABAAAABoIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMAAAAAAAAAAwAAAA
User-Agent: Evolution/1.10.1

302 Moved Temporarily
E2k-Debug: 0x823b868 @ 1193329501
Set-Cookie: sessionid=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: cadata=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
Location: https://webmail.exchange.bell.ca/exchweb/bin/auth/owalogon.asp?url=https://webmail.exchange.bell.ca/exchange/darren.fuller&reason=0&replaceCurrent=1
Connection: close
Content-Length: 0

GET /exchweb/bin/auth/owalogon.asp?url=https://webmail.exchange.bell.ca/exchange/darren.fuller&reason=0&replaceCurrent=1 HTTP/1.1
E2k-Debug: 0x823b868 @ 1193329501 [restarted]
Host: webmail.exchange.bell.ca
Authorization: NTLM TlRMTVNTUAABAAAABoIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMAAAAAAAAAAwAAAA
User-Agent: Evolution/1.10.1

200 OK
E2k-Debug: 0x823b868 @ 1193329501
Pragma: no-cache
X-AspNet-Version: 2.0.50727
Date: Thu, 25 Oct 2007 16:25:02 GMT
X-Powered-By: ASP.NET
Expires: -1
Server: Microsoft-IIS/6.0
Cache-Control: no-cache
Content-Length: 8377
Content-Type: text/html; charset=utf-8
X-OWA-Version: 8.1.177.3


(evolution-2.10:12446): libsoup-CRITICAL **: soup_message_set_request: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution-2.10:12446): libsoup-CRITICAL **: soup_message_set_flags: assertion `SOUP_IS_MESSAGE (msg)' failed

(evolution-2.10:12446): libsoup-CRITICAL **: soup_session_send_message: assertion `SOUP_IS_MESSAGE (msg)' failed
Segmentation fault (core dumped)

```

---

### Post by mikawber on 2007-10-28
I'm getting this error message in Feisty. Does anybody have/know a fix for this issue. Its highly annoying. Thanks

---

### Post by airflow on 2007-11-06
..bump...

having the same problem. Interestingly, this problem only occurs for me when I'm inside the company-network. From outside, it works like it should. From what I know about the differences, there is another certificate used when coming from outside (Verisign vs. Company-CA). Could that be the problem?

Thanks for any hints,
airflow

---

### Post by bodybuzz on 2007-11-06
You're lucky..   at least you can connect at some time!!   Mine never works...

---

### Post by pagingmrherman on 2007-11-19
As of a new evolution update today, I've still got the same problem. 

I have no idea where to start troubleshooting this thing but I'm sure if enough bug reports show up in gnome, the developers will take a look at it.  I put one in a while ago and nothing has happened but eventually, they tend to get addressed.  They either get closed, deleted, marked as a duplicate or whatever.  Here's the address to file a bug: [http://bugzilla.gnome.org](http://bugzilla.gnome.org)

Remember, the squeaky wheel gets the grease!!! :-)

---

### Post by airflow on 2007-11-19
> **pagingmrherman said:**
> I have no idea where to start troubleshooting this thing but I'm sure if enough bug reports show up in gnome, the developers will take a look at it.
I'm not sure if it helps to file a lot of duplicate bug-reports. I think it's better to second existing bugs, as it will make this specific bug more important.

Besides, I found a workaround to circumvent the problem (at least in my case). It's not perfect, but it works fine until the root-cause is fixed. I found that the name of my OWA-URL is resolving differently depending on whether I'm out- or inside the corporate network. The same name (configured in evolution) resolved to two different IPs. I made a fixed name-resolution entry in the configuration of gnome's network manager. In both cases the "outside"-IP of the OWA-service is now used. Luckily, it seems the firewall-configuration seems to allow access to the "outside"-IP from inside, therefore it works now. Perhaps this idea can at least help some.

greez,
airflow

---

### Post by pagingmrherman on 2007-12-17
In theory, duplicate bug reports would be an indicator of how many people are having the same problem. Hopefully (wishful thinking) the bug will get noticed or become a giant pain in the *** and it's priority will bubble up to the top.  Like I said, squeaky wheel gets the grease.

---

