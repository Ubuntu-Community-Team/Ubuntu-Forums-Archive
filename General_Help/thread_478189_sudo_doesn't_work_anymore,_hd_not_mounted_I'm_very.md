---
title: "sudo doesn't work anymore, hd not mounted: I'm very close to reinstall"
date: 2007-06-19
forum: General Help
---

### Post by willywongi on 2007-06-19
Hi everyone,
yesterday, after trying to mount an img file through FUSEIMG, my self-compiled audio driver disappeared, the sudo command doesn't work anymore (ie. it asks me for the password but then does nothing), and my NTFS partitions aren't mounted by default anymore (and can't mount them because of the non-working sudo). 
As I googled through the forum I found that I could try getting in as root by the recover option on startup and then dpkg -i another version of the sudo program, which I did, or try to dpkg-reconfigure the package sudo, which I did too, but nothing helped.
A part from reinstall, which I will do probably with the Gibbon (I'm gonna resize that useless winxp partition), what could I try to do?
Thank you.

---

### Post by willywongi on 2007-06-19
Solved! Everything was messed up because of the corrupted sudo configuration. I followed a clear and straightforward guide founded in the signature of ubuntu forum's users.
If you happen to step into this problem take a look here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Thanks, and good luck folks!

---

