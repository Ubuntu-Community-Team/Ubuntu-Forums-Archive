---
title: "tor keeps restarting"
date: 2015-12-08
forum: General Help
---

### Post by hunterkasy on 2015-12-08
I installed tor using the instructions from tor's site.  I am running ubuntu 15.10 64  I would like to be able to get tor running and stable. 

Thanks

> Nov 26 21:32:36.000 [notice] Tor 0.2.7.5 (git-6184c873e90d93b2) opening log file.
Nov 26 21:32:36.183 [warn] OpenSSL version from headers does not match the version we're running with. If you get weird crashes, that might be why. (Compiled with 1000106f: OpenSSL 1.0.1f 6 Jan 2014; running with 1000204f: OpenSSL 1.0.2d 9 Jul 2015).
Nov 26 21:32:36.237 [notice] Tor v0.2.7.5 (git-6184c873e90d93b2) running on Linux with Libevent 2.0.21-stable, OpenSSL 1.0.2d and Zlib 1.2.8.
Nov 26 21:32:36.237 [notice] Tor can't help you if you use it wrong! Learn how to be safe at [https://www.torproject.org/download/download#warning](https://www.torproject.org/download/download#warning)
Nov 26 21:32:36.238 [notice] Read configuration file "/usr/share/tor/tor-service-defaults-torrc".
Nov 26 21:32:36.238 [notice] Read configuration file "/etc/tor/torrc".
Nov 26 21:32:36.244 [notice] Based on detected system memory, MaxMemInQueues is set to 5987 MB. You can override this by setting MaxMemInQueues by hand.
Nov 26 21:32:36.244 [notice] Opening Socks listener on 127.0.0.1:9050
Nov 26 21:32:36.245 [notice] Opening Control listener on /var/run/tor/control
Nov 26 21:32:36.245 [notice] Opening OR listener on 0.0.0.0:443
Nov 26 21:32:36.245 [notice] Opening Directory listener on 0.0.0.0:9030
Nov 26 21:32:36.000 [notice] Parsing GEOIP IPv4 file /usr/share/tor/geoip.
Nov 26 21:32:36.000 [notice] Parsing GEOIP IPv6 file /usr/share/tor/geoip6.
Nov 26 21:32:36.000 [notice] Configured to measure statistics. Look for the *-stats files that will first be written to the data directory in 24 hours from now.
Nov 26 21:32:36.000 [notice] Your Tor server's identity key fingerprint is 'hunterkasy C5A339B69A17A8F9C177D1582578A3CC08298A4E'
Nov 26 21:32:36.000 [notice] Bootstrapped 0%: Starting
Nov 26 21:32:39.000 [notice] Bootstrapped 80%: Connecting to the Tor network
Nov 26 21:32:39.000 [warn] Unable to send readiness to systemd: Unknown error -13
Nov 26 21:32:40.000 [notice] Bootstrapped 85%: Finishing handshake with first hop
Nov 26 21:32:41.000 [notice] Bootstrapped 90%: Establishing a Tor circuit
Nov 26 21:32:41.000 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Nov 26 21:32:41.000 [notice] Bootstrapped 100%: Done
Nov 26 21:34:36.000 [notice] Interrupt: we have stopped accepting new connections, and will shut down in 30 seconds. Interrupt again to exit now.
Nov 26 21:35:06.000 [notice] Clean shutdown finished. Exiting.

---

### Post by Ricardo_Velasco on 2015-12-08
Greetings

Could you send me the link from where you followed the instructions to install the program ?.

Because according to what I saw , no installation is required to run the program ? ..

I send him because the operating system is rebooted:


> Nov 26 21:32:36.000 [notice] Tor 0.2.7.5 (git-6184c873e90d93b2) opening log file.

Nov 26 21:32:36.183 [warn] OpenSSL version from headers does not match 
the version we're running with. If you get weird crashes, that might be 
why. (Compiled with 1000106f: OpenSSL 1.0.1f 6 Jan 2014; running with 
1000204f: OpenSSL 1.0.2d 9 Jul 2015).

