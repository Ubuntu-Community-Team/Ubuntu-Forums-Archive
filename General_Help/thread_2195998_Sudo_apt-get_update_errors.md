---
title: "Sudo apt-get update errors"
date: 2013-12-27
forum: General Help
---

### Post by willzhigaylo on 2013-12-27
I get the erros:

```
W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/binary-amd64/Packages  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages  404  Not Found [IP: 23.33.186.26 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


```
 How do I remove them?

---

### Post by deadflowr on 2013-12-27
I don't know what [distro] is.
post the output of 
```
cat /etc/apt/sources.list
```
and I think that the skype one is a file in the folder 
/etc/apt/sources.list.d
Look for something in there and post what the file says.

---

