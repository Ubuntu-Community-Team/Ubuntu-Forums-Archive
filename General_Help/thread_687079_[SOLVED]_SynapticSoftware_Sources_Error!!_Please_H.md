---
title: "[SOLVED] Synaptic/Software Sources Error??!!? Please Help!"
date: 2008-02-03
forum: General Help
---

### Post by DarkZyzx on 2008-02-03
:confused:I'm getting this error message:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)



Please Help.:confused:

---

### Post by dcstar on 2008-02-04
> **DarkZyzx said:**
> :confused:I'm getting this error message:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)



Please Help.:confused:

Go into Synaptic and choose another repository (preferably one located close to you).

---

### Post by DarkZyzx on 2008-02-06
> **dcstar said:**
> Go into Synaptic and choose another repository (preferably one located close to you).
ummmm..... WHAT?:(

I figured out it is talking about the Security Updates, And System Update Selection...
:confused:
What do I do?????

Why is it saying Malformed Release File???? Wtf...:(
:confused:

---

### Post by kesman on 2008-02-06
Open up terminal and run
```

cat /etc/apt/sources.list

```
And paste the output here. You could also open up system -> administration -> software sources and check if there's something wrong.

---

### Post by DarkZyzx on 2008-02-06
It's okay, I found an answer on about ten other posts, but only one of them worked. DUH....   but thanx for trying to help.

---

