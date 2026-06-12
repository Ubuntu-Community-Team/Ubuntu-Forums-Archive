---
title: "deja-dup (backups) InvalidBackendURL"
date: 2018-11-15
forum: General Help
---

### Post by Mark_in_Hollywood on 2018-11-15
On a clean re-install of 18.04, I tried to restore from Ubuntu's (horribly named) "Backups" which was formerly called deja-dup. Try searching for keywords like: "backups" "ubuntu" invalidbackendurl

When I could not restore, I tried to make a new backup. "Backups" threw this error message:

Error processing remote manifest (duplicity-inc.20181101T144800Z.to.20181109T180656Z.manifest.gpg): GPG Failed, see log below:
===== Begin GnuPG log =====
gpg: WARNING: "--no-use-agent" is an obsolete option - it has no effect
gpg: AES256 encrypted data
gpg: encrypted with 1 passphrase
gpg: decryption failed: Bad session key
===== End GnuPG log =====

and at other times it gives:

InvalidBackendURL: missing // - relative paths not supported for scheme invalid: invalid://

is this fixable? How would I go about repairing this, as "backups" is built-in to Ubuntu?

Is it simpler/quicker to reformat the "Storage Location" and start over? In my case, I have an external disk drive connected via USB cable.

---

### Post by zashboy on 2018-11-29
You need to install the python-oauth package.

$ sudo apt-get install python-oauth

---

### Post by Mark_in_Hollywood on 2018-12-07
I deleted the deja-dup created objects in ./home/cache. I reformatted the external drive and renamed it from dejadup to ExtUSB. Before that deja would not even offer a radio button of backup or restore. Both greyed out. After clearing deja's objects by shift-delete, I could run backup (radio button "working") but after a few moments:

```
Traceback (innermost last):
  File "/usr/bin/duplicity", line 1555, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1541, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1393, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1511, in do_backup
    full_backup(col_stats)
  File "/usr/bin/duplicity", line 572, in full_backup
    globals.backend)
  File "/usr/bin/duplicity", line 454, in write_multivol
    (tdp, dest_filename, vol_num)))
  File "/usr/lib/python2.7/dist-packages/duplicity/asyncscheduler.py", line 146, in schedule_task
    return self.__run_synchronously(fn, params)
  File "/usr/lib/python2.7/dist-packages/duplicity/asyncscheduler.py", line 172, in __run_synchronously
    ret = fn(*params)
  File "/usr/bin/duplicity", line 453, in <lambda>
    vol_num: put(tdp, dest_filename, vol_num),
  File "/usr/bin/duplicity", line 342, in put
    backend.put(tdp, dest_filename)
  File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 395, in inner_retry
    % (n, e.__class__.__name__, util.uexc(e)))
  File "/usr/lib/python2.7/dist-packages/duplicity/util.py", line 79, in uexc
    return ufn(unicode(e).encode('utf-8'))
 UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 37: ordinal not in range(128)
```

HELP!

---

