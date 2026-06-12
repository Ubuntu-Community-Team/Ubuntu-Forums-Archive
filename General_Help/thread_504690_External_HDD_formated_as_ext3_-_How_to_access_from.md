---
title: "External HDD formated as ext3 - How to access from Vista?"
date: 2007-07-19
forum: General Help
---

### Post by kpkeerthi on 2007-07-19
I need to copy some data from my external ext3-formatted hard drive to Windows Vista. I checked [http://www.fs-driver.org/](http://www.fs-driver.org/) but doesn't seem to support Vista yet. Any suggestions?

---

### Post by reckless2k2 on 2007-07-19
boot to a livecd and work around copying that way even if it's from HDD ext3 to flash fat32 then vista will see it. you'll have to jump through some hoops unless you have a network drive or such to offload. in future, think share partition with fat32 format or even ntfs now since the ntfs driver thingie is working well.

---

### Post by dabl on 2007-07-19
If it's going to be an ongoing requirement to share that external hard drive between Windows and Ubuntu, probably the path of least difficulties is (after getting the data safely off of it) to use Windows to format it as NTFS, and then install ntfs-3g on your Ubuntu system. Here's a little writeup from Kubuntu Forums on it:

[http://kubuntuforums.net/forums/index.php?topic=3084679.0](http://kubuntuforums.net/forums/index.php?topic=3084679.0)

:)

---

### Post by ac0rn on 2007-07-19
If you have a network and a linux box, you could SMB share the hard drive, and access it with Vista over the network...

--acorn

---

### Post by kpkeerthi on 2007-07-19
Thanks for the tips guys. 

I was trying to see if there is anyway I could read from the ext3 drive without having to use an intermediate smb/nfs/ftp component to speed up the transfer process (about 20 gig of data - photos and music). But not a problem... where there is ubuntu Live CD, there is a way! Thanks again.

---

