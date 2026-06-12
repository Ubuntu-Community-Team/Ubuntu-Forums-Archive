---
title: "Later version of kernel installed that linux-generic depends on; can't update"
date: 2013-05-07
forum: General Help
---

### Post by andygraybeal on 2013-05-07
Hi, this box has 12.04 installed.

I'm getting the error:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.37.44) but 3.2.0.41.59 is installed

It asks me to do apt-get -f install and when I do, it says the same thing.

I can't update or install any new software on to the machine.


thank you!
Andy

---

### Post by Impavidus on 2013-05-08
My linux-generic (3.2.0.41.49) depends on linux-image-generic (=3.2.0.41.49). It sounds like your linux-generic is outdated. Can you upgrade linux-generic? Probably not.

There may also be a problem with the server you use. As linux-generic is only a metapackage it shouldn't harm you too much if this situation continues for a few days. If it doesn't solve itself, consider trying a different server.

---

