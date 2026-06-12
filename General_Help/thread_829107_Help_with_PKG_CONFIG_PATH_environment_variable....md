---
title: "Help with PKG_CONFIG_PATH environment variable..."
date: 2008-06-14
forum: General Help
---

### Post by rbradt on 2008-06-14
Hey there,

Just got into a situation that I haven't experienced before.

It started with me trying to build Scintilla so I can install Scite.  (The version in the repositories is not the most current).  When building Scintilla, I got an error saying it could not find gtk+-2.0.pc, and it suggested that I include it in the PKG_CONFIG_PATH environment variable.  I tried finding that file, but it seems like it doesn't exist on my computer.

So, I guess my question would be:  What exactly is pkg-config and the PKG_CONFIG_PATH?  How do I set the variable,and how do I know what to set it to?

Like I said, I haven't had to deal with this before.  So, any help would be much appreciated.  Thanks in advance!!

---

### Post by sdennie on 2008-06-14
This kind of error while building stuff usually means that you are missing -dev packages to build the app.  In this case (where you are building a newer version of something that is already in the repos), it's very easy to get all the build deps for and application:

```

sudo apt-get build-dep libqscintilla7 scite

```

That should download all the packages you need to build both of the things you are trying to build.

---

### Post by rbradt on 2008-06-16
Thanks a lot.  That did solve the problem.  

Do you know when it is necessary to mess with the PKG_CONFIG_PATH environment variable?

---

### Post by sdennie on 2008-06-16
I've never messed with it actually.  When I'm building something from source and it complains like that I just use build-dep or look through synaptic for the appropriate -dev packages.  It might be useful to modify that variable if you had some custom library that installed in a non-standard place.

---

### Post by geirha on 2008-06-16
> **rbradt said:**
> Thanks a lot.  That did solve the problem.  

Do you know when it is necessary to mess with the PKG_CONFIG_PATH environment variable?

pkg-config will look through /usr/local/lib/pkgconfig/ and /usr/lib/pkgconfig/ for .pc-files. If you have something installed that has put its pkgconfig-file somewhere else than those two directories, then you'll need to add it to the PKG_CONFIG_PATH.

---

