---
title: "Can't install nodejs on Ubuntu 16.10"
date: 2016-12-04
forum: General Help
---

### Post by sangeethmanayil on 2016-12-04
I'm just getting into Linux and have been working with Ubuntu for a while. I am the impatient type when it comes to updates so I didn't wait a bit to update my machines to 16.10. I have a clean installations in all my machines and I wanted to install nodejs on them since I work with it. I'm following the instructions at [https://nodejs.org/en/download/package-manager/](https://nodejs.org/en/download/package-manager/)  to install nodejs. However, I'm getting the following error when executing curl:

```
- snip -
Fetched 940 kB in 18s (50.2 kB/s)
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/noobslab/themes/ubuntu yakkety Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: https://download.01.org/gfx/ubuntu/16.10/main yakkety InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 611B903CAB97EA77
W: The repository 'https://download.01.org/gfx/ubuntu/16.10/main yakkety InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/noobslab/themes/ubuntu/dists/yakkety/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
Error executing command, exiting

```

I believe since Yakkety is a new release, they have to sign the packages for it or something like that. But I really want to install this and I don't know which is the right way to do this without messing stuff up. Can someone tell me a workaround for this so that I can use nodejs now and can you also tell me whether these workarounds are good for long term (like if it's still applicable after those packages are signed and stuff)?

---

### Post by wildmanne39 on 2016-12-04
*Thread moved to **General Help**.*

---

### Post by ansari.ibrahim1 on 2016-12-07
The error is caused because the ppa:noobslab/themes doesn't work with 16.10, which throws an error. You need to delete the repository by executing
```
sudo add-apt-repository --remove ppa:noobslab/themes
```
then running the script to install nodejs again :)

---

### Post by sangeethmanayil on 2016-12-10
That was **so** stupid of me. Darn it, I should take a look at the error logs more carefully next time. Thanks a lot for pointing it out dude! I removed all the broken sources and now everything works as expected.

---

