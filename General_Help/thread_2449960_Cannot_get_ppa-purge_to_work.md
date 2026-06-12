---
title: "Cannot get ppa-purge to work"
date: 2020-09-04
forum: General Help
---

### Post by cscj01 on 2020-09-04
I have Ubuntu 18.04.5 x64.  I recently added the ppa at [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu).  I wasn't thrilled with the results, so I decided to remove it with ppa-purge so it would replace the original package. I first tried```
sudo ppa-purge -o libreoffice
``` and received the following> Updating packages lists
PPA to be removed: libreoffice ppa
Warning:  Could not find package list for PPA: libreoffice ppaThen I tried```
 sudo ppa-purge http://ppa.launchpad.net/libreoffice
```and received the following> Updating packages lists
PPA to be removed: [http://ppa.launchpad.net](http://ppa.launchpad.net) libreoffice
Warning:  Could not find package list for PPA: [http://ppa.launchpad.net](http://ppa.launchpad.net) 
libreofficeThen I tried```
sudo ppa-purge [ppa:]libreoffice/ubuntu
```and received the following> Updating packages lists
PPA to be removed: [ppa:]libreoffice ubuntu
Warning:  Could not find package list for PPA: [ppa:]libreoffice ubuntuFinally I tried```
sudo ppa-purge http://ppa.launchpad.net/libreoffice/ppa/ubuntu
```and received the following> Updating packages lists
PPA to be removed: [http://ppa.launchpad.net/libreoffice/ppa](http://ppa.launchpad.net/libreoffice/ppa) ubuntu
Warning:  Could not find package list for PPA: 
[http://ppa.launchpad.net/libreoffice/ppa](http://ppa.launchpad.net/libreoffice/ppa) ubuntuObviously one of two things is wrong:
[LIST=1]
[*]I haven't used the correct format yet or;
[*]ppa-purge is not working.
[/LIST]
Anybody have ideas as to what is wrong?

---

### Post by deadflowr on 2020-09-04
Try
```
sudo ppa-purge ppa:libreoffice/ppa
```
unless you have one of the distinct libreoffice ppas for 6-4 or 7-0 or other.
In which case it would be
```
sudo ppa-purge ppa:libreoffice/libreoffice-#-#
```
replacing the #-# with the actual release number.

---

### Post by cscj01 on 2020-09-04
> **deadflowr said:**
> Try
```
sudo ppa-purge ppa:libreoffice/ppa
```
unless you have one of the distinct libreoffice ppas for 6-4 or 7-0 or other.
In which case it would be
```
sudo ppa-purge ppa:libreoffice/libreoffice-#-#
```
replacing the #-# with the actual release number.
Thank you for your suggestions.  The ppa I have is for libreoffice 6.0.7.3.  I tried```
sudo ppa-purge ppa:libreoffice/ppa
```and got> Updating packages lists
PPA to be removed: libreoffice ppa
Warning:  Could not find package list for PPA: libreoffice ppaThen I tried```
sudo ppa-purge ppa:libreoffice/libreoffice-6.0
``` and got> Updating packages lists
PPA to be removed: libreoffice libreoffice-6.0
Warning:  Could not find package list for PPA: libreoffice libreoffice-6.0Then I tried```
sudo ppa-purge ppa:libreoffice/libreoffice-6.0.7.3
```and got> Updating packages lists
PPA to be removed: libreoffice libreoffice-6.0.7.3
Warning:  Could not find package list for PPA: libreoffice libreoffice-6.0.7.3It seems to me that this ppa is defying all efforts of ppa-purge to be removed.  I have some screens and queries defined for Libreoffice Base that I want to preserve.  That's why I haven't just removed Libreoffice and reinstalled the distro version.  I'm not sure whether that would cause me to lose those definitions.  I will say that those items I want tp preserve are not dependent on Libreoffice 6.0.  They were developed some releases ago, even before the distro versions.

That brings up a thought.  I had to do a fresh install after a system drive failure.  After I replaced the drive and installed from the Live DVD, I restored my home directory that I had backed up.  Then I installed all the programs  I use.  Libreoffice was part of the Live DVD installation.  I wonder why that didn't get rid of the items I want to save.  I also had to install Base separately, and that didn't get rid of the items.  All of this is to ask if I remove the ppa version and install the distro version, will I still have those items.  I'm not sure where Libreoffice keeps anything, so I really wanted ppa-purge to work.  I recall with Synaptic that you can remove or remove completely.  I wonder if I use Synaptic to remove if it will leave those panels and queries alone.

---

### Post by CelticWarrior on 2020-09-04
You can easily check which one you actually have in Software & Updates > Other software.
You can also remove the PPA from there but it won't have the same effect as ppa-purge. Ppa-purge uninstalls any software from the PPA and then removes it.

---

### Post by mc4man on 2020-09-04
Above or just run and post
```
apt-cache policy libreoffice-core
```

---

### Post by cscj01 on 2020-09-04
> **mc4man said:**
> Above or just run and post
```
apt-cache policy libreoffice-core
```

```
apt-cache policy libreoffice-core
libreoffice-core:
  Installed: 1:6.0.7-0ubuntu0.18.04.10
  Candidate: 1:6.0.7-0ubuntu0.18.04.10
  Version table:
 *** 1:6.0.7-0ubuntu0.18.04.10 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:6.0.3-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
