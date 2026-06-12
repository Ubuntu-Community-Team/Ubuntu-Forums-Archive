---
title: "Hmmmm... am I being hacked?"
date: 2013-02-08
forum: General Help
---

### Post by Niemand000 on 2013-02-08
I received this message after I clicked on "buckys C++ programming tutorial - 9 Functions".  I'd been concerned about being hacked recently, is this proof?

"Our systems have detected unusual traffic from your computer network.  Please try your request again later.  [Why did this happen?]("http://www.google.com/sorry/?continue=http://www.youtube.com/watch%3Fv%3DbsWWHo4KDHE#")

        This page appears when Google automatically detects requests coming  from your computer network which appear to be in violation of the [Terms of Service]("http://www.google.com/accounts/TOS"). The block will expire shortly after those requests stop.

This  traffic may have been sent by malicious software, a browser plug-in, or  a script that sends automated requests.  If you share your network  connection, ask your administrator for help — a different computer using  the same IP address may be responsible.  [Learn more]("http://www.google.com/support/bin/answer.py?answer=86640")

Sometimes you may see this page if you are using advanced terms that robots are known to use, or sending requests very quickly.    

   IP address: 107.7.72.58
Time: 2013-02-08T18:57:31Z
URL: http://www.youtube.com/watch?v=bsWWHo4KDHE"

---

### Post by zero2xiii on 2013-02-08
Hay,

New to linux I assume? However non the less,

Firstly - OPEN LESS TABS ON YOUTUBE
Sencondly - Stop skipping youtube adverts
Thirdly - Stop downloading the videos from the tube.

If non of the above is relevent, strange.... Anyhow.. read on...

Try using other google tools aswell? But here are some suggested reading material so you can see if you are "Hacked"

[http://ubuntuforums.org/showthread.php?t=965242](http://ubuntuforums.org/showthread.php?t=965242)
[http://superuser.com/questions/408144/ubuntu-tool-for-showing-internet-traffic-for-each-process](http://superuser.com/questions/408144/ubuntu-tool-for-showing-internet-traffic-for-each-process)

If that does not make heads or tails for you... I strongly suggest getting a beer, and a kitkat and just pause and breathe for a moment.

Unless you browse some dark and dodgey sites (pr0n included and some p2p or some TPB love... we all have a dark lover somewhere).. Chances are zero. If you visit some questionable sites, STOP, and find another source (its the internet for ffs, there is NO SINGLE COPY of a file.. always more.. Also keeping your computer up to date is easy and will destroy the last shreds of chances.. Getting hit by a zero day exploit on ubuntu is RARE unless you are some high risk target, but then you wont be here :)

Good luck and have fun.. Keep your eyes peeled and make sure you buy from a HTTP**S** site. Then you should not have much to fear anyway even **IF** you are hacked...

PS. This should be in the security discussion section not general help.

Cherz and good luck

---

### Post by CharlesA on 2013-02-08
zero2xiii pretty much nailed it. If you had checked the actual message you got by clicking on "Why did this happen?" you would have known what the problem was.

> This page appears when Google automatically detects requests coming from your computer network which appear to be in violation of the [Terms of Service]("http://www.google.com/accounts/TOS"). The block will expire shortly after those requests stop.

This traffic may have been sent by malicious software, a browser plug-in, or a script that sends automated requests. If you share your network connection, ask your administrator for help &#8212; a different computer using the same IP address may be responsible. [Learn more]("http://www.google.com/support/bin/answer.py?answer=86640")

Sometimes you may see this page if you are using advanced terms that robots are known to use, or sending requests very quickly. 

That being said, either you were doing the actions zero2xiii suggested or someone on your network is.

---

### Post by haqking on 2013-02-08
> **Niemand000 said:**
> I received this message after I clicked on "buckys C++ programming tutorial - 9 Functions".  I'd been concerned about being hacked recently, is this proof?

"Our systems have detected unusual traffic from your computer network.  Please try your request again later.  [Why did this happen?]("http://www.google.com/sorry/?continue=http://www.youtube.com/watch%3Fv%3DbsWWHo4KDHE#")

        This page appears when Google automatically detects requests coming  from your computer network which appear to be in violation of the [Terms of Service]("http://www.google.com/accounts/TOS"). The block will expire shortly after those requests stop.

This  traffic may have been sent by malicious software, a browser plug-in, or  a script that sends automated requests.  If you share your network  connection, ask your administrator for help &#8212; a different computer using  the same IP address may be responsible.  [Learn more]("http://www.google.com/support/bin/answer.py?answer=86640")

Sometimes you may see this page if you are using advanced terms that robots are known to use, or sending requests very quickly.    

   IP address: 107.7.72.58
Time: 2013-02-08T18:57:31Z
URL: http://www.youtube.com/watch?v=bsWWHo4KDHE"


I see this message all the time, it is usually because I am usually connected through Tor or some other proxy and its a IP thing.

Your IP address is a educational shared IP, I expect thats why.  The traffic thing can be a bit misleading I think, but who knows, you may be 0wn3d ;-)

Peace

---

### Post by eival on 2013-02-08
those messages normally only appear when you're using a public proxy or TOR browser, then you have to enter a captcha code to be able to continue using it, google.com does it even just merely trying to access it, not even running a search, im assuming youtube probably has similar checks since they're now run by google

i highly doubt you're overloading or setting off triggers at youtube, considering i have the fasterfox plugin set to turbo, and i use addons to download youtube vids at max settings all the time, they throttle their video streams anyways, it always goes down to about a few hundred Kb/s after starting with a bust of a few Mb/s

---

### Post by oleink on 2013-02-08
> **Niemand000 said:**
> I received this message after I clicked on "buckys C++ programming tutorial - 9 Functions".  I'd been concerned about being hacked recently, is this proof?

"Our systems have detected unusual traffic from your computer network.  Please try your request again later.  [Why did this happen?]("http://www.google.com/sorry/?continue=http://www.youtube.com/watch%3Fv%3DbsWWHo4KDHE#")

        This page appears when Google automatically detects requests coming  from your computer network which appear to be in violation of the [Terms of Service]("http://www.google.com/accounts/TOS"). The block will expire shortly after those requests stop.

This  traffic may have been sent by malicious software, a browser plug-in, or  a script that sends automated requests.  If you share your network  connection, ask your administrator for help — a different computer using  the same IP address may be responsible.  [Learn more]("http://www.google.com/support/bin/answer.py?answer=86640")

Sometimes you may see this page if you are using advanced terms that robots are known to use, or sending requests very quickly.    

   IP address: 107.7.72.58
Time: 2013-02-08T18:57:31Z
URL: http://www.youtube.com/watch?v=bsWWHo4KDHE"

if the above answers didn't help (aka if you arent doing any of the above)  try using wireshark or something of the sort to monitor your network traffic.  It is unlikely you are being "hacked" and more likely you are being tampered with.  If nothing is on your local network and you can do this, try to have your router generate log files and check them out.  good luck

---

