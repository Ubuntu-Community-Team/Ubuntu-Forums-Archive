---
title: "Duplicity list files errors out on google cloud storage"
date: 2014-09-03
forum: General Help
---

### Post by alienz2 on 2014-09-03
Hi, I am having issues using duplicity. It hasn't had issues backing up, but when I try to list files, I can't actually see anything.

Can anyone help with this?

```

root@server [~]# duplicity list-current-files gs://project/bucket
Import of duplicity.backends.dpbxbackend Failed: No module named dropbox
Synchronizing remote metadata to local cache...
Copying duplicity-full-signatures.20140830T054607Z.sigtar.gz to local cache.
Download gs://project/bucket/duplicity-full-signatures.20140830T054607Z.sigtar.gz failed (attempt #1, reason: StorageDataError: BotoClientError: Out of space for destination file /tmp/duplicity-PKapXY-tempdir/mktemp-EB3R4R-1)


Failed to read /tmp/duplicity-PKapXY-tempdir/mktemp-EB3R4R-1: (<type 'exceptions.IOError'>, IOError('Not a gzipped file',), <traceback object at 0x120ef80>)

```

---

