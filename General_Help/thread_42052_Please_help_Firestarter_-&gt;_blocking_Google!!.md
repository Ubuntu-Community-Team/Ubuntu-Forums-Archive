---
title: "Please help: Firestarter -&gt; blocking Google!?!"
date: 2005-06-15
forum: General Help
---

### Post by Taoism on 2005-06-15
Hi all,

I have no idea how or why this happened.  I haven't touched Firestarter in a long, long time.

Here's the scoop.  I noticed this past week that Googlebar in Firefox wasn't working, and that any sites that loaded ads from googlesyndication.com were timing out before they could load.  I couldn't browse to google.com either.  I kept seeing "waiting for google.com" in the Firefox statusbar, so it was connecting to the site, but just not getting any further.

I did a traceroute:

```

youngka@pandora:~$ traceroute www.google.com
traceroute: Warning: www.google.com has multiple addresses; using 72.14.207.99
traceroute to www.l.google.com (72.14.207.99), 30 hops max, 38 byte packets
 1  192.168.0.1 (192.168.0.1)  9.804 ms  5.122 ms  11.906 ms
 2  * * *
 3  rc2nr-ge3-0-5.wp.shawcable.net (64.59.178.131)  14.361 ms  10.008 ms  9.952 ms
 4  rc1nr-pos15-0.wp.shawcable.net (66.163.73.129)  15.267 ms  15.081 ms  12.173 ms
 5  * rc1sh-pos13-0.mt.shawcable.net (66.163.76.73)  31.760 ms  30.426 ms
 6  rc2sh-pos15-0.mt.shawcable.net (66.163.66.14)  43.295 ms  30.807 ms  31.934 ms
 7  gw-google.torontointernetxchange.net (198.32.245.6)  32.926 ms  32.197 ms *
 8  66.249.94.92 (66.249.94.92)  38.759 ms  32.310 ms  59.969 ms
 9  66.249.94.105 (66.249.94.105)  34.902 ms  34.723 ms  35.155 ms
10  * * *
11  * * *
...
30  * * *

```

I can get to most sites just fine.  I thought at first it was a Google issue.  But from work I can reach Google just fine.  I just tried using Google on my XP machine on my home network and had no problems (so not my router).  It then occurred to me to start the Firestarter GUI and turn off the firewall and try Google again.  Well, all the Google stuff started working again.  

As a side note, gmail was unaffected - I assume because it is an https connection?

So, since I have never had to deal with this before, how can I tell Firestarter to leave Google-related incoming requests alone?

Thanks in advance for any help!

Cheers,
Keith.

---

### Post by deBaas on 2005-06-20
What rules have you made in firestarter?

---

### Post by burg on 2005-06-29
I'm having the same issue.  Telnet to google.com 80 works fine, but telnet [www.google.com](www.google.com) 80 doesn't.  The firewall is dropping the reply from google.  And of course I don't have a rule to do that specifically, so something is just different enough about the [www.google](www.google) response to get flagged and dropped.  Any other sites I've tried work fine.

---

### Post by crispingatiesa on 2005-06-29
Guys,go here: 

 [http://www.ubuntuforums.org/showthread.php?t=41238](http://www.ubuntuforums.org/showthread.php?t=41238)

---

