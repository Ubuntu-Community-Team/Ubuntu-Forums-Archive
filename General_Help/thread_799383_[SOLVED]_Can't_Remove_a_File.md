---
title: "[SOLVED] Can't Remove a File"
date: 2008-05-19
forum: General Help
---

### Post by BlueNoteExpress on 2008-05-19
I've got what appears to be a "ghost file" for lack of a better term.  When I list the contents of this directory, I see a file that shows up in red letters with a black background.  When I try to remove it, I get the following error message:

rm: cannot remove `dsc00579.jpg': No such file or directory

It does exist in some form though because it won't let me save anything else with that name to that directory, and this is what it looks like when I do a long listing of the contents of that directory.

   ? ?--------- ? ?    ?        ?                ? dsc00579.jpg

Anyone know how I can get rid of this file?

Thanks.

---

### Post by kbuel on 2008-05-19
can you give the output when you do an 'ls -ltrh'  in the folder

---

### Post by BlueNoteExpress on 2008-05-19
> **kbuel said:**
> can you give the output when you do an 'ls -ltrh'  in the folder

Here's the results of an ls -ltrh:

?--------- ? ?    ?      ?                ? dsc00579.jpg
-rwxrwxrwx 1 root root 34K 2008-05-18 22:54 dsc00581.jpg
-rwxrwxrwx 1 root root 27K 2008-05-18 22:54 dsc00583.jpg
-rwxrwxrwx 1 root root 36K 2008-05-18 22:54 dsc00584.jpg
-rwxrwxrwx 1 root root 17K 2008-05-18 22:54 dsc00585.jpg
-rwxrwxrwx 1 root root 24K 2008-05-18 22:54 dsc00588.jpg
-rwxrwxrwx 1 root root 28K 2008-05-18 22:55 dsc00589.jpg
-rwxrwxrwx 1 root root 25K 2008-05-18 22:55 dsc00590.jpg
-rwxrwxrwx 1 root root 30K 2008-05-18 22:55 dsc00592.jpg
-rwxrwxrwx 1 root root 25K 2008-05-18 22:55 dsc00597.jpg
-rwxrwxrwx 1 root root 20K 2008-05-18 22:55 dsc00601.jpg
-rwxrwxrwx 1 root root 24K 2008-05-18 22:55 dsc00602.jpg
-rwxrwxrwx 1 root root 28K 2008-05-18 22:55 dsc00603.jpg
-rwxrwxrwx 1 root root 19K 2008-05-18 22:55 dsc00604.jpg
-rwxrwxrwx 1 root root 20K 2008-05-18 22:55 dsc00605.jpg
-rwxrwxrwx 1 root root 19K 2008-05-18 22:55 dsc00608.jpg
-rwxrwxrwx 1 root root 23K 2008-05-18 22:55 dsc00610.jpg
-rwxrwxrwx 1 root root 22K 2008-05-18 22:55 dsc00612.jpg
-rwxrwxrwx 1 root root 19K 2008-05-18 22:55 dsc00614.jpg
-rwxrwxrwx 1 root root 21K 2008-05-18 22:55 dsc00615.jpg

---

### Post by BlueNoteExpress on 2008-05-19
I don't know what happened, but it looks like that file up and decided to start behaving correctly all of a sudden.

---

