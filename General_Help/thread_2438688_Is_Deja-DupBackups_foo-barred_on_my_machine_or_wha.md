---
title: "Is Deja-Dup/Backups foo-barred on my machine or what?"
date: 2020-03-16
forum: General Help
---

### Post by tornadof3 on 2020-03-16
I have a bizarre problem when using the Duplicity/Deja-Dup package to do a backup... recently, it has consistently failed with the following error:

Failed with an unknown error:

```
Traceback (innermost last):
  File "/usr/local/bin/duplicity", line 101, in <module>
    with_tempdir(main)
  File "/usr/local/bin/duplicity", line 87, in with_tempdir
    fn()
  File "/usr/local/lib/python2.7/dist-packages/duplicity/dup_main.py", line 1532, in main
    do_backup(action)
  File "/usr/local/lib/python2.7/dist-packages/duplicity/dup_main.py", line 1668, in do_backup
    incremental_backup(sig_chain)
  File "/usr/local/lib/python2.7/dist-packages/duplicity/dup_main.py", line 658, in incremental_backup
    globals.backend)
  File "/usr/local/lib/python2.7/dist-packages/duplicity/dup_main.py", line 443, in write_multivol
    (tdp, dest_filename, vol_num)))
  File "/usr/local/lib/python2.7/dist-packages/duplicity/asyncscheduler.py", line 150, in schedule_task
    return self.__run_synchronously(fn, params)
  File "/usr/local/lib/python2.7/dist-packages/duplicity/asyncscheduler.py", line 176, in __run_synchronously
    ret = fn(*params)
  File "/usr/local/lib/python2.7/dist-packages/duplicity/dup_main.py", line 442, in <lambda>
    vol_num: put(tdp, dest_filename, vol_num),
  File "/usr/local/lib/python2.7/dist-packages/duplicity/dup_main.py", line 331, in put
    backend.put(tdp, dest_filename)
  File "/usr/local/lib/python2.7/dist-packages/duplicity/backend.py", line 378, in inner_retry
    % exception_traceback())
  File "/usr/local/lib/python2.7/dist-packages/duplicity/util.py", line 91, in exception_traceback
    msg = msg + u"%-20s %s" % (string.join(lines[:-1], u""), lines[-1])
 UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 44: ordinal not in range(128)
```

I see there are a few other posts around here about that but I'm not sure what the solution is... is there a file I'm trying to backup that has an obscure filename - if so, how do I find it? Any help would be appreciated

---

### Post by deadflowr on 2020-03-16
Did you install it from source?
Installed from a deb package duplicity path should be /usr/lib, not /usr/local/lib.

Edit: Found this old (resolved) bug report with the same issue:
[https://bugs.launchpad.net/ubuntu/+source/duplicity/+bug/1770929]("https://bugs.launchpad.net/ubuntu/+source/duplicity/+bug/1770929")
Comment #15 might give some insights, from what I gather skimming it, oh so briefly.

---

### Post by HermanAB on 2020-03-17
Hmm, this is probably no help to you, but the reason I don't use Dejadup is because of the opaque file format that it uses.  My preference is to use rsync with hard linked versioned backups, since any file browser can read it. If Dejadup cannot read your data, then your only other option is using duplicity directly - without the GUI.

---

### Post by Tadaen_Sylvermane on 2020-03-17
I'm out and about now but when I get home I will post the script I use for duplicity. Runs as root on a loop through the local users. Haven't had a negative experience with it yet.

---

### Post by tornadof3 on 2020-03-17
> **deadflowr said:**
> 
Edit: Found this old (resolved) bug report with the same issue:
[https://bugs.launchpad.net/ubuntu/+source/duplicity/+bug/1770929]("https://bugs.launchpad.net/ubuntu/+source/duplicity/+bug/1770929")
Comment #15 might give some insights, from what I gather skimming it, oh so briefly.


Thanks for this - now all sorted, I followed the advice about removing the deb and installing the updated snap and this has fixed it:

```
sudo apt-get remove duplicity deja-dup
snap install deja-dup --classic --candidate
```

and my thanks to the other responders too

---

