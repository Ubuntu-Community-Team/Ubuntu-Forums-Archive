---
title: "too many damned keys (I think)"
date: 2014-04-03
forum: General Help
---

### Post by ray field on 2014-04-03
Attempting to migrate from Quantal to the last Trusty beta a couple days ago, but the excess third-party crap I've brought along is causing me troubles. I first became aware something was wrong when apt-get install would spit nasty messages at me about packages that couldn't be authenticated and to add insult, defaulted to halt. 
```

apt-get update
``` results in

```
W: GPG error: http://us.archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://us.archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://security.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://linux.dropbox.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912E
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6A9653F936FD5529
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED08E6DC7A2DA9DB
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8CD60EC948894010
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: Failed to fetch http://ppa.launchpad.net/alexmurray/indicator-sensors/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/atareao/lenses/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/bhdouglass/indicator-remindor/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/diodon-team/stable/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/guilhem-fr/mupdf/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/happy-neko/ps3mediaserver/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jtaylor/keepass/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/leolik/leolik/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nae-team/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pywapi-devel/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/super-friends/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/webupd8team/experiments/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/webupd8team/rhythmbox/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/yorba/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Can someone explain to me just what is wrong and how I can fix things? I'm sure I brought on these problems by trying to use YPPA manager to bring over those PPAs -- what can I say? I've grown fond of a lot of those gizmos -- but I'm just not sure of the depth of the problems or how to go about fixing them. Is it just that I have too many keys? or has my attempt to add Trusty to repos that haven't yet got this release added?

This afternoon after failing to install the Dropbox repo, I spent the better part of an hour trying to purge/delete keys, but I still couldn't seem to do it (used the .deb file from the Dropbox site, had to use Gdebi since the Ubuntu Software Center was too good for it) -- when I tried to run

```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
```

here's what I got:

```
[sudo] password for raphael: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.K49OHsPB94 --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/alexmurray-indicator-sensors.gpg --keyring /etc/apt/trusted.gpg.d/andrewsomething-typecatcher.gpg --keyring /etc/apt/trusted.gpg.d/bhdouglass-indicator-remindor.gpg --keyring /etc/apt/trusted.gpg.d/caffeine-developers-ppa.gpg --keyring /etc/apt/trusted.gpg.d/danielrichter2007-grub-customizer.gpg --keyring /etc/apt/trusted.gpg.d/debian-archive-squeeze-automatic.gpg --keyring /etc/apt/trusted.gpg.d/debian-archive-squeeze-stable.gpg --keyring /etc/apt/trusted.gpg.d/debian-archive-wheezy-automatic.gpg --keyring /etc/apt/trusted.gpg.d/debian-archive-wheezy-stable.gpg --keyring /etc/apt/trusted.gpg.d/diesch-testing.gpg --keyring /etc/apt/trusted.gpg.d/diodon-team-stable.gpg --keyring /etc/apt/trusted.gpg.d/ehoover-compholio.gpg --keyring /etc/apt/trusted.gpg.d/eugenesan-ppa.gpg --keyring /etc/apt/trusted.gpg.d/finalterm-daily.gpg --keyring /etc/apt/trusted.gpg.d/happy-neko-ps3mediaserver.gpg --keyring /etc/apt/trusted.gpg.d/i-nex-development-team-stable.gpg --keyring /etc/apt/trusted.gpg.d/indicator-multiload-stable-daily.gpg --keyring /etc/apt/trusted.gpg.d/jconti-recent-notifications.gpg --keyring /etc/apt/trusted.gpg.d/jon-severinsson-ffmpeg.gpg --keyring /etc/apt/trusted.gpg.d/jtaylor-keepass.gpg --keyring /etc/apt/trusted.gpg.d/langdalepl-gvfs-mtp.gpg --keyring /etc/apt/trusted.gpg.d/leolik-leolik.gpg --keyring /etc/apt/trusted.gpg.d/libreoffice-libreoffice-4-0.gpg --keyring /etc/apt/trusted.gpg.d/markjtully-ppa.gpg --keyring /etc/apt/trusted.gpg.d/nae-team-ppa.gpg --keyring /etc/apt/trusted.gpg.d/nilarimogard-webupd8.gpg --keyring /etc/apt/trusted.gpg.d/nowrep-qupzilla.gpg --keyring /etc/apt/trusted.gpg.d/otto-kesselgulasch-gimp.gpg --keyring /etc/apt/trusted.gpg.d/pj-assis-ppa.gpg --keyring /etc/apt/trusted.gpg.d/pkg-games-ppa.gpg --keyring /etc/apt/trusted.gpg.d/pywapi-devel-ppa.gpg --keyring /etc/apt/trusted.gpg.d/scopes-packagers-ppa.gpg --keyring /etc/apt/trusted.gpg.d/skunk-pepper-flash.gpg --keyring /etc/apt/trusted.gpg.d/stebbins-handbrake-snapshots.gpg --keyring /etc/apt/trusted.gpg.d/teejee2008-ppa.gpg --keyring /etc/apt/trusted.gpg.d/tsbarnes-indicator-keylock.gpg --keyring /etc/apt/trusted.gpg.d/ubuntu-tweak-testing-ppa.gpg --keyring /etc/apt/trusted.gpg.d/ubuntu-wine-ppa.gpg --keyring /etc/apt/trusted.gpg.d/ubuntu-x-swat-x-updates.gpg --keyring /etc/apt/trusted.gpg.d/undistract-me-packagers-daily.gpg --keyring /etc/apt/trusted.gpg.d/weather-indicator-team-ppa.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-experiments.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-java.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-rhythmbox.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-themes.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg --keyring /etc/apt/trusted.gpg.d/yorba-ppa.gpg --keyserver pgp.mit.edu --recv-keys 5044912E
gpg: keyblock resource `/etc/apt/trusted.gpg.d/ubuntu-x-swat-x-updates.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/undistract-me-packagers-daily.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/weather-indicator-team-ppa.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-experiments.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-java.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-rhythmbox.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-themes.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yorba-ppa.gpg': resource limit
gpg: requesting key 5044912E from hkp server pgp.mit.edu
gpg: key 5044912E: public key "Dropbox Automatic Signing Key <linux@dropbox.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```

