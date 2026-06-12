---
title: "gcc not found"
date: 2007-06-03
forum: General Help
---

### Post by owl on 2007-06-03
Hello everybody  :)

Well, it is very strange indeed. I have dapper drake and kubuntu installed ( I have everything concerning gcc (different versions installed), build essential is there as well. I checked everything with locate and adept.
So as everything seems (to my knowledge) to be there to compile, how is it that i get the answer gcc: not found every time i try to compile from source?? What can be he problem in this case?
 is it a problem with my PATH? here it is:

 ~$ echo $PATH
/home/grandhibou/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

when i locate gcc:
/$ locate gcc
/var/lib/dpkg/info/gcc-4.0-base.postinst
/var/lib/dpkg/info/gcc-4.0-base.list
/var/lib/dpkg/info/gcc-4.0-base.md5sums
/var/lib/dpkg/info/libgcc1.shlibs
/var/lib/dpkg/info/libgcc1.list
/var/lib/dpkg/info/libgcc1.postinst
/var/lib/dpkg/info/libgcc1.postrm
/var/lib/dpkg/info/libgcc1.md5sums
/var/lib/dpkg/info/gcc-3.3-base.md5sums
/var/lib/dpkg/info/gcc-3.3-base.list
/var/lib/dpkg/info/gcc-3.3.md5sums
/var/lib/dpkg/info/gcc-3.3.list
/var/lib/dpkg/info/gcc-3.4-base.md5sums
/var/lib/dpkg/info/gcc-3.4-base.list
/var/lib/dpkg/info/gcc-3.4.md5sums
/var/lib/dpkg/info/gcc-3.4.list
/var/lib/dpkg/info/gcc-4.0.md5sums
/var/lib/dpkg/info/gcc-4.0.list
/var/lib/dpkg/info/gcc.postinst
/var/lib/dpkg/info/gcc.list
/var/lib/dpkg/info/gcc.preinst
/var/lib/dpkg/info/gcc.prerm
/var/lib/dpkg/info/gcc.md5sums
/home/grandhibou/images/gcc.jpg
/home/grandhibou/OS/vmware linux 5.5.1.1.191175/setup/vmware-distrib/lib/lib/libgcc_s.so.1
/home/grandhibou/OS/vmware linux 5.5.1.1.191175/setup/vmware-distrib/lib/lib/libgcc_s.so.1/libgcc_s.so.1
/home/grandhibou/logiciels/multimedia/freevo-1.5.4/freevo-1.5.4/contrib/rpm/SDL-1.2.6-gcc3.patch
/home/grandhibou/logiciels/java/jre1.5.0_06/lib/i386/libjavaplugin_nscp_gcc29.so
/home/grandhibou/logiciels/java/jre1.5.0_06/plugin/i386/ns7-gcc29
/home/grandhibou/logiciels/java/jre1.5.0_06/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/home/grandhibou/logiciels/outils_système/Vmware linux workstation 5.5.3.34685/VMware-workstation-5.5.3/vmware-distrib/lib/lib/libgcc_s.so.1
/home/grandhibou/logiciels/outils_système/Vmware linux workstation 5.5.3.34685/VMware-workstation-5.5.3/vmware-distrib/lib/lib/libgcc_s.so.1/libgcc_s.so.1
/home/grandhibou/White hat/hydra-5.4-src/hydra-5.4-src/arm/gcc-arm-env.sh
/lib/libgcc_s.so.1
/usr/share/doc/gcc-4.0-base
/usr/share/doc/gcc-4.0-base/changelog.gz
/usr/share/doc/gcc-4.0-base/TODO.Debian
/usr/share/doc/gcc-4.0-base/copyright
/usr/share/doc/gcc-4.0-base/.copyright
/usr/share/doc/gcc-4.0-base/README.Debian.gz
/usr/share/doc/gcc-4.0-base/changelog.Debian.gz
/usr/share/doc/gcc-4.0-base/.changelog.Debian.gz
/usr/share/doc/gcc-4.0-base/README.Bugs
/usr/share/doc/gcc-4.0-base/gcc
/usr/share/doc/gcc-4.0-base/gcc/changelog.gz
/usr/share/doc/gcc-4.0-base/NEWS.html
/usr/share/doc/gcc-4.0-base/NEWS.gz
/usr/share/doc/gcc-4.0-base/test-summary.gz
/usr/share/doc/gcc-4.0-base/FAQ.gz
/usr/share/doc/gcc-4.0-base/C++
/usr/share/doc/gcc-4.0-base/C++/README.libstdc++-baseline
/usr/share/doc/gcc-4.0-base/C++/libstdc++_symbols.txt
/usr/share/doc/gcc-4.0-base/C++/changelog.libstdc++.gz
/usr/share/doc/gcc-4.0-base/C++/README.C++
/usr/share/doc/gcc-4.0-base/C++/changelog.gz
/usr/share/doc/libgcc1
/usr/share/doc/gcc-3.3-base
/usr/share/doc/gcc-3.3-base/changelog.Debian.gz
/usr/share/doc/gcc-3.3-base/README.Debian
/usr/share/doc/gcc-3.3-base/TODO.Debian
/usr/share/doc/gcc-3.3-base/copyright
/usr/share/doc/gcc-3.3-base/changelog.gz
/usr/share/doc/gcc-3.3-base/README.Bugs
/usr/share/doc/gcc-3.3-base/gcc
/usr/share/doc/gcc-3.3-base/gcc/changelog.gz
/usr/share/doc/gcc-3.3-base/NEWS.html
/usr/share/doc/gcc-3.3-base/NEWS.gz
/usr/share/doc/gcc-3.3-base/test-summary.gz
/usr/share/doc/gcc-3.3-base/FAQ.gz
/usr/share/doc/gcc-3.4-base
/usr/share/doc/gcc-3.4-base/README.Debian.gz
/usr/share/doc/gcc-3.4-base/NEWS.Debian.gz
/usr/share/doc/gcc-3.4-base/TODO.Debian
/usr/share/doc/gcc-3.4-base/copyright
/usr/share/doc/gcc-3.4-base/changelog.gz
/usr/share/doc/gcc-3.4-base/README.Bugs
/usr/share/doc/gcc-3.4-base/gcc
/usr/share/doc/gcc-3.4-base/gcc/changelog.gz
/usr/share/doc/gcc-3.4-base/changelog.Debian.gz
/usr/share/doc/gcc-3.4-base/NEWS.html
/usr/share/doc/gcc-3.4-base/NEWS.gz
/usr/share/doc/gcc-3.4-base/test-summary.gz
/usr/share/doc/gcc-3.4-base/FAQ.gz
/usr/share/doc/gcc-3.3
/usr/share/doc/gcc-3.4
/usr/share/doc/gcc-4.0
/usr/share/doc/gcc
/usr/share/man/man1/winegcc.1.gz
/usr/share/man/man1/gccbug-3.3.1.gz
/usr/share/man/man1/gcc-3.3.1.gz
/usr/share/man/man1/gccbug-3.4.1.gz
/usr/share/man/man1/i486-linux-gnu-gcc-3.3.1.gz
/usr/share/man/man1/gcc-3.4.1.gz
/usr/share/man/man1/i486-linux-gnu-gcc-3.4.1.gz
/usr/share/man/man1/gccbug-4.0.1.gz
/usr/share/man/man1/gcc-4.0.1.gz
/usr/share/man/man1/i486-linux-gnu-gcc-4.0.1.gz
/usr/share/man/man1/gccbug.1.gz
/usr/share/man/man1/gcc.1.gz
/usr/share/man/man1/i486-linux-gnu-gcc.1.gz
/usr/share/man/man7/gfdl.7gcc.gz
/usr/share/man/man7/gpl.7gcc.gz
/usr/share/man/man7/fsf-funding.7gcc.gz
/usr/share/lintian/overrides/libgcc1
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gcc-4.0.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gcc-3.4.mo
/usr/share/locale-langpack/fr/LC_MESSAGES/gcc-3.4.mo
/usr/share/locale-langpack/fr/LC_MESSAGES/gcc-4.0.mo
/usr/bin/gcc
/usr/bin/winegcc
/usr/bin/gcc-3.3
/usr/bin/gccbug-3.3
/usr/bin/gcc-3.4
/usr/bin/i486-linux-gnu-gcc-3.3
/usr/bin/gccbug-3.4
/usr/bin/i486-linux-gnu-gcc-3.4
/usr/bin/gcc-4.0
/usr/bin/i486-linux-gnu-gcc
/usr/bin/gccbug-4.0
/usr/bin/gccbug
/usr/bin/i486-linux-gnu-gcc-4.0
/usr/lib/libgccpp.so.1.0.2
/usr/lib/libgccpp.so.1
/usr/lib/openoffice/program/libsalhelpergcc3.so.3
/usr/lib/openoffice/program/libcppuhelpergcc3.so.3
/usr/lib/openoffice/program/libcomphelp4gcc3.so
/usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
/usr/lib/openoffice/program/libgcc3_uno.so
/usr/lib/openoffice/program/libi18nregexpgcc3.so
/usr/lib/openoffice/program/libi18nisolang1gcc3.so
/usr/lib/openoffice/program/libi18nutilgcc3.so
/usr/lib/openoffice/program/libjvmaccessgcc3.so.3
/usr/lib/openoffice/program/libuno_salhelpergcc3.so.3
/usr/lib/openoffice/program/libucbhelper3gcc3.so
/usr/lib/openoffice/program/libvos3gcc3.so
/usr/lib/libstlport_gcc.so.4.6
/usr/lib/gcc
/usr/lib/gcc/i486-linux-gnu
/usr/lib/gcc/i486-linux-gnu/4.0.3
/usr/lib/gcc/i486-linux-gnu/4.0.3/collect2
/usr/lib/gcc/i486-linux-gnu/4.0.3/include
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/iso646.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/README
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mcpp_gcc40_predef_old.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mcpp_gcc40_predef_std.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mcpp_gxx40_predef_old.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mcpp_gxx40_predef_std.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/float.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/stdarg.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/stdbool.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/stddef.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/syslimits.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/unwind.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/varargs.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/asm
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/asm/posix_types.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mmintrin.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/emmintrin.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/pmmintrin.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/xmmintrin.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mm3dnow.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mm_malloc.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/cc1
/usr/lib/gcc/i486-linux-gnu/4.0.3/64
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/libstdc++.so
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/libgcc.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/libgcc_eh.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/libgcov.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/crtbegin.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/crtbeginS.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/crtbeginT.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/crtend.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/crtendS.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/libgcc_s.so
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/libstdc++.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/libsupc++.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/SYSCALLS.c.X
/usr/lib/gcc/i486-linux-gnu/4.0.3/libgcc.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/libgcc_eh.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/libgcov.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/crtbegin.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/crtbeginS.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/crtbeginT.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/crtend.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/crtendS.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/libgcc_s_64.so
/usr/lib/gcc/i486-linux-gnu/4.0.3/libgcc_s.so
/usr/lib/gcc/i486-linux-gnu/4.0.3/libstdc++.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/libsupc++.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/libstdc++.so
/usr/lib/gcc/i486-linux-gnu/4.0.3/cc1plus
/usr/lib/gcc/i486-linux-gnu/3.4.6
/usr/lib/gcc/i486-linux-gnu/3.4.6/include
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/iso646.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/README
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/float.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/limits.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/stdarg.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/stdbool.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/stddef.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/syslimits.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/unwind.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/varargs.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/asm
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/asm/posix_types.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/mmintrin.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/emmintrin.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/pmmintrin.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/include/xmmintrin.h
/usr/lib/gcc/i486-linux-gnu/3.4.6/cc1
/usr/lib/gcc/i486-linux-gnu/3.4.6/collect2
/usr/lib/gcc/i486-linux-gnu/3.4.6/64
/usr/lib/gcc/i486-linux-gnu/3.4.6/64/libgcc_s_64.so
/usr/lib/gcc/i486-linux-gnu/3.4.6/64/libgcc.a
/usr/lib/gcc/i486-linux-gnu/3.4.6/64/libgcc_eh.a
/usr/lib/gcc/i486-linux-gnu/3.4.6/64/libgcov.a
/usr/lib/gcc/i486-linux-gnu/3.4.6/64/crtbegin.o
/usr/lib/gcc/i486-linux-gnu/3.4.6/64/crtbeginS.o
/usr/lib/gcc/i486-linux-gnu/3.4.6/64/crtbeginT.o
/usr/lib/gcc/i486-linux-gnu/3.4.6/64/crtend.o
/usr/lib/gcc/i486-linux-gnu/3.4.6/64/crtendS.o
/usr/lib/gcc/i486-linux-gnu/3.4.6/64/libgcc_s.so
/usr/lib/gcc/i486-linux-gnu/3.4.6/libgcc.a
/usr/lib/gcc/i486-linux-gnu/3.4.6/specs
/usr/lib/gcc/i486-linux-gnu/3.4.6/libgcc_s_64.so
/usr/lib/gcc/i486-linux-gnu/3.4.6/libgcc_eh.a
/usr/lib/gcc/i486-linux-gnu/3.4.6/libgcov.a
/usr/lib/gcc/i486-linux-gnu/3.4.6/crtbegin.o
/usr/lib/gcc/i486-linux-gnu/3.4.6/crtbeginS.o
/usr/lib/gcc/i486-linux-gnu/3.4.6/crtbeginT.o
/usr/lib/gcc/i486-linux-gnu/3.4.6/crtend.o
/usr/lib/gcc/i486-linux-gnu/3.4.6/crtendS.o
/usr/lib/gcc/i486-linux-gnu/3.4.6/libgcc_s.so
/usr/lib/vmware/lib/libgcc_s.so.1
/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1.old.0
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjavaplugin_nscp_gcc29.so
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7-gcc29
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/googleearth/libgcc_s.so.1
/usr/lib/gcc-lib
/usr/lib/gcc-lib/i486-linux-gnu
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/iso646.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/README
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/float.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/limits.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/stdarg.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/stdbool.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/stddef.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/syslimits.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/unwind.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/varargs.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/asm
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/asm/posix_types.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/mmintrin.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/emmintrin.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/pmmintrin.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/xmmintrin.h
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/cc1
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/collect2
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/specs
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/libgcc.a
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/libgcc_eh.a
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/crtbegin.o
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/crtbeginS.o
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/crtbeginT.o
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/crtend.o
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/crtendS.o
/usr/lib/gcc-lib/i486-linux-gnu/3.3.6/libgcc_s.so
/usr/src/linux-headers-2.6.15-28-386/include/linux/compiler-gcc.h
/usr/src/linux-headers-2.6.15-28-386/include/linux/compiler-gcc2.h
/usr/src/linux-headers-2.6.15-28-386/include/linux/compiler-gcc3.h
/usr/src/linux-headers-2.6.15-28-386/include/linux/compiler-gcc4.h
/usr/src/linux-headers-2.6.15-28-386/scripts/gcc-version.sh
/usr/src/linux-headers-2.6.15-28/include/acpi/platform/acgcc.h
/usr/src/linux-headers-2.6.15-28/include/asm-ia64/gcc_intrin.h
/usr/src/linux-headers-2.6.15-28/include/asm-mips/gcc
/usr/src/linux-headers-2.6.15-28/include/asm-mips/gcc/sgidefs.h
/usr/src/linux-headers-2.6.15-28/include/linux/compiler-gcc.h
/usr/src/linux-headers-2.6.15-28/include/linux/compiler-gcc2.h
/usr/src/linux-headers-2.6.15-28/include/linux/compiler-gcc3.h
/usr/src/linux-headers-2.6.15-28/include/linux/compiler-gcc4.h
/usr/src/linux-headers-2.6.15-28/scripts/gcc-version.sh
/usr/src/linux-headers-2.6.15-28-k7/include/linux/compiler-gcc.h
/usr/src/linux-headers-2.6.15-28-k7/include/linux/compiler-gcc2.h
/usr/src/linux-headers-2.6.15-28-k7/include/linux/compiler-gcc3.h
/usr/src/linux-headers-2.6.15-28-k7/include/linux/compiler-gcc4.h
/usr/src/linux-headers-2.6.15-28-k7/scripts/gcc-version.sh
/usr/libexec/autopackage/libgcc_s.so.1


 When i type:
:/$ whereis gcc
gcc: /usr/bin/gcc /usr/lib/gcc /usr/bin/X11/gcc /usr/share/man/man1/gcc.1.gz

But then when i try to use it:
:/$ gcc
bash: gcc : commande introuvable
(means command not found in french!)

how is that possible? what can be wrong on my kubuntu?  :(

---

### Post by mlind on 2007-06-03
is /usr/bin/gcc symlink broken?

---

### Post by owl on 2007-06-04
well i don't know indeed, but may be somebody can tell me how to check that and than how to fix it if possible.
Would be great.

---

### Post by mlind on 2007-06-04
> **owl said:**
> well i don't know indeed, but may be somebody can tell me how to check that and than how to fix it if possible.
Would be great.

What's the output of
```

file /usr/bin/gcc

```

You can also see broken symlink with
```

ls -la /usr/bin/gcc

```
If the font is red in black background, symlink is broken (in gnome-terminal at least)

---

### Post by owl on 2007-06-04
That's it!

~$ file /usr/bin/gcc
/usr/bin/gcc: broken symbolic link to `/usr/bin/gcc3.4'

but how to fix that now?

---

### Post by nemarasu on 2007-06-04
you can try:

apt-get reinstall build-essential

---

### Post by owl on 2007-06-04
Ok!  i did use reinstall. but the exact command was  apt-get install --reinstall gcc
and now when i check with
~$ file /usr/bin/gcc
/usr/bin/gcc: symbolic link to `gcc-4.0'
It looks all right no? il give it a try later. Thanks guy. If not anyway i would come back in this tread of course.;)

---

### Post by mlind on 2007-06-04
I dunno if gcc uses alternatives, but I'd make the symlink point to the default compiler executable. That's gcc which build-essential installs, so I guess you're alright.

---

