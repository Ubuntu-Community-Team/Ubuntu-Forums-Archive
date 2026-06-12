---
title: "Owncloud client in 16.04"
date: 2016-04-17
forum: General Help
---

### Post by HereInOz on 2016-04-17
Hi All,

I have an installation of 16.04 and I notice that there is a version of the ownCloud client in the Ubuntu repositories, as well as one in the ownCloud repositories, and 16.04 consistently upgrades to the Ubuntu version.  The problem is that the version 2.1.1 in the ownCloud (opensuse) repositories is actually much better than the one in the Ubuntu repositories, and I would really like to use the ownCloud version.

Is there any way in which I can tell my 16.04 system to only use the version in the ownCloud repositories and to ignore the version in the Ubuntu repositories?  I have tried "Force version" in Synaptic, but for some reason it always defaults back to the Ubuntu version.  Very sad.

Hope you can help.

Cheers,

Alan.

---

### Post by ajgreeny on 2016-04-17
Pretty old but I assume it still works on xenial.

Give it a try.
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by howefield on 2016-04-18
What worked for me was to create a preferences file in /etc/apt/ and add the following in to it.

```
Package: owncloud-client
Pin: release n=xenial
Pin-Priority: -10

#Package: owncloud-client
#Pin: release n=devel
#Pin-Priority: 900

Package: libowncloudsync0
Pin: release n=xenial
Pin-Priority: -10

#Package: libowncloudsync0
#Pin: release n=devel
#Pin-Priority: 900
```

Had the commented out lines in the file originally but they don't seem to make any difference, hence commented out. Apt doesn't try to upgrade to the Ubuntu versions.

---

### Post by HereInOz on 2016-04-18
Thank you.

I will give that a go.  I have actually "held" the ownCloud version, so that it does not update to the ubuntu version, and my plan was to remove the hold as soon as ownCloud released an update, and the theory was that as long as the ownCloud version was newer than the Ubuntu version, all would be well.  

This appears a better solution, however.  Many thanks.

Alan

---

### Post by howefield on 2016-04-19
> **HereInOz said:**
> Thank you.

I will give that a go.  I have actually "held" the ownCloud version, so that it does not update to the ubuntu version, and my plan was to remove the hold as soon as ownCloud released an update, and the theory was that as long as the ownCloud version was newer than the Ubuntu version, all would be well.  

This appears a better solution, however.  Many thanks.

Alan

Benefit of giving the Ubuntu package a lower priority than the suse repo package is that you won't have to remember as you obviously realise.

Side note: For a while I was downloading the owncloud-client and libowncloudsync0 debs from the suse repository and using gdebi to install them so was happy to note that the Ubuntu xenial package had "caught up" to the current version, but it doesn't give me an owncloud indicator on the panel whereas the sue repository package does.

---

### Post by johan-ehnberg on 2016-04-27
If you check the ownCloud 16.04 repository, you will see that it does not currently even contain a client package at the time when I am writing this. So unless you use some outdated repository such as 14.04 after the update, you are out of luck.

It would be interesting to know what the strategy of Debian/Ubuntu and ownCloud is on this. Having an up-to-date or at least security supported client package in the ubuntu repos would be great.

---

### Post by howefield on 2016-04-27
> **johan-ehnberg said:**
> If you check the ownCloud 16.04 repository, you will see that it does not currently even contain a client package at the time when I am writing this. So unless you use some outdated repository such as 14.04 after the update, you are out of luck.

I'm taking the deb packages from [here]("http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/Ubuntu_15.10/amd64/")... the 15.10 repository which contains the current version and works fine with 16.04. To be honest, I download the deb packages and use gdebi to install then keep an eye out for updates. Not suggesting others do that just that it works for me.


> It would be interesting to know what the strategy of Debian/Ubuntu and ownCloud is on this. Having an up-to-date or at least security supported client package in the ubuntu repos would be great.

Not sure what you mean, the owncloud-client package in the 16.04 repository is up to date.

---

