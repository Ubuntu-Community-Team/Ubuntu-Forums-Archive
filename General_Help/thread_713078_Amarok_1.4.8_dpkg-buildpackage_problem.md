---
title: "Amarok 1.4.8 dpkg-buildpackage problem"
date: 2008-03-02
forum: General Help
---

### Post by descentspb on 2008-03-02
I want to compile Amarok with MP4/AAC tag write support, and i have no problem with it - it finishes succesfully and works. But when i am doing the same with "dpkg-buildpackage -rfakeroot" to make a .deb for installation on other systems, i have such an error int the middle of the make process:

```
../../amarok/src/magnatunebrowser/.libs/libmagnatunebrowser.a(magnatuneartistinfobox.o):(.data.rel.ro._ZTC22MagnatuneArtistInfoBox40_N6KParts8PartBaseE[vtable for MagnatuneArtistInfoBox]+0x80): undefined reference to `virtual thunk to KParts::PartBase::setInstance(KInstance*)'
collect2: ld returned 1 exit status
make[5]: *** [libamarok.la] Error 1
make[5]: Leaving directory `/home/descent/sources/amarok-1.4.8/amarok/src'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/descent/sources/amarok-1.4.8/amarok/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/descent/sources/amarok-1.4.8/amarok'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/descent/sources/amarok-1.4.8'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/descent/sources/amarok-1.4.8'
make: *** [build-stamp] Error 2

```

Note, that just ./configure - make - make install works perfectly. What can i try to do to solve the problem?

Also, checkinstalling doesn't work. I mean it works, but amarok from it can't launch after the installation on a clean system.

---

### Post by descentspb on 2008-03-03
bump-bump.

---

### Post by descentspb on 2008-03-06
and a bump again

---

### Post by descentspb on 2008-03-13
Bumpy Bumpy Bump

---

### Post by descentspb on 2008-05-05
bump

---

### Post by descentspb on 2008-05-06
bump

---

