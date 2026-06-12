---
title: "Errors (python2.7) with trash-cli tool"
date: 2016-12-13
forum: General Help
---

### Post by kazakore on 2016-12-13
I have been using a cli tool which is part of trash-cli (installable from repos) with the command "trash-empty 30" to delete all files in my recycle bin over 30 days old every so often for a long time without issues. Currently running Ubuntu Studio 16.04 and trying to run it now and I get these errors printed.

> ~$ trash-empty 30
Traceback (most recent call last):
File "/usr/bin/trash-empty", line 5, in 
sys.exit(main())
File "/usr/lib/python2.7/dist-packages/trashcli/cmds.py", line 31, in empty
).run(*sys.argv)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 937, in run
parse(argv)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 806, in **call**
self.default_action()
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 963, in _empty_all_trashdirs
self.trashdirs.list_trashdirs()
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 880, in list_trashdirs
self._for_each_volume_trashcan()
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 887, in _for_each_volume_trashcan
self.emit_trashcans_for(volume)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 890, in emit_trashcans_for
self.emit_trashcan_2_for(volume)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 903, in emit_trashcan_2_for
self.on_trash_dir_found(alt_top_trashdir, volume)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 978, in _analize_trash_directory
self.trashdir.each_trashinfo(self.on_trashinfo_found)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 1087, in each_trashinfo
action(os.path.join(self._info_dir(), entry))
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 856, in delete_if_expired
self._maybe_delete(trashinfo_path)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 864, in _delete_according_date
)(contents)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 1173, in **call**
self.found_deletion_date(date)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 987, in **call**
self.then()
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 862, in 
lambda: self._delete_unconditionally(trashinfo_path)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 866, in _delete_unconditionally
self._trashcan.delete_trashinfo_and_backup_copy(trashinfo_path)
File "/usr/lib/python2.7/dist-packages/trashcli/trash.py", line 839, in delete_trashinfo_and_backup_copy
self._file_remover.remove_file_if_exists(backup_copy)
File "/usr/lib/python2.7/dist-packages/trashcli/fs.py", line 27, in remove_file_if_exists
if os.path.exists(path): self.remove_file(path)
File "/usr/lib/python2.7/dist-packages/trashcli/fs.py", line 25, in remove_file
shutil.rmtree(path)
File "/usr/lib/python2.7/shutil.py", line 247, in rmtree
rmtree(fullname, ignore_errors, onerror)
File "/usr/lib/python2.7/shutil.py", line 252, in rmtree
onerror(os.remove, fullname, sys.exc_info())
File "/usr/lib/python2.7/shutil.py", line 250, in rmtree
os.remove(fullname)
OSError: [Errno 13] Permission denied:  '/media/xxxx/Data/.Trash-1000/files/Pornophonik - Rubycurve [P36-011]  (2)/Rubycurve/7TheEndOfRubycurveRubycurvePart3.ogg'

I have done an Update and Upgrade and tried removing and reinstalling the trash-cli toolkit but haven't touched phython2.7

Any idea what is going wrong here or possibly changed to cause this to suddenly stop working?

---

### Post by untrustytahr on 2016-12-13
> Any idea what is going wrong here or possibly changed to cause this to suddenly stop working?

```
OSError: [Errno 13] Permission denied:   '/media/xxxx/Data/.Trash-1000/files/Pornophonik - Rubycurve [P36-011]   (2)/Rubycurve/7TheEndOfRubycurveRubycurvePart3.ogg'
```

I would guess that you do not have the correct permissions to delete.  If sudo trash-empty works you know you do not.  This also looks like it could be on a usb stick (mounted on /media) so check that it's not mounted as read-only or that there is no physical write protection on the stick.

---

### Post by kazakore on 2016-12-13
> **untrustytahr said:**
> ```
OSError: [Errno 13] Permission denied:   '/media/xxxx/Data/.Trash-1000/files/Pornophonik - Rubycurve [P36-011]   (2)/Rubycurve/7TheEndOfRubycurveRubycurvePart3.ogg'
```

I would guess that you do not have the correct permissions to delete.  If sudo trash-empty works you know you do not.  This also looks like it could be on a usb stick (mounted on /media) so check that it's not mounted as read-only or that there is no physical write protection on the stick.

Partition on internal drive mounted at boot which I have no problems writing to so shouldn't be permissions. Plus  it always worked in the past. A little hesitant to run it as sudo when I know it shouldn't be required...

But I have just gone in and deleted the directory that file was in from within Thunar (so with normal permissions) and it now seems to run fine so definitely something funny there. Thanks for the pointer to what should have been obvious :)

---