```Does this give information about why ppa-purge won't work?

---

### Post by deadflowr on 2020-09-04
> **cscj01 said:**
> ```
apt-cache policy libreoffice-core
libreoffice-core:
  Installed: 1:6.0.7-0ubuntu0.18.04.10
  Candidate: 1:6.0.7-0ubuntu0.18.04.10
  Version table:
 *** 1:6.0.7-0ubuntu0.18.04.10 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:6.0.3-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
```Does this give information about why ppa-purge won't work?

Yes.
It shows 
1) It shows you have no LibreOffice PPA.
and 
2) The version you have from the Ubuntu Repositories is actually higher/newer than the version from the [LibreOffice-6-0 PPA]("https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-6-0?field.series_filter=bionic").

So even if you had the PPA, ppa-purge would be basically useless since you can't downgrade the packages.
If you happen to actually have a LibreOffice PPA you can just disable/remove the PPA from your sources.

---

### Post by monkeybrain20122 on 2020-09-05
It looks like you have deactivated the ppa already, so you have to reactivate it in order to use ppa-purge.

Edited: just saw deadflower's post above, so yes if the repo's version is higher than the ppa's then the ppa wouldn't have any effect, in that case you can either remove it or leave it so that next time when the ppa does get a new version you will get the upgrade.

---

### Post by cscj01 on 2020-09-05
> **monkeybrain20122 said:**
> It looks like you have deactivated the ppa already, so you have to reactivate it in order to use ppa-purge.

Edited: just saw deadflower's post above, so yes if the repo's version is higher than the ppa's then the ppa wouldn't have any effect, in that case you can either remove it or leave it so that next time when the ppa does get a new version you will get the upgrade.

> **deadflowr said:**
> Yes.
It shows 
1) It shows you have no LibreOffice PPA.
and 
2) The version you have from the Ubuntu Repositories is actually higher/newer than the version from the [LibreOffice-6-0 PPA]("https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-6-0?field.series_filter=bionic").

So even if you had the PPA, ppa-purge would be basically useless since you can't downgrade the packages.
If you happen to actually have a LibreOffice PPA you can just disable/remove the PPA from your sources.Thanks folks.  I did nothing to remove this PPA, and I didn't think about the repo's getting updated while I was "using" this PPA, although it makes sense that that could happen.  So I removed the PPA from my sources.  With that, I'll mark this thread as closed.  Thanks again.

---

