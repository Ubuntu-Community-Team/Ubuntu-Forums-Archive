---
title: "How to un-install OpenShot Video Editor"
date: 2022-01-02
forum: General Help
---

### Post by satimis on 2022-01-02
Hi all,

I have OpenShop video editor installed on software download on openshop.org sometimes ago.  It can be found on Activities.

I expect to uninstall it.  Please advise how to do it.  Thanks

Regards

---

### Post by KBar on 2022-01-02
First, check if it was installed via *Software*. Refer to [this]("https://help.ubuntu.com/lts/ubuntu-help/addremove-remove.html.en") guide. Try this method and tell us the results.

You say you downloaded it from openshot.org. The [download page](https://www.openshot.org/download/) distributes it in two formats: an AppImage and a .deb package from PPA.

---

### Post by schragge on 2022-01-02
I presume you're speaking about [OpenShot]("https://www.openshot.org/download")? How did you installed it? AppImage? [PPA]("https://www.openshot.org/ppa")? If the latter, which one? [Stable]("https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa") or [daily]("https://launchpad.net/~openshot.developers/+archive/ubuntu/daily")?.

---

### Post by satimis on 2022-01-02
> **schragge said:**
> I presume you're speaking about [OpenShot]("https://www.openshot.org/download")? How did you installed it? AppImage? [PPA]("https://www.openshot.org/ppa")? If the latter, which one? [Stable]("https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa") or [daily]("https://launchpad.net/~openshot.developers/+archive/ubuntu/daily")?.
Oh, sorry.  My typing mistake.

Old version
Version: 2.6.0-dev
libopenshot: 0.2.6-dev

Installed sometimes ago - download software on openshot.org.

I need to uninstall it and run the latest version AppImage;
OpenShot-v2.6.1-x86_64.AppImage

Thanks

Regards

---

### Post by ajgreeny on 2022-01-02
First try ```
sudo apt remove openshot
``` which will remove the application if it was installed from the repos in the normal way.

There are many dependencies that will probably also have been installed that you may need to remove as well; running command ```
sudo apt autoremove
``` should clear them away for you, as they will  not be required for an Appimage which contains all dependencies within the image itself.

---

### Post by satimis on 2022-01-02
Hi all,

Thanks for your advice.

To my recollection OpenShot was not installed on repo.  It was download and installed on openshot.org

$ apt policy openshot```

openshot:
  Installed: (none)
  Candidate: 2.4.3+dfsg1-1
  Version table:
     2.4.3+dfsg1-1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe i386 Packages

```

Regards

---

### Post by satimis on 2022-01-02
Problem solved running below command on Terminal;

$ sudo apt remove --autoremove openshot-qt

Regards

---

### Post by KBar on 2022-01-02
Please consider marking your threads as [SOLVED]

---

### Post by satimis on 2022-01-02
> **KBar said:**
> Please consider marking your threads as [SOLVED]
Already did it.

Thanks

---

