---
title: "Fixing stuffed-up Firefox 1.0.4  install"
date: 2005-07-06
forum: General Help
---

### Post by oliwally on 2005-07-06
Oops ! I've stuffed up my Firefox installation by trying to upgrade to version 1.0.4.

I added repositories to Synaptic and tried to install Firefox 1.0.4. All went reasonably well until a message came up saying:

*E: /var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox*

Now I cannot use Firefox at all - it just won't start up. 

I have tried to reinstall Firefox 1.0.1 using Synaptic but again to no avail.

How do I either complete the 1.0.4 installation or revert back to the original  version that came with ubuntu (1.0.1 ?) Is there a clever 'apt' way of fixing it all?


_**EDIT**_

Find a solution to this in my last post here

---

### Post by oliwally on 2005-07-06
Bump

---

### Post by Razvan on 2005-07-06
try installing one of them with 'sudo apt-get install -f firefox' this will force the install.

if it works remove it and install it again cleanly

cheers

---

### Post by oliwally on 2005-07-07
Thanks for helping out.

I tried this and had the following output:

```
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  firefox-gnome-support latex-xft-fonts xprint
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 63 not upgraded.
1 not fully installed or removed.
Need to get 0B/8579kB of archives.
After unpacking 24.9MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  firefox
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... 75771 files and directories currently installed.)
Unpacking firefox (from .../firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What is the command for removing a program ?

---

### Post by daniel311 on 2005-07-07
[QUOTE=oliwally]Thanks for helping out.

What is the command for removing a program ?[/QUOTE]
 apt-get remove [--purge] package-name

where --purge removes configuration, too

---

### Post by oliwally on 2005-07-07
Ok, i did this but getting warnings that I will do serious damage to my system, witht he following packages being removed:

```
WARNING: The following essential packages will be removed
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++5 (due to apt)
  base-files base-passwd (due to base-files) bash passwd (due to bash)
  libncurses5 (due to bash) bsdutils coreutils libacl1 (due to coreutils)
  debianutils diff dpkg dselect (due to dpkg) e2fsprogs e2fslibs (due to
  e2fsprogs) libblkid1 (due to e2fsprogs) libcomerr2 (due to e2fsprogs) libss2
  (due to e2fsprogs) libuuid1 (due to e2fsprogs) findutils grep gzip hostname
  login libpam-modules (due to login) libpam0g (due to login) libpam-runtime
  (due to login) mount ncurses-base ncurses-bin perl-base python-minimal
  python2.4-minimal (due to python-minimal) sed sysvinit initscripts (due to
  sysvinit) sysv-rc (due to sysvinit) tar util-linux lsb-base (due to
  util-linux) slang1a-utf8 (due to util-linux) zlib1g (due to util-linux)

```

Is it safe to do this? Is there a better way?

---

### Post by mrcbrown on 2005-07-08
Why not just download FF from mozilla.org and install it in your homedir? Install is pretty painless and graphical - granted I love a good apt-get in the morning, but even if just for the temporary till you can sort out apt-get, it'd get you some browser action back. Just a thought.

---

### Post by oliwally on 2005-07-08
That's a good suggestion. I'm currently using Konqueror as  a back-up (not a bad little browser by the way !) so I've got browser action without any trouble.

Does anybody know what that original error message means and how to fix it?

*E: /var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb: trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox*

---

### Post by JayCnrs on 2005-07-08
I remember getting that error what I did I believe it has been a while was:

[B]sudo apt-get clean
sudo rm -rf /var/lib/mozilla-firefox
sudo apt-get update
sudo apt-get install firefox[/B]

I hope I am remembering the right steps, let us know how it goes

---

### Post by oliwally on 2005-07-09
You little ripper, I solved the problem.

JayCnrs - thanks for your help. I didn't end up using it, so I don't know if it works. I ended up figuring out a solution before, and I haven't had a chance to post it until now.

The solution was was staring me in the face .... ;-) 

I used Synaptic and marked the bamboozled installations 'for complete removal'. Very simple.

After that it was no trouble to install the firefox version of my choice. The only problem was that KDE didn't stick a shortcut into the Kmenu. So I created one with the command "firefox %u". I have no Idea what that actually means or where it points to, but hey, it works !

Thanks everyone for helping out. I've learned a bit about apt-get commands !

---

