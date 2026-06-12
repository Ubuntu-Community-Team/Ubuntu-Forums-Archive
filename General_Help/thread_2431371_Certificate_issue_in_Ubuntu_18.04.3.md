---
title: "Certificate issue in Ubuntu 18.04.3"
date: 2019-11-15
forum: General Help
---

### Post by Macten on 2019-11-15
I am running 18.04.3 in a virtualbox vm and just within the last week or so I have been getting some strange errors. It started with PHPStorm notifying me that server certificates were invalid, then I noticed in the terminal when I run sudo apt-get update there are two errors.

Err:5 [https://deb.nodesource.com/node_10.x](https://deb.nodesource.com/node_10.x) bionic Release                                                                                                                                
  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 99.86.230.92 443]
Err:6 [https://dl.yarnpkg.com/debian](https://dl.yarnpkg.com/debian) stable Release                                                                                                                                       
  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 104.18.126.100 443]

I also noticed that LivePatch was having an issue as well, I disabled it but it wouldn't come back up when I tried to re-enable it. 

Then I realized on my Windows 7 host machine that PhpStorm was giving me the same certificate error that I'm getting on the VM. 

I'm assuming these events are somehow all related but I'm not sure where to begin as far as troubleshooting them.

**EDIT: I'm beginning to suspect it is a network security issue. I'll update this post when I find out more information.**

---

### Post by Macten on 2019-11-15
Also - when I go to Ubuntu Software -> Updates and click the refresh button it says 

"Unable to download updates from "extensions.gnome.org":[*/*/*/source/shell-extensions/*] failed to download [https://extensions.gnome.org//static/extensions.json:](https://extensions.gnome.org//static/extensions.json:) SSL handshake failed.
"Unable to download updates from "extensions.gnome.org":[*/*/*/source/odrs/*] failed to download [https://odrs.gnome.org/1.0/reviews/api/ratings:](https://odrs.gnome.org/1.0/reviews/api/ratings:) SSL handshake failed.

---

### Post by Macten on 2019-11-15
LivePatch error:

Failed to enable Livepatch: cannot enable machine: cannot send request: Post [https://livepatch.canonical.com/api/machine-tokens:](https://livepatch.canonical.com/api/machine-tokens:) x509: certificate signed by unknown authority

---

