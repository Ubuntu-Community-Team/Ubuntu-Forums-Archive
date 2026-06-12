---
title: "Upgrade to Heron/gnupg error"
date: 2008-05-21
forum: General Help
---

### Post by Culito on 2008-05-21
Hello all, I've been trying to upgrade to 8.04 from 7.10 and can't seem to get there.
Update-manager just tells me this:

Authenticating the upgrade failed. There may be a problem with the network or with the server.

If I run update manager from the terminal:

```
cully@AM/FM:~/.gnup[/email]g$ sudo update-manager
warning: could not initiate dbus
Fontconfig error: Cannot load default config file
Fontconfig error: Cannot load default config file
extracting '/tmp/tmpmvI8Vq/hardy.tar.gz'
authenticate '/tmp/tmpmvI8Vq/hardy.tar.gz' against '/tmp/tmpmvI8Vq/hardy.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information: 

gpg: WARNING: unsafe permissions on homedir `/tmp/tmpmvI8Vq'
secmem usage: 1408/1408 bytes in 2/2 blocks of pool 1408/32768

gpg: Signature made Fri 09 May 2008 11:46:50 AM CDT using DSA key ID 437D05B5
gpg: failed to create temporary file `/tmp/tmpmvI8Vq/.#lk0x8123310.AM/FM.7728': No such file or directory
gpg: fatal: can't create lock for `/tmp/tmpmvI8Vq/trustdb.gpg'
```

Any ideas here?  Is there something I should check in gpg.conf?  I'd like to upgrade but I'm stuck!

Thanks,
-C

---

### Post by Culito on 2008-05-27
Bump....still no luck.

---

### Post by Culito on 2008-06-01
So far:

sudo do-release-upgrade returns me the same error.

I've re-installed gnupg and its associated files to no avail.

---

### Post by OliverW on 2008-06-01
> **Culito said:**
> So far:

sudo do-release-upgrade returns me the same error.

I've re-installed gnupg and its associated files to no avail.


There was a similair bug report for a previous version of Ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/82464](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/82464)

The solution is creating a .gnupg file for the root user:
```
sudo mkdir /root/.gnupg
```

---

### Post by Culito on 2008-06-01
```
mkdir: cannot create directory `/root/.gnupg': File exists
```

---

### Post by OliverW on 2008-06-01
Do you also have a .gnupg directory in your users home dir?

---

### Post by Culito on 2008-06-02
Sure do.  But your avatar reminds me *I* need to be sawing logs right now...

---

### Post by Culito on 2008-06-13
Well, crap.  I still can't figure it out.
It looks like I'll have to download the iso., back everything up and install Hardy from cd.

What a gyp!!!

---

