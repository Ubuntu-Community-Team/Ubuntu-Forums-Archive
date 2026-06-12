---
title: "make a command globally executable"
date: 2012-10-18
forum: General Help
---

### Post by abraxas334 on 2012-10-18
I would like to know how to do the following:
I have a directory with exactuable scripts:
$path_to_dir/mm_script1
$path_to_dir/mm_script1
$path_to_dir/mm_script1

at the moment I can execute them by either giving an absolute path or relative path.

What variable do I need to set in order to be able to just type
./mm_scrip1 in any directory in the terminal?

Thanks for the help!

---

### Post by Lars Noodén on 2012-10-18
You need to set $PATH.  That can be done in .profile, I think.  But it might be better if you were to put them in ~/bin/  If that directory exists, it is automatically added to your path and you will be able to execute programs stored there from anywhere.

---

