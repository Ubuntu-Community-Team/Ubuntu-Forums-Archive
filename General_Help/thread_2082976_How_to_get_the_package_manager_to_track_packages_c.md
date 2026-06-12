---
title: "How to get the package manager to track packages compiled from source?"
date: 2012-11-11
forum: General Help
---

### Post by Stonecold1995 on 2012-11-11
I know running
```
./configure
make
sudo make install
```
to compile and install a package from source will have it bypass the package manager and the computer won't be able to take it into consideration when upgrading other packages or working with dependencies.  So my question is how to get the package manager to remember that it's installed?  If I am correct, running "apt-get source --compile package_name" will do that because it's installed by using .deb files by dpkg.  And I assume "sudo checkinstall -D" will also?  Am I correct in that, or if not, how do I get dpkg to remember what I installed from source?

---

### Post by Zorael on 2012-11-11
Yes, you need to build deb files and have the package manager itself install them to have the files tracked. As a small relief, installing into a /usr/local prefix at least won't pollute "real" tracked directories, but for instance udev requires its rules to be in /lib/udev/rules.d and won't accept a /usr/local equavilence.

checkinstall may make this very easy; I'm not very familiar with it, but looking at its description it sounds like exactly what you're looking for.

As for the traditional approach, if there is a version of whatever you're trying to build already in the repos, you can probably download its source and overwrite the files with your new version. You will however need to edit files in the debian/ directory to...
[list][*]reflect changed dependencies (debian/control)
[*]mark a new package version (dch -n)
[*]disable any patches (debian/patches) that are no longer needed
[*]update additional files in there (*.dirs, *.files) if it's a multi-package source (eg. that builds into **package** as well as **libpackage0**), to define which files belong to which *if* files have been added or removed. I recommend a make install into /usr/local and then reviewing its tree[/list]
Packaging is an art and I only know enough of it to know that I *don't* know enough of it.

---

### Post by Stonecold1995 on 2012-11-11
> **Zorael said:**
> Yes, you need to build deb files and have the package manager itself install them to have the files tracked.
I did that ("apt-get source --compile packagename" does that) and it installed, but as soon as I ran "sudo apt-get update; sudo apt-get dist-upgrade", it wanted to overwrite the compiled packages.

---

### Post by mc4man on 2012-11-11
If you're building deb packages(s) to the same name as the current repo package(s) then many times the repo package(s) will be seen as an upgrade to the locally built one(s).

Simple example in the screen where I've modded & built the current nautilus source but left the version/name the same. So in this case nautilus is built as 6 separate packages, 2 of which are seen as being upgradeable back to repo package even though same name/version.

If I didn't want that then before starting the actual build I'd edit the /Debian/changelog & slightly up the version like in screen 2 where I've rebuild gtk & upped from the current of ...0ubuntu4 to ...0ubuntu4.1 
(.1 is used for proposed packages, you could also use something like this, - adding +nmu1 instead of .1 - 
...0ubuntu4+nmu1

---

### Post by Stonecold1995 on 2012-11-12
> **mc4man said:**
> If I didn't want that then before starting the actual build I'd edit the /Debian/changelog
How do I do that?

---

### Post by Zorael on 2012-11-13
> **Stonecold1995 said:**
> How do I do that?
When in debian/, run dch -n.

---

### Post by Stonecold1995 on 2012-11-14
Thank you.

---

### Post by Stonecold1995 on 2012-11-16
**Update:** I'm having some troubles reverting the changes.  I've installed a few packages this way, but I think it's causing another problem I'm having where almost [nothing will compile]("http://ubuntuforums.org/showthread.php?p=12357246").  Anyways, I tried reinstalling bash to see if that would work, but apparently using the method you described won't allow the package to be uninstalled.

```
alex@kubuntu:~$ sudo apt-get install --reinstall bash
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reinstallation of bash is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

alex@kubuntu:~$ sudo apt-get install --reinstall xserver-xorg
[sudo] password for alex:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reinstallation of xserver-xorg is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

alex@kubuntu:~$ sudo apt-get install --reinstall clamav
[sudo] password for alex:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reinstallation of clamav is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

But this is only with packages I compiled and installed.

---

### Post by mc4man on 2012-11-16
If you have built a source with upped version # & then wish to downgrade you'll need to get the package or packages you installed  from either launchpad, packages.ubuntu.com or sometimes from /var/cache/apt/archives
(launchpad is usually the easiest

You'd then create a folder, place them inside, cd to that folder & run
```
sudo dpkg -i *.deb
```

If you were missing one or more dpkg will report an issue/broken packages. Just read thru, get what's missing & run the above command till it completes correctly
(Edit - if you inadvertently include a package that Wasn't installed & it has missing deps - dpkg will not install for you. In that case use synaptic to fix after the dpkg fail. So try to only gather the packages you compiled & installed in the case of  multi-package sources

So - Example bash
Main LP page for 12.10
[https://launchpad.net/ubuntu/quantal/+source/bash](https://launchpad.net/ubuntu/quantal/+source/bash)

clicking on last release link (4.2-5ubuntu1
[https://launchpad.net/ubuntu/+source/bash/4.2-5ubuntu1](https://launchpad.net/ubuntu/+source/bash/4.2-5ubuntu1)

Under "Builds" choosing arch - ex. amd64
[https://launchpad.net/ubuntu/+source/bash/4.2-5ubuntu1/+build/3798462](https://launchpad.net/ubuntu/+source/bash/4.2-5ubuntu1/+build/3798462)

Under "Built files" you'll see 3 .debs. Download all  _that you installed from your compile_, place in an empty folder & above command.

If you  build .debs & are not sure of their viability then just leave at the same version. This way to replace them you Can simply re-install.

---

