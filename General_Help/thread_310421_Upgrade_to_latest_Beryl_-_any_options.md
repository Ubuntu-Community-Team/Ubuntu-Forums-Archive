---
title: "Upgrade to latest Beryl - any options?"
date: 2006-12-01
forum: General Help
---

### Post by elbowgeek on 2006-12-01
I have Beryl 0.1.1 on my system and I'm rather proud that I managed to get it working, especially after my previous attempts failed so miserably.

Anyway, I saw screen shots and video of what 0.1.3 can do and I'd love to get it working on my system.  However it seems that the the Beryl home paged has been down for quite some time now.

Are there any options for upgrading to the latest version out there, or are we stuck until the Beryl Project rebuilds its web site?

Cheers

---

### Post by Biker on 2006-12-01
You can find the latest official update 0.1.2 here,
[http://compiz-mirror.lupine.me.uk/dists/edgy/main/](http://compiz-mirror.lupine.me.uk/dists/edgy/main/)

Where do you saw the video of Beryl 0.1.3 ?

---

### Post by tribaal on 2006-12-01
Beryl 0.1.3 is available through trevino's repositories.

"Version" 0.1.3 is a SVN version (unstable developpment branch - breaks once in a While)! Make sure you understand what this implies before you use it!

To install version 0.1.3 just install beryl normally, then add the following repo to your /etc/aptsources.list :

```
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn

```

Then simply "sudo apt-get update && sudo apt-get upgrade", and everything should work... _should_ work!
Sometimes the old Beryl and emerald settings screw up the rendering... if you don't see window borders when you run beryl, try removing ~/.beryl and ~/.emerald and restarting beryl. Of course, you'll loose your config... it's a devloppment version, remember? :)

Hope this helps.

- trib'

---

### Post by elbowgeek on 2006-12-01
Many thanks for pointing me in the right direction.  I'm now having a bit of an issue with 0.1.2, so we'll see how that goes first.

I can't remember where I saw the video demo of 0.1.3, but it looked pretty darned impressive.  I'm just testing it on a non-production machine, one intended to get nuked.  Reminds me of the days I'd intentionally try to nuke DOS on my PS/2 Model 30 *grin*.

Many thanks...

---

### Post by elbowgeek on 2006-12-01
I did add the repositories and ran the command mentioned, but there were a few errors.  Looks like some critical locations are missing and I need a gpg key.  Cheers

> Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release.gpg
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
  404 Not Found
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [23.3kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [11.5kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [34.3kB]
Get:11 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:12 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:13 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:15 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release [23.3kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:16 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Get:17 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release [7100B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release
Get:18 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Packages [7399B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Get:19 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:20 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Sources [37B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [2430B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Get:22 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Packages [11.5kB]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages [21.8kB]
Get:24 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:25 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Packages [34.3kB]
91% [23 Packages gzip 0] [22 Packages bzip2 0] [25 Packages 2100/34.3kB 6%]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
  Sub-process gzip returned an error code (1)
Get:26 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Packages [2430B]
Get:27 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Sources [3644B]
Get:28 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:29 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Sources [8905B]
Get:30 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Sources [1058B]
Get:31 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources [60.2kB]
99% [31 Sources gzip 0]                                             17.7kB/s 0s
gzip: stdin: not in gzip format
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
  Sub-process gzip returned an error code (1)
Fetched 172kB in 19s (8596B/s)
Failed to fetch [http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages](http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages). gz  404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/so](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/so) urce/Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/b](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/b) inary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release: The following signatur es couldn't be verified because the public key is not available: NO_PUBKEY 2D6CF B44DD800CD9
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

---

### Post by coolclassic on 2006-12-01
And here's the video:

[http://www.youtube.com/watch?v=YY6X-QuAh20](http://www.youtube.com/watch?v=YY6X-QuAh20)


COOL!

---

### Post by tribaal on 2006-12-01
Here's the command for the GPG key signing:

```
KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
```

You may want to check out the "official" unofficial way to install beryl (by the maintainer of the repositories himself) [here]("http://ubuntuforums.org/showthread.php?t=279456").

Hope you like it :)

- trib'

---

