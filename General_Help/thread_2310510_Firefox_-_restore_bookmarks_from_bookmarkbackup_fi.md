---
title: "Firefox - restore bookmarks from bookmarkbackup file"
date: 2016-01-19
forum: General Help
---

### Post by oygle on 2016-01-19
The Firefox bookmarks are gone, due to a remove and re-install. In the trash, I can see quite a few files in the /bookmarkbackups path

How do I use that file to load/import into the Firefox bookmarks please ?

---

### Post by vasa1 on 2016-01-19
First, copy over the **entire** bookmarkbackups folder from Trash to ~/.mozilla/firefox/whatever_your_profile_is/.

I have this:
```
10:14 AM ~ $ cd /home/vasa1/.mozilla/firefox/yfska9ip.Main/bookmarkbackups
10:14 AM ~/.../yfska9ip.Main/bookmarkbackups $ ll
total 240
-rw------- 1 vasa1 vasa1 12865 Sep 25 06:52 bookmarks-2015-09-29_106_rG61z1rHP7rOZDzZF+rJMw==.jsonlz4
-rw------- 1 vasa1 vasa1 12866 Oct  1 07:50 bookmarks-2015-10-09_106_lBVWXGyp3ZcGmpTMD+r6dQ==.jsonlz4
-rw------- 1 vasa1 vasa1 12905 Oct 11 06:51 bookmarks-2015-10-11_106_CKh4UNymqHUXn81G1I+LZQ==.jsonlz4
-rw------- 1 vasa1 vasa1 12888 Oct 12 07:50 bookmarks-2015-10-12_106_5uhFtStsiDgXIyb0DApocQ==.jsonlz4
-rw------- 1 vasa1 vasa1 12990 Oct 13 06:55 bookmarks-2015-10-14_107_5sdKShZQoWBDWqRVo1nf6Q==.jsonlz4
-rw------- 1 vasa1 vasa1 13096 Oct 15 07:45 bookmarks-2015-10-17_108_ykx2jxKgnPEPIWTQvC7x8Q==.jsonlz4
-rw------- 1 vasa1 vasa1 13108 Oct 18 07:03 bookmarks-2015-10-24_108_pWeZKMmm6odjvqrujYYVUQ==.jsonlz4
-rw------- 1 vasa1 vasa1 13193 Oct 25 14:37 bookmarks-2015-11-03_109_0dUAFe+r+t+aAGxpmFyuIA==.jsonlz4
-rw------- 1 vasa1 vasa1 13178 Nov  5 18:31 bookmarks-2015-11-09_109_tRYN30G2QRZIZNU+6EuVDA==.jsonlz4
-rw------- 1 vasa1 vasa1 13184 Nov 10 20:16 bookmarks-2015-11-11_109_Fz0XTu7K9le7Dc8sN2JZ1A==.jsonlz4
-rw------- 1 vasa1 vasa1 13179 Nov 12 07:49 bookmarks-2015-11-12_109_5D92m1-NGM9syY-Z3rA3cQ==.jsonlz4
-rw------- 1 vasa1 vasa1 13182 Nov 13 07:59 bookmarks-2015-12-03_109_izOfFZLSPjE8qnHpAeA2-w==.jsonlz4
-rw------- 1 vasa1 vasa1 13252 Dec  4 19:51 bookmarks-2015-12-06_110_Ke2KCg+iv+bng4UBohuEsQ==.jsonlz4
-rw------- 1 vasa1 vasa1 13243 Dec  7 06:23 bookmarks-2016-01-04_110_W1YramgF1USRXA+QG2WQng==.jsonlz4
-rw------- 1 vasa1 vasa1 13239 Jan  5 07:55 bookmarks-2016-01-19_110_VrMq+HacKQ-oXFLGymRILg==.jsonlz4
10:14 AM ~/.../yfska9ip.Main/bookmarkbackups $ 

```Then, open Firefox and press Alt+B to get the "Bookmarks" dropdown. 
Choose "Show all bookmarks". A new window called "Library" should open. 
Click on "Import and Backup".
Click on "Restore".
From the context menu, choose the particular "Bookmarks" you wish to restore.

That will do it.

---

### Post by oygle on 2016-01-20
Thanks, I did try that with just one file. But I copied all of them into the correct path, but when I did the import,etc, no filenames appeared. Could be I need to restart Firefox.

**Later** - yes, just needed to close Firefox and open again, then the import showed all those files. Selected one (latest) and it appears all the bookmarks are back again. The bookmarks menu/s have all the icons missing, however I notice if I use that bookmark, that icon appears back in the bookmarks.  Thanks  :)

---

