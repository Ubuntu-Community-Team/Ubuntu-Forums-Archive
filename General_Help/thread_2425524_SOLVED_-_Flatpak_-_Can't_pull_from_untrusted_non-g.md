---
title: "SOLVED - Flatpak - Can't pull from untrusted non-gpg verified remote"
date: 2019-08-26
forum: General Help
---

### Post by drbuckingham on 2019-08-26
When trying to install flatpak's, the dependencies fail with:

Error: Can't pull from untrusted non-gpg verified remote
error: Failed to install org.kde.Platform: Can't pull from untrusted non-gpg verified remote

As an example, when trying to install MakeMKV (from either the command-line or from the flathub store "install" button), it fails on the org.kde.Platform dependency.  If I try to install org.kde.Platform by itself first, its dependencies fail with the same error.  I have been through the setup guide multiple times to no avail.

I had been on 18.04, but with the all the reported flatpak issues and the reports that they had been fixed in 19.04, I upgraded to 19.04 --- but I have the exact same issues.  Any help would be appreciated.

---

### Post by drbuckingham on 2019-08-26
I resolved it by deleting the old 18.04 -> 19.04 installation and starting fresh with 19.04.  Now the flatpak installation works without error.  :\

---

### Post by #&amp;thj^% on 2019-08-26
Thanks for the share. :)
Did you ever try ?:
```
flatpak update
```

---

