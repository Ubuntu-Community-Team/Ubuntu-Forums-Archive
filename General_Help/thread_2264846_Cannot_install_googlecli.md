---
title: "Cannot install googlecli"
date: 2015-02-10
forum: General Help
---

### Post by CkDGTAT on 2015-02-10
Hi,

Any idea about the origin?
```
googlecl_0.9.14-2_all.deb
(Reading database ... 253123 files and directories currently installed.)
Preparing to unpack googlecl_0.9.14-2_all.deb ...
Unpacking googlecl (0.9.14-2) over (0.9.13-1) ...
dpkg-deb (subprocess): cannot copy archive member from 'googlecl_0.9.14-2_all.deb' to decompressor pipe: unexpected end of file or stream
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing archive googlecl_0.9.14-2_all.deb (--install):
 cannot copy extracted data for './usr/bin/google' to '/usr/bin/google.dpkg-new': unexpected end of file or stream
Processing triggers for python-support (1.0.15) ...
Errors were encountered while processing:
 googlecl_0.9.14-2_all.deb

```

---

### Post by oldos2er on 2015-02-10
Did you check the SHA1 Checksum? I'm wondering if you have a corrupted file. What version of Ubuntu are you running?

---

### Post by CkDGTAT on 2015-02-11
```
DISTRIB_ID=UbuntuDISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
NAME="Ubuntu"
VERSION="14.04.1 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.1 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
cat: file.: No such file or directory



```

```

[~]%sha1sum googlecl_0.9.14-2_all.debfdef1af0ac30611edafd422e5f5b95df85b73574  googlecl_0.9.14-2_all.deb
[~]% sha1sum -c googlecl_0.9.14-2_all.deb
sha1sum: googlecl_0.9.14-2_all.deb: no properly formatted SHA1 checksum lines found



```

---

### Post by raptir on 2015-02-11
> **CkDGTAT said:**
> 
```

[~]%sha1sum googlecl_0.9.14-2_all.debfdef1af0ac30611edafd422e5f5b95df85b73574  googlecl_0.9.14-2_all.deb
[~]% sha1sum -c googlecl_0.9.14-2_all.deb
sha1sum: googlecl_0.9.14-2_all.deb: no properly formatted SHA1 checksum lines found

```

Yeah, bad download. The proper sha1sum for that file is 5693bc15b35b26146cf828f33056770fc5c114ac.

[https://code.google.com/p/googlecl/downloads/detail?name=googlecl_0.9.14-2_all.deb&can=2&q=](https://code.google.com/p/googlecl/downloads/detail?name=googlecl_0.9.14-2_all.deb&can=2&q=)

---

