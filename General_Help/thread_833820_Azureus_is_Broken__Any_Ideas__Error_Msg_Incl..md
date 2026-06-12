---
title: "Azureus is Broken?  Any Ideas?  Error Msg Incl."
date: 2008-06-18
forum: General Help
---

### Post by nuclearj on 2008-06-18
Hi I can't seen to get Azureus to work any more.  I deleted everything with Azureus on it and reinstalled it but that did not work.  When I tried to run in from the command line I got this error

```
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
[GUI] StartServer ERROR: unable to bind to 127.0.0.1:6880 listening for passed torrent info: Address already in use
StartSocket: passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]

```

I do not really know what any of that means. Would someone land a hand?

---

### Post by etnlIcarus on 2008-06-19
I'd make sure you completely remove and reinstall JRE and Azereus from the repositories and delete any java or Azureus related folders in /home/user and /home/user/.config


Frankly, I stopped using Azureus a long time ago on *nix due to constant problems. I'm not sure if it's still like that now but if you want a full-featured torrent client, I suggest Ktorrent for more advanced use or Deluge for basic downloading/seeding.

---

### Post by nuclearj on 2008-06-19
Thanks for the help etnlIcarus, what I ended up doing was use bittornado.  And I like it!  Thanks again!

---

### Post by cozmicharlie on 2008-06-19
I had the same problem - it happened with an Azureus update.  I have used Azureus for years with no problem then after this update I started getting the same error messages as nuclearj.  I tried everything suggested on this thread (reinstalled everything) and I could not fix it.  I assume it has something to do with the new Vuze format so I went into Synaptic and reinstalled the older 2.5 version and it works like a charm again.  Yes, I would agree, if all you need is basic bittorrent find another one to use.  I use Azureus because of all the great plugins and I have not found a substitute that can do all that Azureus does.  For those like me that want to use Azureus but are having problems with the new Vuze, my suggestion is go to Synaptic and install the older version.  Most likely this will eventually be fixed- at least I hope so(.

---

### Post by yammosk on 2008-09-26
Had the exact same problem and found a solution that worked for me in the archives: 


> tocnon
July 16th, 2006, 04:17 PM
the problem turned out to be related to the installation of the network-manager util. The "lo" interface was being shutdown without having the local 127.0.0.1 address assigned, therefore java could not open a listen port on this interface for 6880. I was able to fix the problem by reenabling the "lo" interface with these commands. I'll simply adjust the config for network-manager to make permanent:

/sbin/ifconfig lo 127.0.0.1
/sbin/route add -net 127.0.0.0 netmask 255.0.0.0 lo

You need sudo for those commands. After that everything worked fine. Haven't restarted yet, so I don't know if it's truly permanent or not. 


Cheers 

Yammosk

---

### Post by cozmicharlie on 2008-09-26
Thanks - I will give it a try

---

