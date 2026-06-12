---
title: "ListGarden won't run"
date: 2006-08-18
forum: General Help
---

### Post by wilcal on 2006-08-18
Requesting some direction here on running the application

[http://www.softwaregarden.com/products/listgarden/](http://www.softwaregarden.com/products/listgarden/)

As instructed if you run:

perl listgarden.pl

gets the following error message:

BEGIN failed--compilation aborted at ListGarden.pm line 24.
Compilation failed in require at listgarden.pl line 21.
BEGIN failed--compilation aborted at listgarden.pl line 21.

Thanks

---

### Post by ciscosurfer on 2006-08-18
You need to be in the directory you downloaded first.  Second, make sure have the appropriate perl modules loaded and be sure to check your perl version```
perl -v
```Also, you can get a list of options by running```
perl listgarden.pl -h
```Once you load listgarden via perl, go to a browser and type in```
http://127.0.0.1:6555
```That will bring you to a UI for ListGarden.

Reinstall perl if need be.

---

