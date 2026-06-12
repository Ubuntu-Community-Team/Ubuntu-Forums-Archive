---
title: "Configure apt-get to install from Software DVD"
date: 2008-05-15
forum: General Help
---

### Post by soumen08 on 2008-05-15
Hello,
I have a small question here. I had downloaded the live CD of hardy and installed from it and have by now downloaded and installed all programs i need. I have only just finished downloading the Hardy DVD from the cdimage.ubuntu.com site and i can't get hardy to install things from the DVD without downloading them from the internet. I have added the DVD as a software source. I interpret the problem to be one of repositories. When i refresh the repos for a full set of sources, it downloads lists of new packages and even when i have added the DVD it tries only to install the newer versions of the packages from the web. I want to know if this can be prevented. I should be able to install a package try it out and then update it to it's latest version if i wish to. Grateful for help:),
Soumen

---

### Post by kirios on 2008-05-15
Try disabling the Internet repos (Settings > Repositories). 

> **soumen08 said:**
> Hello,
I have a small question here. I had downloaded the live CD of hardy and installed from it and have by now downloaded and installed all programs i need. I have only just finished downloading the Hardy DVD from the cdimage.ubuntu.com site and i can't get hardy to install things from the DVD without downloading them from the internet. I have added the DVD as a software source. I interpret the problem to be one of repositories. When i refresh the repos for a full set of sources, it downloads lists of new packages and even when i have added the DVD it tries only to install the newer versions of the packages from the web. I want to know if this can be prevented. I should be able to install a package try it out and then update it to it's latest version if i wish to. Grateful for help:),
Soumen

---

### Post by Vivaldi Gloria on 2008-05-15
You can always copy the packages from DVD to

```
/var/cache/apt/archives
```

Then they won't be downloaded from web.

---

