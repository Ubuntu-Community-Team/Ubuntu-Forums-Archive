---
title: "The public key is not available"
date: 2014-10-02
forum: General Help
---

### Post by CantankRus on 2014-10-02
At the end of **sudo apt-get update** I get this message...
```
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://linux.dropbox.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912E
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 517590D9A8492E35
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 517590D9A8492E35
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
```

I used [**_[COLOR="#B22222"]launchpad-getkeys[/COLOR]_**]("http://www.webupd8.org/2011/02/launchpad-getkeys-gets-proxy-support.html") which is supposed to automatically import all missing GPG keys but still get same results.
Anyone know what the problem is?

---

### Post by vasa1 on 2014-10-02
Here's a bug where people try to find a workaround: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540)
And this: [http://ubuntuforums.org/showthread.php?t=1869890&p=11396851#post11396851](http://ubuntuforums.org/showthread.php?t=1869890&p=11396851#post11396851)

---

### Post by CantankRus on 2014-10-02
> **vasa1 said:**
> Here's a bug where people try to find a workaround: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540)
And this: [http://ubuntuforums.org/showthread.php?t=1869890&p=11396851#post11396851](http://ubuntuforums.org/showthread.php?t=1869890&p=11396851#post11396851)
Thanks, seems like there's a limit to the number of keyrings.
I removed/purged all the ppas I no longer use and deleted the associated keyrings in **/etc/apt/trusted.gpg.d** and all is good.

---

