---
title: "How do I install testdisk without internet access?"
date: 2007-11-11
forum: General Help
---

### Post by level125newb on 2007-11-11
Hello.  I have ran into a problem with finding out how to install testdisk/photorec without internet access from the computer with Ubuntu on it.

This is what I did:
I went here: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download) and downloaded the "Linux, tar.bz2 " one.  I extracted it on my windows computer and put the extracted files on my memory stick.
I opened the memory stick up on my ubuntu computer.
There are folders with files I don't know what to do with.

Could someone please give me exact instructions on what to do with the files that are in there to install it?  Inside of there there's a folder called linux that has two "troff" documents, and two files that are called photorec_static and testdisk_static.  They are executables.  But when I double click on one of them it doesn't do anything.  Please, I really need help.


Thanks.

---

### Post by ppietryga on 2007-11-11
Ok, here is what I did:

```

wget http://www.cgsecurity.org/testdisk-6.8.linuxstatic.tar.bz2

```

then put it on memory stick (without decompressing)

then put the memory stick in ubuntu machine

copy that testdisk-6.8.linuxstatic.tar.bz2 to your home directory

I like command line so in a terminal window I did this:

```

cd ~
tar -xvf testdisk-6.8.linuxstatic.tar.bz2
cd testdisk-6.8/linux
./testdisk_static

```

And you have your testdisk.

You can miss some of these steps, but:
1. It is not a good idea to run anything from memory stick
2. I guess you have a FAT filesystem on that memorystick witch does not support linux file permissions (so everything is executable)

Hope it helps :)

---

