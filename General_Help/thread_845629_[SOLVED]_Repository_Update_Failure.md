---
title: "[SOLVED] Repository Update Failure"
date: 2008-06-30
forum: General Help
---

### Post by Relysis on 2008-06-30
I have searched through many threads for a very long while, and either haven't come across an answer, or haven't understood the answer well enough.  There are apparently two problems with my repository updates.  I tried several different servers using Software Sources, and still the same result.  Here is the error:

Here is the error I get when I try to update:

```
GPG error: http://moblock-deb.sourceforge.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870BFailed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

I'm sure it's something simple, but I have tried to update keys, update repository info, etc.  Still no luck.  Thanks for the help.

-Update: Fixed first error by... reading.  Solution to Moblock update problem printed in plain view on their website.... sorry.  Still not able to fix the "Failed to fetch cdrom" error.

---

### Post by a94060 on 2008-06-30
well,according to that. Try to remove the moblock repositry, or go ahead to their site and install the gpg key for it. Disabling the cdrom from software sources should alleviate the problems with the cdrom


```

To let apt verify the integrity of the packages you have to add my gpg key to the apt keyring (may be optional depending on your system's settings):

gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -


```
Add the missing keys with that

---

### Post by Relysis on 2008-06-30
Ok as you said, that completely fixed the problem (and I feel like an idiot).  However, am I right in assuming that anything I installed from that repository will continue to be updated?  Dumb question; I just don't want to remove something I need just to remove an error.  Thanks for your fast reply!

---

### Post by soccerboy on 2008-06-30
if you installed something from a third-party repo and then removed the repo, the software installed won't be updated anymore until you add the repo back or update it manually.

---

### Post by jre on 2008-07-02
As I understand it Relysis added the GPG key but didn't remove the repository. so he will continue to get updates.

---

