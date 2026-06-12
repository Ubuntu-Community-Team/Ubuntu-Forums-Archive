---
title: "Any caveats before sharing /home dirs over NFS?"
date: 2007-03-16
forum: General Help
---

### Post by isync on 2007-03-16
I intend to share the complete /home directory tree via NFS (and SAMBA) over a local network. Are there any caveats, warnings or things to keep in mind before doing this?

So far I had only shared the dir /home/forall under the /home branch, but I will now set up central mail for all and thus it would be helpful to have real permission-controlled homedirs in use again (btw: cyrus imap-daemon).

One important! thing that might rise problems is that sometimes a user is logged in on multiple machines running firefox/mozilla (which stores it's bookmarks, history, etc. by default in ".hiddenfile" files in the /home/userdir path). Will mozilla complain about conflicts?

Will I crash my systems?? (so many questions...)

---

### Post by isync on 2007-03-16
Anyone?

(or are there no caveats?? ;-)  )

---

