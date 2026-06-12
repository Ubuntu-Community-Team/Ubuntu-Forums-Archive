---
title: "nfs mounted data inaccessible?"
date: 2017-01-18
forum: General Help
---

### Post by lou.degenaro on 2017-01-18
Here is my id:

lou@HAL9000:/nfs/cloud/lou/photos$ id
uid=1000(lou) gid=1000(lou) groups=1000(lou),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare),1004(tomcat)

Here is the mounted filesystem:

lou@HAL9000:/nfs/cloud/lou/photos$ df .
Filesystem                    1K-blocks       Used  Available Use% Mounted on
192.168.1.110:/nfs/cloud.lou 3841446736 1739816800 2062585504  46% /nfs.cloud.lou

Here are the contents:

lou@HAL9000:/nfs/cloud/lou/photos$ ls -atl
total 28
drwxrwxrwx  7 lou  lou  4096 Jan 18 20:12 .
drwxrwxrwx 25 root root 4096 Jan 12 18:08 ..
drwxrwxr-x  5  501 lou  4096 Jan 11 18:34 iphone
drwxrwxrwx  2 lou  lou  4096 Dec 25  2015 2008
drwxrwxrwx  3 lou  lou  4096 Dec 24  2015 2015
drwx------  2 lou  lou  4096 Aug  8  2015 2015_08_07
drwx------  4 lou  lou  4096 Jun 28  2015 Pictures

Here's what happens when I try to cd into one of the subdirectories that have owner only permissions:

lou@HAL9000:/nfs/cloud/lou/photos$ cd Pictures/
bash: cd: Pictures/: Permission denied

Why?

Thanks.

Lou.

---

### Post by SeijiSensei on 2017-01-18
Do you have uid 1000 on the client as well?

---

### Post by lou.degenaro on 2017-01-19
What's shown is the client machine.  I'm mystified as to why I can cd into all directories except the last 2.

---

### Post by SeijiSensei on 2017-01-19
And those directories are owned by user 1000 and have the execute privilege enabled?

Are they in the same physical filesystem as the other directories, or are they mounted from other locations?  NFS won't re-export a mounted share for security reasons.

---

