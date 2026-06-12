---
title: "FIrefox Bookmarks, GONE!!!"
date: 2007-12-22
forum: General Help
---

### Post by Nimaran on 2007-12-22
All my Firefox bookmarks have DISAPPEARED! They are all GONE!

All I was doing was changing the screensaver lock theme and then I got online for something and there were no Bookmarks. Any Help? Please. :confused: :(

---

### Post by taurus on 2007-12-22
What's the output of this command from a terminal?

```
ls -la ~/.mozilla/firefox
```

---

### Post by Nimaran on 2007-12-22
```
total 20
drwx------ 3 seth seth 4096 2007-10-21 13:53 .
drwx------ 3 seth seth 4096 2007-10-21 13:52 ..
drwx------ 7 seth seth 4096 2007-12-22 21:03 50y2tj7h.default
-rw------- 1 seth seth 3859 2007-12-22 21:03 pluginreg.dat
-rw-r--r-- 1 seth seth   94 2007-10-21 13:52 profiles.ini

```

---

### Post by taurus on 2007-12-22
How about

```
ls -la ~/.mozilla/firefox/50y2tj7h.default
```

---

### Post by Nimaran on 2007-12-22
```
total 8068
drwx------  7 seth seth    4096 2007-12-22 21:06 .
drwx------  3 seth seth    4096 2007-10-21 13:53 ..
-rw-r--r--  1 seth seth     435 2007-12-21 17:19 blocklist.xml
drwx------  2 seth seth    4096 2007-12-22 13:36 bookmarkbackups
-rwx------  1 seth seth     410 2007-12-22 20:59 bookmarks.bak
-rwx------  1 seth seth     410 2007-12-22 20:59 bookmarks.html
drwxr-xr-x  2 seth seth   32768 2007-12-22 21:04 Cache
-rw-------  1 seth seth   65536 2007-12-22 20:59 cert8.db
drwxr-xr-x  2 seth seth    4096 2007-10-27 18:59 chrome
-rw-------  1 seth seth     126 2007-12-04 18:42 compatibility.ini
-rw-r--r--  1 seth seth  133660 2007-12-19 16:56 compreg.dat
-rw-------  1 seth seth  118315 2007-12-22 21:06 cookies.txt
-rw-r--r--  1 seth seth   13125 2007-12-22 18:19 downloads.rdf
-rw-r--r--  1 seth seth     788 2007-12-07 16:22 dta_history.xml
drwxr-xr-x 16 seth seth    4096 2007-12-21 17:19 extensions
-rw-r--r--  1 seth seth    1666 2007-12-19 16:56 extensions.cache
-rw-r--r--  1 seth seth    1281 2007-12-19 16:56 extensions.ini
-rw-r--r--  1 seth seth   20517 2007-12-21 17:19 extensions.rdf
-rw-r--r--  1 seth seth  137327 2007-12-22 20:59 formhistory.dat
drwxr-xr-x  2 seth seth    4096 2007-11-02 21:01 FoxyTunes
-rw-r--r--  1 seth seth  663569 2007-12-22 21:04 history.dat
-rw-------  1 seth seth     361 2007-12-21 19:52 hostperm.1
-rw-r--r--  1 seth seth    7147 2007-12-19 16:56 install.log
-rw-------  1 seth seth   16384 2007-12-22 20:59 key3.db
-rw-r--r--  1 seth seth   33833 2007-12-22 20:59 localstore.rdf
lrwxrwxrwx  1 seth seth      15 2007-12-22 21:02 lock -> 127.0.1.1:+5532
-rw-r--r--  1 seth seth   12542 2007-12-13 20:53 mimeTypes.rdf
-rw-r--r--  1 seth seth       0 2007-12-22 21:02 .parentlock
-rw-r--r--  1 seth seth      26 2007-12-17 21:16 persdict.dat
-rw-r--r--  1 seth seth   20861 2007-12-22 20:59 prefs.js
-rw-r--r--  1 seth seth    3287 2007-10-21 13:52 search.rdf
-rw-r--r--  1 seth seth    2048 2007-10-21 13:52 search.sqlite
-rw-------  1 seth seth   16384 2007-10-21 13:52 secmod.db
-rw-------  1 seth seth    4229 2007-12-22 21:06 sessionstore.js
-rw-------  1 seth seth    2403 2007-12-17 19:10 signons2.txt
-rw-r--r--  1 seth seth 3617792 2007-12-22 20:57 urlclassifier2.sqlite
-rw-r--r--  1 seth seth 1722488 2007-12-04 18:43 XPC.mfasl
-rw-r--r--  1 seth seth  103387 2007-12-19 16:56 xpti.dat
-rw-r--r--  1 seth seth 1369087 2007-12-22 20:52 XUL.mfasl

```

---

### Post by taurus on 2007-12-22
Look in ~/.mozilla/firefox/50y2tj7h.default/bookmarkbackups for the backups.  Look for the date and just copy it back to ~/.mozilla/firefox/50y2tj7h.default/bookmarks.html.

---

### Post by Nimaran on 2007-12-22
I did that and restarted Firefox but they are still not there. Should I try from a couple days ago?

---

### Post by taurus on 2007-12-22
What exactly did you do to move a backup file up one directory?

```
ls -la ~/.mozilla/firefox/50y2tj7h.default/*.html
ls -la ~/.mozilla/firefox/50y2tj7h.default/bookmarkbackups
```

---

### Post by Nimaran on 2007-12-22
```
-rwx------ 1 seth seth 410 2007-12-22 21:12 /home/seth/.mozilla/firefox/50y2tj7h.default/bookmarks.html
seth@seth-desktop:~$ ls -la ~/.mozilla/firefox/50y2tj7h.default/bookmarkbackups
total 532
drwx------ 2 seth seth   4096 2007-12-22 13:36 .
drwx------ 7 seth seth   4096 2007-12-22 21:17 ..
-rwx------ 1 seth seth  99564 2007-12-18 16:40 bookmarks-2007-12-18.html
-rwx------ 1 seth seth  99564 2007-12-19 16:56 bookmarks-2007-12-19.html
-rwx------ 1 seth seth  99564 2007-12-20 16:54 bookmarks-2007-12-20.html
-rwx------ 1 seth seth  99564 2007-12-21 16:58 bookmarks-2007-12-21.html
-rwx------ 1 seth seth 103707 2007-12-22 13:36 bookmarks-2007-12-22.html

```

I don't know if that told you or not, but I copied the backup file and placed it in the main bookmarks folder, then I deleted the original and renamed the new one.

---

### Post by taurus on 2007-12-22
```
cd ~/.mozilla/firefox/50y2tj7h.default/bookmarkbackups
cp bookmarks-2007-12-22.html ../bookmarks.html
```
Now, fire up firefox and see if everything is back to normal.

---

### Post by Nimaran on 2007-12-22
Wait, I entered what you told me, but it didn't do anything besides this:

```
seth@seth-desktop:~$ cd ~/.mozilla/firefox/50y2tj7h.default/bookmarkbackups
seth@seth-desktop:~/.mozilla/firefox/50y2tj7h.default/bookmarkbackups$ cp bookmarks-2007-12-22.html ../bookmarks.html
seth@seth-desktop:~/.mozilla/firefox/50y2tj7h.default/bookmarkbackups$ 
```

---

### Post by taurus on 2007-12-22
What else do you expect it to do?  You just copied the newest backup back to bookmarks.html.  You can check with the output of this command.

```
ls -la ~/.mozilla/firefox/50y2tj7h.default/bookmarks.html
```

---

### Post by Nimaran on 2007-12-22
Oh, sorry forgive my ignorance. When I restarted it, it didn't fix, but the code you gave told me this:

```
-rwx------ 1 seth seth 103707 2007-12-22 21:25 /home/seth/.mozilla/firefox/50y2tj7h.default/bookmarks.html

```

I'll try restarting Firefox again though.

---

### Post by Nimaran on 2007-12-22
I tried manually copying the file again. When I open the .html file in the backup folder it is normal, all my bookmarks are in place. I then copy that file over and replace the normal one. I check it again, still good. I then close firefox and open it again. No bookmarks, I then go into that html file, no bookmarks their either.

---

### Post by taurus on 2007-12-22
From firefox, go into Bookmarks tab and then Organize Bookmarks... -> File -> Import... and import your bookmarks again.

---

### Post by Nimaran on 2007-12-23
Oh, YES!

That worked, thank you SO much. Your help was awesome!

I'd have to say the number one thing about linux is the support, for me that is a huge feature which is often overlooked, but it is by far my favorite. You guys are great.

Again, thank you so much! :) :) :)

---

