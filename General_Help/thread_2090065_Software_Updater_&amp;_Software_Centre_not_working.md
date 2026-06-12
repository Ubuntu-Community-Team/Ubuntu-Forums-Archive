---
title: "Software Updater &amp; Software Centre not working"
date: 2012-12-01
forum: General Help
---

### Post by tornadof3 on 2012-12-01
Hello

Every now and then the 'Software Updater' pops up with a list of new packages. Clicking the "Install Now" button used to work just fine. Now it greys out the window as if it were about to ask for my password, but never does.

Ubuntu Software Center loads OK, but if I click the 'install' button of a package, absolutely nothing happens. Apt-get from the command line is fine for installing things, however

```
sudo apt-get update
sudo apt-get upgrade all
```

does not list or install the updates that Software Updater says are available.

Does anyone have a hint as to what might be wrong? Are there any logs I can check?

Many thanks.

---

### Post by plucky on 2012-12-01
> **tornadof3 said:**
> Hello

Every now and then the 'Software Updater' pops up with a list of new packages. Clicking the "Install Now" button used to work just fine. Now it greys out the window as if it were about to ask for my password, but never does.

Ubuntu Software Center loads OK, but if I click the 'install' button of a package, absolutely nothing happens. Apt-get from the command line is fine for installing things, however

```
sudo apt-get update
sudo apt-get upgrade all
```

does not list or install the updates that Software Updater says are available.

Does anyone have a hint as to what might be wrong? Are there any logs I can check?

Many thanks.


Try ```
sudo apt-get dist-upgrade
``` and see what updates that will install.

dist-upgrade will not upgrade you to the next version,it will install held packages.

Good Luck

---

### Post by tornadof3 on 2012-12-01
```
sudo apt-get dist-upgrade
[sudo] password for pmreid: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Hmm. Might this be because I used Synaptic Package Manager a few mins ago to do the necessary updates? I think I can do updates now via Synaptic, I was just wondering if there is anyway to get Software Center / Automatic Updates working again?

Thanks for your reply.

---

