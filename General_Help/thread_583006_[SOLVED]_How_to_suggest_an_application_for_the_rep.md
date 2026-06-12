---
title: "[SOLVED] How to suggest an application for the repository?"
date: 2007-10-20
forum: General Help
---

### Post by mivo on 2007-10-20
Is there a way to suggest software for the repositories?

I had looked for a good WYSIWYG HTML editor, but NVU had been removed from the Ubuntu repositories earlier this year because the project had been inactive for quite some time. I found an actively maintained spin-off of the project, called [KompoZer]("http://kompozer.net/"), and their .deb works just fine with Ubuntu 6.06 through 7.10. But it would still be nice if it could be added to the repositories because there currently is no WYSIWYG HTML editor in there at all (unless you count OpenOffice Writer, but that one is somewhat limited).

---

### Post by Stemp on 2007-10-20
Kompozer is in the repositories (in Universe).

```
~$ LANG=C aptitude show kompozer
Package: kompozer
New: yes
State: not installed
Version: 0.7.10-0ubuntu1
Priority: optional
Section: universe/web
Maintainer: Anthony Yarusso <tonyyarusso@ubuntu.com>
Uncompressed Size: 26.8M
Depends: libatk1.0-0 (>= 1.13.2), libc6 (>= 2.6-1), libcairo2 (>= 1.4.0),
         libfontconfig1 (>= 2.4.0), libgcc1 (>= 1:4.2.1), libglib2.0-0 (>=
         2.14.0), libgtk2.0-0 (>= 2.11.6), libidl0, libpango1.0-0 (>= 1.18.1),
         libstdc++6 (>= 4.2.1), libx11-6, libxcomposite1 (>= 1:0.3-1),
         libxcursor1 (> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>=
         1:4.0.1), libxft2 (> 2.1.1), libxi6, libxinerama1, libxrandr2 (>=
         2:1.2.0), libxrender1, libxt6, zlib1g (>= 1:1.2.3.3.dfsg-1)
Description: Complete Web Authoring System
 KompoZer is a complete Web Authoring System that combines web file management
 and easy-to-use WYSIWYG (What You See Is What You Get) web page editing. 
 
 KompoZer is designed to be extremely easy to use, making it ideal for
 non-technical computer users who want to create an attractive,
 professional-looking web site without needing to know HTML or web coding. 
 
 For more details look at http://kompozer.sourceforge.net/
```

---

### Post by mivo on 2007-10-20
Ah, thanks! Looks like it is for 7.10, didn't find it in Feisty. Glad it was added. :)

---

