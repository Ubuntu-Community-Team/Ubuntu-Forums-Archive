---
title: "How to connect to Google Talk (GTalk) from Ubuntu (Dapper Drake) throug an http proxy"
date: 2006-10-19
forum: General Help
---

### Post by maheshjagadeesan on 2006-10-19
[FONT="Trebuchet MS"]I had started using Linux at work recently, and I chose Ubuntu because I'd seen it before and I'd liked what I saw :-) I installed Breezy, upgraded to Dapper (online), and found that the Ubuntu folks had just released Edgy, so I upgraded to that as well! On the way, I also installed the complete KDE package, so my installation changed its name to Kubuntu. 

Anyway, there was this one issue that was driving me mad: we connect to the Net through an http proxy (on port 80) - with user authentication - and no other ports are open. When I was using the GTalk client on Windows, I used to get connected without any issues. However, after I switched to Ubuntu, I was unable to sign in using Gaim (the latest beta 2.0.0 beta4), no matter what I tried.

I started out by checking the GTalk help pages and tried out suggestions on [this page]("http://www.google.com/support/talk/bin/answer.py?answer=24073"), but it didn't help. Next, I tried writing to the good people at Google asking them what could be wrong. Bingo! After an exchange of mails explaining the problem to them, they gave me a solution. It's very simple really. 

Apart from what's mentioned in the page linked above([this one]("http://www.google.com/support/talk/bin/answer.py?answer=24073")), all I did was change the port to 443 (my proxy tunnels only to this port - to allow https pages) and check "Force old SSL". And voila, my connection was successfully made. Now, I chat with my friends without any problems :-)

[/FONT]

---

### Post by SendDerek on 2006-11-12
Thank you very much for this information.  After "forcing old SSL" it logged right in!  Thanks much.

---

### Post by maheshjagadeesan on 2006-11-13
I'm happy it was of help - I was wondering if anyone was even going to read my post ;-)

---

### Post by SendDerek on 2006-11-13
> **maheshjagadeesan said:**
> I'm happy it was of help - I was wondering if anyone was even going to read my post ;-)

lol.

I feel the same way about some of my posts!

And actually I gotta let you know that I'm not setup through any proxies.  It just worked for me.  I have censored web access though through my college campus which presents all kinds of connectivity issues for me.

What finally got it working for me was this setup (to confirm):

[ ] Use TLS if Available (unchecked)
[ ] Requite TLS (unchecked)
[/] Force old (port 5223) SSL (checked)
[ ] Allow plaintext (unchecked)

Connect Port:  443
Connect Server: talk.google.com

---

### Post by B0buntu_Olivaw on 2006-12-10
Hi there,

Thanks for this post, solved my problem, now onward with the time-wasting ho!

---

### Post by maheshjagadeesan on 2006-12-11
Thanks Derek (I assume that's your name?)

May Ubuntu be with you ;-)

---

### Post by maheshjagadeesan on 2006-12-11
Enjoy! :-)

---

### Post by think!! on 2007-10-01
Although it's late, thank you very much for the post, I'm already was already searching a long time for an possibility to use GTalk behind a proxy.

think!!

---

### Post by wrongman on 2008-03-06
very thx, worked like a charm :)

---

### Post by maheshjagadeesan on 2008-03-06
You're welcome, wrongman.

---

