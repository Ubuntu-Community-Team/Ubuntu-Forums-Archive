---
title: "Trouble with apt-get"
date: 2007-08-05
forum: General Help
---

### Post by Draylorre on 2007-08-05
Yes, yes, another apt-get problem-post. I've read through a few threads and I've done this so far:


1) Configured my eth0 as 192.168.0.51 statically, and installed ssh. Successfully pinged everything on my LAN.
2) blacklisted IPv6
3) added my public IP address as my nameserver in /etc/resolv.conf
4) Removed the proxy info in /etc/apt/apt.conf
5) Probably a few other things that I've failed to mention.

Before I couldn't contact, now after doing all of these things, I'm able to at least SEE the URLs (us.archive.ubuntu.com, and all that jazz related.)

I am in the US, Ohio to be exact, and whenever I contact the URLs, I stay at 0% and then get a lovely...

[I]Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
[/I]

Now, I can't ping [www.google.com](www.google.com) or anything similar, but I can ping my router.

It'd be worth mentioning I've had some sever issues with my router in the past (Yes, I'm getting a new one soon) and I've come to the conclusion that it just might be the router.

Before I start throwing out DMZs and all that fun stuff, does anyone else have any suggestions? I've been trolling these forums for the past 5 hours looking for solutions and so far found none that suit my problems.



Thanks in advance,
Draylorre

---

### Post by ZipoTe on 2007-08-05
you can try changing your DNS, check out this ones: [http://www.opendns.com/]("http://www.opendns.com/") they explain how to change them, all the advantages and this stuff :)

post here if this solves your problem! ;)

---

### Post by Draylorre on 2007-08-05
> **ZipoTe said:**
> you can try changing your DNS, check out this ones: [http://www.opendns.com/]("http://www.opendns.com/") they explain how to change them, all the advantages and this stuff :)

post here if this solves your problem! ;)

As my idol, GIR, would say: "Thank you...I...I love you."

---

### Post by strabes on 2007-08-05
Opendns is the best.

---

### Post by Draylorre on 2007-08-05
> **strabes said:**
> Opendns is the best.

OpenDNS is my ***_[SIZE="5"]GOD[/SIZE]_***.

---

### Post by ZipoTe on 2007-08-05
glad to see openDNS solved your problem ^^

---

