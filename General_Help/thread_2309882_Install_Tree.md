---
title: "Install Tree"
date: 2016-01-14
forum: General Help
---

### Post by Ayshea on 2016-01-14
Hi, I have been trying to install TREE using Ubuntu I am using this command:     [EMAIL="user@ubuntu:~$"]user@ubuntu:~$[/EMAIL] sudo apt-get install tree

This is what it comes back with.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tree

Any ideas please?

---

### Post by slickymaster on 2016-01-14
Hi Ayshea, welcome to the forums.

The package tree is available in the [Universe repository]("http://packages.ubuntu.com/search?keywords=tree"). Do you have it enabled?

---

### Post by matt_symes on 2016-01-14
Hi

tree is in the Universe repository.
```

matthew-xu-16-04:/home/matthew/raspberry-pi-2-images:1 % acsh ^tree$
Package: tree
Priority: optional
**Section: universe/utils**
Installed-Size: 135
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Florian Ernst <florian@debian.org>
Architecture: amd64
Version: 1.7.0-3
Depends: libc6 (>= 2.14)
Filename: pool/universe/t/tree/tree_1.7.0-3_amd64.deb
Size: 40572
MD5sum: fefa3e2233bec6823b1b61cfd6ba0105
SHA1: 4fec27e396ff048441be18ded0d9f36e88a17a53
SHA256: d3423501d3464436199e293efaa6e95ec9296e74b6b597edc373e5dc386f9e5b
Description-en: displays an indented directory tree, in color
 Tree is a recursive directory listing command that produces a depth indented
 listing of files, which is colorized ala dircolors if the LS_COLORS environment
 variable is set and output is to tty.
Description-md5: 9b53b68087a50d4cd859ac0117aecc08
Homepage: http://mama.indstate.edu/users/ice/tree/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

matthew-xu-16-04:/home/matthew/raspberry-pi-2-images:1 % 
```

Do you have this repository enabled ?

Also post what version of Ubuntu you are using.

Enable the universe repository and try to install tree again.

If this fixes the problem for you then please mark this thread as solved using the thread tools under post #1.

Kind regards

---

