---
title: "how do upgrade firefox"
date: 2007-11-03
forum: General Help
---

### Post by scuba_suit on 2007-11-03
i dl'ed it, now when i open it where do i extract the file to?

---

### Post by strabes on 2007-11-03
Generally it's better to simply wait until the new versions of programs are put into the repositories. When something is in the repositories it is **generally** decently stable and quality. Plus, you can upgrade your entire system by simply running:```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by elcasey on 2007-11-03
If you're talking about running Gran Paradiso, the alpha of Firefox 3.x, you can do what I did.

Unpack the tarball into /opt (for "optional software"), e.g. /opt/firefox. You can choose to type "/opt/firefox/firefox" into the Run (Alt+F2) dialog, or you can change the path of the Firefox shortcuts in your menus.

Be aware that you cannot run 2.x and 3.x at the same time...it's one or the other. I just recently switched back to 2.0.0.6 because most of my extensions don't work in 3.0a8.

---

### Post by kostkon on 2007-11-03
If you mean about updating to 2.0.0.9 I recommend you to wait because sooner or later, in one or two days, as *strabes* said, it will come to you as an update. Thus, you don't need to do anything.

---

