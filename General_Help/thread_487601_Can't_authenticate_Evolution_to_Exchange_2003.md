---
title: "Can't authenticate Evolution to Exchange 2003"
date: 2007-06-29
forum: General Help
---

### Post by iAMbigFISH on 2007-06-29
Hi everyone!

I've been trying to use Ubuntu for two weeks now :) and I've learn't a lot.

Finally got compiz running and my ThinkPad T60 wireless adapter, but now I'm faced with another issue, Evolution and Exchange 2003.

I've configured Evolution via the OWA ([http://192.168.1.200:8080/exchange/](http://192.168.1.200:8080/exchange/)) but I cannot authenticate -- when I try the username/password via Firefox or IE it works fine, but not in Evolution... help! :)

---

### Post by letkemanp on 2007-06-29
It may be a username problem. There are several ways that you can provide a user name for to OWA:
[email]username@domain.name.com[/email]
domainname\username
username

Windows is case insensitive for the username however you may want to try putting the domain name in uppercase if you still have problems.

The good thing about FireFox is that it's cross platform. You said that OWA with with IE, so you have a Windows system. If you install FireFox on a WIndows system and try OWA does it work?

Have you checked your firewall settings on both the client system and the Exchange 2003 system?

Exchange should be logging your OWA login attempts, perhaps something more information could be found in the Exchange 2003/Windows 2003 Security Logs.

I use FireFox all the time and I've not had a problem where I can't log into my Exchange 2003 system using OWA, so I don't thinks it's a FireFox problem.

You may also want to try out Crossover Office, [http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/) and install Outlook. They have a free trial. I've found Crossover Office + Outlook 2003 works quite well for the most part. Only found a couple of problems with it that I can live with.

---

### Post by iAMbigFISH on 2007-06-29
Ok, it seems Evolution does NOT like my non-standard OWA port of 8080, when I changed it from 8080 to 80 Evolution was able to connect!

Is there a work around or did I just enter the address incorrectly?

Here's how I originaly did it: [http://192.168.1.200:8080/exchange/](http://192.168.1.200:8080/exchange/)

---

### Post by prkfriryce on 2007-09-05
I'm trying to authenticate Evolution exchange with my corporate webmail.  I type my <username> without the <domainname>\ in front and the OWA <http://ABC.domainname.com/exchange> and I am able to successfully authenticate my user. 

When I finish setting up my user, Evolution prompts for my <username> password so it can connect to the webmail url, but instead of <username>@<http://ABC.domainname.com/exchange>, it switches to a different username@OWA addres: <username>@<http://XYZ.domainname.com/exchange> !

Has anyone encountered this problem b/c I am unalbe to authenticate my <username> to this second OWA.  

If I manually place the <http://XYZ.domainname.com/exchange> into firefox, it authenticates. 

Why is the redirection not authenticating correctly in Evolution? 

thanks

---

