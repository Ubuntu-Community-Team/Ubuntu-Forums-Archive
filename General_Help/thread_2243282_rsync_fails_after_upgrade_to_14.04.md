---
title: "rsync fails after upgrade to 14.04"
date: 2014-09-07
forum: General Help
---

### Post by cle-ziskind on 2014-09-07
"protocol version mismatch -- is your shell clean?"

The man page suggestions do not pan out - in particular, 

ssh remotehost /bin/true > out.dat

produces a zero-length file, just like it should. I'm rsync-ing in to SCO OSE 5.0.6 box (it's SCO, so no changes this century), FWIW.

?

---

### Post by nerdtron on 2014-09-07
From the man page:
```
       --protocol=NUM
              Force an older protocol version to be used.  This is useful  for  creating  a
              batch  file that is compatible with an older version of rsync.  For instance,
              if rsync 2.6.4 is being used with the --write-batch option, but  rsync  2.6.3
              is what will be used to run the --read-batch option, you should use “--proto-
              col=28” when creating the batch file to force the older protocol  version  to
              be  used in the batch file (assuming you can’t upgrade the rsync on the read-
              ing system).


```

Have you tired protocol=28?

---

### Post by cle-ziskind on 2014-09-19
> **nerdtron said:**
> From the man page:
```
       --protocol=NUM
              Force an older protocol version to be used.  This is useful  for  creating  a
              batch  file that is compatible with an older version of rsync.  For instance,
              if rsync 2.6.4 is being used with the --write-batch option, but  rsync  2.6.3
              is what will be used to run the --read-batch option, you should use “--proto-
              col=28” when creating the batch file to force the older protocol  version  to
              be  used in the batch file (assuming you can’t upgrade the rsync on the read-
              ing system).


```

Have you tired protocol=28?

Yes, that was exactly it. Thanks!

---

