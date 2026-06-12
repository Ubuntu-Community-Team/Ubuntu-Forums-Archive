---
title: "Setting up a proxy with Ubuntu 11.04"
date: 2015-01-04
forum: General Help
---

### Post by Peter_Nagel on 2015-01-04
Hi there,

I am extremely new to Ubuntu. I just ordered a VPS and accessed it by using PuTTY. I have been following this guide:
[http://www.ownedcore.com/forums/world-of-warcraft/world-of-warcraft-bots-programs/351393-guide-complete-guide-having-unique-ip-wow-battle-net-safe-botting.html](http://www.ownedcore.com/forums/world-of-warcraft/world-of-warcraft-bots-programs/351393-guide-complete-guide-having-unique-ip-wow-battle-net-safe-botting.html)

It explains how to setup a proxy. However when I try to install squid I get the following error:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/squid-langpack/s](http://us.archive.ubuntu.com/ubuntu/pool/main/s/squid-langpack/s)                                                                                                                                                             quid-langpack_20110214-1_all.deb  404  Not Found [IP: 91.189.91.24 80]


Is that happening because Ubuntu 11.04 is too old? How can I fix this? I could install Ubuntu 14.04 but then the guide isn't working anymore. Is there perhaps another guide to explains step by step to setup a proxy?

Hopefully you guys can help me!

Thanks!

---

### Post by Impavidus on 2015-01-04
Yes, 11.04 is too old (and not very secure). I didn't read your guide, but most things haven't changed too much.

---

### Post by Peter_Nagel on 2015-01-04
Thanks for your reply. I've upgraded  to 14.04 x86

I still have the same error though([COLOR=#333333][FONT=arial] Error writing /etc/squid/squid.conf: No such file or directory )[/FONT][/COLOR], when I try to safe the custom config file provided in the guide (which is here: [http://pastebin.com/zHZ6VFzr](http://pastebin.com/zHZ6VFzr)). So I can't safe it as it doesn't exist, and there lies my problem. Also when I try to restart it with this command: [COLOR=#333333]/etc/init.d/squid restart [/COLOR]I get the same error. So  I guess the guide is outdated?

[COLOR=#333333][FONT=arial]
[/FONT][/COLOR]

---

### Post by Peter_Nagel on 2015-01-04
[FONT=Georgia, Utopia, Palatino Linotype, Palatino, serif][COLOR=#000000]Seems like the error can be fixed (I think) by installing Squid 2.7. 

So I download this:
[/COLOR][/FONT][COLOR=#000000][FONT=Georgia]wget [http://www.squid-cache.org/Versions/v2/2.7/squid-2.7.STABLE9.tar.bz2](http://www.squid-cache.org/Versions/v2/2.7/squid-2.7.STABLE9.tar.bz2)

How do I install it? It's in the root directory and then there is that file. 

Sorry I am very new to this :P[/FONT][/COLOR]

---

