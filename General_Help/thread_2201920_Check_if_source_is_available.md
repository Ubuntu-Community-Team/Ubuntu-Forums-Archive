---
title: "Check if source is available"
date: 2014-01-26
forum: General Help
---

### Post by Tristan_Williams on 2014-01-26
I am running Ubuntu Minimal 13.10

I have built a full desktop system and I want it to be built entirely from source (as much as possible)

I have run the following command:
```
dpkg --get-selections | awk '{if ($2 == "install")print $1}' > ~/Desktop/pkgs
```

Now I have a list of all installed packages on my system.

However if I run "apt-build world" right now, I would get errors saying how some package wasn't found and that apt-build can't continue unless every freaking package is available.

So I need one of two things:
a) A way to check which packages from that list are available as source packages
b) A way to make apt-build ignore "not-found" errors

Thanks in advance :)

---

