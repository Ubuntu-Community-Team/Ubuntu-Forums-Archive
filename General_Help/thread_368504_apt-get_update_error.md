---
title: "apt-get update error"
date: 2007-02-23
forum: General Help
---

### Post by bns on 2007-02-23
I am getting a consistant error when I try to update my package list.  At first I ran it in Adept, then the command line to get a more verbose error message.  This is the error:

> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-1386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-1386/Packages.gz)  Sub-process gzip returned an error code (1)

I'm not sure what the problem is.  Any help?

---

### Post by bns on 2007-02-23
I first noticed the problem after I activated the medibuntu repository using the howto found here:

[HTML]http://medibuntu.sos-sts.com/repository.php[/HTML]

---

### Post by taurus on 2007-02-23
Edit /etc/apt/sources.list 

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all the repos.  Then, run these two commands again and see what happens.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by bns on 2007-02-23
That fixed it.  Thanks a bunch.  There were a lot of packages that needed updating too.  59 packages including OpenOffice.org kde and xorg.  Is the us repository a problem or did they just lag on a couple of updates?

---

### Post by taurus on 2007-02-23
I am not sure if the US mirror is still up and even if it were up, it was running real slow.  So, use the main repos then.

---

