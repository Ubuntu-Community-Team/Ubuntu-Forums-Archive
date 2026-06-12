---
title: "problems running software updater"
date: 2013-03-06
forum: General Help
---

### Post by hunterkasy on 2013-03-06
I am running ubuntu 12.10 64

when I try to check for updates I get this: 

W:Failed to fetch [http://ppa.launchpad.net/ubuntu-adk-admins/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/ubuntu-adk-admins/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-adk-admins/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-adk-admins/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-adk-admins/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-adk-admins/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2013-03-06
ubuntu-adk-admins is either down or no longer available.  Uncheck them from your software sources for now and try them again later.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by cortman on 2013-03-06
Another way to do as ibjsb4 says (which is correct) is to run

```
gksu nautlius
```

and navigate to /etc/apt/sources.list.d/ and find the files corresponding to the non-existent repositories. Delete them and run the update again.

---

