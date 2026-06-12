---
title: "gconfd error"
date: 2006-10-13
forum: General Help
---

### Post by pt123 on 2006-10-13
```
Oct 12 20:43:00 localhost hpiod: 0.9.7 accepting connections at 59692... 
Oct 12 20:43:14 localhost gconfd (nitro-5565): starting (version 2.14.0), pid 5565 user 'nitro'
Oct 12 20:43:14 localhost gconfd (nitro-5565): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct 12 20:43:14 localhost gconfd (nitro-5565): Resolved address "xml:readwrite:/home/nitro/.gconf" to a writable configuration source at position 1
Oct 12 20:43:14 localhost gconfd (nitro-5565): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct 12 20:43:14 localhost gconfd (nitro-5565): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct 12 20:43:14 localhost gconfd (nitro-5565): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct 12 20:43:22 localhost gconfd (nitro-5565): Resolved address "xml:readwrite:/home/nitro/.gconf" to a writable configuration source at position 0
Oct 12 20:55:25 localhost gconfd (root-6521): starting (version 2.14.0), pid 6521 user 'root'
Oct 12 20:55:25 localhost gconfd (root-6521): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct 12 20:55:25 localhost gconfd (root-6521): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Oct 12 20:55:25 localhost gconfd (root-6521): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct 12 20:55:25 localhost gconfd (root-6521): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct 12 20:55:25 localhost gconfd (root-6521): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct 12 20:59:55 localhost gconfd (root-6521): GConf server is not in use, shutting down.
Oct 12 20:59:55 localhost gconfd (root-6521): Exiting
Oct 12 23:36:15 localhost gconfd (nitro-5565): Exiting
```

When my computer boots up I get these msgs in the daemon log. I am thinking it is my internet connection causing this. But I dont remember seeing this in the logs a week before this. 

I always had trouble with connecting to the internet on Ubuntu. If there is no connection I always have to reboot and hope it connects.

Edit: I remember I used to get this error in the daemon log:
Oct  1 19:08:14 localhost gdm[5068]: gdm_auth_user_add: /home/nitro/.Xauthority is not owned by uid 1000.

On a thread it said to delete the file for this type of error, and I think I did this a week ago.

---

