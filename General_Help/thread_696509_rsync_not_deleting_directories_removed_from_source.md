---
title: "rsync not deleting directories removed from source"
date: 2008-02-14
forum: General Help
---

### Post by Nonney on 2008-02-14
I have done a fair bit of googling on this but not managed to find a definitive answer.

I am using the following rsync command to "synchronise" my file server with Amazon S3 using Jungledisk.

rsync -avvt --inplace --delete-after --force --log-file=/var/samba/njg.log homes/nigel/Documents/test/* media/jungledisk/homes/nigel/Documents/test

test has a subdirectory dir1 containing one file. If I delete the file and re-run the rsynch the file is deleted on the remote host. If I then remove the directory dir1 and re-run the rsync the directory is not removed. I have also tried running without the trailing "*" as some posts via Google suggested this; same result.

Is this a syntax error or is it an rsync feature/bug.

Any suggestions gratefully received.

Thanks.

---

### Post by perroazul on 2008-05-18
hi, I was having a similar problem, and I found this examplein a rsync manual: 
[INDENT]
rsync -avz foo:src/bar/ /data/tmp

a trailing slash on the source changes this behavior to transfer all files from the directory src/bar on the machine foo into the /data/tmp/. A trailing / on a source name means "copy the contents of this directory". Without a trailing slash it means "copy the directory". This difference becomes particularly important when using the --delete option. [/INDENT]
I changed my scripts accordingly and now the synchronization is working fine

---

