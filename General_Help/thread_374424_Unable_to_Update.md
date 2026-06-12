---
title: "Unable to Update"
date: 2007-03-02
forum: General Help
---

### Post by nastavirss on 2007-03-02
I installed Dapper Drake on my system and tried updating using

sudo apt-get install update


i am getting errors. Here is a sample list of errors

```
Err http://us.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 91.189.89.8 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 91.189.89.8 80]
Ign http://security.ubuntu.com dapper-security Release
Err http://us.archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 91.189.89.8 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://us.archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://us.archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://us.archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://us.archive.ubuntu.com dapper/restricted Packages
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed

```


I am using the default repository list(provided with installation)

Kindly help me

---

### Post by Shatrat on 2007-03-02
Well, looks like a connection problem.
Do you have an internet connection working? 
Can you ping 91.189.89.8 or us.archive.ubuntu.com?

---

### Post by nastavirss on 2007-03-02
i am able to ping

---

### Post by nastavirss on 2007-03-02
if i change all http links in my source repository to "ftp" then it works.
Can somebody explain whats happening? If possible a solution to correct this error

---

