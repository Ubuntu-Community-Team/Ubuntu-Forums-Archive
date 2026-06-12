---
title: "evolution to exchange server"
date: 2007-04-14
forum: General Help
---

### Post by leupi on 2007-04-14
I am trying to get Evolution to work with my Company's Exchange server. I had it working a while back but lost the setting and now I can't figure out how I did it. I am sure that the issue is with the format of the URL for the OWA. The URL in a browser when I access it is:
> https://mail.<company>.net/exchweb/bin/auth/owalogon.asp?url=https://mail.<company>.net/exchange&reason=0
I tried https://mail.<company>.net/exchange and some other variation but I keep getting an error the the URL is wrong. Any idea as to what the proper format would be for this?

Thanks,
Todd

---

### Post by jvanderb on 2007-04-16
From my experience, all you need for the URL is https://mail.<company>.net/.  None of the path after that is necessary.  

One other thing you need to be aware of - Evolution only supports Exchange 2000 or newer.  It's been a while, so pardon me if I'm wrong, but the URL you posted looks suspiciously like Exchange 5.5.  

Hope this helps!

---

### Post by leupi on 2007-04-18
I appreciate the reply. I tried with just that part of the address, such as:
http://mail.<company>.net
and
http://mail.<company>.net/exchange
but no luck. I would be sure that we have Exchange 2000 or newer as I was able to do this on my Linux laptop before. I have now installed Evolution on my company laptop that has windows and have since lost the settings that I previously used and cannot get it to work again.

Thanks,
Todd

---

### Post by dcstar on 2007-04-18
> **leupi said:**
> I appreciate the reply. I tried with just that part of the address, such as:
http://mail.<company>.net
and
http://mail.<company>.net/exchange
but no luck. I would be sure that we have Exchange 2000 or newer as I was able to do this on my Linux laptop before. I have now installed Evolution on my company laptop that has windows and have since lost the settings that I previously used and cannot get it to work again.

Thanks,
Todd

Use whatever "vanilla" URL you put into your web browser to get the login screen for OWA, then cut and paste that into Evolution.

