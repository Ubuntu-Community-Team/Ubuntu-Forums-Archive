---
title: "A tor-browser question .... works then does not ....   and why? If anyone knows"
date: 2021-08-21
forum: General Help
---

### Post by shantiq on 2021-08-21
Downloaded the tor-browser bundle tor-browser-linux64-10.5.5_en-US.tar.xz

and unpacked to my home folder

Now i want this to be set to Spain although i am sitting in England

i set my nodes in torrc to

```
EntryNodes {es}
ExitNodes {es}
```

and start it again with  ```
./Browser/start-tor-browser --detach --verbose
``` in the folder and for 3 days perfect


Day 4 ....    no dice

So my question here is why would it stop?
And obviously how to correct it?

This is what it says in the terminal

```
./Browser/start-tor-browser --detach --verboseFontconfig warning: "/home/shan/tor-browser_en-US/Browser/TorBrowser/Data/fontconfig/fonts.conf", line 85: unknown element "blank"
Aug 21 07:14:29.594 [notice] Tor 0.4.5.10 (git-fd74f7628eba2525) running on Linux with Libevent 2.1.12-stable, OpenSSL 1.1.1k, Zlib 1.2.11, Liblzma N/A, Libzstd N/A and Glibc 2.31 as libc.
Aug 21 07:14:29.594 [notice] Tor can't help you if you use it wrong! Learn how to be safe at https://www.torproject.org/download/download#warning
Aug 21 07:14:29.594 [notice] Read configuration file "/home/shan/tor-browser_en-US/Browser/TorBrowser/Data/Tor/torrc-defaults".
Aug 21 07:14:29.594 [notice] Read configuration file "/home/shan/tor-browser_en-US/Browser/TorBrowser/Data/Tor/torrc".
Aug 21 07:14:29.595 [notice] Opening Control listener on 127.0.0.1:9151
Aug 21 07:14:29.595 [notice] Opened Control listener connection (ready) on 127.0.0.1:9151
Aug 21 07:14:29.595 [notice] DisableNetwork is set. Tor will not make or accept non-control network connections. Shutting down all existing connections.
Aug 21 07:14:29.000 [notice] Parsing GEOIP IPv4 file /home/shan/tor-browser_en-US/Browser/TorBrowser/Data/Tor/geoip.
Aug 21 07:14:29.000 [notice] Parsing GEOIP IPv6 file /home/shan/tor-browser_en-US/Browser/TorBrowser/Data/Tor/geoip6.
Aug 21 07:14:29.000 [notice] Bootstrapped 0% (starting): Starting
Aug 21 07:14:29.000 [warn] Your configuration excludes 99% of all possible guards. That's likely to make you stand out from the rest of the world.
Aug 21 07:14:29.000 [notice] Starting with guard context "restricted"
Aug 21 07:14:29.000 [notice] Delaying directory fetches: DisableNetwork is set.
Aug 21 07:14:29.000 [notice] New control connection opened from 127.0.0.1.
Aug 21 07:14:29.000 [notice] DisableNetwork is set. Tor will not make or accept non-control network connections. Shutting down all existing connections.
Aug 21 07:14:29.000 [notice] New control connection opened from 127.0.0.1.
Aug 21 07:14:30.000 [notice] New control connection opened from 127.0.0.1.
Aug 21 07:14:30.000 [notice] New control connection opened from 127.0.0.1.
Fontconfig warning: "/home/shan/tor-browser_en-US/Browser/TorBrowser/Data/fontconfig/fonts.conf", line 85: unknown element "blank"
Aug 21 07:14:30.000 [notice] New control connection opened from 127.0.0.1.
Aug 21 07:14:30.000 [notice] Opening Socks listener on 127.0.0.1:9150
Aug 21 07:14:30.000 [notice] Opened Socks listener connection (ready) on 127.0.0.1:9150
Aug 21 07:14:30.000 [notice] Bootstrapped 5% (conn): Connecting to a relay
Aug 21 07:14:30.000 [notice] Bootstrapped 10% (conn_done): Connected to a relay
Aug 21 07:14:31.000 [notice] Bootstrapped 14% (handshake): Handshaking with a relay
Fontconfig warning: "/home/shan/tor-browser_en-US/Browser/TorBrowser/Data/fontconfig/fonts.conf", line 85: unknown element "blank"
Aug 21 07:14:31.000 [notice] Bootstrapped 15% (handshake_done): Handshake with a relay done
Aug 21 07:14:31.000 [notice] Bootstrapped 45% (requesting_descriptors): Asking for relay descriptors
Aug 21 07:14:31.000 [notice] I learned some more directory information, but not enough to build a circuit: We need more microdescriptors: we have 6701/6715, and can only build 0% of likely paths. (We have 100% of guards bw, 99% of midpoint bw, and 0% of exit bw = 0% of path bw.)
Aug 21 07:14:31.000 [notice] Bootstrapped 50% (loading_descriptors): Loading relay descriptors





```
TI have read around this and tried a few things but still not happening

Anyone with experience could kindly advise please?


Thanx

shan


PS    i have also tried it with au (australia)   and it worked fine but no longer does
if i set it to fr (france)   it works fine  ...the terminal output is TOTALLY different in each case


PS2 also did [reset time]("https://askubuntu.com/questions/81293/what-is-the-command-to-update-time-and-date-from-internet") and verified [signature]("https://support.torproject.org/tbb/how-to-verify-signature/")

---

### Post by shantiq on 2021-08-23
anyone? any clever suggestions?


thanx

---

### Post by ActionParsnip on 2021-08-23
What is the output of
```

lsb_release -a; uname -a

```
Thanks

---

### Post by ActionParsnip on 2021-08-23
This looks pretty good. Seems they have a repository
[https://ubuntuhandbook.org/index.php/2021/01/install-tor-tor-browser-ubuntu-20-10-20-04/](https://ubuntuhandbook.org/index.php/2021/01/install-tor-tor-browser-ubuntu-20-10-20-04/)

---

### Post by shantiq on 2021-08-23
```
lsb_release -a; uname -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal



```


which can be seen on my profile
I asked for hopefully specialist help here not vague around the topic offerings :o
apologies if i missed something

---

