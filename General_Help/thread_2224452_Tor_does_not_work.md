---
title: "Tor does not work"
date: 2014-05-16
forum: General Help
---

### Post by bazsound on 2014-05-16
Now the frustration is really pissing me off, especialy since i typed out a detailed post, go away to try a few more searches, to come back and ive been logged out! post lost

This login through another site is complete bollocks.

Anyway


simply put tor installed on 2 different machines with the same results.

Ive been through tons of pages tried different things only to mess torchat up even further.

Ive narrowed it down to the tor that is included with tor chat, as if i start tor with the tor.sh file it cannot connect to the tor network.

However i have tor installed on my system which works fine, its just torchats tor portable thing that is not working.
if i start tor from thje command line, it starts tor via tor.sh

May 16 14:37:56.382 [notice] Initialized libevent version 2.0.16-stable using method epoll. Good.
May 16 14:37:56.382 [notice] Opening Socks listener on 127.0.0.1:11109
May 16 14:37:56.386 [notice] Parsing GEOIP file /usr/share/tor/geoip.
May 16 14:37:56.617 [notice] OpenSSL OpenSSL 1.0.1 14 Mar 2012 looks like version 0.9.8m or later; I will try SSL_OP to enable renegotiation
May 16 14:37:56.653 [notice] I learned some more directory information, but not enough to build a circuit: We have no network-status consensus.
May 16 14:38:00.564 [warn] Received http status code 302 ("Moved Temporarily") from server '193.23.244.244:80' while fetching consensus directory.
May 16 14:38:06.511 [warn] We don't have a consensus, so we can't perform v2 rendezvous operations.
May 16 14:38:06.511 [warn] We don't have a consensus, so we can't perform v2 rendezvous operations.
May 16 14:38:06.511 [notice] Closing stream for '[scrubbed].onion': hidden service is unavailable (try again later).



tor chat opens, but it never connects, my user stays greyed out and friends dont see me online.

---

### Post by bazsound on 2014-05-17
apologies for the rant,

but spent 2 days trying to get it to work..

anywone any ideas the developer doent reply to emails

---

### Post by jim_deadlock on 2014-05-18
I've installed Tor and added the Torchat plugin for Pidgin and it's working like a charm. Did you properly install Tor to your system though - the instructions on the site don't include the final step which is 'make install'. So the full installation instructions are:

Install a couple of dependencies:

> sudo apt-get install libevent libssl-dev

Then go to your Tor source directory and do:

> ./configure && make && sudo make install

That will install Tor to /usr/local/bin and then Torchat will be able to find it and create a connection.

---

### Post by CaptainMark on 2014-05-18
I've got tor installed straight from the ubuntu repos, much easier

---

### Post by ejbiow on 2014-05-20
FWIW, the torproject site [recommends]("https://www.torproject.org/docs/debian.html.en") adding their own repository to Ubuntu to get the basic tor packages, apparently the version in universe is not reliably updated, though apparently Debian manage to backport important security fixes to its repository version.

---

