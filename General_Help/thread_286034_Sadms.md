---
title: "Sadms"
date: 2006-10-27
forum: General Help
---

### Post by rickymartin91 on 2006-10-27
Hi,

Has anyone else got a problem running the install on the sadms giu? It fails with a _include.sh problem?

Thanks
Richard

---

### Post by stevea1210 on 2006-11-14
I'm having the same issue.  After validating the data I added, then clicking install, I get the below error:

```
./_include.sh: 7: pushd: not found
.: 8: Can't open ./_include-defaults.sh
[ERROR]
returned error code 4
```

Anyone have any ideas?  This is on a clean install of edgy

---

### Post by stevea1210 on 2006-11-20
bump...

---

### Post by adamkane on 2006-11-21
Download the Ubuntu version:
[sadms-install-ubu-2.0.6.tar.gz]("http://downloads.sourceforge.net/sadms/sadms-install-ubu-2.0.6.tar.gz?modtime=1156923238&big_mirror=0")

Extract archive.

Go to folder:
/sadms-2.0.6/ubuntu

Double click the .deb file:
sadms_2.0.6-1_all.deb

No need to install from source.

---

### Post by stevea1210 on 2006-11-29
@ adamkane:
  The error wasn't actually during the install of SADMS itself.  
After successfully installing the app, and running it, one of the steps is labeled "install".  Sorry for the confusion.

It is a moot point however, as a new version was released last week, and works fine.  I uninstalled the older version, installed the newer version, and it worked like a charm, no errors :)

---

