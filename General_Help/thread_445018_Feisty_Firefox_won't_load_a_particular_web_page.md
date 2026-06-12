---
title: "Feisty: Firefox won't load a particular web page"
date: 2007-05-15
forum: General Help
---

### Post by MarkMadsen on 2007-05-15
Hello all,

I have a Fresh Feisty install with minimal tweaking.  The networking is fine, Firefox works as expected, with one exception.  I often use this weather site:

[http://www.meteoswiss.ch/web/en/weather.html]("http://www.meteoswiss.ch/web/en/weather.html")

This site gives me "The connection was reset by the server...."  Retrying does not change anything.  

[LIST]
[*]All other sites I have visited from Firefox on this machine have been fine.
[*]All the other machines on my network (including several Dapper and Edgy boxes) can load that site OK.
[*]Kazehakase under Feisty can load that site OK.
[/LIST]

The site does not seem to use anything weird, and I have tried with each of {Java; Javascript; IPv6} turned on and off.  Can anyone explain what I am missing here?

Addendum: exactly the same thing happens with my wife's Powerbook G4 running Feisty.  All other sites work, but not that one.

Thanks in advance,
Mark

---

### Post by heimo on 2007-05-15
Well. It does it to me too. I used wireshark to capture my browser talking to the server. TCP handshake is ok, connection is established, browser sends HTTP GET command to get a page and server not-so-politely answers with RST, tearing down connection. Does this work with you in any browser / computer / OS?

---

### Post by ahaslam on 2007-05-15
Works fine here, Firefox 2.0.0.3.

---

### Post by heimo on 2007-05-15
> **Anthony Haslam said:**
> Works fine here, Firefox 2.0.0.3.

Weird problem. Same Firefox version. I just installed konqueror and it works fine there... Only thing I can think of is that the server doesn't like about some HTTP headers - accepted encoding / charset / language and can't handle it correctly. Server is most probably running Apache on Solaris (according to Netcraft). I don't think there's much to do (but let the server admins know about it).

---

### Post by bedake on 2007-05-16
The site doesnt work for me, I get the message The connection to the server was reset while the page was loading.

This also happens for another site for me.  I havent been able to access this site for like 2 weeks, the other day it started working for a few hours but quit again... very strange problem.

I tried using lynx and it wont connect to it either.


The site I am having the same problem is this: [http://www.ureg.ohio-state.edu](http://www.ureg.ohio-state.edu)

---

### Post by heimo on 2007-05-17
> **bedake said:**
> The site I am having the same problem is this: [http://www.ureg.ohio-state.edu](http://www.ureg.ohio-state.edu)

Works fine here with same computer and Firefox 2.0.03 which has problems with  [http://www.meteoswiss.ch/]("http://www.meteoswiss.ch/web/en/weather.html")

---

### Post by mdurham on 2007-05-17
okay here

---

### Post by MarkMadsen on 2007-05-21
**An Important Update**

Today I had  a polite message from the webmaster at Meteoswiss:

> Thank you for your e-mail. To solve this problem we can give you the following approach:
Enter "**about:config**" into the address field of your firefox and then press the enter button.

Search for the text string "**general.useragent.extra.firefoxComment**" 
and change the value from "***Ubuntu-feisty***" to "***Ubuntu 7.04***". 

After this change you should connect to our website without any problems.

This change does indeed fix the problem for me.  Thanks to everyone who made constructive posts.

Best,
Mark

---

### Post by heimo on 2007-05-21
This should be reported to Launchpad as a bug. Probably for Firefox package. Well, to be exact, this may not be a real bug (in firefox), but some kind of incompatibility or a bug on the server side, but having that value in agent string seems to cause problems, so it should be fixed in Ubuntus firefox package too (or wher-ever this value comes from).

Can someone confirm this problem and fix/solution?

---

### Post by popey on 2007-05-21
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/95241](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/95241)

It already is a bug in launchpad.

However it's more of an issue with the 3rd party proxy software.

---

### Post by heimo on 2007-05-21
> **popeydc said:**
> [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/95241](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/95241)

It already is a bug in launchpad.

However it's more of an issue with the 3rd party proxy software.

Oh, true. Very good. Links to this thread also.

---

### Post by bedake on 2007-05-23
> **MarkMadsen said:**
> **An Important Update**

Today I had  a polite message from the webmaster at Meteoswiss:



This change does indeed fix the problem for me.  Thanks to everyone who made constructive posts.

Best,
Mark



No luck for me and the site I was having trouble loading

---

### Post by yotam on 2007-06-02
Thank you !! 
for the **general.useragent.extra.firefoxComment** tip.
Now I can surf to:   yes.co.il

---

### Post by Paulo79 on 2007-06-07
> **bedake said:**
> I tried using lynx and it wont connect to it either.

The site I am having the same problem is this: [http://www.ureg.ohio-state.edu](http://www.ureg.ohio-state.edu)

I'm having the same problem, same URL (site). The tip on change the about:config entry in Firefox didn't work here. Also, I tried to browse that page using konqueror and it didn't work either.

Any one knows of another tip?

---

### Post by bedake on 2007-06-07
I actually reformatted the other day, trying to get my wireless working so that I could connect to other wlans other than my own.  After formatting I still cannot access either sites at all on my ubuntu partition.

---

### Post by kurrrt on 2007-06-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/95241](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/95241) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Paulo79 said:**
> I'm having the same problem, same URL (site). The tip on change the about:config entry in Firefox didn't work here. Also, I tried to browse that page using konqueror and it didn't work either.

Any one knows of another tip?

I am having the same problem. The about:config does not work for me (ubuntu 7.04, firefix 2.0.0.4) with [http://www.ureg.ohio-state.edu/](http://www.ureg.ohio-state.edu/) (but ok for the other site). 
More frustrating is the http authentication page which the college library WiFi network uses does not work either. :(

---

