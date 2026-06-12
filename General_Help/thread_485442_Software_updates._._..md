---
title: "Software updates. . ."
date: 2007-06-26
forum: General Help
---

### Post by krpnm on 2007-06-26
Question:  How do I get rid of programs that I have utterly and completely no, as in zero, need for.

Os:  Ubuntu v7.04.

Here are the packages:

a.  Samba-Common
b.  SMB client

I do *not* want to upgrade the blasted things, I want to permanently remove them (apt-get uninstall --purge).  However, if I do that then the Ubuntu-desktop is also purged.

Those packages are for networking a winblows share.  Our network is composed only of GNU/Linux boxes.

krp

---

### Post by UK-Wobbie on 2007-06-26
> **krpnm said:**
> Question:  How do I get rid of programs that I have utterly and completely no, as in zero, need for.

Os:  Ubuntu v7.04.

Here are the packages:

a.  Samba-Common
b.  SMB client

I do *not* want to upgrade the blasted things, I want to permanently remove them (apt-get uninstall --purge).  However, if I do that then the Ubuntu-desktop is also purged.

Those packages are for networking a winblows share.  Our network is composed only of GNU/Linux boxes.

krp



Have a go in Synaptic Package Manage and put the names down in search!
Go to System and then Administration, --> Synaptic Package Manage
On the thing you wanna  remove! Right click on it and go to remove or completely remove.

I hope this will help :D

---

### Post by SoggyCornflake on 2007-06-26
> **krpnm said:**
> Question:  How do I get rid of programs that I have utterly and completely no, as in zero, need for.

Os:  Ubuntu v7.04.

Here are the packages:

a.  Samba-Common
b.  SMB client

I do *not* want to upgrade the blasted things, I want to permanently remove them (apt-get uninstall --purge).  However, if I do that then the Ubuntu-desktop is also purged.

Those packages are for networking a winblows share.  Our network is composed only of GNU/Linux boxes.

krp

One of the prices of being a Distro for the the Masses is defaulting to a Windows  Friendly configuration I guess.

Looking over at [http://packages.ubuntu.com/feisty/metapackages/edubuntu-desktop]("http://packages.ubuntu.com/feisty/metapackages/edubuntu-desktop")  I see that SMB-Client is a required package for Ubuntu-Desktop,  so you're stuck I think.

---

### Post by UK-Wobbie on 2007-06-26
> **SoggyCornflake said:**
> One of the prices of being a Distro for the the Masses is defaulting to a Windows  Friendly configuration I guess.

Looking over at [http://packages.ubuntu.com/feisty/metapackages/edubuntu-desktop]("http://packages.ubuntu.com/feisty/metapackages/edubuntu-desktop")  I see that SMB-Client is a required package for Ubuntu-Desktop,  so you're stuck I think.

Yer i no what you mean! It's like installing a kde desktop on ubuntu, Sometimes when you unstall it it can f**k up! So when you reboot the pc it gets a black screen what is not showing anything only some erro codes :(
Then you can say bye bye to ubuntu lmfao

---

### Post by krpnm on 2007-06-27
> **UK-Wobbie said:**
> Have a go in Synaptic Package Manage and put the names down in search!
Go to System and then Administration, --> Synaptic Package Manage
On the thing you wanna  remove! Right click on it and go to remove or completely remove.

I hope this will help :D

No joy there.  That will also purge dependency Ubuntu-desktop.

But thank you anyway.

---

### Post by Steveway on 2007-06-27
It should be safe to remove Ubuntu-Desktop, since it is only a Meta-package.

---

### Post by krpnm on 2007-06-27
> **SoggyCornflake said:**
> One of the prices of being a Distro for the the Masses is defaulting to a Windows  Friendly configuration I guess.

Looking over at [http://packages.ubuntu.com/feisty/metapackages/edubuntu-desktop]("http://packages.ubuntu.com/feisty/metapackages/edubuntu-desktop")  I see that SMB-Client is a required package for Ubuntu-Desktop,  so you're stuck I think.

Yes, I do believe you are right.

Okay, let me ask this question -- how do I contact the Ubuntu desktop development folks to see if in the future we can dump that required dependency.

I think what would be the best way to fly in this particular case is to have an option available:

a.  NFS (what I use).
b.  Samba (For those who still need/want to be tied to Winblows).
c.  Neither.

The same holds true with Evolution.  I would not be caught dead at a dog fight running that hog (which is a huge put down on swine).  I prefer Thunderbird (though in all fairness T-bird is not at all ... slim).  But to fully purge Evolution you end up purging Ubuntu-desktop as well (I think the dependency is Evolution-ical, could be mistaken about that).

Thank you for your time and trouble.

---

### Post by krpnm on 2007-06-27
> **Steveway said:**
> It should be safe to remove Ubuntu-Desktop, since it is only a Meta-package.

I'm not so sure about that.  Comments contained within Synaptic are:

"The Ubuntu desktop system

"This package depends on all of the packages in the Ubuntu desktop system

"It is also used to help ensure proper upgrades, so it is recommended that
it not be removed."

Now if you are running Xubuntu you *can* remove it.

---

### Post by rbmorse on 2007-06-27
And you might want to look at Xubuntu. It's designed to "lite" right out of the box.

---

