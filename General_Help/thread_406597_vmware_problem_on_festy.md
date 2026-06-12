---
title: "vmware problem on festy"
date: 2007-04-11
forum: General Help
---

### Post by toketin on 2007-04-11
i've a problem with Vmware workstation, when i try to convert the .rpm pack to a deb one it gives me this:

> marco@marco-desktop:~/Desktop$ sudo alien --scripts VMware-workstation-e.x.p-42757.x86_64.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/vmwareworkstation
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXtst (soname 6, path libXtst.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXtst (soname 6, path libXtst.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXtst (soname 6, path libXtst.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libtiff.so.3
dpkg-shlibdeps: warning: unable to find dependency information for shared library libtiff (soname 3, path libtiff.so.3, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: VMwareWorkstation-e.x.p: Nessun file o directory


i'm using ubuntu feisty amd64, how can i resolve?

---

### Post by rufius on 2007-04-11
There should be a vmware workstation package in the repos. Check this command: ```
apt-cache search vmware
```

---

### Post by toketin on 2007-04-11
i've installed it by the source

---

