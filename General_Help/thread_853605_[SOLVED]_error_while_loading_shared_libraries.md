---
title: "[SOLVED] error while loading shared libraries"
date: 2008-07-08
forum: General Help
---

### Post by dodle on 2008-07-08
I am trying to install [LiVES]("http://sourceforge.net/project/showfiles.php?group_id=64341") onto my system.  I've already tried compiling the source (unsuccessfully).  So I decided to convert the lives-0.9.8.12-1.fc8.i386.rpm package to a .deb with alien.  I open a terminal and type in *lives*, and get the following error:  

[QUOTE="LiVES when I tried to run it in a terminal"]lives: error while loading shared libraries: libmjpegutils-1.9.so.0: cannot open shared object file: No such file or directory[/QUOTE]

Before the installation, gdebi confirmed that all package dependencies were satisfied.  Any ideas?

<HTML>ARG</HTML>

---

### Post by HalPomeranz on 2008-07-08
On my system that library is part of the "libmjpegtools0c2a" package.  Try "sudo apt-get install libmjpegtools0c2a".

Note that on my system the version of the library in the package from the repositories is libmjpegutils-1.8.so.0 (not 1.9), but I'm on x86_64.  It may be that you still have problems after the apt-get install due to the mismatch in version numbers.  The following command will probably fix your problem if this is the case:

```

sudo ln -s /usr/lib/libmjpegutils-1.8.so.0 /usr/lib/libmjpegutils-1.9.so.0

```

---

### Post by dodle on 2008-07-08
Thanks, that worked.  I already had the libmjpegtools installed, and you were right it was 1.8.

What does it mean to make a symbolic link?

---

### Post by HalPomeranz on 2008-07-08
A symbolic link is just a pointer that links one file name to another file.  In this case, the binary you're using is looking for v1.9 of the library, and we use the symlink to fool the binary into thinking it's opening v1.9 when it's in fact opening v1.8.  In most cases this works because the differences between the two versions are not significant changes to the function call API, just minor functionality improvements or bug fixes.

In terms of what's going on at a technical level, a symlink is just a special kind of file that's recognized by the operating system.  The contents of the symlink "file" is actually the path name of the file that the symlink points to.  Try this:

```

$ **ls -l /usr/lib/libmjpegutils-1.9.so.0**
lrwxrwxrwx 1 root root 31 2008-07-08 15:55 /usr/lib/libmjpegutils-1.9.so.0 -> /usr/lib/libmjpegutils-1.8.so.0

```

Do you see that the size of the symlink "file" is 31 bytes?  If you count the characters in "/usr/lib/libmjpegutils-1.8.so.0" you'll find that it's exactly 31 characters.

---

