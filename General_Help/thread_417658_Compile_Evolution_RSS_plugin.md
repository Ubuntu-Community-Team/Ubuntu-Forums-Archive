---
title: "Compile Evolution RSS plugin"
date: 2007-04-21
forum: General Help
---

### Post by Robvdl on 2007-04-21
Hi all, I am trying to compile the newly released Evolution RSS reader plugin in Ubuntu Feisty: [http://mips.edu.ms/evo/index.php/Evolution_RSS_Reader_Plugin](http://mips.edu.ms/evo/index.php/Evolution_RSS_Reader_Plugin)

I tried running ./configure and installed any development packages it told me it needed. All but one that is...

No package 'evolution-plugin-2.8' found

The package requirements for building state that evolution-plugin-2.8 >= 2.3.1 is needed however evolution-plugins-2-10.1-0ubuntu2 is installed (I am not sure if this is the same package). I also installed evolution-dev. It still complains about needing evolution-plugin-2.8

Any ideas what I can do to compile this package for Feisty?

---

### Post by mapes on 2007-04-25
Hi, 

First make sure you have evolution-dev installed (apt-get install evolution-dev).
Then use the this patch [http://mips.edu.ms/evo-rss-0.0.1.patch]("http://mips.edu.ms/evo-rss-0.0.1.patch")
To apply patch copy evo-rss-0.0.1.patch to evolution-rss-0.0.1 directory and issue: 

```
patch -p1 < evo-rss-0.0.1.patch
autoconf
automake
```

then continue installation as normal:

```
./configure
make
make install
```

---

### Post by Robvdl on 2007-04-30
Sorry for the late reply, but thanks.. the patch works great. :)

---

### Post by drew1964 on 2007-11-08
Hi,

I'm new to ubuntu and trying to get a handle on it. At the moment I'm trying to get the RSS plugin working for evolution.... I can't find the patch you guys are talking about the link seems dead. Any idea where it might be now?

Thanks

Drew

---

