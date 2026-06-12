---
title: "backup errors"
date: 2014-01-10
forum: General Help
---

### Post by ELMIT on 2014-01-10
I try to use (scheduled) backup the following directories:
/home
/var/www
/etc


I get following errors:


Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1414, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1407, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1389, in main
    incremental_backup(sig_chain)
  File "/usr/bin/duplicity", line 575, in incremental_backup
    bytes_written = dummy_backup(tarblock_iter)
  File "/usr/bin/duplicity", line 199, in dummy_backup
    while tarblock_iter.next():
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 516, in next
    result = self.process(self.input_iter.next())
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 188, in get_delta_iter
    for new_path, sig_path in collated:
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 279, in collate2iters
    relem2 = riter2.next()
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 348, in combine_path_iters
    refresh_triple_list(triple_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 334, in refresh_triple_list
    new_triple = get_triple(old_triple[1])
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 320, in get_triple
    path = path_iter_list[iter_index].next()
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 232, in sigtar2path_iter
    for tarinfo in tf:
  File "/usr/lib/python2.7/dist-packages/duplicity/tarfile.py", line 2470, in next
    tarinfo = self.tarfile.next()
  File "/usr/lib/python2.7/dist-packages/duplicity/tarfile.py", line 2343, in next
    raise ReadError(str(e))
ReadError: missing or bad subsequent header

---

### Post by grier-devon on 2014-01-10
okay so my question is have you been doing the schedule backup with no problems and then this happened or was this your first attempt to set it up and that was the error it prompted you?

---

### Post by Erik1984 on 2014-01-10
Apparently the error you are receiving is related to this issue: [https://bugs.launchpad.net/duplicity/+bug/1252484](https://bugs.launchpad.net/duplicity/+bug/1252484)

---

### Post by grier-devon on 2014-01-12
My personal recommendation is to just do manual backups. The only time I recommend the automatic backups is on a system which is on 24x7x365, something like a server even if that is a small home server. I do monthly backups, anything important which I may fear in losing in between I use in Ubuntu One cloud. This will make for less of an headache.

---

