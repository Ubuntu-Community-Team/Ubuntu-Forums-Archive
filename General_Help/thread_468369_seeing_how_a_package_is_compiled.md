---
title: "seeing how a package is compiled"
date: 2007-06-08
forum: General Help
---

### Post by pjkoczan on 2007-06-08
Hi all,

Although the click-and-drool (or apt-get-and-drool) method of installing software is very, very nice, I would like to start compiling some software from source.

Is there any nice way to see how a .deb package is compiled (the configure and make options specifically) so I can figure out what the .deb package is doing and perhaps how I could configure things for my pusposes?

---

### Post by tbroderick on 2007-06-08
You can go to packages.ubuntu.com, search for the what you want to compile, and then scrool to the bottom of the package's page. Under "More Information on *xxx*", there is a *xxx*.diff.gz. You can view that and search for the ./configure line.

---

### Post by az on 2007-06-08
Make sure you have the deb-src repos enabled in your sources.list.

sudo apt-get update

sudo apt-get build-dep foo

apt-get source foo

[I]source causes apt-get to fetch source packages. APT will examine the
          available packages to decide which source package to fetch. It will
          then find and download into the current directory the newest
          available version of that source package. Source packages are
          tracked separately from binary packages via deb-src type lines in
          the sources.list(5) file. This probably will mean that you will not
          get the same source as the package you have installed or as you
          could install. If the --compile options is specified then the
          package will be compiled to a binary .deb using dpkg-buildpackage,
          if --download-only is specified then the source package will not be
          unpacked.

          A specific source version can be retrieved by postfixing the source
          name with an equals and then the version to fetch, similar to the
          mechanism used for the package files. This enables exact matching of
          the source package name and version, implicitly enabling the
          APT::Get::Only-Source option.

          Note that source packages are not tracked like binary packages, they
          exist only in the current directory and are similar to downloading
          source tar balls.
[/I]

---

### Post by freakavoid on 2007-06-08
[Here]("http://www.linux.com/article.pl?sid=07/02/21/1546215") is a link about .deb packages.

---

