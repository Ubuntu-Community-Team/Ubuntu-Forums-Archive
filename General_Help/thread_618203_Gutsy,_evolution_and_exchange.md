---
title: "Gutsy, evolution and exchange"
date: 2007-11-20
forum: General Help
---

### Post by quentinc on 2007-11-20
I am trying to connect up evolution to exchange. I can use Firefox to connect up to OWA but when I use the same credentials in the evolution setup assistant wizard, I get "Could not authenticate to server".

Is there some log file that I should be looking into to investigate this or is there something obvious I could have wrong?

Thanks in advance!

Quentin

---

### Post by jchildrose on 2007-11-20
Evolution does use OWA to connect to an Exchange server, so if you can connect via OWA then evolution should have no issues.

Some OWA setups will redirect from http to https, but I don't know if Evolution will follow the redirection. The URL you provide to evolution should be something like [https://owa.yourdomain.com/exchange](https://owa.yourdomain.com/exchange) if the server was set up using a default configuration.

Also, you should specify the NetBIOS domain name with your username in the form of DOMAIN\username instead of just your username.

Hope that helps.

---

### Post by quentinc on 2007-11-20
It helps, it confirms that I am entering the right information. My server is only accessible through https so I am using that in the URL and I was using DOMAIN\username format already...

But as I say I can use the same URL and credentials in Firefox to access owa on the same machine.

Quentin

---

### Post by ephro on 2007-11-20
I use evolution extensively. Your best bet is to login to owa, then hover over the Inbox link. You will see something like this:

[https://owa.domain.tld/exchange/XXXXXX/Inbox/?Cmd=contents&Page=1](https://owa.domain.tld/exchange/XXXXXX/Inbox/?Cmd=contents&Page=1)

The XXXXXX is your login name. So in this case you should use:

[https://owa.domain.tld/exchange/XXXXXX/](https://owa.domain.tld/exchange/XXXXXX/)

Also make sure you download locally and only check every 5 or 10 minutes. I think there is some threading issues which cause some long delays if you don't do that with 2.12.X.



ephro

---

### Post by quentinc on 2007-12-01
More as an FYI but I never did get this to. I am confident I have the right username, password and URL.

---

### Post by dustobub on 2007-12-04
If you are using Exchange 2007, Evolution is not compatible yet. If you want to use the Premium OWA client check out my post on page two here.

[http://ubuntuforums.org/showthread.php?t=519672](http://ubuntuforums.org/showthread.php?t=519672)

Dustin

---

