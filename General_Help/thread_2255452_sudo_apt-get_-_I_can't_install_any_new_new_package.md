---
title: "sudo apt-get - I can't install any new new packages"
date: 2014-12-05
forum: General Help
---

### Post by LownuxiusXVII on 2014-12-05
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
smoof@Socrates:~/Desktop/nuMOTO/moto/linux64$ 


I get this error message with each and every package I try to download.
Can anyone assist me? I don't want to have to reinstall this entire LAMP stack and drupal environment. ...
thanks for any assistance.

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

---

### Post by slickymaster on 2014-12-05
Hi LownuxiusXVII, welcome to the forums.

That error is generally a indication of corrupted control files. In a terminal window run the following, one at a time:```
sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade
```

---

