---
title: "Deja dup can not restore backups - LockFailed"
date: 2015-01-08
forum: General Help
---

### Post by score100 on 2015-01-08
Hello,
I'm trying to restore a backup and deja dup is starting to fail me with this error message. I did first try to do a restore that I cancelled while it was busy early on, because I accidentally chose the wrong folder to restore it towards. Then I tried again and got an error message that there was another instance of deja-dub busy with it, and that i should delete the lockfile from /home/moritz/.cache/deja-dup/39afb19e77e4e2bcc50620ee20a659ef if that wasn't the case. It wasn´t, as I had already restarted in between the last cancelled backup and there was no other instance running it. So I deleted the lockfile. Now I get this error immediately after hitting restore, re-installing doesn't help. :(

```
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1334, in main
    globals.lockfile.acquire(timeout = 0)
  File "/usr/lib/python2.7/dist-packages/lockfile.py", line 239, in acquire
    raise LockFailed("failed to create %s" % self.unique_name)
LockFailed: failed to create /home/moritz/.cache/deja-dup/39afb19e77e4e2bcc50620ee20a659ef/moritz-1008HA.MainThread-8415
```

Any Python experts know what that means?

---

### Post by score100 on 2015-01-12
huhu, anyone? :/

---

### Post by score100 on 2015-01-16
Am now trying to the same from a different laptop, same hard drive though and getting an error. Could it have to do with accidentally having deleted crucial files while erasing old backups? The packages are all still there, same as the duplicity manifest of that one backup I need. Here the new error:
```
Traceback (most recent call last):

  File "/usr/bin/duplicity", line 1494, in <module>

    with_tempdir(main)

  File "/usr/bin/duplicity", line 1488, in with_tempdir

    fn()

  File "/usr/bin/duplicity", line 1337, in main

    do_backup(action)

  File "/usr/bin/duplicity", line 1422, in do_backup

    restore(col_stats)

  File "/usr/bin/duplicity", line 697, in restore

    restore_get_patched_rop_iter(col_stats)):

  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 536, in Write_ROPaths

    for ropath in rop_iter:

  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 500, in integrate_patch_iters

    for patch_seq in collated:

  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 380, in yield_tuples

    setrorps( overflow, elems )

  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 369, in setrorps

    elems[i] = iter_list[i].next()

  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 113, in difftar2path_iter

    tarinfo_list = [tar_iter.next()]

  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 330, in next

    self.set_tarfile()

  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 324, in set_tarfile

    self.current_fp = self.fileobj_iter.next()

  File "/usr/bin/duplicity", line 733, in get_fileobj_iter

    backup_set.volume_name_dict[vol_num],

KeyError: 1

```

---

### Post by VanillaMozilla on 2015-09-17
I think duplicity is running with insufficient privilege to create a cache file.  Try the command again with sudo.  That worked for me.

In other words:
sudo duplicity <your command here>

Sorry I'm late to the party.  I was hoping you guys would tell me the answer.  Don't ask me how I figured it out, because right now I don't even see the clue.

---

