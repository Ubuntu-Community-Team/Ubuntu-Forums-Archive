---
title: "compiling apparmor"
date: 2014-01-09
forum: General Help
---

### Post by Previous1 on 2014-01-09
On Xubuntu 12.04 (3.8 raring kernel), apparmor doesn't support block_suspend, per bug 1199933:

[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1199933](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1199933)

If I understand correctly I have to recompile apparmor to get it working. After installing texlive-install-base, make and make check succeeded for apparmor-parser (2.8.2 from launchpad). I then uninstalled apparmor/apparmor-utils and ran (sudo checkinstall) make install. 

When installing the package, I got the following error:
```
trying to overwrite '/usr/lib/gcc/i686-linux-gnu/4.6/libstdc++.a', which is also in package libstdc++6-4.6-dev 4.6.3-1ubuntu5
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
```

But removing libstdc++ would also remove 
```
build-essential g++ g++-4.6 kernel-package libstdc++6-4.6-dev
```

I'd appreciate a push in the right direction

---

### Post by mc4man on 2014-01-09
I think you'd be far better off just getting the current apparmor source for precise, patching it, rebuilding to the package set & then installing whatever package(s) from that set that you need.
So in this case the package(s) you do replace are basically just a re-install. Now when you do that, after re-install sometimes those packages will show up as being upgradeable back to the ubuntu repo ones you just replaced.

Not really that big of a deal as you just don't let them get upgraded back to the non patched one(s).
The only way around that is to up the new build version slightly, ex. in this case from 2.7.102-0ubuntu3.9 to 2.7.102-0ubuntu3.9.1 
The danger there may be that there could be some sources *may* dep on a specific apparmor version rather than a >=. 
So i'd just leave current version alone which, if your patched version was an issue would let you just upgrade back to the current unpatched packages

Basically simple - 
create a build folder, cd to it, then - 
```
sudo apt-get build-dep apparmor
```
```
apt-get source apparmor
```
cd to the apparmor folder & apply your patch

apparmor uses quilt so generally better to commit the changes before building though possibly this command will let you bypass - 
```
fakeroot debian/rules binary
```

To commit first, after patching & at the prompt of the apparmor source - 
```
dpkg-source --commit
```
if asked choose nano, once open no editing needed, just go - 
ctrl+o
enter
ctrl+x
Then from same prompt - 
```
dpkg-buildpackage -rfakeroot -d -us -uc
```

After build put any of the packages created that you need to replace in a new folder, cd to that folder & go (just make a folder inside your build folder named in
```
sudo dpkg -i *.deb
```

If only replacing 1 package then just click on that package & use gdebi or maybe even software-center (haven't used 12.04 in a while

---

### Post by Previous1 on 2014-01-09
It worked! (I installed debian-keyring also) Thanks for the detailed reply.

---

