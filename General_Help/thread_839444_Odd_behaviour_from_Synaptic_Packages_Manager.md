---
title: "Odd behaviour from Synaptic Packages Manager"
date: 2008-06-24
forum: General Help
---

### Post by Tim.Read on 2008-06-24
Hi All,

I'm having very odd behaviour from from Synaptic Package Manager, Update Manager & apt....

Synaptic Package Manager does not work...  shows packages as "local & obsolete"

Updates Manager does not work... shows updates but won't install them.

apt works... installs the packages that the Update Manager shows but won't install.

How can this be?

---

### Post by drs305 on 2008-06-24
Are you getting any hostname error messages? If so, post:
```
cat /etc/hosts
```

---

### Post by oldos2er on 2008-06-24
In Synaptic, click the 'Status' button in the lower left. Does it show you more options?

 If you're seeing any error messages, it would help if you would post them.

---

### Post by Tim.Read on 2008-06-25
I'm not getting any hostname errors.

When I click the 'Status' in Synaptic then I see the normal "not installed", "installed",... I also see packages listed under "local & obsolete" but none listed as "upgradeable".

At the "same time" I see packages listed as "Recommended Updates" in Update manager. These packages do not install when I click the install button - Upadate Manager "Refreshes" and show the exact same information.

I've checked the "sources.list" files serveral times and I can find nothing out of place.

---

### Post by iaculallad on 2008-06-25
Doing the command below on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

Does it show any error?

---

### Post by plucky on 2008-06-25
> I've checked the "sources.list" files serveral times and I can find nothing out of place. 


Can you actually post your "sources.list" file?

Sometimes update are held back in the repositories if they are found to have problems,but are usually grayed out,but still appear in the Update Manager.

---

### Post by Tim.Read on 2008-06-25
Thats the really odd behaviour....

When I use apt-get everything installs to as it should without any errors.... then when I open the Update Manager there are no more updates listed. Synaptic still lists several packages as "local & obsolete"

However, give it a couple of days and there will be new updates and then the whole process starts again.

---

### Post by Tim.Read on 2008-06-25
I will post my 'sources.list' when I get home...

---

### Post by Tim.Read on 2008-06-25
/etc/apt/sources.list

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse universe
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy universe
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy universe
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-updates universe
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-updates universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) hardy partner
# deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) hardy partner

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-security main restricted
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-security universe
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-security multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe

---

### Post by drs305 on 2008-06-25
The sources.list looks ok. Do you have some odd proxy setup in syaptic (settings, pref, network)?

---

### Post by Tim.Read on 2008-06-25
No proxy settings, no "odd" network configurations...

I have the understanding that Synaptic, Update Manager & apt all use the same sources.list file...

How come they give differing results?

---

### Post by avtolle on 2008-06-25
Don't know if this will provide a clue for someone, but when you install from the command line, you are operating as root, temporarily. Wondering if your user is somehow not a part of the appropriate group(s) to use Update Manager and Synaptic?

---

### Post by Tim.Read on 2008-06-25
No, my network preferences are set to "direct conection to internet"

---

### Post by Tim.Read on 2008-06-25
one more thing I just noticed.

I installed a new package with Synaptic (so the root question is answered).

Immediately after I ran the Update Manager and it showed an update to that same package.... but it wouldn't install it.

I then ran "sudo apt-get upgrade" and the update installed.....

There must be something I'm missing, or some configuration file I messed up but I can't track it down...

---

### Post by plucky on 2008-06-25
> **Tim.Read said:**
> one more thing I just noticed.

Immediately after I ran the Update Manager and it showed an update to that same package.... but it wouldn't install it.

I then ran "sudo apt-get upgrade" and the update installed.....

There must be something I'm missing, or some configuration file I messed up but I can't track it down...

Under **System > Administration > Software Sources > Updates** how have you set up **Automatic Updates**.

Does it automatically download the updates?

I have mine set up to only notify about available updates.

Good Luck

---

