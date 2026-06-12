---
title: "Problems with Valgrind"
date: 2013-05-26
forum: General Help
---

### Post by Raeven on 2013-05-26
Okay so I recently got Valgrind to debug some of my C programs but it doesn't seem to be working. Has anyone recieved this error before and how did you deal with it?

Sorry if this particular question had already been answered but I didn't know what exactly to search for.

---

### Post by steeldriver on 2013-05-26
What system are you running? on my 12.04 32-bit box, libc6-dbg is installed automatically as a dependency of valgrind 

```
$ apt-cache depends valgrind
valgrind
  Depends: libc6
  Depends: libc6-dbg
  Suggests: kcachegrind
  Suggests: alleyoop
  Suggests: valkyrie
  Recommends: gdb
  Conflicts: <valgrind-callgrind>

```

You can check the presence / status of the libc6-dbg package on your system

```
$ dpkg -l | grep libc6
```

---

### Post by Raeven on 2013-05-26
I believe I do. I attached some pictures of my system and results after running your code.

---

### Post by steeldriver on 2013-05-27
You appear to have libc6**-dev** but not libc6**-dbg**

```
sudo apt-get install libc6-dbg
```

---

### Post by Raeven on 2013-05-27
Thanks man!

---

