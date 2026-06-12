---
title: "Noob repository question"
date: 2007-05-07
forum: General Help
---

### Post by VampireBadger on 2007-05-07
Hello there

I have installed Feisty Fawn yesterday and I'm having some serious trouble with installing the programs I want. They simply aren't available in the repo and I'm sure I have enabled them all (main, universe, multiverse, restricted). I don't have anything against compiling stuff but the problem is I can't find a compiler as well.

So, could anyone point me into some kind of 3rd party repository the has more stuff than the ones on the default sources.list ? Gentoo was an annoying time-wasting piece of cr*p but it has all the stuff I needed. Please don't make me install Gentoo again :cry:

---

### Post by eldepeche on 2007-05-07
What programs specifically?

---

### Post by VampireBadger on 2007-05-07
> **eldepeche said:**
> What programs specifically?

Well, I can't find a compiler as I've said before. Apt-get says that GCC is already installed, but running ./configure results in "could not find a working compiler". So far I only need it, so I can compile myself some decent Torrent client (the ones in the repo are pretty bad) but I'm afraid I'm gonna need it for more apps as well.

---

### Post by lynxus on 2007-05-07
Try installing build-essential ?


```
sudo apt-get install build-essential
```

---

