---
title: "PKG_CONFIG_PATH or something!"
date: 2006-11-24
forum: General Help
---

### Post by Homayoon on 2006-11-24
I was trying to build a separate version of python in the directory "/mypy". I could easily manage to install python and then stackless and pygtk onto it. But when I tried to build "gnome-python", the configure script says:

```

...
checking for PYGTK... configure: error: Package requirements (pygtk-2.0 >= 2.6.2) were not met:

No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Although I ran "./configure --prefix=/mypy --exec-prefix=/mypy", it is obvious that the configure script is unable to find my version of pygtk. I tried "export PKG_CONFIG_PATH=/mypy" but it did not help. I'm fairly new to building programs (and in fact to Linux itself). How can I get the configure script find pygtk?

---

### Post by konst88 on 2006-11-24
Have you installed python-gtk2-dev ?

---

### Post by Homayoon on 2006-11-24
I just tried to install it. I ran "sudo apt-get install python-gtk2-dev", but I ran into the following error:

> 
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-gtk2-dev: Depends: python-gtk2 (= 2.8.1-0ubuntu2) but 2.8.6-0ubuntu1 is to be installed
E: Broken packages


Strange! By the way, I had already tried to build python, stackless and wxpython and I have made a complete mess with them! Probably that's why I got the error. How can I get over all this?! ](*,)

---

### Post by konst88 on 2006-11-24
Don't use apt-get, it can't handle dependencies correctly.
Use aptitude instead:  sudo aptitude install python-gtk2-dev
It will give you solutions to resolve the dependency problems.
Good luck.

---

### Post by Homayoon on 2006-11-26
I could install python-gtk2-dev with aptitude, but this time I need libgnome2-dev. Seems aptitude cannot do anything about this. It suggests a solution, but the solution leads to nothing ("0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded."). Any ideas about this one?

---

### Post by konst88 on 2006-11-27
Can you post the output from aptitude exactly?

---

