---
title: "extras.ubuntu.com apt-get issue"
date: 2014-05-27
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-05-27
when running apt-get update i get this
```
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com trusty Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```
is there a config error on the server or do i need to update a key and if so how?

---

### Post by pqwoerituytrueiwoq on 2014-05-30
so i changed the source from trusty to saucy for this source and ran apt-get update then changed it back to trusty and ran apt-get update and it fixed it

---

