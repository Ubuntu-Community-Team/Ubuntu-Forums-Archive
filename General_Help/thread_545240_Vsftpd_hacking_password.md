---
title: "Vsftpd hacking password"
date: 2007-09-07
forum: General Help
---

### Post by larry Gaminde on 2007-09-07
I have installed Vsftpd and have it working ! 
My problem is that there are attacks made every day on my system from China, Romania, and Korea yea I know who whadda guessed?? 
How can I stop these attacks they pick a username and just keep trying to log in. I have set up a userlist and denied access to these networks and usernames but I would like to allow only one attempt of three password tries then disallow any more attempts. Would switching to Wu_Ftp program fix this is there anything else I can do with Vsftpd??

---

### Post by kidders on 2007-09-08
Hi there,

This sort of thing happens routinely where someone exposes a well known service to the net, I'm afraid. Most such attempts to gain access to your system are completely harmless ... if you inspect them, I'm sure you'll agree they're all pretty lame hehe. Often, the user of a computer that "attacks" you is not even aware it's happening.

Nonetheless, I find this sort of thing *intensely* irritating, for some reason, so I stamped it out on my box. Your options are...

[LIST]
[*]**Ignore it.** If you trust the quality of your usernames & passwords, I find it unlikely that any of these unsophisticated, brute force attacks will get anywhere.
[*]**Move your FTP service.** Certain things attract malicious activity ... for instance, subscribing to a dynamic DNS service, or running well known services on standard ports. If you were to bind your FTP server to port 100021 (ie instead of port 21), say, the vast majority of the attacks should evaporate. Your legitimate users would find this inconvenient though.
[*]**Actively block IPs.** I do this on my box, simply because it puts my mind at rest. I created a little script that watches my authentication logs for repeated login failures & configures iptables to block the originating IP on the fly.[/LIST]What (if anything) to do is entirely up to you. Because of its _total_ lack of security, I never use FTP, but I assume today's FTP servers are similar to other kinds of servers, in that the one thing you *won't* be able to do is dynamically alter the server's own authentication rules on the fly, in response to an attack.

One other possible option (that sort of falls under the "Ignore it" category) would be to alter your system's login failure delay. You may have noticed that, when using sudo or logging into your graphical environment, your system seems to take a strangely long time to figure out that a password you entered is wrong. This delay is deliberate, and is designed to make brute force attacks impractical, by artificially increasing the amount of time they would take to perform. If you're using an FTP server that integrates with your Linux system's own authentication mechanism, you could always hike up the "bad login" delay. Even a 10-second delay would force an attacker to waste 3 entire hours, just to try 1,000 passwords for a username that probably doesn't exist anyway.

So, in a way, that's four ideas. Let me know what you think. :-)

---

### Post by bodhi.zazen on 2007-09-08
You can also look at deynhosts, which is for ssh, but it will give you some additional converage depending on how it is configured.

I do not know, however, if Vsftpd will benefit ??

You could also change the default port, or tunnel over ssh.

---

### Post by larry Gaminde on 2007-09-09
Thanks I have already changed the port to 42. I am the only one that will use the FTP server, I use it to update things stored on the htp server. now how would I change the timer for password login?

> **kidders said:**
> Hi there,

This sort of thing happens routinely where someone exposes a well known service to the net, I'm afraid. Most such attempts to gain access to your system are completely harmless ... if you inspect them, I'm sure you'll agree they're all pretty lame hehe. Often, the user of a computer that "attacks" you is not even aware it's happening.

Nonetheless, I find this sort of thing *intensely* irritating, for some reason, so I stamped it out on my box. Your options are...
[LIST]
[*]**Ignore it.** If you trust the quality of your usernames & passwords, I find it unlikely that any of these unsophisticated, brute force attacks will get anywhere.
[*]**Move your FTP service.** Certain things attract malicious activity ... for instance, subscribing to a dynamic DNS service, or running well known services on standard ports. If you were to bind your FTP server to port 100021 (ie instead of port 21), say, the vast majority of the attacks should evaporate. Your legitimate users would find this inconvenient though.
[*]**Actively block IPs.** I do this on my box, simply because it puts my mind at rest. I created a little script that watches my authentication logs for repeated login failures & configures iptables to block the originating IP on the fly.[/LIST]What (if anything) to do is entirely up to you. Because of its _total_ lack of security, I never use FTP, but I assume today's FTP servers are similar to other kinds of servers, in that the one thing you *won't* be able to do is dynamically alter the server's own authentication rules on the fly, in response to an attack.

One other possible option (that sort of falls under the "Ignore it" category) would be to alter your system's login failure delay. You may have noticed that, when using sudo or logging into your graphical environment, your system seems to take a strangely long time to figure out that a password you entered is wrong. This delay is deliberate, and is designed to make brute force attacks impractical, by artificially increasing the amount of time they would take to perform. If you're using an FTP server that integrates with your Linux system's own authentication mechanism, you could always hike up the "bad login" delay. Even a 10-second delay would force an attacker to waste 3 entire hours, just to try 1,000 passwords for a username that probably doesn't exist anyway.

So, in a way, that's four ideas. Let me know what you think. :-)

---

### Post by kidders on 2007-09-09
> **larry Gaminde said:**
> how would I change the timer for password login?The failure delay? It seems as though it's no longer possible to easily manipulate the length of it. :-( The old mechanism for doing so doesn't seem to work in Ubuntu, and I can't seem to find a convenient replacement. Sorry for the bad advice on that one.

---

### Post by HermanAB on 2007-09-09
Another solution is to use iptables rate limiting to throttle new connection attempts.  Some Googling for 'iptables rate limit' will get you going.  This way, a script kiddie will never get to do more than a handful of tries and will give up and go away pretty quickly.

In general, rate limiting is a good way to fend off anything from password attacks, to DOS and spam. Yes, even spam. My mail server has a 5 second sleep between accepting and incoming connection and sending the banner, plus a 1 second sleep every step of the way in SMTP.  The result is that most spammers give up and go away, while normal mail works perfectly.  It is only bad guys that want to hog bandwidth - they are trying to steal from you and want to steal as much as possible - everybody else is patient.

Cheers,

H.

---

