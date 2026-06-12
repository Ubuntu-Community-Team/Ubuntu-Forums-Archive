---
title: "Installed GNU C++ Compiler not found"
date: 2006-12-05
forum: General Help
---

### Post by LordRaiden on 2006-12-05
I'm running Kubuntu Edgy and I am having trouble compiling KTorrent and Kile from source. I have the dependencies installed with build-dep and I have the build-essential package. Nevertheless, I get this error while at ./configure:

```

configure: error: Your Installation isn't able to compile simple C++ programs. Check config.log for details - if you're using a Linux distribution you might miss a package named similar to libstdc++-dev.

```I have libstdc++6-4.1-dev so I do not think that is the problem. 
Many thanks in advance

---

### Post by LLRNR on 2006-12-05
Sometimes it happens. Look in the directory you were issuing "./configure" from, there's a file called "config.log", and towards the end of this file you will find an error about a missing library I suppose. If you're lucky, it will be something you never heard of before, like "libsomething", and you will just have to "sudo aptitude install libsomething-dev".

I hope this helps,

LLRNR

PS: By the way, why are you trying to build KTorrent from source ? Isn't it installed by default ? Mine seems to be working good...

---

### Post by LordRaiden on 2006-12-05
I looked in my config.log, it says that libstdc++-dev is missing but I clearlu have libstdc++-6-4.1-dev. 

Also, the ./configure command gives this result which seems like a problem 
```

checking whether we are using the GNU C++ compiler... no

```I have g++, so again I am confused.

It's not so much KTorrent anymore ( I found a page where someone is building KTorrent .debs on an almost daily basis from subversion), but I'd like to look at the new version of Kile.

---

### Post by unimatrix on 2008-03-17
Bump
Same problem in Gutsy.

---

