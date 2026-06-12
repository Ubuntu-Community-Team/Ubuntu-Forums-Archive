---
title: "Wifi signal scanner,"
date: 2013-02-03
forum: General Help
---

### Post by CaptainMark on 2013-02-03
I have two routers and I'm trying to figure out which gives the best signal strength around my house, basically I plan to plug them both in and walk around on a laptop reading the signal strength.  Is there a wifi scanner utility that shows all detected wireless networks in real-time and their current signal strength. I vaguely remember aircrack-ng having such a tool (airmon??) but I can't seem to install it now, is there something else that does this?

Regards

---

### Post by Cheesemill on 2013-02-03
How about...
```
watch cat /proc/net/wireless
```

---

### Post by Rebelli0us on 2013-02-03
Use synaptic to install hardinfo. Then go network > interfaces, gives you live reading on signal strength.

---

### Post by haqking on 2013-02-03
> **CaptainMark said:**
> I have two routers and I'm trying to figure out which gives the best signal strength around my house, basically I plan to plug them both in and walk around on a laptop reading the signal strength.  Is there a wifi scanner utility that shows all detected wireless networks in real-time and their current signal strength. I vaguely remember aircrack-ng having such a tool (airmon??) but I can't seem to install it now, is there something else that does this?

Regards

I think you meant airodump-ng

Anyways there are tons.

Kismet is my personal preference.

Peace

---

### Post by Zill on 2013-02-03
iwScanner is a wireless scanner for linux with an easy to use graphic interface.

I use v0.2.4 on Ubuntu Lucid (10.04) and it works well.  However, it isn't yet in the repos so you would need to download the deb and then install with GDebi:
[LIST]
[*][http://www.kuthulu.com/iwscanner]("http://www.kuthulu.com/iwscanner")
[/LIST]

Caveat: because I don't use any later Ubuntu releases than Lucid I cannot confirm that iwScanner will work with these.  My guess is it *should* work OK but no guarantees. ;-)

---

### Post by CaptainMark on 2013-02-03
I've continued digging and found wavemon its a curses based program that does exactly what I need, thanks for the suggestions though

---

