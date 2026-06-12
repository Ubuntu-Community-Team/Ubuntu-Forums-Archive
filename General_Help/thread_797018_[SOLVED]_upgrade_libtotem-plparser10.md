---
title: "[SOLVED] upgrade libtotem-plparser10"
date: 2008-05-16
forum: General Help
---

### Post by tacutu on 2008-05-16
today an update for libtotem-plparser10 was released but synaptic wouldn't update it. Instead it complains that: 
```
libtotem-plparser10:
  Depends: libcamel1.2-11 (>=2.22.1.1) but 2.22.1-0ubuntu2.1 is to be installed
  Depends: libedataserver1.2-9 (>=2.22.1.1) but 2.22.1-0ubuntu2.1 is to be installed
```

I previously removed totem (since I only use mplayer) but the libtotem-plparser10 was kept on the system not to brek dependencies.

Any ideas how to solve this?

Thanks

---

### Post by Gunman1982 on 2008-05-16
It is sometimes possible that updated packages depend on other packages which are not yet in the repository. Wait a day or two ... or more ;)

---

### Post by bryncoles on 2008-05-17
im also getting libtotem-plparser10 as an available update - but update manager wont let me select it. ill assume its the same issue though - and that it'll be fixed in a few days. 

might just bookmark this thread too though ;-)

---

### Post by reyhan on 2008-05-17
Hey!! i've got libtotem-plparser10
Update too But i'cant upgrade it!!

---

### Post by tacutu on 2008-05-17
Thanks guys! So at least I know the fault lies somewhere else, not with my system :)

---

### Post by bryncoles on 2008-05-17
patience is a virtue it would seem... 

try updating now. i just did, and libtotem-etc has updated fine! must just have been waiting for the repo's to catch up!

---

### Post by tacutu on 2008-05-17
yeah, it is solved.
thanks.

---

### Post by reilly2040 on 2008-05-22
I'm in the UK, and I was still having this problem today. 

However, seeing that it was solved in this thread, I went into Synaptic and changed the source for my updates from the UK server to the main one and its now updated fine, so apparently the UK server is lagging behind.

Thanks guys :-)

---

