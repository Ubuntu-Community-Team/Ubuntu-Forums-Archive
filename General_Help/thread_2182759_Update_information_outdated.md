---
title: "Update information outdated"
date: 2013-10-22
forum: General Help
---

### Post by Panawe on 2013-10-22
Hi,

A permanent red triangle has recently appeared on my desktop and persists despite my doing what it says and checking for updates. I did a *sudo apt-get update* in Terminal and got the following.

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/Release](http://packages.medibuntu.org/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

I'm a beginner so spell it out pls.

TIA

---

### Post by howefield on 2013-10-22
The medibuntu repositories no longer exist so you have to remove them from your sources.list file.

Open up the Software Centre, and from the Edit menu, select Software Sources, you should be able to remove or uncheck anything labeled medibuntu from the Other Software tab.

---

### Post by ibjsb4 on 2013-10-22
More here

[http://ubuntuforums.org/showthread.php?t=2181557](http://ubuntuforums.org/showthread.php?t=2181557)

---

### Post by Panawe on 2013-10-22
Jolly good. I guessed it was repository related.

---