Nov 26 21:32:36.237 [notice] Tor v0.2.7.5 (git-6184c873e90d93b2) running
 on Linux with Libevent 2.0.21-stable, OpenSSL 1.0.2d and Zlib 1.2.8.

Nov 26 21:32:36.237 [notice] Tor can't help you if you use it wrong! Learn how to be safe at [https://www.torproject.org/download/download#warning](https://www.torproject.org/download/download#warning)

Nov 26 21:32:36.238 [notice] Read configuration file "/usr/share/tor/tor-service-defaults-torrc".

Nov 26 21:32:36.238 [notice] Read configuration file "/etc/tor/torrc".

Nov 26 21:32:36.244 [notice] Based on detected system memory, 
MaxMemInQueues is set to 5987 MB. You can override this by setting 
MaxMemInQueues by hand.

Nov 26 21:32:36.244 [notice] Opening Socks listener on 127.0.0.1:9050

Nov 26 21:32:36.245 [notice] Opening Control listener on /var/run/tor/control

Nov 26 21:32:36.245 [notice] Opening OR listener on 0.0.0.0:443

Nov 26 21:32:36.245 [notice] Opening Directory listener on 0.0.0.0:9030

Nov 26 21:32:36.000 [notice] Parsing GEOIP IPv4 file /usr/share/tor/geoip.

Nov 26 21:32:36.000 [notice] Parsing GEOIP IPv6 file /usr/share/tor/geoip6.

Nov 26 21:32:36.000 [notice] Configured to measure statistics. Look for 
the *-stats files that will first be written to the data directory in 24
 hours from now.

Nov 26 21:32:36.000 [notice] Your Tor server's identity key fingerprint is 'hunterkasy C5A339B69A17A8F9C177D1582578A3CC08298A4E'

Nov 26 21:32:36.000 [notice] Bootstrapped 0%: Starting

Nov 26 21:32:39.000 [notice] Bootstrapped 80%: Connecting to the Tor network

Nov 26 21:32:39.000 [warn] Unable to send readiness to systemd: Unknown error -13

Nov 26 21:32:40.000 [notice] Bootstrapped 85%: Finishing handshake with first hop

Nov 26 21:32:41.000 [notice] Bootstrapped 90%: Establishing a Tor circuit

Nov 26 21:32:41.000 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.

Nov 26 21:32:41.000 [notice] Bootstrapped 100%: Done

[B]Nov 26 21:34:36.000 [notice] Interrupt: we have stopped accepting new 
connections, and will shut down in 30 seconds. Interrupt again to exit 
now.[/B]

Nov 26 21:35:06.000 [notice] Clean shutdown finished. Exiting.


I send you the link where you just have to download and unzip .


Really do not understand , please explain to me better as you installed :)



[URL="https://www.torproject.org/dist/torbrowser/5.0.4/tor-browser-linux64-5.0.4_en-US.tar.xz"]https://www.torproject.org/dist/torbrowser/5.0.4/tor-browser-linux64-5.0.4_en-US.tar.xz







[/URL]

---

### Post by hunterkasy on 2015-12-08
I followed the instructions below, installed just fine.

[https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)

You need to add the following entry in /etc/apt/sources.list or a new file in /etc/apt/sources.list.d/:

    deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) wily main
    deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) wily main

Then add the gpg key used to sign the packages by running the following commands at your command prompt:

    gpg --keyserver keys.gnupg.net --recv 886DDD89
    gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

You can install it with the following commands:

    $ apt-get update
    $ apt-get install tor deb.torproject.org-keyring

---

### Post by Ricardo_Velasco on 2015-12-09
Greetings:

You could download the file that you send and unzip it. ?

Then open it without installing it , maybe you can make it work.

If this is not the case , please put a comment .

---

