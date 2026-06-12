---
title: "Can't download updates!"
date: 2008-06-04
forum: General Help
---

### Post by Fixman on 2008-06-04
Each time I apt-get update, I get this message:

```

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

```

Any idea of what it may be?

---

### Post by drs305 on 2008-06-04
Firefox or some other app has messed with your sources.list by adding *web* or additional tags at the end of your sources. If you don't know how to correct this post the results here:

To edit sources.list:
```
gksudo gedit /etc/apt/sources.list
```

You can also each source from within synaptic, settings, repositories.

---

### Post by Fixman on 2008-06-04
> **drs305 said:**
> Firefox or some other app has messed with your sources.list by adding *web* or additional tags at the end of your sources. If you don't know how to correct this post the results here:

To edit sources.list:
```
gksudo gedit /etc/apt/sources.list
```

You can also each source from within synaptic, settings, repositories.

Actually, this happenned when I added the updates repositories from Synaptic.

---

### Post by drs305 on 2008-06-04
> **Fixman said:**
> Actually, this happenned when I added the updates repositories from Synaptic.

I haven't read about that happening but I suppose anything's possible. Were there erroneous extras added to the end of the sources?

---

### Post by Fixman on 2008-06-04
> **drs305 said:**
> I haven't read about that happening but I suppose anything's possible. Were there erroneous extras added to the end of the sources?

This is my whole problem:

[IMG]http://201.235.238.54/img/pepe.png[/IMG]

---

### Post by Fixman on 2008-06-04
Help!

---

### Post by drs305 on 2008-06-04
I guess I'm not making myself clear enough. Did you open the sources.list and look at the actual entries to see what was causing the error message? It doesn't really matter what repositories you have checked, just the contents of the sources.list.

If you haven't or need us to find the errors, post the results of 
```
cat /etc/apt/sources.list
```

---

### Post by Fixman on 2008-06-04
> **drs305 said:**
> I guess I'm not making myself clear enough. Did you open the sources.list and look at the actual entries to see what was causing the error message? It doesn't really matter what repositories you have checked, just the contents of the sources.list.

If you haven't or need us to find the errors, post the results of 
```
cat /etc/apt/sources.list
```

Yes it was the first thing I did.

```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe web
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse web universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse web universe
deb http://mundogeek.net/repo ubuntu all

```

Theres nothing wrong.

---

### Post by drs305 on 2008-06-04
Each of your uncommented lines except the last one has the word *web* on it. This has to be removed from each line to get rid of the error messages.

---

### Post by HpZ on 2008-06-04
Same thing happens to me. Did you upgrade from a previous version of Ubuntu by any chance? I'd like this to be solved :(.

---

### Post by ohiomoto on 2008-06-04
Seems a lot of issues when using the updated kernel.

Check this out:

[http://ubuntuforums.org/showthread.php?t=818608](http://ubuntuforums.org/showthread.php?t=818608)

---

### Post by Fixman on 2008-06-05
> **drs305 said:**
> Each of your uncommented lines except the last one has the word *web* on it. This has to be removed from each line to get rid of the error messages.

This solved it!

---

