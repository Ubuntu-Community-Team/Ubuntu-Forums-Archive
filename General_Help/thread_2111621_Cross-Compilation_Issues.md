---
title: "Cross-Compilation Issues"
date: 2013-02-02
forum: General Help
---

### Post by bearbin on 2013-02-02
I am using gcc to compile a C++ application on my CI server ([http://ci.berboe.co.uk](http://ci.berboe.co.uk)) and as the vps that it is compiled on has the x86-64 architecture I need to cross-compile to get the compiled program to work on x86 computers.

I have installed gcc-multilib and g++-multilib and several other packages that were suggested in other places, but I still get an error when trying to compile. It is:

```
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
```

Full logs are available here: [http://ci.berboe.co.uk/job/MCServer%20Linux-x86/11/console](http://ci.berboe.co.uk/job/MCServer%20Linux-x86/11/console)

Any help towards resolving this issue would be much appreciated.

---

