---
title: "How do I change permissions for Transmission ?"
date: 2014-11-26
forum: General Help
---

### Post by typos1 on 2014-11-26
In the past I ve sometimes used transmission to download torrents to my desktop, I ve tried that today (first time doing this on 41.10) and I keep getting the error - "permission denied", I ve never got this before, can someone tell me how to change permissions for Transmission ? Thanks

---

### Post by nerdtron on 2014-11-26
This could be the problem on the save folder.
What is the location of the save folder of transmission?
Then in the terminal run:
```
ls -lah /path/to/save/folder 
```

Now let's see if there are permission problems.

---

### Post by jmeich777 on 2015-04-02
jmich77@jmich77-server:~$ ls -lah /media/jmich77/passport
total 36K
drwx------  1 jmich77 jmich77 4.0K Apr  2 16:57 .
drwxrwxrwx+ 5 jmich77 root    4.0K Apr  2 16:56 ..
drwx------  1 jmich77 jmich77    0 Apr  2 16:56 downloading
drwx------  1 jmich77 jmich77 8.0K Mar 25 19:59 Movies
drwx------  1 jmich77 jmich77  16K Mar 23 22:39 Music
drwx------  1 jmich77 jmich77    0 Apr  2 16:57 needsorting
drwx------  1 jmich77 jmich77    0 Mar  9 12:39 $RECYCLE.BIN
drwx------  1 jmich77 jmich77    0 Nov 18 19:06 System Volume Information
drwx------  1 jmich77 jmich77    0 Apr  2 16:04 .Trash-1000
drwx------  1 jmich77 jmich77 4.0K Apr  2 16:04 Tv series

I am actually having the same problem aND here is my output.

---

