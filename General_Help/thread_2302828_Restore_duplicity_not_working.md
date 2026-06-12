---
title: "Restore duplicity not working"
date: 2015-11-13
forum: General Help
---

### Post by bmaring on 2015-11-13
Running Kubuntu 15.10.  Need to restore encrypted user in home.  I know the keyphrase.  Here is what I am getting:

bmaring@bmaring-Vostro-3555:~$ sudo mount /dev/sdc1 /media/usb
bmaring@bmaring-Vostro-3555:~$ sudo duplicity file:///media/usb/KubuntuBackup /tmp/restore
Synchronizing remote metadata to local cache...
GnuPG passphrase: 
Copying duplicity-full-signatures.20150724T121013Z.sigtar to local cache.
Copying duplicity-full.20150724T121013Z.manifest to local cache.
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1519, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1513, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1370, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1395, in do_backup
    globals.archive_dir).set_values()
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 700, in set_values
    self.get_backup_chains(partials + backend_filename_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 825, in get_backup_chains
    add_to_sets(f)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 813, in add_to_sets
    if set.add_filename(filename):
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 100, in add_filename
    self.set_manifest(filename)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 131, in set_manifest
    remote_filename)
AssertionError: ('duplicity-full.20150724T121013Z.manifest.gpg', 'duplicity-full.20150724T121013Z.manifest')

I am far from being proficient with Kubuntu.  Can anyone tell me what to try?

---

### Post by bmaring on 2015-11-13
Resolved.  Got it working after 4 days.

---

