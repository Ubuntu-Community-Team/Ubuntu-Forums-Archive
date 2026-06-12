---
title: "hardy trash bug"
date: 2008-06-05
forum: General Help
---

### Post by Darkchef on 2008-06-05
Hi,

I don't know if this is a bug with nautilus or what but it seems that after updating ubuntu , i cannot delete my files in trash using the 'Empty Deleted Files' button. I can only do it by deleting the files in '/home/dan/.local/share/Trash/Files/' with root.

Does anyone else have this problem and is there a fix?

Cheers

---

### Post by sizzam on 2008-06-05
Mine works correctly.

Check the permissons on 'Trash' and 'Trash/files', make sure you have write-access to them.

```
$ ls -ltr /home/dan/.local/share/
```
```
$ ls -ltr /home/dan/.local/Trash/
```

Both of those directories should be owned by user dan and group dan, and the permissions should be:
```
drwx------
```

If they are something other than that, try this:
```
$ sudo chown -R dan /home/dan/.local/share/Trash
$ sudo chgrp -R dan /home/dan/.local/share/Trash
$ chmod -R 700 /home/dan/.local/share/Trash
```

Then retest.

---

### Post by Darkchef on 2008-06-05
> **sizzam said:**
> Mine works correctly.

Check the permissons on 'Trash' and 'Trash/files', make sure you have write-access to them.

```
$ ls -ltr /home/dan/.local/share/
```
```
$ ls -ltr /home/dan/.local/Trash/
```

Both of those directories should be owned by user dan and group dan, and the permissions should be:
```
drwx------
```

If they are something other than that, try this:
```
$ sudo chown -R dan /home/dan/.local/share/Trash
$ sudo chgrp -R dan /home/dan/.local/share/Trash
$ chmod -R 700 /home/dan/.local/share/Trash
```

Then retest.

Ok thanks for the info, the permissions were set correctly as i thought they were. I've applied the permissions anyway just to see if that was the problem but there isn't any change. ill try a restart in a moment to test whether it just needs rebooting.

EDIT : I've rebooted and it seems to be working again, thanks for the help

---

