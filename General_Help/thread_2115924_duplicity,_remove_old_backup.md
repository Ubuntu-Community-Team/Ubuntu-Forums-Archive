---
title: "duplicity, remove old backup"
date: 2013-02-14
forum: General Help
---

### Post by derata on 2013-02-14
Good day

[B] I have a problem with deleting old backups. I have duplicity version 0.6.19 and ubuntu 12.10.

I am create a full backup[/B]

duplicity --no-encryption full /home/honza/Downloads scp://honza@192.168.80.161//home/honza/Documents

[B]then I change date +1 day a create second full backup

and again full backup

Then I wont to delete old backup with[/B]

duplicity --no-encryption remove-all-but-n-full 1 --force scp://honza@192.168.80.161//home/honza/Documents

root@ubuntu:/# duplicity --no-encryption remove-all-but-n-full 1 --force scp://honza@192.168.80.161//home/honza/Documents
Local and Remote metadata are synchronized, no sync needed.
Last full backup date: Tue Feb 19 06:06:27 2013
Deleting backup sets at times:
Sat Feb 16 05:57:21 2013
Sun Feb 17 06:02:54 2013
Mon Feb 18 06:05:01 2013
Deleting set full Mon Feb 18 06:05:01 2013
Deleting set full Sun Feb 17 06:02:54 2013
Deleting set full Sat Feb 16 05:57:21 2013
Warning, found incomplete backup sets, probably left from aborted session
Deleting these files from backend:
duplicity-full.20130217T140254Z.vol1.difftar.gz
duplicity-full.20130217T140254Z.vol2.difftar.gz
duplicity-full.20130217T140254Z.vol3.difftar.gz
duplicity-full.20130217T140254Z.vol4.difftar.gz
duplicity-full.20130217T140254Z.vol5.difftar.gz
duplicity-full.20130217T140254Z.vol6.difftar.gz
duplicity-full.20130217T140254Z.vol7.difftar.gz
duplicity-full.20130217T140254Z.vol8.difftar.gz
duplicity-full.20130216T135721Z.vol1.difftar.gz
duplicity-full.20130216T135721Z.vol2.difftar.gz
duplicity-full.20130216T135721Z.vol3.difftar.gz
duplicity-full.20130216T135721Z.vol4.difftar.gz
duplicity-full.20130216T135721Z.vol5.difftar.gz
duplicity-full.20130216T135721Z.vol6.difftar.gz
duplicity-full.20130216T135721Z.vol7.difftar.gz
duplicity-full.20130216T135721Z.vol8.difftar.gz
duplicity-full.20130218T140501Z.vol1.difftar.gz
duplicity-full.20130218T140501Z.vol2.difftar.gz
duplicity-full.20130218T140501Z.vol3.difftar.gz
duplicity-full.20130218T140501Z.vol4.difftar.gz
duplicity-full.20130218T140501Z.vol5.difftar.gz
duplicity-full.20130218T140501Z.vol6.difftar.gz
duplicity-full.20130218T140501Z.vol7.difftar.gz
duplicity-full.20130218T140501Z.vol8.difftar.gz
duplicity-full-signatures.20130216T135721Z.sigtar.gz
duplicity-full-signatures.20130217T140254Z.sigtar.gz
duplicity-full-signatures.20130218T140501Z.sigtar.gz


[B]But it only delete .manifest and archive file are still there and take up space on disk. If I use the same process and backup on local disk with file://backup it works good.

I do not know where is the problem and why this method does not delete old backup.
I tried this script [http://duplicity.nongnu.org/contrib/jwfull](http://duplicity.nongnu.org/contrib/jwfull) but same problem[/B]

---

