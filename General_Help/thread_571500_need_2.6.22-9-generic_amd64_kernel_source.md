---
title: "need 2.6.22-9-generic amd64 kernel source"
date: 2007-10-09
forum: General Help
---

### Post by Ron Overdrive on 2007-10-09
Hey all, I'm using Fiesty Fawn with the 2.6.22-9 gutsey kernel and in order to get Truecrypt working again I need to compile it from source, but it needs the kernel source for my kernel. I've tried searching the forums and google, but nothing really came up that could help me. Can anyone help me out here?

---

### Post by rsambuca on 2007-10-09
You can get all of the packages and source code from the [ubuntu packages website]("http://packages.ubuntu.com/").

---

### Post by jocko on 2007-10-09
> **Ron Overdrive said:**
> Hey all, I'm using Fiesty Fawn with the 2.6.22-9 gutsey kernel and in order to get Truecrypt working again I need to compile it from source, but it needs the kernel source for my kernel. I've tried searching the forums and google, but nothing really came up that could help me. Can anyone help me out here?

You'll probably not need the entire source. The headers are usually enough.
The package you need should be named linux-headers-2.6.22-9-generic.
If you really need the entire source, look for a package named linux-source-2.6.22.

---

