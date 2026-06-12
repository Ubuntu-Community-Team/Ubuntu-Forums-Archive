---
title: "File attributes..."
date: 2012-11-29
forum: General Help
---

### Post by DoctorVell on 2012-11-29
[B]Here is what I want to do:
[/B][B]
Change permissions to have my file "resume 02.doc" the same as the others with the permissions (as you can see they all have the doctorvell and doctorvell twice, that's what I want to do).[/B]

[B]I don't remember the correct commands to do it.  The file was originally on a Windows machine (MS Word but I now use Ubuntu completely).

[/B]doctorvell@DoctorVell:~/dos$ ls -l
total 156
-rw-------   1 doctorvell doctorvell     0 Apr  5  2011 config.sys
drwx------   2 doctorvell doctorvell  4096 Jul 23 07:33 IFA
drwx------   3 doctorvell doctorvell  4096 May 16  2012 INTRPLAY
drwxrwxr-x  24 doctorvell doctorvell  4096 Feb 14  2012 pics
-rw-rw-r--   1 doctorvell doctorvell    17 May 16  2012 READY
-rwxr--r--   1 doctorvell doctorvell 23040 May 27  2012 resume 01.doc
-rwxr--r--   1 nobody     nogroup    23040 Jul 28 10:26 resume 02.doc
drwxrwxr-x   2 doctorvell doctorvell  4096 Jul  1 07:15 ring
drwxrwxrwx   7 doctorvell doctorvell  4096 Jun  6 10:51 ringtones
drwx------   4 doctorvell doctorvell  4096 May 20  2012 SIERRA
drwxrwxr-x 476 doctorvell doctorvell 65536 Jun  9 11:52 utils
drwx------   8 doctorvell doctorvell  4096 May 21  2012 win3
drwxrwxr-x   9 doctorvell doctorvell 12288 Jul 23 07:33 windows
doctorvell@DoctorVell:~/dos$

---

### Post by claracc on 2012-11-29
You have to change owner and group for the file you want with commands chown and chgrp. Here, [http://www.computerhope.com/unix/uchown.htm#01](http://www.computerhope.com/unix/uchown.htm#01) and here, [http://www.computerhope.com/unix/uchgrp.htm](http://www.computerhope.com/unix/uchgrp.htm) you have the instructions to use the proper syntax.

---

### Post by pkadeel on 2012-11-29
> **DoctorVell said:**
> [B]Here is what I want to do:
[/B][B]
Change permissions to have my file "resume 02.doc" the same as the others with the permissions (as you can see they all have the doctorvell and doctorvell twice, that's what I want to do).[/B]

[B]I don't remember the correct commands to do it.  The file was originally on a Windows machine (MS Word but I now use Ubuntu completely).

[/B]doctorvell@DoctorVell:~/dos$ ls -l
total 156
-rw-------   1 doctorvell doctorvell     0 Apr  5  2011 config.sys
drwx------   2 doctorvell doctorvell  4096 Jul 23 07:33 IFA
drwx------   3 doctorvell doctorvell  4096 May 16  2012 INTRPLAY
drwxrwxr-x  24 doctorvell doctorvell  4096 Feb 14  2012 pics
-rw-rw-r--   1 doctorvell doctorvell    17 May 16  2012 READY
-rwxr--r--   1 doctorvell doctorvell 23040 May 27  2012 resume 01.doc
-rwxr--r--   1 nobody     nogroup    23040 Jul 28 10:26 resume 02.doc
drwxrwxr-x   2 doctorvell doctorvell  4096 Jul  1 07:15 ring
drwxrwxrwx   7 doctorvell doctorvell  4096 Jun  6 10:51 ringtones
drwx------   4 doctorvell doctorvell  4096 May 20  2012 SIERRA
drwxrwxr-x 476 doctorvell doctorvell 65536 Jun  9 11:52 utils
drwx------   8 doctorvell doctorvell  4096 May 21  2012 win3
drwxrwxr-x   9 doctorvell doctorvell 12288 Jul 23 07:33 windows
doctorvell@DoctorVell:~/dos$
```

sudo chown doctorvell:doctorvell /home/doctorvell/dos/resume\ 02.doc

```

---

### Post by DoctorVell on 2012-11-30
Thank you both for helping, it worked great.  :)

---

