---
title: "Failed to download repository information"
date: 2019-12-30
forum: General Help
---

### Post by cyakat on 2019-12-30
I would like help on ubuntu 17.10. I'm trying to get updates but I can't download them. It just says "Failed to download repository information - Check your internet connection."
```
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful InRelease
Ign:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates InRelease
Ign:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports InRelease
Ign:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security InRelease
Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful Release
  404  Not Found [IP: 91.189.88.174 80]
Err:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates Release
  404  Not Found [IP: 91.189.88.174 80]
Err:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports Release
  404  Not Found [IP: 91.189.88.174 80]
Err:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security Release
  404  Not Found [IP: 91.189.88.174 80]
Reading package lists... Done
E: The repository '[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository '[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository '[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository '[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

Any help would be appreciated thanks :)

---

### Post by wildmanne39 on 2019-12-30
Hello and welcome to the forum, you can not update 17.10 because it is no longer supported and is a serious security risk if connected to the internet, I recommend you upgrade to a supported version of Ubuntu.

---

### Post by crip720 on 2019-12-30
It might be easier to to download and do a clean install.  Your choices are 18.04 or 19.10.  19.10 is supported for nine months from October past.  18.04 is supported for at least three more years, maybe more.  18.10 and 19.04 are no longer supported either.  Backup all your data you want to keep.

---

### Post by mörgæs on 2019-12-30
Why do you want 17.10 and not a supported version?

---

### Post by cyakat on 2020-01-09
Thank you for all of the feedback. I have 17.10 installed because it was the latest install I just had laying around and I was trying to update it to 18.04 or 19.10. Thank you for all of your help. I will just do a clean install of a later version.

---

