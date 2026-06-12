---
title: "Codec installation problems"
date: 2005-10-01
forum: General Help
---

### Post by Panthios on 2005-10-01
Hi. I tried to follow this: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
And the only package I actually got installed was w32codecs.
But I can't play wmv files - does anyone know why?
I use Xine, on Kubuntu.
This is my sources.list:
```
deb http://dk.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu hoary main restricted
deb http://dk.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://dk.archive.ubuntu.com/ubuntu hoary universe
deb-src http://dk.archive.ubuntu.com/ubuntu hoary universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
##########################
##########################
# Codecs
deb ftp://ftp.nerim.net/debian-marillat/ sid main
```
When I try to install - like, lidxvidcore4, it says:
```
root@kubuntu:/home/stig # aptitude install libxvidcore4
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following packages have unmet dependencies:
libxvidcore4: Depends: libc6 (>= 2.3.5-1) but 2.3.2.ds1-20ubuntu14 is installed.
```
But I cannot understand why I have broken packages.
I've installed Kubuntu yesterday, and have NOT touched the sources.list file or installede anything that required dependcies that could give problems.
I have just added the ftp.nerim.net deb source in the sources.list - and install w32codecs - thats all.
Im confused :confused: :confused: :???:

---

### Post by SilentCacophony on 2005-10-01
Hello. Looks like it's trying to get that package from the debian sid repo, and it requires a newer version of libc6 than hoary has. Debian (Sid) is not quite compatible with Ubuntu on a lot of packages.

I know Breezy has libxvidcore4 in the multiverse repos, but I'm not sure about Hoary. I'd try commenting out the merillat mirror, clean the cache, and re-update and see if it's there on the ubuntu repos.

The -f option to try and fix dependency problems may be worth a try, too, though I've never had to use it myself.

---

### Post by pdundas on 2005-10-06
I was doing that too:  Was trying to install w32 codecs (as per <a href="https://wiki.ubuntu.com//RestrictedFormats#head-ae79fed9d60ccdf06f400ae76ad53867d94bb2b8">Restricted Formats</a>) and had an error: GPG couldn't verify the signatures, cos no public key.
Is their system secure (reasonably)? 
Does it normally have workin keys. Is there any problem installing those packages under breezy?

Paul

---

