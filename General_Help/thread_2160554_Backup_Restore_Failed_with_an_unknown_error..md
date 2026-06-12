---
title: "Backup Restore: Failed with an unknown error."
date: 2013-07-07
forum: General Help
---

### Post by SnakesAlive on 2013-07-07
Hi All,

The hard drive on my laptop died and had it replaced. I have done a clean install and I am attempting to restore from an external hard drive i backed up onto.
I have tried copying the files locally, clearning the .cache directory for duplicity and ive tried different restore dates. I have also uninstalled and reinstalled duplicity and dejadupe and have tried to restore from the command line. Anyone got any ideas on what is wrong?

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1411, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1404, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1338, in main
    restore(col_stats)
  File "/usr/bin/duplicity", line 632, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 526, in Write_ROPaths
    for ropath in rop_iter:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 499, in integrate_patch_iters
    final_ropath = patch_seq2ropath( normalize_ps( patch_seq ) )
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 463, in patch_seq2ropath
    assert first.difftype != "diff", patch_seq
AssertionError: [(('home', 'nathaniel', '.gnupg', 'random_seed') reg), (('home', 'nathaniel', '.gnupg', 'random_seed') reg), (('home', 'nathaniel', '.gnupg', 'random_seed') reg), (('home', 'nathaniel', '.gnupg', 'random_seed') reg), (('home', 'nathaniel', '.gnupg', 'random_seed') reg)]

---

### Post by SnakesAlive on 2013-07-07
Anyone got any ideas at all?

---

### Post by SnakesAlive on 2013-07-09
Bump please! Anything got anything to suggest?

---

### Post by SnakesAlive on 2013-07-10
hello there?

---

### Post by SnakesAlive on 2013-07-11
.. any suggestions on where i can get some help?

---

### Post by SnakesAlive on 2013-07-15
bump! anyone?

---

### Post by SnakesAlive on 2013-07-17
I don't even like fish

---

### Post by ubuking on 2013-10-23
I am having the same issue after upgrading to Ubuntu 13.10. I am now trying to restore directory by directory, which seems to work. For example, open Nautilus and go to your Documents folder (supposed that you have backed-up files from the Documents folder). Right-click and select "Restore Missing Files" . Deja-dup will now run an analysis between the current files in the Documents folder and the latest ones in the back-up, and will restore the back-up files where appropriate. Tedious and time consuming, but so far it seems to work

---

### Post by jpvrlau on 2013-10-26
While trying to restore 1 file via nautilis/revert/deja-dup I got the error listing below.  Really a bummer!!!
Ubunut 12.04LTS

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1411, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1404, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1284, in main
    globals.archive_dir).set_values()
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 691, in set_values
    self.get_backup_chains(partials + backend_filename_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 814, in get_backup_chains
    map(add_to_sets, filename_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 804, in add_to_sets
    if set.add_filename(filename):
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 93, in add_filename
    self.set_manifest(filename)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 124, in set_manifest
    remote_filename)
AssertionError: ('duplicity-full.20131015T135524Z.manifest', 'duplicity-full.20131015T135524Z.manifest.gpg')

---

### Post by jpvrlau on 2013-10-26
I tried restoring directory and continued to get same error.
Also, I was able to restore different item from same usb stick and backup about 10 days ago without issues.

Even the backup failed with same errors suggesting a serious problem with recent updates.

---

