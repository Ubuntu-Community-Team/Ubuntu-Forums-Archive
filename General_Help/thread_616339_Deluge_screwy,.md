---
title: "Deluge screwy,"
date: 2007-11-18
forum: General Help
---

### Post by leetrefz on 2007-11-18
I installed 7.10 and deluge, torrents pause for a second all the time and never show progress despite having download rates. tracker status goes ok- sent- timeout all the time. deluge refused to stay open for more than a second after reboot so I removed & reinstalled it, but same problems. Is it a bug or reed for router setup or what? It worked fine in mint on other computer through same router.

---

### Post by lightstream on 2007-11-18
what ports is deluge set to use? (preferences > network)

make sure whatever it's using is open (forwarded to your computer's local IP) in your router

(if you need to find your computer's local IP, right-click on the network icon in the um taskbar, and select 'Connection Information')

---

### Post by leetrefz on 2007-11-20
I'd like to set the prefs, but now despite having "completely removed" and reinstalled deluge it now won't open. Earlier I completely removed and reinstalled it and the old torrent was still listed. How can I get rid of that? then maybe after completely removing and reinstalling I can change prefs. 

Connection info is unselectable for me. Shouldn't be a problem tho.

---

### Post by leetrefz on 2007-11-20
All that was different in the settings between this and the deluge on a computer on same router that worked without setup was that extra mutorrent-pex was selected here.   not seeing any place for an IP. still behaving screwy.

actually maximum dl rate was auto set to -1 kbps! I turned this up just a bit but still screwy.

fox torrent hasn't been working either, My Lan module is a huge pain in the kaboose, usually have to boot 2ce to get a connection, Maybe not deluge's problem? Firefox is fine when the connection is, besides that plugin.

---

### Post by cknight on 2007-11-27
Apologies for the late reply, but give this a shot which worked for me when I couldn't open deluge, even after a reinstall.

```
rm ~/.config/deluge/persistent.state
```

---

### Post by leetrefz on 2007-11-29
i got it running ok but still doesn't really download anything, pausing all the time  & never progressing. might be the hardware.

---

### Post by Xtrmi on 2008-05-24
Nope mine does it also. It is a screwy program. friend told me it was good, but no thank you it just sucks imo. I need to figure out how to update azureus now.

---

