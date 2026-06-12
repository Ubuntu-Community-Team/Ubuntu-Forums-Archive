---
title: "the update information is outdated and error msg inside"
date: 2012-12-19
forum: General Help
---

### Post by MaN227 on 2012-12-19
hello, sorry if this has been covered I did not see the particulars covered.  

as topic title says update info is outdated and  when runing apt-get update I get this returned. 

> W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-amd64/Packages](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-amd64/Packages)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-i386/Packages](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-i386/Packages)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en_US](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en_US)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en)  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.
would someone kindly help me with this? I'd much appreciate it. thanks and good daY  ;)

In settings I have chosen my country USA and the "pick the best for me" option.  no clue if this has any bearing, I changed to that from default in hopes it would perhaps rectify my problem, but no.

---

### Post by Elfy on 2012-12-19
getdeb is down and has been for a while now

---

### Post by MaN227 on 2012-12-19
first thanks Elfy for the reply :)

is it safe to delete those entries from the sources list then? do said entries need a replacement url entry?  sorry if questions seem daft.

---

### Post by zombifier25 on 2012-12-19
You can remove them from the sources completely, [or replace them with a mirror](http://forums.linuxmint.com/viewtopic.php?f=47&t=118809&p=656166#p656112). Remember to replace lucid with your Ubuntu version. Also, since it's just a mirror of the main site and the main site is down, softwares found in it won't receive updates.

---

### Post by Elfy on 2012-12-19
You should be able to remove them from Software Sources, you'll need to out them back if you want to use getdeb in the future obviously.

Question doesn't seem daft at all :)

---

