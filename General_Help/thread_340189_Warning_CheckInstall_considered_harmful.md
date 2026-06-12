---
title: "Warning: CheckInstall considered harmful"
date: 2007-01-16
forum: General Help
---

### Post by BReflection on 2007-01-16
I am posting this here so that it will come up when people Google for CheckInstall and so that they do not waste their time with the software like I did. I have sent e-mails containing this information to their development list, but their mailing list archives are not public and I received no response. CheckInstall was initially suggested to me in #ubuntu on Freenode. Please do not recommend this software to others anymore.

CheckInstall would be very convenient software for creating packages, were it not for its practically non-existent handling of symlinks. A very prevalent versioning system (especially if you use the autotools) is to use symlinks in /usr/local/lib to point to your current library, such as this:

> ls -l /usr/local/lib | grep Blah
libBlah.so -> libBlah.so.3.2.5

But CheckInstall DOES NOT put your symlinks in the package, even if you manually specify them using "--include=". When you try to run your software after installing the package, it will complain about not being able to find your libraries. It's not a huge hassle to just add the symlinks yourself, but that defies the point of creating packages in the first place.

But it doesn't end there. CheckInstall is actually *dangerous*. Our laboratory has /usr/local as a symlink to another hard drive. Because CheckInstall does not handle symlinks correctly, any directories which are actually symlinks will be deleted when you uninstall your package. Any directories that are not symlinks will cause dpkg to give an error, saying that it was told to delete these directories but it is not going to do it because they are not empty.

I ran across this software because I need to create .rpm and .deb packages and it sounded promising. If you find this thread, I suggest you instead stick to the [Debian New Maintainer's Guide](http://www.debian.org/doc/maint-guide/ch-start.en.html). It is more time consuming, but you will not take the risk of creating harmful packages.

I hope you find this information useful. ](*,)

---

### Post by frodon on 2007-01-17
This is normal because the purpose of checkinstall is not to create packages, the package provided is just a plus which may be sometimes useful but this is clearly not the way to create packages.

---

### Post by Perfect Storm on 2007-01-17
I agree. Checkinstall is not the way to make package(s). Generally it's used for if you compiled X application and want to an "easy" way to uninstall it via synaptic or other. Though having the sourcecode you compiled X application you can easely run sudo make uninstall or similiar.

---

