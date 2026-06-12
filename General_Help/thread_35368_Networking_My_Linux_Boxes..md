---
title: "Networking My Linux Boxes."
date: 2005-05-18
forum: General Help
---

### Post by persis on 2005-05-18
Been running Ubuntu for several months now - and passing it around to friends.  Seems to be spreading like a virus.

I have two computers  both running ubuntu (5.04) - got 'em connected to a wireless router that also feeds to my wireless laptops.  Wondering if there are any docs on how to setup my system so I can rsync and other perform other fun activities between all my computers?

Any good resources out there?

thanks -

---

### Post by sfw5000 on 2005-05-18
You probably want to check out the linux documentation project -- not sure if there is an ubuntu specific how-to, but you should set up NFS on all the computers. THis allows for sharing files between linux computers. Depending on how ambitious you feel, you could also set up NIS, which sets up a common user database among your computers so all accounts exist on all computers... for rsync you don't really have to set anything up, just read the rsync man page.

NFS hotwo: [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)
NIS Howto: [http://www.tldp.org/HOWTO/NIS-HOWTO/](http://www.tldp.org/HOWTO/NIS-HOWTO/)
Rsync basic info: [http://www.aplawrence.com/Basics/rsync.html](http://www.aplawrence.com/Basics/rsync.html)

---

### Post by persis on 2005-05-18
Thanks for the advice!  I'll look into it and get back to yas.

---

