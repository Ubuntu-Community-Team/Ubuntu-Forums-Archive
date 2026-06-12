---
title: "404 errors when trying to upgrade/update"
date: 2014-10-21
forum: General Help
---

### Post by duke3 on 2014-10-21
I have been trying to update my VPS through terminal (Putty) and i keep getting various errors such as 
```

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.15 80]

```

I even reinstalled OS and it still gives the error.

---

### Post by Impavidus on 2014-10-21
Raring is Ubuntu 13.04, which is unsupported. The repositories are no longer there. They have been moved to the old releases, but those won't do you any good either as no new updates are created and pushed through any more. To install updates, you'll have to install a supported version of Ubuntu. I recommend 14.04. Best to make it a clean install. Ubuntu 14.04 will be supported until April 2019.

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

