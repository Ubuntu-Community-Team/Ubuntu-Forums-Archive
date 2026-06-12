---
title: "need help"
date: 2018-08-23
forum: General Help
---

### Post by eaglewand on 2018-08-23
when I am trying tor un sudo apt update I am getting this error
I am not able to understand it.

avinash@avinash:~$ sudo apt update
Err:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic InRelease
  Could not resolve 'in.archive.ubuntu.com'
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
  Could not resolve 'security.ubuntu.com'
Err:3 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease              
  Could not resolve 'packages.microsoft.com'
Err:4 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
  Could not resolve 'in.archive.ubuntu.com'
Err:5 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) bionic-backports InRelease
  Could not resolve 'in.archive.ubuntu.com'
Err:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
  Could not resolve 'dl.google.com'
Reading package lists... Done   
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/bionic/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/bionic/InRelease)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Could not resolve 'in.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  Could not resolve 'dl.google.com'
W: Failed to fetch [http://packages.microsoft.com/repos/vscode/dists/stable/InRelease](http://packages.microsoft.com/repos/vscode/dists/stable/InRelease)  Could not resolve 'packages.microsoft.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by oldos2er on 2018-08-23
Looks like you have no Internet connection.

---

