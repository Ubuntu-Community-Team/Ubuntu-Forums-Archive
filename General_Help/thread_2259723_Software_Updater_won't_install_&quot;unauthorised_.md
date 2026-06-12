---
title: "Software Updater won't install &quot;unauthorised packages&quot;"
date: 2015-01-06
forum: General Help
---

### Post by Gordonbp531 on 2015-01-06
I have the OwnCloud desktop sync utility installed.
Software Updater tells me there is an update, but when I click on "Install Now", it tells me there are unauthorised packages and to either click on Settings or OK.
If I click on Settings I can't find any option to allow these packages to install, and if I click on "OK" the software updater just closes.
Can I tell the Software Updater to permanently ignore this item?

---

### Post by slickymaster on 2015-01-06
Can you please post back here in the thread, [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect, the output you get from```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Gordonbp531 on 2015-01-07
Output from apt-get-update:

```
W: GPG error: [http://download.opensuse.org](http://download.opensuse.org)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 977C43A8BA684223
W: Duplicate sources.list entry [http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/](http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/)  Packages (/var/lib/apt/lists/download.opensuse.org_repositories_isv:_ownCloud:_desktop_xUbuntu%5f14.04_Packages)
```

Using the apt-get upgrade command in the terminal allowed the installation of the unauthorised packages, so it seems to be solved!
(Don't know why the Software Updater doesn't have that option...)

---

### Post by slickymaster on 2015-01-07
> **Gordonbp531 said:**
> Output from apt-get-update:

```
W: GPG error: [http://download.opensuse.org](http://download.opensuse.org)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 977C43A8BA684223

```
<---snip--->
To solve that GPG error, run the following in a terminal window:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 977C43A8BA684223
sudo apt-get update
```

---

### Post by slickymaster on 2015-01-07
> **Gordonbp531 said:**
> Output from apt-get-update:

```
W: Duplicate sources.list entry [http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/](http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/)  Packages (/var/lib/apt/lists/download.opensuse.org_repositories_isv:_ownCloud:_desktop_xUbuntu%5f14.04_Packages)
```

<---snip--->
Can you please post here in the thread the contents of the **/etc/apt/sources.list.d/owncloud-client.list**

---

### Post by Gordonbp531 on 2015-01-07
Thanks for your input - I've removed the duplicate ppa from the sources list and now everything seems to be OK!

---

### Post by slickymaster on 2015-01-07
You're welcome. Glad you got it fixed.

---

### Post by dalethomasnyc on 2015-09-08
Great thread!  Resolved my issue as well.  Had the exact same problem.

---

