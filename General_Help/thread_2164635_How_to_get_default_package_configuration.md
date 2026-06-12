---
title: "How to get default package configuration"
date: 2013-08-01
forum: General Help
---

### Post by startas on 2013-08-01
How can i get ubuntu's default configuration of some package ? I want to build some new versions of libraries and drivers myself from source, and i need to know, how to get default configure flags, i.e., i have "intel-2d-driver", or "calculations-library", and i need to get default configure flags, that ubuntu uses - "./configure --prefix=install/here --enable-feature-1 --enable-something="a, b, c" --disable-feature-3".

---

### Post by slickymaster on 2013-08-01
I'm not quite sure if what you're looking for is this, but you can reconfigure any package with ```
dpkg-reconfigure PACKAGENAME
```

---

### Post by startas on 2013-08-01
Not this. I need to get default ubuntu configuration, that is used to build packages from source, i.e. if you have gnu c compiler, then you can type "gcc -v", and you will get many info, version number, and configuration flags, that are used to build gcc, its something like : "--enable-languages=c,c++ --with-gmp=/ ...", so i need a way to get those configure flags of every other ubuntu package.

---

### Post by startas on 2013-08-01
Found it - you have to go to [https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/) , then go to any version, then select/search for package, then select url under "source package", select arch under "builds", and there is "buildlog", and just search for "./configure", or "configure".

---

