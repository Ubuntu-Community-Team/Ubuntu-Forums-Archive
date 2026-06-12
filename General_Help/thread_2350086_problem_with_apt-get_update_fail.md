---
title: "problem with apt-get update fail"
date: 2017-01-21
forum: General Help
---

### Post by samiaa71 on 2017-01-21
helloo mates

i am using ubuntu 14.04 server 

i have problem with apt-get update command fails


this is what said in terminal


****

login as: root
root@192.168.1.2's password:
Welcome to Ubuntu 14.04.5 LTS (GNU/Linux 4.2.0-42-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Sat Jan 21 13:24:02 2017 from 192.168.1.42
root@ubuntu:~# apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease

Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease

Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:~#

---

### Post by samiaa71 on 2017-01-21
still same when iu edit dns google

---

