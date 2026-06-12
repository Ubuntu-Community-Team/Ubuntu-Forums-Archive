---
title: "Deja-Dup not restoring from UbuntuOne"
date: 2012-10-28
forum: General Help
---

### Post by Firepowerforfreedom on 2012-10-28
I'm trying to restore from a Deja-Dup backup to UbuntuOne, but as soon as the restore hits something like "syncdaemon/tritcask" (I'll post the full line when it shows up again) it sits for a little while, then goes back to the beginning and starts all over. Eventually, it gives up and says "Restore Failed", with this error:

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1404, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1397, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1331, in main
    restore(col_stats)
  File "/usr/bin/duplicity", line 624, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 522, in Write_ROPaths
    for ropath in rop_iter:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 495, in integrate_patch_iters
    final_ropath = patch_seq2ropath( normalize_ps( patch_seq ) )
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 462, in patch_seq2ropath
    assert first.difftype != "diff", patch_seq
AssertionError: [(('home', 'malinda', '.local', 'share', 'ubuntuone', 'syncdaemon', 'tritcask', '1351207089149357.live.tritcask-v1.data') reg)]

Help! :(

---

