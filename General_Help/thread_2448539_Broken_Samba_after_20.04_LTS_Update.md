---
title: "Broken Samba after 20.04 LTS Update"
date: 2020-08-09
forum: General Help
---

### Post by csete on 2020-08-09
My server machine has been on 18.04 LTS until today when I decided to update to 20.04.  Somewhere along the way I had attempted to update to a newer version of Samba via a PPA and it appears that I've now managed to hose up things.  At first I was unable to updated to 20.04 so I attempted to uninstall Samba, but it seems like I left things in a bad state.  After the 20.04 update if I try to reinstall Samba, I'm seeing:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: python3-samba but it is not going to be installed
         Depends: samba-common-bin (= 2:4.11.6+dfsg-0ubuntu1.3) but it is not going to be installed
         Depends: samba-libs (= 2:4.11.6+dfsg-0ubuntu1.3) but it is not going to be installed
         Recommends: samba-dsdb-modules but it is not going to be installed
         Recommends: samba-vfs-modules but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I've tried a variety of things using apt, dpkg, aptitude and synaptic.  Nothing I've found has thus far fixed this situation and I'm at a loss for how to proceed.  I'd really appreciate some pointers on how to resolve these issues and get Samba back up and running.

Thanks,
Craig

---

### Post by csete on 2020-08-09
I was finally able to get this fixed.  I found that libtalloc2 was stuck with the wrong PPA version.  I was able to force install the correct version:

```

sudo apt install libtalloc2=2.3.0-3ubuntu1

```

---

