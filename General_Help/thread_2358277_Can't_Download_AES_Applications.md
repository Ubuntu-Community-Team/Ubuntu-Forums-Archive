---
title: "Can't Download AES Applications"
date: 2017-04-11
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-04-11
I'm trying to work on some Linux security so I'm looking for anything involving AES and DES.  I'm on Software and found ssocks and ghostwriter-casept.  When I click to download them I get the following message in the screen shot.  I've had this problem before with an earlier version of Ubuntu, but I think I just moved on .  I know how to get them manually, but was wondering what was up with Software?  Is there any way to resolve this?

---

### Post by deadflowr on 2017-04-11
Those are snap packages.
while the issues of Ubuntu Software and UbuntuSSO should have been solved,
(there was an issue during the initial release of 16.04 that prevented users from logging into their SSO account in the software center) 
that issue should be fixed, and in all cases I have seen it has, you would need to run a system update to get the fixes)

That said, as these are snap packages, you can simply install them with the snap command line:
```
sudo snap install ghostwriter-casept
sudo snap install ssocks
```
I put both installs as separate commands since I've never tried to see if you can install multiple snap packages like you would with apt-get, ala
```
sudo apt-get install package1 package2 package3
```

hope it helps or makes sense.
good luck

---

### Post by shane_faulkinbury2 on 2017-04-12
Thanks a lot deadflowr!  I assume this will be fixed in 17.04?

---

