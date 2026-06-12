---
title: "HAProxy ssl passthrough reverse proxy slow connection speeds"
date: 2016-09-13
forum: General Help
---

### Post by courtney2 on 2016-09-13
I have HAProxy set up as a reverse proxy right now and one thing it's doing is passing through ssl connections and performing permanent redirects for port 80 connections to an https connection. Right now, however my performance is REALLY bad. It takes about 7-15 seconds to load a page where before it would take quite a bit less time before I set up the reverse proxy. I do have 15Mbps upload speeds, but I'm wondering if HAProxy is the bottleneck right now. Are there any known ways to speed it up?

The speeds are very variable too. Sometimes just getting / takes 10  seconds, other times it's immediate. Sometimes images load quickly,  other times it takes 7 seconds to fetch it. Each time I do this I do  have a cleared cache on the web browser I use. I've been testing with Firefox, QupZilla, Google Chrome and Konquerer and Safari for iOS

---

### Post by courtney2 on 2016-10-05
Bump

And update: slow TTFB only happens with my Wordpress server. If I resend the request immediately after my initial GET, the web browser retrieves the entire contents of the website almost immediately

---

