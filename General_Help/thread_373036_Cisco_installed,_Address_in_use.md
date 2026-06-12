---
title: "Cisco installed, Address in use"
date: 2007-02-28
forum: General Help
---

### Post by Dragonbite on 2007-02-28
Alright, after much grunting and huffing I got Cisco's vpnclient installed!  I've tried vpnc and Kvpnc and neither of them have worked and vpnclient has worked successfully before on my Gentoo installation.

[I]To my surprise, I was having problems installing vpnclient until I realized the system was trying to reference a directory that had a space, so it only grabbed the 2nd word and not the first word, then died because it could not find the directory! Whoops! After beating my head for weeks, I finally got past that step.
[/I]
Installing is not what I have a question about.

After running ```
sudo vpnclient connect *abcxyz*
```
I get
```
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Illegal seek
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Address already in use
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Address already in use
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Address already in use
Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.
```
I connect using a dial-up internet connection and I am tryin to connect to work so I can run remote desktop.

Any ideas?

---

### Post by Dragonbite on 2007-03-02
Would this be better in the Networking section? If so, how would i move it there, instead of creating duplicate threads?:guitar:

---

### Post by Dragonbite on 2007-03-07
Last night I found the culprit in getting my Cisco VPN  Client from working on my Windows 2000 machine.

Seems the Cisco doesn't like or work with my ZoneAlarm Firewall.  Shutting it down is not enough either, it has to be completely removed! #-o 

Once removed I was able to connect without a hitch. \\:D/ 

Since I don't like the idea of running Windows 2000 online (even dial-up) without protection, I started looking around for another free alternative and decided to try one of them; [Comodo]("http://www.personalfirewall.comodo.com/").

Works like a charm! So now I have a firewall AND I can connect to work via the VPN! :guitar: 

This doesn't answer WHY I cannot connect in Ubuntu, but the firewall may be a direction to look into.  If anybody has any ideas or suggestions on what to do with the firewall, please feel free to post!

---

