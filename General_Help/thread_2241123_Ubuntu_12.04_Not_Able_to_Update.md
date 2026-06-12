---
title: "Ubuntu 12.04 Not Able to Update"
date: 2014-08-24
forum: General Help
---

### Post by Simon_Ng on 2014-08-24
Hello all,
I am running Ubuntu 12.04. I have been seeing the following error message whenever I try to update the OS. Please help. 

[B]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W:Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages), W:Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages), W:Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages), W:Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages), W:Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages), E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'[/B]

Seems like I have duplicate resources. Where and how I can remove the duplicate?
Thanks.

---

### Post by Jesse_Campton on 2014-08-24
Take a look here at this thread: [http://ubuntuforums.org/showthread.php?t=1981513](http://ubuntuforums.org/showthread.php?t=1981513)

---

### Post by Simon_Ng on 2014-08-24
Thanks Managed to solve the duplicate issue. But I cannot solve this...

**E:Encountered a section with no Package: header, E:razz:roblem  with MergeList  /var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_i18n_Tra   nslation-en, E:The package lists or status file could not be parsed or  opened.'**

---

### Post by ibjsb4 on 2014-08-24
> **Simon_Ng said:**
> Thanks Managed to solve the duplicate issue. But I cannot solve this...

**E:Encountered a section with no Package: header, E:razz:roblem  with MergeList  /var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_i18n_Tra   nslation-en, E:The package lists or status file could not be parsed or  opened.'**
Medibuntu sources have been closed for a while now.  Open your software sources and either delete it or uncheck it.
[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

If you still get that message ..
```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```
You can find more here on the subject :)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened.&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened.&sa=Search&cof=FORID:9)

---

### Post by Simon_Ng on 2014-08-25
Thank you!! It works!! Learned something today.

---

### Post by sandyd on 2014-08-25
Hi, please mark this thread as solved via Thread Tools -> Mark Thread As Solved if you have found a solution.

Thanks!

---

