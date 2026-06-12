---
title: "Deja Dup won't work"
date: 2019-10-07
forum: General Help
---

### Post by elsuzu on 2019-10-07
hey guys!
I did a fresh Ubuntu 18.04. install and upgraded my RAM, as well as switching from a HDD to a SSD. Deja Dup seemed to work after a fresh install on the HDD but now on the SSD, it's still not working.

Here's what it says:
```
Nach 5 Versuchen wird aufgegeben. Error: gdata-service-error-quark: Legitimierung erforderlich: {
 "error": {
  "errors": [
   {
    "domain": "global",
    "reason": "authError",
    "message": "Invalid Credentials",
    "locationType": "header",
    "location": "Authorization"
   }
  ],
  "code": 401,
  "message": "Invalid Credentials"
 }
}
 (4)

```

The german means "stopped after 5 tries. I tried reinstalling deja-dup and it didn't help. I'm trying to get an upgrade on my Google Drive.
Any suggestions?

---

### Post by PaulW2U on 2019-10-07
> **elsuzu said:**
> I'm trying to get an upgrade on my Google Drive.
With respect to Google Drive, Deja-dup is broken in Ubuntu 18.04.

See the bug report: [Authentication error with google drive]("https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/1747646")

According to that report the snap, which has been updated to a later version than available in Ubuntu 18.04, works. Install with
```
sudo snap install deja-dup --classic
```
in a terminal window. I haven't tried it myself though as I don't backup to Google Drive.

---

### Post by elsuzu on 2019-10-07
thank you, I installed it this way and it looked quite promising, it was uploading for a few hours and now, another problem:

```
Traceback (innermost last):
  File "/snap/deja-dup/190/bin/duplicity", line 1711, in <module>
    with_tempdir(main)
  File "/snap/deja-dup/190/bin/duplicity", line 1697, in with_tempdir
    fn()
  File "/snap/deja-dup/190/bin/duplicity", line 1543, in main
    do_backup(action)
  File "/snap/deja-dup/190/bin/duplicity", line 1667, in do_backup
    full_backup(col_stats)
  File "/snap/deja-dup/190/bin/duplicity", line 573, in full_backup
    globals.backend)
  File "/snap/deja-dup/190/bin/duplicity", line 454, in write_multivol
    (tdp, dest_filename, vol_num)))
  File "/snap/deja-dup/190/lib/python3.6/site-packages/duplicity/asyncscheduler.py", line 150, in schedule_task
    return self.__run_synchronously(fn, params)
  File "/snap/deja-dup/190/lib/python3.6/site-packages/duplicity/asyncscheduler.py", line 176, in __run_synchronously
    ret = fn(*params)
  File "/snap/deja-dup/190/bin/duplicity", line 453, in <lambda>
    vol_num: put(tdp, dest_filename, vol_num),
  File "/snap/deja-dup/190/bin/duplicity", line 343, in put
    validate_block(putsize, dest_filename)
  File "/snap/deja-dup/190/bin/duplicity", line 325, in validate_block
    info = backend.query_info([dest_filename])[dest_filename]
  File "/snap/deja-dup/190/lib/python3.6/site-packages/duplicity/backend.py", line 633, in query_info
    info[filename] = self._do_query(filename)
  File "/snap/deja-dup/190/lib/python3.6/site-packages/duplicity/backend.py", line 401, in inner_retry
    % (n, e.__class__.__name__, util.uexc(e)))
  File "/snap/deja-dup/190/lib/python3.6/site-packages/duplicity/util.py", line 120, in uexc
    return fsdecode(m)
  File "/snap/core18/current/usr/lib/python3.6/os.py", line 812, in fsdecode
    filename = fspath(filename)  # Does type-checking of `filename`.
 TypeError: expected str, bytes or os.PathLike object, not Response
```

maybe i should just stick to uploading my files manually ;)

---

