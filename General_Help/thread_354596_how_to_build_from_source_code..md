---
title: "how to build from source code."
date: 2007-02-06
forum: General Help
---

### Post by burmanabhay88 on 2007-02-06
I have the source code to VMWare Server. It was available in .tar.gz form. Can someone please tell me as to how do i build the software from the source. I'm new to linux, please give as many details as possible.

---

### Post by boredandblogging.com on 2007-02-06
Why do you want to build from source? I didn't know the source was even available for vmware.

---

### Post by lamego on 2007-02-06
That is not the source, it's an archive but with the binaries.

Read how to install it:
[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

---

### Post by Dr Small on 2007-02-06
If it isn't in the repository, then building from source is an only option....
Most programs you compile from source have an INSTALL and or README file located in the extracted directory. Read that, and begin from there.


Dr Small

---

### Post by renzokuken on 2007-02-06
not sure on the specifics for vmware server but its usually

```
sudo apt-get install build-essential
```

(needed for compiling from source)

then, extract the .tar.bz file (its like a .zip) just right click and select "extract here". then cd to the directory

```
cd /path/to/extracted/directory
```

then run

```

./configure
make
sudo make install

```

**EDIT**:about 4 poeple beat me with a better answer, but the above is worth noting if you do ever need to compile from source

---

