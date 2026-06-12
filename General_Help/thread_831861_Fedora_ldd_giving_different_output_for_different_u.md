---
title: "Fedora: ldd giving different output for different users"
date: 2008-06-17
forum: General Help
---

### Post by amitst on 2008-06-17
I have upgraded one of my machines from Fedora7 to Fedora9. I am faced with a strange issue while using the svn binary. Through the regular user, the svn binary is working fine. However, through root user it is giving a library missing error. I checked that the binary path is the same in both cases. The error given is,
```
# svn
svn: error while loading shared libraries: libneon.so.25: cannot open shared object file: No such file or directory

```

I found that the ldd command is displaying different output through a non-root user and the root user (su). Notably libneon.so.25 library is used instead of libneon.so.27 as shown in the regular user. What might be going wrong?

Here is the ldd output from both users,

Non root user output
```
$ ldd /usr/bin/svn | grep libneon
        libneon.so.27 => /usr/lib/libneon.so.27 (0x004cd000)

```

The output for root user (su)
```
# ldd /usr/bin/svn | grep libneon
        libneon.so.27 => /usr/lib/libneon.so.27 (0x004b1000)
        libneon.so.25 => not found

```

---

### Post by amitst on 2008-06-18
For now I have put the following hack to make the svn binary work for the root user,

```
# cd /usr/lib
# ln -s libneon.so.27 libneon.so.25

```

---

