---
title: "Seahorse ldap error"
date: 2006-10-31
forum: General Help
---

### Post by DoomedTX on 2006-10-31
I am using Seahorse 0.9.5 on Edgy. Whenever I try to sync a key with ldap://keyserver.pgp.com I get the following message:
```

Couldn't publish keys to server: ldap://keyserver.pgp.com

entry has no objectClass attribute
```

There's a [bug]("http://bugzilla.gnome.org/show_bug.cgi?id=351969") on Gnome's bugzilla, but the developer reports that he doesn't see the error and it's: [QUOTE="Nate Nielsen"]Probably something to do with how openldap is installed on your machine. You should look at configure.in and see how it can be changed to detect your installation properly.[/QUOTE]

Any ideas how to fix this without recompiling seahorse?

---

### Post by AtrejuT on 2007-03-17
Has ther been any solution to this?
I have this problem on Feisty after having installed seahorse.
When I try to publish to hkp://pgp.mit.edu:11371 I also get an error:
Error decoding keyblock

so I can publish to neither ldap nor http servers... :-(

atreju

---

### Post by david.rahrer on 2007-04-18
I'm getting the same error as the OP.  Does anyone do this successfully?

---

### Post by Cherry Cotton on 2007-06-04
I'm getting the same two errors. So, yes, any help would be appreciated!

---

### Post by russell.sim on 2008-07-22
I think this could be related to this bug [http://bugzilla.gnome.org/show_bug.cgi?id=351966]("http://bugzilla.gnome.org/show_bug.cgi?id=351966") regarding the use of images in keys not working with older servers like the mit one. I removed the image from my key and it's working for me now.

---

