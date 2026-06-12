---
title: "Very slow sudo when connected to network without internet"
date: 2017-01-31
forum: General Help
---

### Post by kivuve on 2017-01-31
Recently my ISP suffered an outage & I had no internet access. I was still connected to my router with my laptop so I could access files off my NAS.  While I had no internet I noticed running sudo on my local machine took a very long time before it prompted me for my password.  Also strange, when running sudo while my laptop was connected to another network I get the error message
"sudo: unable to resolve host ubuntu"
I have checked /etc/hosts and my 127.0.0.1 points to my correct hostname.  What may potentially be causing this is I edited /etc/nsswitch.conf so I could access hosts on my network by their hostname.  I don't remember what changes I made but I included it below:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat
gshadow:        files

#hosts:          files resolve [!UNAVAIL=return] mdns4_minimal [NOTFOUND=return] dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

Thanks

---

### Post by TheFu on 2017-02-01
Well, you broke the name resolution line. Fix that.

---

