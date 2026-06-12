---
title: "[SOLVED] How to delete files in garbage when it says you have no permissons"
date: 2007-11-25
forum: General Help
---

### Post by stinger30au on 2007-11-25
Tonight i experienced a very strange error.
when i tried to empty my garbage can it says i have no permissions to do so.


so i fired up terminal and did this

 cd .Trash/


(takes you to the trash can directory)


cd data

(go in to the directory with the files it wont let me delete via gui)

 sudo rm -r *

(delete all files no matter what it is)

cd ..

(go back one directory level to the .Trash directory again)

 sudo rm -r *

(delete all files in this directory, no matter what it is)

exit

(quit terminal)


now my garbage can or recycle tin or whatever you want to call it is empty.

this is wierd, never seen this error before

did a google and found this thread as well
[http://ubuntuforums.org/archive/index.php/t-351549.html](http://ubuntuforums.org/archive/index.php/t-351549.html)

hope this helps someone

---

### Post by K.Mandla on 2007-11-27
Moved to General Help.

As an added reminder, be cautious when using the rm command, particularly with sudo. Double-check that you don't accidentally damage your system by using that command from the wrong location. :)

---

