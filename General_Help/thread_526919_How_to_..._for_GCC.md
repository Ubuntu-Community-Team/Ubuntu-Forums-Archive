---
title: "How to ... for GCC"
date: 2007-08-16
forum: General Help
---

### Post by hairyhi on 2007-08-16
Hi,
i need help with gcc... plz help!

All i want to do is while running an application complied via gcc,  i want to fix some timeout for it, i.e. the execution is terminated after some specific seconds like 2-3 seconds (specially for the cases of infinitely running application). What i want is to develop a automated gcc compile and run application...

plz plz plz help! its urgent

---

### Post by HermanAB on 2007-08-16
You can probably do it with a combination of the 'at' daemon and 'killall'.  

See:
$ man at
$ man killall

I hope that helps!

Herman

---

