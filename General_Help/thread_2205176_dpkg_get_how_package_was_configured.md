---
title: "dpkg get how package was configured"
date: 2014-02-12
forum: General Help
---

### Post by krafczyk-matthew on 2014-02-12
Hi, I'd like to know how an installed package was configured.

for instance gcc gives this information when you execute gcc -v, however I'd like to know that for libc or binutils which consists of several sub programs.

Any idea how to do this?

---

### Post by jeanjd63 on 2014-02-12
Hello
You can try :
**dpkg -L *name_of_package***

---

### Post by krafczyk-matthew on 2014-02-12
That just gives me a list of the files installed with the package, and not the options used to configure the package.

what I would like is ./configure --option1 --option2 etc..

---

### Post by philinux on 2014-02-12
> **krafczyk-matthew said:**
> Hi, I'd like to know how an installed package was configured.

for instance gcc gives this information when you execute gcc -v, however I'd like to know that for libc or binutils which consists of several sub programs.

Any idea how to do this?

You might need to look at the source code for the package.

[http://askubuntu.com/questions/86054/configuration-and-compilation-settings-used-for-ubuntu-packages](http://askubuntu.com/questions/86054/configuration-and-compilation-settings-used-for-ubuntu-packages)

And see [http://ubuntuforums.org/showthread.php?t=2063328](http://ubuntuforums.org/showthread.php?t=2063328)

---

### Post by jeanjd63 on 2014-02-12
> **krafczyk-matthew said:**
> That just gives me a list of the files installed with the package, and not the options used to configure the package.

what I would like is ./configure --option1 --option2 etc..


The package files for inst suppress etc.. are in :
**/var/lib/dpkg/info**

---

### Post by krafczyk-matthew on 2014-02-12
For jeanjd63's suggestion, the only files for binutils are:

binutils.list
binutils.md5sums
binutils.postinst
binutils.postrm
binutils.shlibs

And none of these files seems to be a list of options the package was configured with.

For philinux's suggestion,

apt-get source binutils gets me the source for the binutils package. The posts you linked me to suggested that I look in debian/rules inside that source package, however this file is a huge script with no clear section giving all the options. Is there a way to run just the configure step for this package? Then ideally I could just look at the config.log to see the used options.

---

### Post by krafczyk-matthew on 2014-02-13
In the end I found the answer here: [http://askubuntu.com/questions/48499/where-can-i-find-the-configure-options-used-to-build-a-package](http://askubuntu.com/questions/48499/where-can-i-find-the-configure-options-used-to-build-a-package)

You can navigate to the launchpad source page for the package in question, then for a specific version of ubuntu and a specific architecture, you can find the buildlog. If you search for 'configure' you'll see the options used.

---

