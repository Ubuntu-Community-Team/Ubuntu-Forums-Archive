---
title: "Ubuntu 7.10 packages"
date: 2008-02-25
forum: General Help
---

### Post by gsingh144 on 2008-02-25
Hi,
 I am new to ubuntu and I have just installed ubuntu 7.10 from ubuntu-7.10-desktop-i386.iso. I think I have certain basic packages missing as I could not use emacs and when trying to install Mplayer I also got some dependency issue. Please let me know where I can get the packages for ubuntu. Following is the output when I tried to install emacs and mplayer.

[B]$ sudo apt-get install emacs
[/B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emacs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emacs has no installation candidate
[B]
$ sudo apt-get install mplayer[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
           Depends: libaudio2 but it is not installable
           Depends: liblzo1 but it is not installable
           Depends: libmpcdec3 but it is not installable
           Depends: libungif4g (>= 4.1.3) but it is not installable
           Depends: libxvmc1 but it is not installable
E: Broken packages

TIA
Gaurav

---

### Post by pointone on 2008-02-25
Edit your /etc/apt/sources.list file and comment out the CD-ROM source. Also uncomment the universe and multiverse sources. Then run "sudo apt-get update" and try again.

---

### Post by gsingh144 on 2008-02-26
Hi pointone,
 Thanks a lot, that worked.

---

