---
title: "Rio Karma in Ubuntu with Amarok. Any luck?"
date: 2006-12-01
forum: General Help
---

### Post by cleentrax on 2006-12-01
I am really excited to use my Rio Karma with the new version of Amarok. I am following the instructions [here]("http://linux-karma.sourceforge.net/Karma-HOWTO.html"), which I found from the kde/Amarok website. The first part goes OK. I can mount the Karma and view its file structure with Nautilus.

But I get the following errors when I try to install libkarma:

```
gcc -fPIC -D_REENTRANT -Wall -pedantic -ggdb -W -Wchar-subscripts -Wmissing-prototypes  -Wmissing-declarations -Wno-switch -Wredundant-decls -Wno-unused   -c -o fdb.o fdb.c
fdb.c:12:18: error: zlib.h: No such file or directory
fdb.c:22: error: expected ‘)’ before ‘fdb_file’
fdb.c: In function ‘lk_fdb_load’:
fdb.c:57: error: ‘gzFile’ undeclared (first use in this function)
fdb.c:57: error: (Each undeclared identifier is reported only once
fdb.c:57: error: for each function it appears in.)
fdb.c:57: error: expected ‘;’ before ‘fdb_file’
fdb.c:58: warning: ISO C90 forbids mixed declarations and code
fdb.c:78: warning: implicit declaration of function ‘unlink’
fdb.c:85: error: ‘fdb_file’ undeclared (first use in this function)
fdb.c:85: warning: implicit declaration of function ‘gzopen’
fdb.c:90: warning: implicit declaration of function ‘fdb_read_header’
fdb.c:95: warning: implicit declaration of function ‘gzread’
fdb.c:98: warning: implicit declaration of function ‘gzclose’
fdb.c: In function ‘lk_fdb_getlist’:
fdb.c:126: error: ‘gzFile’ undeclared (first use in this function)
fdb.c:126: error: expected ‘;’ before ‘fdb_file’
fdb.c:127: warning: ISO C90 forbids mixed declarations and code
fdb.c:135: error: ‘fdb_file’ undeclared (first use in this function)
fdb.c: In function ‘lk_fdb_save’:
fdb.c:179: error: ‘gzFile’ undeclared (first use in this function)
fdb.c:179: error: expected ‘;’ before ‘fdb_file’
fdb.c:180: warning: ISO C90 forbids mixed declarations and code
fdb.c:187: error: ‘fdb_file’ undeclared (first use in this function)
fdb.c:191: warning: implicit declaration of function ‘gzwrite’
make[1]: *** [fdb.o] Error 1
make[1]: Leaving directory `.../Desktop/libkarma-0.0.6/src'
make: *** [libkarma] Error 2

```

Anyone else have their Karma working with Banshee or Amarok?

Anyone have an idea why I can't get libkarma to make install?

Thanks!

---

### Post by cleentrax on 2006-12-02
shameless bump

---

### Post by augied on 2006-12-03
Try installing zlib1g-dev, libtagc0-dev, and libusb-dev.  That worked for me.

The packages in the kubuntu repos don't have karma support.  You'll have to build it yourself.  If anyone could point me to a good guide to creating debs, I could do it.

Augie

---

### Post by augied on 2006-12-03
I'm having a different amarok/karma related problem, but I'm too lazy to start a new thread, so hear it is.

I've gotten amarok to recognize my karma in edgy.  The features are limited, but it works great.  My sister also has a karma, and she uses dapper.  I've been trying all day to set up my karma in my dapper installation, but have had no luck.  I compiled a new kernel because of some missing features needed by omfs, and then repeated everything I did in edgy.  Everything compiled fine, my karma can be mounted, and as far as I can tell, everything is installed properly, but when I try to add the karma in amarok, it is not even given as an option.

Any ideas?

Augie

---

### Post by cleentrax on 2006-12-04
I added the extra libraries you listed, and I was able to get libkarma installed thanks for that.

My Karma is mounted and available to browse in Nautilus, but I'm not getting the Karma plugin in Amarok 1.4.4 -- it's just not on the list. I'm in Edgy by the way. Haven't tried this in Dapper.

How did you get the Karma to work in Amarok in Edgy?

---

### Post by augied on 2006-12-04
> **cleentrax said:**
> I added the extra libraries you listed, and I was able to get libkarma installed thanks for that.

My Karma is mounted and available to browse in Nautilus, but I'm not getting the Karma plugin in Amarok 1.4.4 -- it's just not on the list. I'm in Edgy by the way. Haven't tried this in Dapper.

How did you get the Karma to work in Amarok in Edgy?
Are you using packages from kubuntu.org?  Like I said, karma support wasn't included, you'll have to build it yourself.  Use the '--with-libkarma' option when running the configure script.  I don't know if it's possible to build just the karma specific stuff without also building the whole program.  When I tried, it gave me a bunch of errors.  What I did was build all of amarok, then change to the karma directory (something like 'amarok-1.4.4/amarok/src/mediadevice/riokarma/') and run 'sudo make install' and everything worked.

---

### Post by cleentrax on 2006-12-04
I misunderstood you initially. I am using the Kubuntu Edgy package from kde.org. I thought that it included the Karma plugin. I'm not quite up to the task of compiling from scratch myself. Thanks for the info.

---

### Post by augied on 2006-12-05
Ok, I think I've found everything I need to know to make a deb.  As soon as I get home, I'll give it a try.

---

### Post by augied on 2006-12-06
Well, that took longer than I would have liked.  I got it completely wrong the first time, but I think I have it now.  Seeing as this is the first time I've tried something like this, I give no guaranty that these packages will work.  But I think they will.

[http://www.auddex.com/ubuntu]("http://www.auddex.com/ubuntu")

---

### Post by cleentrax on 2006-12-19
> **augied said:**
> Well, that took longer than I would have liked.  I got it completely wrong the first time, but I think I have it now.  Seeing as this is the first time I've tried something like this, I give no guaranty that these packages will work.  But I think they will.

[http://www.auddex.com/ubuntu]("http://www.auddex.com/ubuntu")

Thanks for all of your help in this. I have downloaded and installed your Amarok debs, and now I can add a "Rio Karma Media Device."

With my Karma mounted, I try to add it to Amarok, and I get the following error:
```
KLibLoader could not load the plugin: *libamarok_riokarma-mediadevice*
Error message: *libkarma.so: cannot open shared object file: No such file or directory* 
```

Everything else in Amarok seems to be working.

---

### Post by cleentrax on 2007-02-15
I finally got my karma working with amarok! It took a lot of experimenting, and a lot of help from this page ([http://jcconnor.wordpress.com/2007/02/11/my-karma-is-better-than-your-karma/)](http://jcconnor.wordpress.com/2007/02/11/my-karma-is-better-than-your-karma/)).

If you use this jcconnor walk-through, note that some of his terminal commands are missing the ends of the phrases. But you should be able to reconstruct them with a bit of common sense.

---

