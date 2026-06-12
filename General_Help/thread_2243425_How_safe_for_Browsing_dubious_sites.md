---
title: "How safe for Browsing dubious sites?"
date: 2014-09-08
forum: General Help
---

### Post by FerryGnu on 2014-09-08
Hi All, I just spent a day and a half rebuilding my win8.0 laptop after using a shortened (Bitly) link that hammered my system within seconds of landing there. Had to reinstall win8.0 and then install some 35 applications and backed up data. NOT fun.

So, I have just installed VMWare Player and Ubuntu and will use Firefox for those dubious links in future. Being VERY gun-shy right now, just how safe is this going to be with Player/Ubuntu/Firefox?

Before using the Guest system, I will make a copy and if I ever get hammered again, I can just overwrite the Guest with the backup.

The irritating part is the Bitly link was on a Professional Engineering site I have been using for years.

Thanks

---

### Post by TheFu on 2014-09-08
Linux isn't any safer than Windows.  The best tool is your brain.  Practice defensive web browsing and don't click on links that you don't know where they land.  Basically - NO link shorteners are safe.

For desktop users, security practices are about the same across every OS.

---

### Post by MrSteve on 2014-09-08
it would help if you could give some details on how your win system was hammered
ie virus, highjack was any exe file downloaded ? ...

---

### Post by CaptainMark on 2014-09-09
The safest thing you could possibly do is to install qubes in virtualbox, I dont expect you could cause any damage if you tried through that, just if you want to test a strange link, it would be slow for everyday browsing

---

### Post by whitesmith on 2014-09-09
One reasonably safe way to browse dubious sites is to install VirtualBox. A windows application running in that environment only has access to the local sandbox, not the host OS (Linux). Interprocess communications between the two are virtually nonexistent, so a virus has nowhere to go. If you pick something up, just delete that VM and return to the clean, original version you started with.

---

