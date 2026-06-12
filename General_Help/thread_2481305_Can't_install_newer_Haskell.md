---
title: "Can't install newer Haskell"
date: 2022-11-25
forum: General Help
---

### Post by Acharn on 2022-11-25
I've never used Haskell, but it looked interesting, so I installed the tools on my Ubuntu 22.04. When I compiled the "hello, world" program, I got error messages indicating that the linker in gcc had failed. I tried nuking the installation and reinstalling it, and noticed a very brief message saying Haskell 9.2.5 is not compatible with something and I should use a newer compiler. I've tried using ```
ghcup tui
```, but after installing 9.3.4 and 9.3.2, the command ```
ghc --version
``` returns "the Glorious Glasgow Haskell Compilation System, version 9.2.5." What am I doing wrong?

---