Experiment with the web browser to get the login - (and I'm not sure if Evolution supports HTTPS Exchange login, so if your Exchange admin has blocked HTTP access to OWA you might be in trouble).

---

### Post by biton on 2007-05-09
I have exactly the same problem as Leupi. When i use IE or FF the URL is 
https://mail.<company>.net/exchweb/bin/auth/owalogon.asp?url=https://mail.<company>.net/exchange&reason=0

I tried every variations but still get the same authentication error. Does somebody know:
 - what is the correct OWA URL based on the previously entered URL
- what should be the login name ? in IE it's domain\name.surname but when I check my mailbox settings in exchange it's surname,initial. - name - 

thanks for your help

---

### Post by dcstar on 2007-05-10
> **biton said:**
> I have exactly the same problem as Leupi. When i use IE or FF the URL is 
https://mail.<company>.net/exchweb/bin/auth/owalogon.asp?url=https://mail.<company>.net/exchange&reason=0

I tried every variations but still get the same authentication error. Does somebody know:
 - what is the correct OWA URL based on the previously entered URL
- what should be the login name ? in IE it's domain\name.surname but when I check my mailbox settings in exchange it's surname,initial. - name - 

thanks for your help

The "normal" default OWA URL should be something like:

https://mail.<company>.net/exchange

This is what should be in Evolution, the other one you are using seems to be the login screen URL.

---

### Post by biton on 2007-05-10
> **dcstar said:**
> The "normal" default OWA URL should be something like:

https://mail.<company>.net/exchange

This is what should be in Evolution, the other one you are using seems to be the login screen URL.

Thanks but this gets me an 'Unable to locate server' error. When I use [https://webmail.company.com/exchange/&reason=0](https://webmail.company.com/exchange/&reason=0), I get an authentication error which I thought was more promising

---

### Post by extremecarver on 2007-05-22
I have exactly the same problem --> my university set up Exchange server 2007 recently and since then no more luck with evolution. following some information, maybe someone can help out here. I know that this setup of Exchange Server 2007 is incompatible with outlook 2002 or earlier.
**Outlook IE login**
This is the url to acces it: [http://www.fh-krems.ac.at/exchange](http://www.fh-krems.ac.at/exchange) which resolves in  [https://email.fh-krems.ac.at](https://email.fh-krems.ac.at) and then forwards to [https://email.fh-krems.ac.at/exchweb/bin/auth/owalogon.asp?url=https://email.fh-krems.ac.at/exchange/&reason=2&replaceCurrent=1](https://email.fh-krems.ac.at/exchweb/bin/auth/owalogon.asp?url=https://email.fh-krems.ac.at/exchange/&reason=2&replaceCurrent=1)

**Outlook Light login**
The other URL that does work is [https://email.fh-krems.ac.at/owa/](https://email.fh-krems.ac.at/owa/) which refers then to [https://email.fh-krems.ac.at/owa/auth/logon.aspx?url=https://email.fh-krems.ac.at/owa/&reason=0](https://email.fh-krems.ac.at/owa/auth/logon.aspx?url=https://email.fh-krems.ac.at/owa/&reason=0)

Mailbox owner: username [username@fh-krems.eu]
User-Agent: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; FDM; .NET CLR 2.0.50727; .NET CLR 3.0.04506.30)
Outlook Web Access experience: Premium
User language: English (United Kingdom)
User time zone: (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
Exchange mailbox address: /O=imc/OU=IMC-KREMS/cn=Recipients/cn=username
Outlook Web Access host address: [https://email.fh-krems.ac.at/owa](https://email.fh-krems.ac.at/owa)
Outlook Web Access version: 8.0.685.24
Outlook Web Access host name: email.fh-krems.ac.at
Exchange Client Access server .NET Framework version: 2.0.50727.235
Microsoft Exchange Client Access server operating system version: Microsoft Windows NT 5.2.3790 Service Pack 2
Microsoft Exchange Client Access server operating system language: en-US
Microsoft Exchange Client Access server version: 8.0.685.0
Microsoft Exchange Client Access server language: en-US
Microsoft Exchange Client Access server time zone: W. Europe Standard Time
Microsoft Exchange Client Access server platform: 64bit
Microsoft Exchange Mailbox server name:** LEJIA.imc-krems.ac.at** (Note: This is the exchange server that I need to enter in Outlook)
Mailbox server Microsoft Exchange version: 8.0.685.0
Other Microsoft Exchange server roles currently installed on the Client Access server: Hub Transport
Authentication type associated with this Outlook Web Access session: Basic
Public logon: No


**Here is a link by our university on howto setup outlook 2007 - can you see any incompatibilities?**
[http://elearning.imc-krems.ac.at/SmarterTicket/Customer/KBArticle.aspx?articleid=19](http://elearning.imc-krems.ac.at/SmarterTicket/Customer/KBArticle.aspx?articleid=19)

---

### Post by aukjan on 2007-06-28
I am not using ubuntu, but would like to confirm this message.  My company also uses exchange 2007, but evolution recognizes it as exchange 5.5.  It seems to me that the connector doesn't recognize the string it gets back from the server and falsely decides its 5.5 .. 
Should be a simple change if Microsoft hasn't changed much between 2003 and 2007 .. :-(

---

### Post by extremecarver on 2007-06-28
Maybe someone should consider having a look into the source code (differences between 1.1.4 and 1.1.5) of Pop2Owa which is able to access Exchange Server 2007 since the newest version 1.1.5 (published last Monday). 
I don't think its too difficult - however some changes are needed. 

The other possibility would be to port Pop2Owa from Windows XP to Ubuntu, the code is on Sourceforge.

I'm not into programming at all but helped the author of Pop2Owa to implement the new 2007 support (betatesting and providing an access).

---

### Post by prkfriryce on 2007-09-10
I am also trying to authenticate Evolution exchange with my corporate webmail. I type my <username> without the <domainname>\ in front and the OWA <http://ABC.domainname.com/exchange> and I am able to successfully authenticate my user.

When I finish setting up my user, Evolution prompts for my <username> password so it can connect to the webmail url, but instead of <username>@<http://ABC.domainname.com/exchange>, it switches to a different OWA address: <username>@<http://XYZ.domainname.com/exchange> !

Has anyone encountered this problem b/c I am unalbe to authenticate my <username> to this second OWA.

If I manually place the <http://XYZ.domainname.com/exchange> into firefox, it authenticates.

Why is the redirection not authenticating correctly in Evolution?

---

### Post by dushkal on 2007-09-13
Hi prkfriryce,

In the good old days when our company's server was still on older exchange server, I had this problem. I's managed to work around this problem by simply putting the same IP address for both the servers (in your case IP address of ABC.domainname.com)

so make this entry in /etc/hosts file:

ABC.domainname.com      xxx.xxx.xxx.xxx
XYZ.domainname.com      xxx.xxx.xxx.xxx

where the xxx.xxx.xxx.xxx is the IP address of ABC.domainname.com and let us know...

---

### Post by prkfriryce on 2007-09-13
> **dushkal said:**
> Hi prkfriryce,

In the good old days when our company's server was still on older exchange server, I had this problem. I's managed to work around this problem by simply putting the same IP address for both the servers (in your case IP address of ABC.domainname.com)

so make this entry in /etc/hosts file:

ABC.domainname.com      xxx.xxx.xxx.xxx
XYZ.domainname.com      xxx.xxx.xxx.xxx

where the xxx.xxx.xxx.xxx is the IP address of ABC.domainname.com and let us know...

I'm a little mad I did not think of putting the aliases in the hosts file myself, but thanks!

xxx.xxx.xxx.xxx  ABC.domainname.com 
xxx.xxx.xxx.xxx  XYZ.domainname.com 

works!  :)

---

### Post by tech3linux on 2007-09-14
I'm a total noob with linux. After doing this I saw the above posts starting with dushkal's and now this doesn't seem so important....

I just used "https://11.0.100.2/exchange" as the OWA address where "11.0.100.2" is the LAN address of the server which is probably the same as your DNS IP 

Anyway, first post! Day late and a dollar short :(

---

