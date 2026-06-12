---
title: "Unoacking tarballs 'tar vxfz"
date: 2008-06-29
forum: General Help
---

### Post by Ballena on 2008-06-29
Hi

How come you always use the parameters : 

```
tar xvfz  <file>
```

when you unpack tarballs? Why just xvfz? I have red the man for tar but still I don't see why you use the combinations of x, v, f, & z. 

Please help me out :)

---

### Post by HalPomeranz on 2008-06-29
"x" is "extract", meaning you'll be unpacking the tarball

"f" is "file" because you're going to be specifying the file name of the tarball on the command line.  This is actually a historical legacy from the days when people still used magnetic tape for storage-- tar stands for "Tape ARchive" and the default if you don't specify a file name with "f" is that tar will try to read from /dev/rmt or whatever your tape device is.

"z" means that the tarball is compressed with gzip (has a .tar.gz or .tgz extension)

"v" is for verbose and causes the names of the files in the archive to be output as the archive is being unpacked.  I actually don't use this option all that much because it really slows down unpacking the archive when there are a lot of files.

Other options you might use include "p" to "preserve" ownerships, timestamps, etc on files unpacked from the archive (this is the default if you unpack the archive with root privs, like when you use "sudo tar ..."), or "j" if the archive is compressed with bzip2 (archive has a .tar.bz2 extension).

---

### Post by Ballena on 2008-06-29
Oh thanks! That explained everything.

---

### Post by geirha on 2008-06-29
the tar installed in ubuntu will automatically detect if it is compressed with gzip or bzip2 though, so you can unpack with just ```
tar xf archive.tar.gz
```

---

