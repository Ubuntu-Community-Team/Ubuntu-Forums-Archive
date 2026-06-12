---
title: "How to find the installed package that includes a certain file/program?"
date: 2008-06-27
forum: General Help
---

### Post by caljohnsmith on 2008-06-27
Say for example I want to find the package that "nm-applet" comes in. If I do "apt-cache search nm-applet" it doesn't return anything, because if I understand it correctly, "apt-cache search" only searches package names and descriptions, not installed files. Is there some easy way to find out which installed package a particular file/program comes in? 

Thanks for any help.

---

### Post by owlgorithm on 2008-06-27
Try visiting this page:

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by suicidejack on 2008-06-27
i always use google...

---

### Post by caljohnsmith on 2008-06-27
> **owlgorithm said:**
> Try visiting this page:

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
Thanks, I forgot about searching the package archives. Sure would be more convenient though if there was a way to search the installed packages on my computer for the file/program I'm after. The information is there, as even Synaptic shows the installed files for a package, but there's no way to search through all of them. Thanks for providing a viable solution though.

---

### Post by brian_p on 2008-06-27
> **caljohnsmith said:**
> Say for example I want to find the package that "nm-applet" comes in. If I do "apt-cache search nm-applet" it doesn't return anything, because if I understand it correctly, "apt-cache search" only searches package names and descriptions, not installed files. Is there some easy way to find out which installed package a particular file/program comes in? 

```
dpkg -S nm-applet
```

The apt-file package for installed **and** non-installed files.

---

### Post by caljohnsmith on 2008-06-27
> **brian_p said:**
> ```
dpkg -S nm-applet
```

The apt-file package for installed **and** non-installed files.

Thanks a bunch Brian, those are exactly the type of commands I was looking for. :)

---

