---
title: "git newbie checkout source compile"
date: 2016-10-29
forum: General Help
---

### Post by Kevin McCready on 2016-10-29
I have looked at the git manual and help book:
[https://git-scm.com/book/en/v2](https://git-scm.com/book/en/v2)

Unfortunately the book is written for experts, not newbies. 

I don't understand what "checkout" means (the book assumes I do).

I am trying to compile the unreleased 1.0.26 version of sane-backends from source and install it.

I installed git and I did this:
git clone git://git.debian.org/sane/sane-backends.git

But I don't know how to find version 1.0.26.
And I don't know how to compile it.

Maybe it's something to do with finding a branch?

---

### Post by kevdog on 2016-10-29
If you've checked out the source already then try to compile it.  You might have to do some reading if you need dependent packages.  You'll need at least the build-essential and linux-`uname -r`-headers packages.  Usually to compile, its something like ./configure, make, sudo make install.

---

### Post by Kevin McCready on 2016-10-29
Thanks. If we could take this step by step it would help me. I haven't "checked out the source" because I don't know how to do that. Apparently in a git repository (now on my local computer)  there are multiple versions of sane-backends? My task is to find one version and compile it. I've been reading about this problem for a couple of weeks and am a little wiser but have not found answers to that question. Thanks for your help.

---

### Post by kevdog on 2016-10-29
Where is the git repository located? URL?
[https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)

---

### Post by steeldriver on 2016-10-29
Presumably you are following some instructions to "compile the  unreleased 1.0.26 version of sane-backends from source and install it"? If so, can you share them?

I just cloned the repo you included in your post and as far as I can see it has no such version (at least, no such branch **or **tag)


You can list branches by entering the cloned directory (e.g. `cd sane-backends`) then typing

```

git branch -a

```

You can list tagged releases (more likely what you are looking for here) using

```

git tag -l

```

See here for example --> [http://stackoverflow.com/a/792027/4440445](http://stackoverflow.com/a/792027/4440445)

---

### Post by Kevin McCready on 2016-10-29
Wow. Despite all my googling I didn't find the CompileSaneFromSource.
So I've followed that recipe, but when I did:
sudo find /usr/lib -name 'libsane-dll.so'

nothing happened.

A friend looked at this thread for me:
[https://ubuntuforums.org/showthread.php?t=2341107](https://ubuntuforums.org/showthread.php?t=2341107)
He said:
"It seems the sm3840 patch was pulled into sane-backends on github 2 weeks AFTER the 1.0.25 release, so it is not in the current ubuntu libsane package.

This is relatively good news, as there is no patching for us to do, only compiling the as yet unreleased 1.0.26 version from source and
installing. This is a relatively trivial matter."

Trivial for experts, not for newbies. So that's where I'm stuck.

---

### Post by Kevin McCready on 2016-10-31
I did 1.:
./configure --prefix=/usr --libdir=/usr/lib/i386-linux-gnu --sysconfdir=/etc --localstatedir=/var  --enable-avahi BACKENDS="microtek2"

output included:
-> Installation directories:
Configuration: /etc
Libraries:     /usr/lib/i386-linux-gnu
Binaries:      /usr/bin and /usr/sbin
Manpages:      /usr/share/man
Documentation: /usr/share/doc/sane-backends
Lockfiles:     Feature is disabled!
-> Network parameters:
Build saned:   yes
IPv6 support:  yes
Avahi support: yes
SNMP support:  no

Then I did 2:
make

Then I did 3:
sudo make install

Then to set permissions I added to
~/Documents/sane/sane-backends/tools/udev $ subl libsane.rules

# Microtek ScanMaker 3880
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="0129", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"

---

