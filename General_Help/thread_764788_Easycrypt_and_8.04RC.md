---
title: "Easycrypt and 8.04RC"
date: 2008-04-24
forum: General Help
---

### Post by RagingAardvark on 2008-04-24
Hi folks,
I took the plunge and upgrade my Gutsy installation to 8.04RC and, for the most part, all is rosy and lovely.

However (!), when using easycrypt to access my truecrypt data, I get an error that the password I have entered is incorrect. 

A bit of digging about in these forums suggests that I'm not alone in this - but without explaining what is causing the problem. It also suggests using the truecrypt command line interface to open the volume.

Great, except how? The suggested "truecrypt -m" returns ;

MAPPED_VOLUME = DEVICE_NUMBER | DEVICE_NAME | MOUNT_POINT | VOLUME_PATH

... which means nothing to me. 

I then tried "truecrypt -m /media/crypt" which returned the same. 

As far as I can tell, the volume is still "there"(tm), but how can I get to it?

Any help would be _vastly_ appreciated.

KJ

---

### Post by RagingAardvark on 2008-04-24
I solved it myself! 

Copied the easycrypt volume to a backup location

Removed the old (4.something) truecrypt package

Installed the latest truecrypt (5.something) package

Used the truecrypt GUI to point to the backed-up file volume et voila!

(Thank fark for that!)

KJ:)

---

