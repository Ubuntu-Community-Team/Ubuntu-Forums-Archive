---
title: "How to hide music from Ubuntu unity search"
date: 2013-06-01
forum: General Help
---

### Post by computerzworld on 2013-06-01
Hello,
              I want to hide music files from Ubuntu unity search. When I am searching for anything one music category comes up underneath applications. I want to hide that music part. I have added my songs directory in hide list. What is the way to hide this music from search? Any help would be appreciated. Thanks.

---

### Post by vanadium on 2013-06-01
```

sudo apt-get remove unity-lens-music

```

There are more lenses you can remove to limit the scope of the dash. I removed all of them, except unity-lens-applications  unity-lens-files.

---

