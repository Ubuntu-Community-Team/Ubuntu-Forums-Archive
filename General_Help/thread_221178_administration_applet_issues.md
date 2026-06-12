---
title: "administration applet issues"
date: 2006-07-22
forum: General Help
---

### Post by alaman on 2006-07-22
ok, I must really be missing something here - not critcial but my system->administration applets that require sudo don't seem to be working.  My password is taken, but the screen never fills in any data.  If I run sudo gksu services-admin in a terminal it just hangs and I get this log entry -->

Jul 22 16:48:58 laptop gconfd (root-6864): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 22 16:48:58 laptop gconfd (root-6864): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 22 16:48:58 laptop gconfd (root-6864): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 22 16:48:58 laptop gconfd (root-6864): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 22 16:49:28 laptop gconfd (root-6864): GConf server is not in use, shutting down.
Jul 22 16:49:28 laptop gconfd (root-6864): Exiting

Other sudo commands work, just not the ones that launch the admin applets.  I've check sudoers and groups (though I had "groups" and "groups-" and I don't know the difference) and they appear to be correct.  Any ideas?  Thanks.

---

### Post by scxtt on 2006-07-22
just cause i'm curious, why are you using both sudo and gksu?

[color=red]sudo[/color] [color=blue]gksu[/color] services-admin

just use **gksudo services-admin** ...

---

### Post by alaman on 2006-07-22
ah, thanks - I was mess'n that up...I now get an authentication error.

(services-admin:7215): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

but it never prompted me for a password this time.

---

### Post by scxtt on 2006-07-22
it stores your sudo password for a period of time, maybe 5 mintes - before it asks again ... so if you've entered it recently, it shouldn't ask you ...

not sure what to do about your new error tho :( - almost seems like a hostname problem ...

---

