---
title: "Unable to connect to au.archive.ubuntu.com"
date: 2008-05-01
forum: General Help
---

### Post by Jarramundi on 2008-05-01
When I try to use the synaptic package manager, I get this msg:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/b/balazar/balazar_0.3.4.ds1-2ubuntu1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/b/balazar/balazar_0.3.4.ds1-2ubuntu1_all.deb)
  Unable to connect to au.archive.ubuntu.com http:

Is the server offline or is it something at my end?

---

### Post by bapoumba on 2008-05-01
I can get the .deb file. Is it working now?

---

### Post by Jarramundi on 2008-05-01
Yes it appears to be working now. Sorry to waste time. :)

---

### Post by bapoumba on 2008-05-01
No problem, you're welcome :)

---

### Post by Jarramundi on 2008-05-05
On second thought, still having problems... Tried to update today (have been away for a couple of days)
Get this error in update manager:

W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hardy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages)

What does it mean?

---

### Post by bapoumba on 2008-05-06
It means a repo has two entries in the sources.list. Please post the output to:
```
cat /etc/apt/sources.list
```

---

### Post by bensode on 2008-05-06
I'm also having issues in the US when attempting to run apt-get update and subsequent apt-get install from multiple machines.  Also trying to perform a new install and getting hung at 40% configuring apt so I figure the Ubuntu servers are getting hammered?

---

### Post by bapoumba on 2008-05-06
> **bensode said:**
> I'm also having issues in the US when attempting to run apt-get update and subsequent apt-get install from multiple machines.  Also trying to perform a new install and getting hung at 40% configuring apt so I figure the Ubuntu servers are getting hammered?
I just ran an update for a test and it hung there. Went through the second time around. So may be yes :)
I'll wait to install the updates.

---

### Post by Jarramundi on 2008-05-08
Here is my /etc/apt/sources.list


#
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://public.planetmirror.com/pub/ubuntu/archive/](http://public.planetmirror.com/pub/ubuntu/archive/) hardy main
deb-src [http://public.planetmirror.com/pub/ubuntu/archive/](http://public.planetmirror.com/pub/ubuntu/archive/) hardy main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse 


When I run the update manager I get this error:

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://public.planetmirror.com/pub/ubuntu/archive/dists/hardy/main/binary-i386/Packages.gz](http://public.planetmirror.com/pub/ubuntu/archive/dists/hardy/main/binary-i386/Packages.gz)  302 Found [IP: 203.16.234.19 80]
Failed to fetch [http://public.planetmirror.com/pub/ubuntu/archive/dists/hardy/main/source/Sources.gz](http://public.planetmirror.com/pub/ubuntu/archive/dists/hardy/main/source/Sources.gz)  302 Found [IP: 203.16.234.19 80]
Some index files failed to download, they have been ignored, or old ones used instead.

What is [http://packages.medibuntu.org?](http://packages.medibuntu.org?) Is this right?

---

### Post by bapoumba on 2008-05-08
[Medibuntu]("http://medibuntu.org/") is a third party repo for non free stuff (such as codecs) for ubuntu. I do not know what planetmirror is, are they hosting the medibuntu packages? Do you use it for some other reason? This is the repo giviing you trouble.
I do not like much to link to my own blog, but [here is a way to get the medibuntu repos]("http://bapoumba.wordpress.com/2008/05/01/medibuntu-non-free-codecs-for-hardy/").

---

### Post by Jarramundi on 2008-05-08
Planetmirror is just a ubuntu repo mirror site for Australia.
I don't know where medibuntu came from, I never added it to my sources.list, and I can't see it anywhere to delete it. I don't particularly want it or need it, so how do I get rid of it?

---

### Post by dgarnett on 2008-05-08
I too am having this issue installing in the US with 7.10 and 8.04 and keep getting Connection Failed [IP:91.189.88.45 80]

---

### Post by Jarramundi on 2008-05-08
Ok, I tried this and it seemed to work, my computer updated at least.

Hit System>Admin>Software Sources

Checked all the boxes, picked 'Server for Australia', exited and restarted ubuntu. 

Haven't had any mention of medibuntu again.

---

### Post by bapoumba on 2008-05-08
Okay, thanks. May be the planetmirror was pointing at medibuntu somehow, or hosting their repos too.

---

