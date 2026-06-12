---
title: "Update error - no public key"
date: 2015-07-05
forum: General Help
---

### Post by GrouchyGaijin on 2015-07-05
Hi Guys,

This problem started today.  I have no idea why as nothing, that I am aware of, has changed since yesterday.
When I run ```
 sudo apt-get update 
```
I get the following error message:
```


W: GPG error: http://apt.insync.io trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 06BBDC2602DFE7E7
W: GPG error: http://apt.insynchq.com trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 06BBDC2602DFE7E7
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://repo.sinew.in stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6F7565879798C2FC
W: GPG error: http://linux.dropbox.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912E
W: GPG error: https://private-ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E131728675254D99
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: https://private-ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E131728675254D99
W: GPG error: https://private-ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E131728675254D99
W: GPG error: https://private-ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E131728675254D99
W: GPG error: http://archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

```

What I really do not understand is why all of a sudden archive.ubuntu.com would register as not having a valid public signature.
Does anyone know how I can fix these errors?  I would really appreciate any help I can get.  I'd hate to hose my system.

---

### Post by dino99 on 2015-07-05
[http://askubuntu.com/questions/520828/gpg-error-no-pubkey-warning-the-following-packages-cannot-be-authenticated](http://askubuntu.com/questions/520828/gpg-error-no-pubkey-warning-the-following-packages-cannot-be-authenticated)

---

### Post by GrouchyGaijin on 2015-07-05
Using the Opera key as an example:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 517590D9A8492E35 
```

I get this:
```

gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-java.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-unstable.gpg': resource limit
gpg: requesting key A8492E35 from hkp server keyserver.ubuntu.com
gpg: key A8492E35: "Opera Software Archive Automatic Signing Key 2013b <packager@opera.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

and the error persists

---

### Post by GrouchyGaijin on 2015-07-05
It seems this is a bug that has been a problem for a while:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540)

The bottom line is I went to /etc/apt/trusted.gpg.d and deleted what seemed to be the offending keys (or temp copies of keys since they all ended with ~).
It seems that the existence of these empty files interfered with the gpg keyblock resource limit.  Who knew there was such a thing?  Not I.
Anyway once I deleted these files I ran ```
sudo apt-get update
``` again and then one by one added every key that had been blocked on to the main /etc/apt/trusted.gpg keyring with apt-key adv as described above.

The end result is that my system is not complaining about no private keys now.

---

