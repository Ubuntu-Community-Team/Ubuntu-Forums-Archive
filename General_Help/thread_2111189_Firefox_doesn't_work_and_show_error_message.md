---
title: "Firefox doesn't work and show error message"
date: 2013-02-01
forum: General Help
---

### Post by Linuxour on 2013-02-01
Hello, 

I work with kubuntu 12.10 . Every time I try opening Firefox this message appears 

" Your Firefox profile cannot be loaded. It may be missing or inaccessible "  

I reinstalled it using Terminal , muon software center , the tar.bz2 file, but the same happened.

---

### Post by zombifier25 on 2013-02-01
Your profile is corrupted somehow. Start fresh by renaming/removing the hidden .mozilla folder in your home folder. Or run this command:
```
mv .mozilla .mozilla.old
```

---

### Post by Linuxour on 2013-02-01
Thank you very much , it worked.

---

