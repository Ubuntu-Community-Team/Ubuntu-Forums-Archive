---
title: "Bit Torrent client - &quot;Address already in use&quot;"
date: 2006-11-01
forum: General Help
---

### Post by JedTheHead on 2006-11-01
In previous versions of Ubunutu I could have multiple Bit Torrents coming in at once with the default Bit Torrent / Gnome client.  I prefer to use this client for my own reasons, but in Edgy, I can only have one downloading at a time.  When I attempt to start other torrents, I receive a "98, Address already is use" error.  What changed?

Thanks!!!

---

### Post by raydar on 2006-11-02
I have the same problem, starting as soon as I upgraded (via Synaptic) from Dapper to Edgy.

I've noticed that if I have one torrent open and stop it, I can successfully open another.

---

### Post by pzonik on 2006-11-02
> **JedTheHead said:**
> In previous versions of Ubunutu I could have multiple Bit Torrents coming in at once with the default Bit Torrent / Gnome client.  I prefer to use this client for my own reasons, but in Edgy, I can only have one downloading at a time.  When I attempt to start other torrents, I receive a "98, Address already is use" error.  What changed?

Thanks!!!

I have the same problem, please help.

---

### Post by klato on 2006-11-02
Ditto over here..

---

### Post by rsambuca on 2006-11-03
I had the same problem as well, so I just used the "Add/Remove Applications" and installed the Bittornado client.  Doesn't really fix the original problem, but the install only takes a minute or so and it works with multiple torrents running at once.

---

### Post by pzonik on 2006-11-03
> **rsambuca said:**
> I had the same problem as well, so I just used the "Add/Remove Applications" and installed the Bittornado client.  Doesn't really fix the original problem, but the install only takes a minute or so and it works with multiple torrents running at once.

Ok, but this is only advice, not solution. I'm interesting what is source of this problem.

---

### Post by klato on 2006-11-03
I'd also like to find the solution to this (then again, I'd also like an Azureus from the repos that works properly ;-)

---

### Post by dannyboy79 on 2006-11-03
> **pzonik said:**
> Ok, but this is only advice, not solution. I'm interesting what is source of this problem.

why don't you go into synaptic and view the version number of the torrent client and see if it differs from the one  in dapper? if it does, then why don't you uninstall it and install the version that works for you, if it's the same, then apparently some settings got changed, have you looked at any config files for the client to see if 1 is the max amount of torrents that can be run at a time? I personally agree with the other guy, Download bittornado and use that, I think that client is way more flexible that the default client. i didn't use the one in the repo's though, I went for the latest and greatest and installed that one.

---

### Post by Peter76 on 2006-11-03
Hi, this is a bug in edgy; I gave a solution here:

[http://www.ubuntuforums.org/showthread.php?t=286702](http://www.ubuntuforums.org/showthread.php?t=286702)

Good luck

---

### Post by zachtib on 2006-11-03
> **klato said:**
> I'd also like to find the solution to this (then again, I'd also like an Azureus from the repos that works properly ;-)

Impossible, it's written in Java

*ducks*

;)

---

### Post by klato on 2006-11-03
Weird thing is that the version in the edgy repos is the version displayed on the azureus page...and yet the systray bug is still present as it was in the dapper version (2.4.0.3 or something)

Yet, when installing the very same version from the tar instead, azureus works fine.

---

### Post by simmo35 on 2007-05-25
> **Peter76 said:**
> Hi, this is a bug in edgy; I gave a solution here:

[http://www.ubuntuforums.org/showthread.php?t=286702](http://www.ubuntuforums.org/showthread.php?t=286702)

Good luck

Thanks ... this fixed it beautifully.

---

