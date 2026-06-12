---
title: "How to use dpkg to uninstall a package"
date: 2008-02-17
forum: General Help
---

### Post by noahsark on 2008-02-17
Hi all,

I just installed an acrobat reader from RPM file using alien and pckg. I later on found that it is not as good as the gnome default PDF reader.

When I was trying to uninstall it, I typed:

dpkg -r adobereader-enu

I think it is all uninstalled. However, I can still see it if I type 

dpkg -l | grep adobereader-enu

All it changes is the prefix from "ii" to "rc"

rc  adobereader-enu                            8.1.2-2 

Does it mean I haven't completely uninstall it? If yes, how can I remove it completely?
What does "ii" and "rc" mean?

Many thanks.

---

### Post by Jussi Kukkonen on 2008-02-17
"apt-cache policy <pkg-name>" will tell you the state of the package (I'm guessing 'rc' means Remaining Configuration).

---

