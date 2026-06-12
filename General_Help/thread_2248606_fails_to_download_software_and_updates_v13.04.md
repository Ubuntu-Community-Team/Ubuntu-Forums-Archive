---
title: "fails to download software and updates v13.04"
date: 2014-10-15
forum: General Help
---

### Post by darioman on 2014-10-15
darioman@darioman-EL1200-05w:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-security/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-security/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-security/main Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Dennis N on 2014-10-15
13.04 release is no longer supported and these Raring repositories no longer work. You need to do a new install of 12.04 or 14.04.

---

