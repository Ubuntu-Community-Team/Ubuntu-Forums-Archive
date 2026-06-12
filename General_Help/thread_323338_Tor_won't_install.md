---
title: "Tor won't install"
date: 2006-12-21
forum: General Help
---

### Post by shanepardue on 2006-12-21
I only get error messages with this install attempt. no other package has a problem. I'm running Kubuntu Edgy on a dual-core intel with a wireless connection if that helps.
```
sudo apt-get install tor privoxy
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  tsocks
Suggested packages:
  mixmaster mixminion anon-proxy
Recommended packages:
  socat
The following NEW packages will be installed:
  privoxy tor tsocks
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1847kB of archives.
After unpacking 4366kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package privoxy.
(Reading database ... 107564 files and directories currently installed.)
Unpacking privoxy (from .../privoxy_3.0.3-2-1_i386.deb) ...
Selecting previously deselected package tsocks.
Unpacking tsocks (from .../tsocks_1.8beta5-2_i386.deb) ...
Selecting previously deselected package tor.
Unpacking tor (from .../tor_0.1.1.23-1_i386.deb) ...
Setting up privoxy (3.0.3-2-1) ...
Starting filtering proxy server: invoke-rc.d: initscript privoxy, action "start" failed.
dpkg: error processing privoxy (--configure):
 subprocess post-installation script returned error exit status 1
Setting up tsocks (1.8beta5-2) ...
Setting up tor (0.1.1.23-1) ...
debian-tor uid check: ok
debian-tor homedir check: ok
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
Dec 21 22:24:36.407 [notice] Tor v0.1.1.23. This is experimental software. Do not rely on it for strong anonymity.
Dec 21 22:24:36.408 [notice] Initialized libevent version 1.1a using method epoll. Good.
Dec 21 22:24:36.408 [notice] connection_create_listener(): Opening Socks listener on 127.0.0.1:9050
Dec 21 22:24:36.408 [warn] connection_create_listener(): Could not bind to 127.0.0.1:9050: Cannot assign requested address
Dec 21 22:24:36.408 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Dec 21 22:24:36.408 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error processing tor (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 privoxy
 tor
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by shanepardue on 2006-12-22
I know that's a long post for a little error, but I'm not sure if it's a package issue or what. Any idea 
what kind of problem it even is?

---

### Post by Dr. Nick on 2006-12-22
EDIT

Try opening synaptic and searching tor and privoxy and completely removing them by right clicking and "mark for complete removal"

I had issues in the past with old versions/installs messing any new ones up. After removing try again and see if it works.

---

### Post by shanepardue on 2006-12-23
I have purged both packages, but I still get the same problem. I've even searched for any files with the words "tor" or "privoxy", nothing. I'd really like to get this machine on the tor network. My desktops are and I like it a lot.

---

### Post by shanepardue on 2006-12-23
It works! I don't know how, but it works! There have been a few changes in the way I network in my 
house recently and I'm wondering if that's what did it. I was on a WPA2 setup, but unfortunately I 
had to downgrade to WEP due to knetworkmanager giving me a headache. I may get WPA2 
figured out at a later time, but no idea why tor installed properly this time. Thanks though!

---

### Post by Dr. Nick on 2006-12-23
Glad you got it, it was flaky for me aswell. I just reinstalled so i get to try again now lol.

---

