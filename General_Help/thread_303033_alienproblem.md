---
title: "alienproblem"
date: 2006-11-19
forum: General Help
---

### Post by doh224 on 2006-11-19
hi all! 

I've tried to convert this rpm file a few times, (thats why it says that it already exist) and it keeps saying this:

doh224@doh224-desktop:~/Desktop$ sudo alien flash.rpm 
Warning: Skipping conversion of scripts in package nspluginwrapper: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
mkdir: kan ikke oprette katalog 'nspluginwrapper-0.9.90.3': File exists
mkdir: kan ikke oprette katalog 'nspluginwrapper-0.9.90.3/debian': File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/nspluginwrapper
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current build architecture i386 does not appear in package's list (amd64)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Fejl 1
find: nspluginwrapper-0.9.90.3: No such file or directory
doh224@doh224-desktop:~/Desktop$ rm nspluginwrapper-i386-0.9.90.1
rm: kan ikke fjerne katalog 'nspluginwrapper-i386-0.9.90.1': Is a directory
doh224@doh224-desktop:~/Desktop$ sudo rm nspluginwrapper-i386-0.9.90.1
rm: kan ikke fjerne 'nspluginwrapper-i386-0.9.90.1': Is a directory

there is created a folder on the Desktop, but it is not a deb file?
thanks, if help comes!

-doh

---

### Post by doh224 on 2006-11-20
please help. I have the 6.10 ubuntu. and I can't get my flash working without alien?

---

### Post by doh224 on 2006-11-20
should I reinstall alien?

---

### Post by xopher on 2006-11-25
I don't know what's causing that but I made deb's of the latest nspluginwrapper, which should work for you too.

Check out my post here:

[http://ubuntuforums.org/showpost.php?p=1792581&postcount=27](http://ubuntuforums.org/showpost.php?p=1792581&postcount=27)

;)

---

