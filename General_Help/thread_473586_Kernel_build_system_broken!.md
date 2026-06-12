---
title: "Kernel build system broken?!"
date: 2007-06-14
forum: General Help
---

### Post by ShockME on 2007-06-14
Hello,

I have a core2duo/asus p5b-deluxe/4GB ram system that I use as a destop at work.
Using the latest generic kernel it is only able to see 2GB of ram because the bios configures a hole in the 2gb-4gb address space. I am currently trying to build a kernel based on the generic config but with 64gb support enabled (PAE), but I'm unable to do it successfully.

<rant>
I have asked all around on IRC: #ubuntu, #kubuntu, #ubuntu-motu have referred me to #ubuntu-kernel. I went there and I was told that it wasn't the right place to ask. I'm hoping someone here can provide a resolution.
</rant>

I'm following the tutorial available here: [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

The output of the commands:

root@mircea:/usr/src# apt-get install linux-kernel-devel fakeroot kernel-wedge kernel-package
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-kernel-devel is already the newest version.
fakeroot is already the newest version.
kernel-wedge is already the newest version.
kernel-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

root@mircea:/usr/src# apt-get build-dep linux-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

root@mircea:/usr/src# apt-get source linux-source-2.6.20
Reading package lists... Done
Building dependency tree
Reading state information... Done
Need to get 63.7MB of source archives.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-source-2.6.20 2.6.20-16.29 (dsc) [2472B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-source-2.6.20 2.6.20-16.29 (tar) [62.2MB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-source-2.6.20 2.6.20-16.29 (diff) [1564kB]
Fetched 63.7MB in 56s (1120kB/s)
gpg: Signature made Thu 07 Jun 2007 08:13:04 PM EEST using DSA key ID 17063E6D
gpg: Can't check signature: public key not found
dpkg-source: extracting linux-source-2.6.20 in linux-source-2.6.20-2.6.20
dpkg-source: unpacking linux-source-2.6.20_2.6.20.orig.tar.gz
dpkg-source: applying ./linux-source-2.6.20_2.6.20-16.29.diff.gz

After this I get errors everywhere I turn:

root@mircea:/usr/src/linux# debian/rules updateconfigs
make: *** No rule to make target `updateconfigs'.  Stop.

root@mircea:/usr/src/linux# AUTOBUILD=1 fakeroot debian/rules binary-debs
make: *** No rule to make target `binary-debs'.  Stop.

root@mircea:/usr/src/linux# AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-debs flavours=generic
make: *** No rule to make target `binary-debs'.  Stop.

I'm out of ideas. What should I do?

Thanks.

---

### Post by southernman on 2007-06-14
Just judging from the guide you linked to, the first thing that jumps out at me is where you do:

> apt-get build-dep linux-source

should read as:
> sudo apt-get build-dep linux-source

Try that... and see.

---

### Post by ShockME on 2007-06-14
I did that. I ran all commands as root. Got more ideas? I'm pretty desperate/frustrated :)

---

### Post by southernman on 2007-06-14
Yes you did.. didn't ya! :/

Where you do:

> apt-get source linux-source-2.6.20

The guide doesn't have the version number included. It would seem to me you shouldn't either. The apt-get (or aptitude) will pull the current kernel source.

Hey, I'm just guessing here. Killing time before heading out to work.

---

### Post by ShockME on 2007-06-14
I did try without the version number too. It got me linux-meta-2.6.20.16.28.1.
Doing debian/rules binary-debs there has the same result (no target)

---

### Post by southernman on 2007-06-14
Well just two more suggestions from the peanut gallery then... ;)

Instead of using apt-get, did you actually try the preferred method of getting the source with "git" also?

And my final thought would be... perhaps you/I should head these following suggestions from the howto link: Notice where the emphasis has been placed below... :p
> 
Reasons for NOT compiling a custom kernel

    *      You merely need to compile a special driver. For this, you only need to install the linux-headers packages.
    *      ***_You have no idea what you are doing, and if you break something, you'll need help fixing it. Depending on what you do wrong, you might end up having to reinstall your system from scratch._***
    *      You got to this page by mistake, but checked it out because it looked interesting. Believe me, this isn't interesting at all :)

Anyway... I owe, I owe, so off to work I go.


Good luck...

---

### Post by ShockME on 2007-06-14
Going to try to get the source with git. Maybe I'll have better results...

---

### Post by ShockME on 2007-06-14
Build works on source retrieved with git. Does this mean that the build system in the sources retrieved with apt is broken somehow?

---

### Post by hazridi on 2007-06-26
Yeah, linux-source-2.6.20.tar.bz2 is broken. I got the sources with git and they work. Maybe someone would like to fix this problem.

---

### Post by Liberator on 2008-06-21
I have updated the [offending wiki page]("https://help.ubuntu.com/community/Kernel/Compile") with a note indicating that the "easy" method (download the source archive) has been broken for over a year, so to use the "git" method instead.  Hopefully that will save the next person the endless hours that you and I have spent trying to modify the kernel using outdated instructions.

Thanks very much for getting this resolved!

---

