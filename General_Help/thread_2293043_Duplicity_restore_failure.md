---
title: "Duplicity restore failure"
date: 2015-09-02
forum: General Help
---

### Post by thijs.hermans on 2015-09-02
I made a backup with Duplicity GUI on Ubuntu 14.04 LTS. Now I try to restore this backup on another Ubuntu Gnome 14.04 LTS, also with Duplicity GUI.
This error shows up:

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1337, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1370, in do_backup
    globals.archive_dir).set_values()
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 697, in set_values
    self.get_backup_chains(partials + backend_filename_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 819, in get_backup_chains
    map(add_to_sets, filename_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 809, in add_to_sets
    if set.add_filename(filename):
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 100, in add_filename
    (self.volume_name_dict, filename)
AssertionError: ({1: 'duplicity-inc.20141203T195212Z.to.20141205T110540Z.vol1.difftar'}, 'duplicity-inc.20141203T195212Z.to.20141205T110540Z.vol1.difftar.gz')

I looked in other similar threats but the error messages where all slightly different than the one above.
How can I restore my backup?

---

### Post by tgalati4 on 2015-09-02
I don't think this is a Use Case that *[duplicity]("https://help.ubuntu.com/community/DuplicityBackupHowto")* supports.  The "diff" file is a difference file, or incremental backup from a base backup file.  If that base file does not exist on another machine, then the "diff" file cannot be applied.

Why do you want to use *duplicity* to move between computers?  What is it that you are trying to accomplish?  If you want to clone one machine to another, there are tools to do that.

---

### Post by thijs.hermans on 2015-09-03
I just made a backup from personal files with the Ubuntu build in tool which I believe is Duplicity. On another Ubuntu computer I want to restore this backup.

---

### Post by tgalati4 on 2015-09-03
If both computers are on the network, then I would use *rsync* between the personal file directories to keep them synchronized.

---

### Post by sgage on 2015-09-04
> **tgalati4 said:**
> I don't think this is a Use Case that *[duplicity]("https://help.ubuntu.com/community/DuplicityBackupHowto")* supports.  The "diff" file is a difference file, or incremental backup from a base backup file.  If that base file does not exist on another machine, then the "diff" file cannot be applied.

Why do you want to use *duplicity* to move between computers?  What is it that you are trying to accomplish?  If you want to clone one machine to another, there are tools to do that.

So if you've diligently been backing up your files with Duplicity, and your system screws up to the point that you need to reinstall it, your backups are useless. That IS the use case for why you back up your personal files, as far as I'm concerned.

---

### Post by thijs.hermans on 2015-09-16
No, there is nothing like crash, network etc.

I switched distro on the same computer. Removed the old one and install the new one. I don't use a multiple distro system.
On the old distro I made a backup from personal files on usb with Duplicity. I want to restore on the new distro this backup that doesnt work.

---

### Post by tgalati4 on 2015-09-17
The error log is showing a problem with the file:  duplicity-inc.20141203T195212Z.to.20141205T110540Z.vol1.diff tar.gz

Can you unzip it and look at the contents?

```
gzunzip duplicity-inc.20141203T195212Z.to.20141205T110540Z.vol1.diff tar.gz
```

Duplicity is a complicated Python script that uses rsync and requires a few metadata files in order to restore data properly.  Did you keep those metadata files?

---

