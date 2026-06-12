---
title: "Help adding new repository in sources.list please"
date: 2006-09-21
forum: General Help
---

### Post by moufranica on 2006-09-21
Dear Gurus,
I have added two repositories in sources.list for installing sipxpbx (sipX server). But when I run **apg-get update** I get the following error:
```

root@ubuntuserver:/home/user/sipxpbx# apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Ign http://scm.calivia.com stable Release.gpg
Ign http://scm.calivia.com stable Release
Hit http://security.ubuntu.com dapper-security Release
Ign http://scm.calivia.com stable/main Packages
Hit http://scm.calivia.com stable/main Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Get:2 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Get:3 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://us.archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Get:4 http://us.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Get:5 http://us.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Fetched 31B in 12s (3B/s)
Reading package lists... Done

```
The packages list doesn't seem to get updated as when I run **apt-get install sipxpbx** I get the follwing:
```

root@ubuntuserver:/home/user/sipxpbx# apt-get install sipxpbx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sipxpbx: Depends: libcgicc1 but it is not installable
           Depends: libsipxcall1 but it is not going to be installed
           Depends: libsipxcommserver1 but it is not going to be installed
           Depends: libsipxmediaadapter1 but it is not going to be installed
           Depends: libcgicc1 (>= 3.2.3) but it is not installable
           Depends: sipxconfig (>= 3.0.1) but it is not going to be installed
           Depends: sipxregistry (>= 3.0.1) but it is not going to be installed
           Depends: sipxproxy (>= 3.0.1) but it is not installable
           Depends: sipxpublisher (>= 3.0.1) but it is not going to be installed
           Depends: sipxvxml (>= 3.0.1) but it is not going to be installed
E: Broken packages


```

Please help. I really want to try out sip!!!

---

### Post by Jussi Kukkonen on 2006-09-21
I believe you need to Read The Fine Manual more carefully: 
[http://sipx-wiki.calivia.com/index.php/SipX_on_Ubuntu](http://sipx-wiki.calivia.com/index.php/SipX_on_Ubuntu) says you need to use the Universe repository too...

---

### Post by moufranica on 2006-09-21
Hi Jussi, that was fast! Thanks. It's working now. Hope I can get this properly configured and running. Cheers!

---

