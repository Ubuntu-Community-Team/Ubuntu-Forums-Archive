---
title: "foxmarks has taken over cpu"
date: 2007-05-18
forum: General Help
---

### Post by eroica on 2007-05-18
hello,
new to ubuntu (mostly a mandriva person) and today I decided to install the foxmarks addon to Firefox. Well as soon as I did this and tried to sync my cpu utilization went to a 100%. I removed the addon but utilization still periodically goes up to 100% and freezes computer making life very annoying. Googling this trouble I see i am not the only one who experienced the problem. Anybody know what files in FF I have to delete or settings to change? The cpu is split about 50/50 between FF & X server when this happens. Any help on how to regain control would be great. Here's a read of tail -F /var/log/messages
$ tail -f /var/log/messages
May 18 09:42:36 Dell1000 gconfd (eroica-5060): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 18 09:42:36 Dell1000 gconfd (eroica-5060): Resolved address "xml:readwrite:/home/eroica/.gconf" to a writable configuration source at position 1
May 18 09:42:36 Dell1000 gconfd (eroica-5060): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 18 09:42:36 Dell1000 gconfd (eroica-5060): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 18 09:42:36 Dell1000 gconfd (eroica-5060): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 18 09:42:45 Dell1000 gconfd (eroica-5060): Resolved address "xml:readwrite:/home/eroica/.gconf" to a writable configuration source at position 0
May 18 10:02:18 Dell1000 -- MARK --
May 18 10:22:18 Dell1000 -- MARK --
May 18 10:42:18 Dell1000 -- MARK --
May 18 11:02:45 Dell1000 -- MARK --

thanx...

---

### Post by eroica on 2007-05-21
just in case anybody runs across this problem what I did was create a new profile and that solved trouble. I saw from doing a about:config in FF that certain keys were still present for Foxmarks even after I had removed extension. Curiously I even moved bookmarks from old profile to new profile and that brought back trouble. This is one toxic extension....

---

