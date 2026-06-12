---
title: "A problem with licenses"
date: 2018-06-05
forum: General Help
---

### Post by tommi-hoynalanmaa on 2018-06-05
I have published some software under GNU GPL and LGPL. However, when I open the Debian packages with Ubuntu Software Installation (18.04) the application claims that the software is proprietary. How can I fix this?

The relevant packages are:

  [http://www.iki.fi/tohoyn/theme-d/theme-d_1.1.0_amd64.deb](http://www.iki.fi/tohoyn/theme-d/theme-d_1.1.0_amd64.deb)
  [http://www.iki.fi/tohoyn/theme-d/th-scheme-utilities_1.4.1_all.deb](http://www.iki.fi/tohoyn/theme-d/th-scheme-utilities_1.4.1_all.deb)
  [http://www.iki.fi/tohoyn/theme-d/libthemedsupport_1.1_amd64.deb](http://www.iki.fi/tohoyn/theme-d/libthemedsupport_1.1_amd64.deb)

     - Tommi Höynälänmaa

---

### Post by nlee2 on 2018-06-05
Are you expecting Ubuntu Software Installation to parse the copyright file in a deb package to determine license? It does not.

---

