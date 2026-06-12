---
title: "Missing 'libgtk-1.2.so.0' Error"
date: 2007-05-12
forum: General Help
---

### Post by jjalocha on 2007-05-12
I'm trying to [install the drivers for a Epson Stylus CX3900]("http://ubuntuforums.org/showthread.php?t=438114") printer, but when I try to run one of the installation scripts, I get the following error message:

```

./pipslite-install: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

I guess, I could just install the 'libgtk1.2' package with 'aptitude', but since in Feisty I have already the 'libgtk2.0-0', and I love to keep my system as "clean" as possible, I'd like to know, if there's another (better?) way to let 'pipsllite-install' use the installed library version 2.

Does this make any sense, or is it better to install various versions of the same library?

---

### Post by noerrorsfound on 2007-05-12
> **jjalocha said:**
> Does this make any sense, or is it better to install various versions of the same library?
I think you should just install multiple versions. I doubt applications will get "mixed up" and choose the wrong version of the library, because as you can see, even though you have a newer version installed, the program still searches for the older version.

You can create a symlink and make libgtk-1.2.so.0 "redirect" to the newer version, but that could cause some problems (if it actually worked, which I doubt it would).

---

### Post by jjalocha on 2007-05-12
Thank you for your explanation! It works like a charm now.

---

### Post by Perfect Storm on 2007-05-12
I doubt it will work for applications that uses libgtk1.2.

It seems a bit risky to make such symlinks.

---

### Post by jjalocha on 2007-05-13
You're right, Artificial Intelligence, I forgot to mention that it worked perfectly after *installing* the 'libgtk1.2' package. I did *not* try to create any such symlinks.

---

