---
title: "How do I easily install tar.bz2 applications?"
date: 2013-05-29
forum: General Help
---

### Post by Deedlebag on 2013-05-29
A lot of applications I encounter online only come in tar.bz2 form, which is very confusing to me. I unpack to a folder, and read the README, but that provides no help at all on how to install it. Most I've encountered don't work with ./config or anything like that. Is there something I can get from the Ubuntu Software Center than can install these files for me? I've heard talk of software called Synaptic? Thank you

---

### Post by Zill on 2013-05-29
The vast majority of Linux applications are installed directly from the repositories, either via the Software Center, Synaptic or apt-get terminal commands.  Compilation of applications from source is rarely, if ever, required.

See this...
[LIST]
[*][Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")
[/LIST]

---

### Post by ohnonot on 2013-05-29
...however, it *is* posible to install from source. it means you download the source code, usually packed in some kind of tar archive, unpack it and run install scripts.
the README often includes only short info about the program itself, there's usually an INSTALL text file which gives installing instructions.
although it usually says "./configure, make, sudo make install", there might be an "autoconf.sh" or sth like that which you can run before make and install.
sounds confusing, but just try. and: think and doublecheck before typing "sudo make install".
always run these from a terminal because they give you feedback on what went wrong.
usually missing dependencies. so read the error messages and think, they don't usually tell you to install package xyz but refer to missing libraries.
at the beginning even the tools for compiling themselves might be missing.
one good thing to know: often you have a dependency installed, but the compilation process needs the <dependency>-dev version.

it's a very frustrating experience at first, but very rewarding when you succeed ;-)

i agree with the dalek penguin that you should try to find a ubuntu package first.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

