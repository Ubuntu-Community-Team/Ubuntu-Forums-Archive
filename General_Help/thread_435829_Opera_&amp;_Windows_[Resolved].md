---
title: "Opera &amp; Windows [Resolved]"
date: 2007-05-07
forum: General Help
---

### Post by Gorlist on 2007-05-07
Hi, quick question in regards to the Opera Web Browser - currently I have all my emails/favorites etc on Windows, is it possible to redirect Ubuntu's Opera Install to use the data files on my Windows drive (hda1), allowing access to emails regardless of what OS im in?

Regards!

---

### Post by asipi on 2007-05-08
maybe yes, but not on an ntfs partition because ubuntu does not have built-in ntfs writing support, however u can solve it also (try google for ntfs writing under linux)

---

### Post by kenmiles on 2007-05-08
> **Gorlist said:**
> Hi, quick question in regards to the Opera Web Browser - currently I have all my emails/favorites etc on Windows, is it possible to redirect Ubuntu's Opera Install to use the data files on my Windows drive (hda1), allowing access to emails regardless of what OS im in?

Regards!
Opera config -
[http://www.opera.com/support/search/view/340/](http://www.opera.com/support/search/view/340/)
and change the path for mail

Regards, Kenneth.

---

### Post by Gorlist on 2007-05-08
Great, thanks for the replies, so now I just need to make Ubuntu NTSF write :)

Regards!

---

### Post by Gorlist on 2007-05-09
Right just to update this thread, I now have Opera working fine on both Windows and Ubuntu whilst sharing emails. 

NTSF write was easy to setup, installed Opera through the package manager, and edited the according config. 

Thanks for the help,

---

