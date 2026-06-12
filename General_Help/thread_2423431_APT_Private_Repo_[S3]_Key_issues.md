---
title: "APT Private Repo [S3] Key issues"
date: 2019-07-23
forum: General Help
---

### Post by liorb2 on 2019-07-23
I am using a private repo on Ubuntu 14.04 and everything works as expected.


While trying to build an Image based on Ubuntu 18.04.2 LTS I am getting this error:


```
W: GPG error: s3://my-repo-path stable Release: The following signatures were invalid: XXXXXXXXXXXXXX
```
This occurs after im adding the key like this:


```
$ aws s3 cp s3://my-repo-pth/key.pgp - | apt-key add
$ OK
$ apt-get update

```Any ideas why?

---

### Post by TheFu on 2019-07-23
Old keys become invalid.  I invalidate and revoke my old gpg keys yearly.  Probably worth checking that.

---