How many problems have I got???

---

### Post by ajgreeny on 2014-04-03
You seem to have masses of ppa repositories enabled and as far as I'm aware there are very few, if any, ppa repos set up yet for trusty.  When it is finally released they will possibly be set up, but some of them, for example the libreoffice-4.0 are not needed as trusty already has version 4 in its repos.

So, disable or delete those third party and ppa repos from your software sources and try again to update or install.  I think the error messages will be gone.

---

### Post by ray field on 2014-04-03
thank you -- I guess somehow I knew that's what I needed to do, just couldn't remember where to untick them all.

apt-get upgrade now runs much more cleanly, except for this:

```
W: GPG error: http://security.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://us.archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://us.archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
```

so, none of these official repos are enabled yet, either?

I'm still a little bit concerned about all those keys, especially since I thought I'd rubbed out around ten of them and my system was apparently still overloaded. are they not checked unless they are explicitly needed? guess I'll find out in a few months anyway.

thanks again.

---

### Post by ray field on 2014-04-03
also, most worrisome of all, I am still getting

```
WARNING: The following packages cannot be authenticated!
```

eg right now when I just tried to install k3b.

---

### Post by ajgreeny on 2014-04-04
How did you make the move from quantal to trusty?  To do that properly you need to go via raring, then saucy, ie one step at a time.

If you simply changed all instances of quantal in your sources.list file and did not carry out the distro update in a properly mabaged manner it could be why you are getting these errors, but unfortunately as I have always worked with clean installs, I can not really help you much more except for suggesting you run ```
sudo apt-key adv --keyserver hkp://subkeys.pgp.net --recv-keys
``` which, with luck, should update all your gpg keys.

---

### Post by oldos2er on 2014-04-04
> **ray field said:**
> also, most worrisome of all, I am still getting

```
WARNING: The following packages cannot be authenticated!
```

eg right now when I just tried to install k3b.

Thread is marked 'Solved' but no solution is posted. If and when you have the time, could you please provide the solution? The main reason for marking a thread 'Solved' is so others searching for solutions to the same problem will be able to find them. Thanks.

---

### Post by ray field on 2014-04-04
oops! I thought I'd posted, guess I was so relieved I passed over the important part.

the problem was in fact too many GPG keys, so after disabling the sources didn't fix the problem, nor "sudo apt-key del #########," I took a cue from a post I saw somewhere and simply went into /etc/apt/trusted.gpg.d and, as root, deleted them. much to my astonishment, I didn't even have to manually register those Ubuntu and Canonical keys, -- next time I apt-get updated, all was well.

was a little annoyed at first that there should be such a limit, until I thought about it and realized about a third of those Launchpad repos were extinct or otherwise useless, turning my apt directory into a sort of cruft nook.

---

### Post by oldos2er on 2014-04-05
Thank you! :)

---

### Post by jpphun on 2014-07-29
> **ray field said:**
> oops! I thought I'd posted, guess I was so relieved I passed over the important part.

the problem was in fact too many GPG keys, so after disabling the sources didn't fix the problem, nor "sudo apt-key del #########," I took a cue from a post I saw somewhere and simply went into /etc/apt/trusted.gpg.d and, as root, deleted them. much to my astonishment, I didn't even have to manually register those Ubuntu and Canonical keys, -- next time I apt-get updated, all was well.

was a little annoyed at first that there should be such a limit, until I thought about it and realized about a third of those Launchpad repos were extinct or otherwise useless, turning my apt directory into a sort of cruft nook.

This worked for me thanks.

---

