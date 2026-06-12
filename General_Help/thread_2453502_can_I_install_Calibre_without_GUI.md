---
title: "can I install Calibre without GUI?"
date: 2020-11-11
forum: General Help
---

### Post by ardouronerous on 2020-11-11
I don't much care for the GUI of Calibre, all I care about is the ebook-convert feature of Calibre, so I was wondering if it's possible to install Calibre's command line without the additional GUI elements. Thanks.

---

### Post by #&amp;thj^% on 2020-11-11
Calibre needs ImageMagick to manipulate graphics, while xvfb is required for running Calibre's services in a headless (no graphical desktop) environment. A completely fresh server install may require libXcomposite for other basic graphics handling.
Also see this: [https://gist.github.com/plembo/337f323e53486cbdb03100692ae8c892](https://gist.github.com/plembo/337f323e53486cbdb03100692ae8c892)
Warning its a bit dated but should be sufficent to install on Newer Servers.

---

### Post by dragonfly41 on 2020-11-11
There is pandoc for cli usage

---

