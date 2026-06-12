---
title: "linux building"
date: 2007-07-02
forum: General Help
---

### Post by Techmobowl on 2007-07-02
I'm fairly new to Linux and am currently trying to build a program from source.  I couldn't find any tutorials online that I could understand and the program is not supported by my distro packager (not Ubuntu), but I thought I'd ask here anyway.

I've downloaded and unpacked the source.  When I try to use the "configure" command I get a "cannot find install-sh" error.  If anyone has any tips for me I'd appreciate it.

---

### Post by nphx on 2007-07-02
>  9. Compiling from source

Ubuntu's package repository is huge, particularly when you factor in packages in the Universe and Multiverse repositories. However, many users find themselves needing to install packages from source, either because they want to use a newer package than is available in the repository, or they want to try something that's not in the Ubuntu repository at all.

If you want to install packages from source, you can use a few shortcuts to make life easier. First, you'll probably want to get the build-essential meta-package if you haven't installed any developer tools. Run sudo apt-get install build-essential; it will grab GCC, the Linux kernel headers, GNU Make, and some other packages that you'll probably need.

Next, if you're going to compile a package such as Gaim because a new version is out, you might be able to satisfy the new version's dependencies with the old version's dependencies. To do this, grab the package's build dependencies with sudo apt-get build-dep packagename . That will grab all of the development packages you need to build the package that's currently available in Ubuntu, and will probably satisfy dependencies for the new version you're compiling.

Finally, don't make install when you compile from source -- use CheckInstall instead. CheckInstall will create a Debian package and install it for you, so you can remove or upgrade the software more easily later on.

Grab CheckInstall with apt-get install checkinstall. After you've run ./configure ; make, just run sudo checkinstall and answer a few simple questions. Note that if you compile packages on AMD64, CheckInstall will select X86_64 as the architecture rather than amd64 -- which will cause the package install to fail, since Ubuntu expects amd64 as the architecture rather than X86_64.

By the way, the packages created by CheckInstall also make it easier to deploy the same package on several machines, if you happen to have several systems running Ubuntu. See Joe Barr's excellent CLI Magic feature on CheckInstall too.

Here is a place that explains it well: [http://www.linux.com/articles/54945](http://www.linux.com/articles/54945)

Also:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_.deb_files_from_source](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_.deb_files_from_source)

Also, if you are a new user check out [http://ubuntuguide.org](http://ubuntuguide.org) they have good tips and tutorials on most things.

---

### Post by Techmobowl on 2007-07-02
Thanks,
As I understand, and I may be wrong, these commands are for building from source in Ubuntu.  Which makes sense because this is an Ubuntu forum.  I was out on a limb to see if anyone had ideas for a non-Ubuntu Linux distro.  Again, thanks for any help.

---

### Post by louieb on 2007-07-02
> **Techmobowl said:**
> ...  I couldn't find any tutorials online that I could understand ...
Building a program from source is pretty much the same in all flavors of Linux. 
This tutorial is about as simple as it gets. 

[Compiling and installing software from source in Linux]("http://www.tuxfiles.org/linuxhelp/softinstall.html#un")

Which distro? Did you check their wiki pages. Do you have the compiler installed?
Ubuntu won't install a program from source out of the box. Ubuntu users  have to install at a minimum a package called **build-essentials.** Building from source is not the easiest thing especially if you have never done it  before. Just keep plugging away and you'll get it. :guitar:

---

### Post by Techmobowl on 2007-07-03
Thanks much for the help.  The link was great.

Just for informations sake, i'm running a small distribution for old pc's called DeLiLinux.  I'm trying to install gfortran.  Delilinux comes with gcc but without gfortran.  The forum there is nice but small so sometimes it takes a little bit to get help.  Thanks again.

---

