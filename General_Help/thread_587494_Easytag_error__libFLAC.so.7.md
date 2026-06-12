---
title: "Easytag error:  libFLAC.so.7"
date: 2007-10-22
forum: General Help
---

### Post by trak87 on 2007-10-22
Got this error in Gutsy while trying to start easytag:

> easytag: error while loading shared libraries: libFLAC.so.7: cannot open shared object file: No such file or directory

Creating a symbolic link to libFLAC.so.8.0.1 seems to solve the problem:

```
cd /usr/lib
sudo ln -s libFLAC.so.8.0.1 libFLAC.so.7
```

---

### Post by trak87 on 2007-10-22
Nope. Don't follow my advice above. It doesn't work. Got this when trying to tag a flac file:

> easytag: symbol lookup error: easytag: undefined symbol: FLAC__file_decoder_new

---

### Post by trak87 on 2007-10-22
Okay, this seems to work: I went to [http://packages.debian.org/etch/libflac7](http://packages.debian.org/etch/libflac7) and installed the package for my platform, libflac7_1.1.2-6_i386.deb in my case. Easytag now handles flac files.

---

