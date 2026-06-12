---
title: "Problem installing llvm on ubuntu 12.04 LTS"
date: 2014-04-08
forum: General Help
---

### Post by Arvid_Stterkvist on 2014-04-08
Hello!

So I installed ubuntu 12.04 LTS yesterday. I'm very new to Ubuntu and don't really know what I'm doing. Just please bear with me :)

I was trying to install the plugin 'YouCompleteMe' for vim and followed the [full installation instructions]("https://github.com/Valloric/YouCompleteMe#full-installation-guide").
It told me to install libclang using the [official binaries from llvm.org]("http://llvm.org/releases/download.html"). Since I have no idea how to install it I googled for instructions and found [the answer to this Stack Overflow question]("http://stackoverflow.com/questions/17657261/how-to-install-clang-pre-built-binaries-ubuntu-12-04").
I followed the instructions but when I try to "Install the whole llvm+clang toolchain" with:
```

sudo apt-get install clang-3.4 clang-3.4-doc libclang-common-3.4-dev libclang-3.4-dev libclang1-3.4 libclang1-3.4-dbg libllvm-3.4-ocaml-dev libllvm3.4 libllvm3.4-dbg lldb-3.4 llvm-3.4 llvm-3.4-dev llvm-3.4-doc llvm-3.4-examples llvm-3.4-runtime cpp11-migrate-3.4 clang-format-3.4

```
I get this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package clang-3.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  clang-3.5:i386 clang-3.5 clang-3.3:i386 clang-3.3


Package clang-format-3.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  clang-format-3.3:i386 clang-format-3.3


Package cpp11-migrate-3.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  clang-modernize-3.5:i386 clang-modernize-3.5 cpp11-migrate-3.3:i386
  cpp11-migrate-3.3


Package lldb-3.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lldb-3.5:i386 lldb-3.5


E: Package 'clang-3.4' has no installation candidate
E: Unable to locate package clang-3.4-doc
E: Couldn't find any package by regex 'clang-3.4-doc'
E: Unable to locate package libclang-common-3.4-dev
E: Couldn't find any package by regex 'libclang-common-3.4-dev'
E: Unable to locate package libclang-3.4-dev
E: Couldn't find any package by regex 'libclang-3.4-dev'
E: Unable to locate package libclang1-3.4
E: Couldn't find any package by regex 'libclang1-3.4'
E: Unable to locate package libclang1-3.4-dbg
E: Couldn't find any package by regex 'libclang1-3.4-dbg'
E: Unable to locate package libllvm-3.4-ocaml-dev
E: Couldn't find any package by regex 'libllvm-3.4-ocaml-dev'
E: Unable to locate package libllvm3.4
E: Couldn't find any package by regex 'libllvm3.4'
E: Unable to locate package libllvm3.4-dbg
E: Couldn't find any package by regex 'libllvm3.4-dbg'
E: Package 'lldb-3.4' has no installation candidate
E: Unable to locate package llvm-3.4
E: Couldn't find any package by regex 'llvm-3.4'
E: Unable to locate package llvm-3.4-dev
E: Couldn't find any package by regex 'llvm-3.4-dev'
E: Unable to locate package llvm-3.4-doc
E: Couldn't find any package by regex 'llvm-3.4-doc'
E: Unable to locate package llvm-3.4-examples
E: Couldn't find any package by regex 'llvm-3.4-examples'
E: Unable to locate package llvm-3.4-runtime
E: Couldn't find any package by regex 'llvm-3.4-runtime'
E: Package 'cpp11-migrate-3.4' has no installation candidate
E: Package 'clang-format-3.4' has no installation candidate

```

I also tried changing all the 3.4 to 3.5, but then I got:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 clang-3.5 : Depends: libstdc++-4.8-dev but it is not installable
             Depends: libgcc-4.8-dev but it is not installable
             Depends: libobjc-4.8-dev but it is not installable
 libclang-3.5-dev : Depends: libstdc++-4.8-dev but it is not installable
                    Depends: libgcc-4.8-dev but it is not installable
                    Depends: libobjc-4.8-dev but it is not installable
 libclang1-3.5 : Depends: libstdc++-4.8-dev but it is not installable
                 Depends: libgcc-4.8-dev but it is not installable
                 Depends: libobjc-4.8-dev but it is not installable
 libclang1-3.5-dbg : Depends: libstdc++-4.8-dev but it is not installable
                     Depends: libgcc-4.8-dev but it is not installable
                     Depends: libobjc-4.8-dev but it is not installable
 lldb-3.5 : Depends: libstdc++6 (>= 4.8) but 4.6.3-1ubuntu5 is to be installed
E: Unable to correct problems, you have held broken packages.

```

I've been stuck here for a couple of hours now. I added (I think) [this ppa]("https://launchpad.net/~ubuntu-toolchain-r/+archive/ppa") after some more googling but nothing changed.


I hope you can help me :)

---

### Post by Kirboosy on 2014-04-08
Welcome to the forums! :D

Hopefully I can be of some help to you.

Under Software center you should be able to see all the software sources you have enabled. Software Center --> Edit --> Software Sources <TAB> Other Software. This menu will allow you to clear out the repositories you added. Right now you have repositories enabled that overlap one of another and we should simplify this. Go ahead and look towards the bottom of the list. It should have the two new repositories you added. Go ahead and delete them.

Rerun the following commands ```
sudo apt-get update
sudo add-apt-repository 'deb http://llvm.org/apt/precise/ llvm-toolchain-precise main'
wget -O - http://llvm.org/apt/llvm-snapshot.gpg.key|sudo apt-key add -
sudo apt-get update


```

If you haven't seen any errors up to this point then that is a good sign. Try the following command once the ones above complete.

```
sudo apt-get install clang-3.4 clang-3.4-doc libclang-common-3.4-dev  libclang-3.4-dev libclang1-3.4 libclang1-3.4-dbg libllvm-3.4-ocaml-dev  libllvm3.4 libllvm3.4-dbg lldb-3.4 llvm-3.4 llvm-3.4-dev llvm-3.4-doc  llvm-3.4-examples llvm-3.4-runtime clang-modernize-3.4 clang-format-3.4  python-clang-3.4 lldb-3.4-dev
```

Hope that helps!
~Caboose

---

### Post by Arvid_Stterkvist on 2014-04-09
Thanks for the reply Caboose885!
I did what you said, but I got the same errors as before.

Anyways with a bit more googling and reading I got it working. Since I'm such a noob I didn't realize that pre-built binaries doesn't have to be installed. So all I had to do was downloading the clang-binaries from llvm.org and use them.

Also, I found [this]("http://lists.cs.uiuc.edu/pipermail/llvmdev/2013-December/068999.html"), which I think means that clang 3.4 is not supported in ubuntu 12.04 because it needs libstdc++ 4.8.

Oh well, thank you! :)

---

