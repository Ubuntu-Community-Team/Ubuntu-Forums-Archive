---
title: "How to tell apt that a package is installed?"
date: 2007-07-14
forum: General Help
---

### Post by piojo on 2007-07-14
Hi. I have installed emacs from source (newer version than in the repos), and I want to install packages that have an emacs dependency. Is there some way to tell my system that I have the (virtual) packages "emacsen" and "editor"? Otherwise, these installs fail, saying that I need to install emacs.

In other distros, this would be called "provided" or "insert" or "inject".

I could not use checkinstall to create a .deb with emacs--it just didn't work. I could make a dummy .deb that contains no files but provides these packages, but that's a hack I would rather avoid, if possible.

Thanks.

---

### Post by gepatino on 2007-07-14
AFAIK, the only way to make a installed package to appear in apt is installing it from a .deb file. If you're using the sources from the repos, and compile them using the debian tools, you should end up with a deb file with your compiled program, then you install that deb.

If you are compiling a non repo source, there's no way to make it appear on apt (or I don't know how). 

Even if you manage to make it appear in apt, I don't think you could make other programs to depend on this one, since the dependencies (package + version) are saved inside each package file. You should have to download the debs, modify the dependencies reconstructing the deb package, and then install that package.

---

### Post by piojo on 2007-07-14
Thank you for your reply. I have posted a hack that solves this, in case someone else wonders how to manually resolve virtual dependencies on debian or ubuntu (though there should be a better solution, I think).

Problem: I compiled a package from source, let's say "emacs", and I need to tell apt that a virtual dependency (normally taken care of by emacs) is now installed. So here is a hack to provide the virtual dependency "emacsen":

1. Enter an empty directory.
2. ```
$ mkdir DEBIAN
```
3. Create a new file, DEBIAN/control, that looks like this:

```
Package: emacs-cvs-dummy
Version: 23.0.0-build1
Section: editors
Priority: optional
Architecture: i386
Depends: libgtk2.0-0 (>= 2.10.3), libxft2
Provides: emacsen, editor, info-browser, mail-reader, news-reader
Replaces: emacs-snapshot, emacs-snapshot-nox, emacs-snapshot-gtk
Installed-Size: 0
Maintainer: nobody
Source:
Description: Dummy package for GNU Emacs from the unicode-2 branch.
```

The important line is "Provides", and nothing else really matters.
Now, not in the DEBIAN directory, create the dummy .deb:

```
$ dpkg --build . .
```

It will be named according to the options in the control file. Install it:

```
$ sudo dpkg -i ./emacs-cvs-dummy_23.0.0-20070714_i386.deb
```

And now your virtual dependency is taken care of.

---

