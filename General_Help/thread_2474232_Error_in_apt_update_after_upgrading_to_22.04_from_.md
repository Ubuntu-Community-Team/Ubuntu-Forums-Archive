---
title: "Error in apt update after upgrading to 22.04 from 20.04"
date: 2022-04-24
forum: General Help
---

### Post by mickee384 on 2022-04-24
EDIT_ Fixed the error by removing the entry from "Other Software" in Software and Updates

Hi!

I upgraded from 20.04 last night to 22.04. When running apt update I get an error referencing key for bionic. Not sure whay that is still there as I am on jammy. Here is the screenshot. Any help in fixing this will be appreciated!

```
mickee@mickeymouse:~$ sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:2 https://packages.microsoft.com/repos/edge stable InRelease                                   
Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]                        
Hit:4 http://dl.google.com/linux/chrome/deb stable InRelease                                       
Hit:5 http://ca.archive.ubuntu.com/ubuntu jammy InRelease                                          
Hit:6 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease               
Hit:7 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Hit:8 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease
Err:3 http://security.ubuntu.com/ubuntu bionic-security InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Fetched 88.7 kB in 2s (44.2 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com/ubuntu bionic-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

