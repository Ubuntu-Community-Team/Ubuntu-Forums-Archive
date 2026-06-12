---
title: "No installable packages even after update on all comps at house"
date: 2008-01-20
forum: General Help
---

### Post by dieselpower on 2008-01-20
Long story short, about three weeks ago I stopped getting updates, and didn't really think anything about it until I wanted to get KDE 4. I removed KDE 4 beta 3 and in the process lost KDM and Konqueror. I am not able to reinstall either of them (package not available). I get BADSIG errors when updating and cannot get them to go away even with adding the no-cache and badproxy options to apt. I figured it was my installation that went south so I reinstalled and SAME PROBLEM! I'm on dialup (netease.net) and all I can figure is they added some filter or proxy about three weeks ago that affects me. I NEED thunderbird installed by noon tomorrow because I have an important business meeting, So, I have a couple of options, one is to deal with dep hell and install manually, and the other is to set up a VPN from my VPS server to my home dialup server, Could someone walk me through this? I have messed with OpenVPN before without success, but from what I can figure I need to somehow do the following.
[LIST]
[*]do nat from eth0 to the VPN (tun0?) on the remote server
[*]get a VPN link up with some sort of keepalive between the two servers. I'd like compression too. Don't really care about encryption at this point.
[*]Switch the GW on my dialup server from my current provider to the main server's VPN IP 
[*]Hopefully not screw my dialup server crazy in the process so I can still google for problems
[*] do an update and hope things become installable...
[/LIST]
So, HEEELP!!!!
Any good ideas? You will forever be my friend!

Lawrence

---

