---
title: "Dependency Hell Problems"
date: 2013-01-27
forum: General Help
---

### Post by nova47 on 2013-01-27
I'm trying to use apt-get to install synaptic, but I'm unable to perform any installations due to some sort of dependency problem:

```

root@bt:~# sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7.8) but 2.11.3-4 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.11.1-0ubuntu7.8) but 2.11.3-4 is to be installed
  libgcc1: Depends: gcc-4.4-base (= 4.4.5-8) but 4.4.3-4ubuntu5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

sudo apt-get install -f, autoclean, clean and all the combinations therein seem to do nothing. I manually downloaded libc6 and libgcc1, but they list EACH OTHER as a dependency so I can't install either! I don't know what to do to get rid of this awful mess :(.

---

### Post by Cheesehead on 2013-01-27
Let's pick one of those dependencies at random: gcc-4.4-base
```
me@me:~$ rmadison gcc-4.4-base
 The package gcc-4.4-base (if it exists) has not been installed
Looking for package "gcc-4.4-base". Checking in Ubuntu...
gcc-4.4-base is currently in the Ubuntu repositories
gcc-4.4-base | 4.4.3-4ubuntu5 |         lucid | amd64, armel, i386, ia64, powerpc, sparc
gcc-4.4-base | 4.4.3-4ubuntu5.1 | lucid-security | amd64, armel, i386, ia64, powerpc, sparc
gcc-4.4-base | 4.4.3-4ubuntu5.1 | lucid-updates | amd64, armel, i386, ia64, powerpc, sparc
gcc-4.4-base | 4.4.6-11ubuntu2 |       oneiric | amd64, armel, i386, powerpc
gcc-4.4-base | 4.4.7-1ubuntu2 |       precise | amd64, armel, armhf, i386, powerpc
gcc-4.4-base | 4.4.7-2ubuntu1 |       quantal | amd64, armel, armhf, i386, powerpc
gcc-4.4-base | 4.4.7-2ubuntu1 |        raring | amd64, armhf, i386, powerpc

```

The system wants to install version 4.4.3-4ubuntu5.1, which means you are running Lucid (10.04).
However, your version of libgcc1 wants the system to install 4.4.5-8, which is not in the repositories at all.

This condition usually occurs when you try to update using PPA, third-party repository, or wrong-release repository. For example, if you added a Natty repository instead of a Lucid repo.
As you have learned, trying to download and install dependencies manually is usually not the right solution. Instead, try disabling unofficial repos.

1) On the command line, run the command [FONT="Courier New"]gksudo software-properties-gtk[/FONT] to open your Software Sources control panel.

2) Go to the 'Other Software' tab. Uncheck everything that's not a real Ubuntu repository. Especially uncheck all PPAs, and uncheck anything not labelled 'Lucid'. Close the control panel.

3) Move any manually-downloaded packages to the Trash.

4) Go back to the command line:
[FONT="Courier New"]sudo apt-get update
sudo apt-get upgrade[/FONT]

5) If you still have the problem, copy-and-paste the entire error message here. AND include the contents of your /etc/apt/sources.list file.

---

### Post by tgalati4 on 2013-01-27
Linux Mint contains synaptic.  Why was it removed from Ubuntu?  Sounds like a packaging problem rather than a real dependency issue.

---

### Post by Cheesehead on 2013-01-27
Perhaps. Their response will tell....

Synaptic was removed from the Ubuntu-desktop metapackage (the default install) because new/unskilled users don't know what it is or how to use it...which makes little sense for a distro oriented to them. Any user with a desire can install it trivially...if their package manager is working.

---

