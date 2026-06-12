---
title: "Problems compiling ndiswrapper"
date: 2005-05-11
forum: General Help
---

### Post by vtrac on 2005-05-11
I'm following the instructions from [http://dossy.org/archives/000110.html](http://dossy.org/archives/000110.html) to compile ndiswrapper 1.1, but I'm having problems.  I can create the ndiswrapper-utils package fine using debian/rules binary-utils, but when I do debian/rules binary-modules, I get this error:

```
victor@saturn:/usr/src/modules/ndiswrapper$ sudo debian/rules binary-modules
sed -e 's/#KVERS#/2.6.10-5-686/g' \
-e 's/#NDISVERS#/1.1/g' \
-e 's/#DATE#/'"`date --rfc-822`"'/g' \
        -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
        debian/changelog.template > debian/changelog
sed -e 's/#KVERS#/2.6.10-5-686/' \
-e 's/#NDISVERS#/1.1/' \
debian/control.modules > debian/control
sed -e 's/#KVERS#/2.6.10-5-686/' debian/postinst.modules > debian/postinst
if [ 6 == 4 ];then \
        module=ndiswrapper.o; \
else \
        module=ndiswrapper.ko; \
fi; \
echo "driver/$module /lib/modules/2.6.10-5-686/misc" \
        > debian/ndiswrapper-modules-2.6.10-5-686.install
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installdocs
dh_installexamples
dh_installdebconf
dh_installdirs lib/modules/2.6.10-5-686/misc
/usr/bin/make -C /usr/src/modules/ndiswrapper/driver
make[1]: Entering directory `/usr/src/modules/ndiswrapper/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-686/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/usr/src/modules/ndiswrapper/driver'
make: *** [build-modules] Error 2
victor@saturn:/usr/src/modules/ndiswrapper$       
```

So I installed the linux-source-2.6.10 package, untar'd the bz file and symlinked it to /usr/src/linux/ and reran "sudo debian/rules binary-modules KSRC=/usr/src/linux", but I am still getting the same error.  

What am I doing wrong?

---

### Post by vtrac on 2005-05-12
Any ideas as to why I can't compile?

---

