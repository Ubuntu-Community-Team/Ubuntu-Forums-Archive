---
title: "Automatic Hostname Resolution"
date: 2005-06-15
forum: General Help
---

### Post by douceur on 2005-06-15
Is there anyway to setup Ubuntu to act more like Windows, as far as hostnames are concerned?  For instance, with a network of Windows PCs, if there is a computer named "blah", you can type "ping blah", and it just works.  Similarly, you can access its shares by going to "\\blah".  I know this is possible by editing /etc/hosts, but I'm wondering if there's a way to make it automatic like Windows does.

---

### Post by desdinova on 2005-06-15
How many windows pc in your network?

---

### Post by douceur on 2005-06-15
[QUOTE=desdinova]How many windows pc in your network?[/QUOTE]

In my network?  Seven.  But how is that relevant?  I would want this to work between Linux PCs, too.

Edit:  I didn't mean to sound like an ass.  I may well be relevant, I just don't understand how.  If it is, I'd certainly like it explained to me.  But either way, sorry if that sounded harsh.  I definitely didn't mean it that way.

---

### Post by douceur on 2005-06-18
Anybody?

---

### Post by blind0wl on 2005-06-20
Add the hostname and their IP's to your /etc/hosts file

Cheers

Blindy

---

### Post by douceur on 2005-06-20
[QUOTE=blind0wl]Add the hostname and their IP's to your /etc/hosts file[/QUOTE]

As I'd mentioned, I realize it's possible to do it this way, but I'm wondering if there's a more "automatic" way to do it, like Windows does.

---

### Post by doclivingston on 2005-06-21
The easiest way I've found to do it, is to use mDNS - which is part of ZeroConf networking (aka revdevous/bonjour). It is built in to recent version of Mac OS X, and you can download the Windows version of Bonjour from Apple's site.

To get it to work on a Ubuntu system you need to:

a) install libnss-mdns and mdnsresponder.
b) edit /etc/nsswitch.conf, and append "mdns4" to the end of the "hosts:" line
c) make mdnsresponder automatically start when you computer boots (manually, using BUM, or whatever)

Once you've done this you should be able to use names like "computername.local"

---

### Post by douceur on 2005-07-12
Thanks a lot.  It works great, except that when I've got Firestarter running, it won't work at all.  I've got all outbound traffic allowed, and I allow all local connections.  Yet it doesn't work with the firewall enabled.  For comparison sake, all other local connections *are* allowed.  Any ideas?

Edit:  To clarify, other computers can ping me, but I can't ping them.  I get the error "sendmsg() failed: Operation not permitted"

---

### Post by sciurus on 2005-12-14
See [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

---

