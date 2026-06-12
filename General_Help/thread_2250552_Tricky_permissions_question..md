---
title: "Tricky permissions question."
date: 2014-10-29
forum: General Help
---

### Post by cherva on 2014-10-29
Hello,
If I have a 775 folder /tmp/test owned by bob with group defaultgroup.
Then rsync it (saving the permissions) to another PC where bob is missing, but the group is present, I end up with /tmp/test having a permissions like 1001:defaultgroup, again 775.

This is the example and here is the question:

On both machines I have apache running with user pete (pete has a default group of defaultgroup) and group www-data.
On the first machine apache is able to write to /tmp/test, on the second apache does not succeed.
Is there some black magic with that pete and bob sharing the same group and that's why Apache can write on the first server and not on the second ?

---

### Post by dragonfly41 on 2014-10-29
Usually (at least in my personal localhost setup) Apache expects ownership of files to be www-data:www-data.

---

### Post by cherva on 2014-10-29
Usually you can setup the user and group that apache will run with...
And my work with User pete and group www-data. :)

---

