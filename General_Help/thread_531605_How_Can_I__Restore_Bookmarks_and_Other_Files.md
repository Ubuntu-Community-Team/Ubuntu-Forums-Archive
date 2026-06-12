---
title: "How Can I  Restore Bookmarks and Other Files"
date: 2007-08-21
forum: General Help
---

### Post by lakelovers on 2007-08-21
I'm having trouble restoring files with Simple Backup. I restored bookmarks.html to the Firefox bookmark file but they don't show up on the bookmark menu. I see the transferred backup in /etc/firefox/profile/ but don't know how to get the backup into the main bookmark file. I tried dragging. That didn't work. I tried importing but haven't made that work. I need some how-to tips.

Jerry

---

### Post by sumguy231 on 2007-08-22
Make sure the boomarks.html file is in **your** Firefox profle (hidden in your home directory.) You can find it using these instructions:
[http://kb.mozillazine.org/Profile_folder_-_Firefox#Linux_and_Unix](http://kb.mozillazine.org/Profile_folder_-_Firefox#Linux_and_Unix)

---

### Post by IanW on 2007-08-22
1: Open Firefox
2: Click "Bookmarks"
3: Click "Organise Bookmarks"
4: Click "File"
5: Click "Import"
6: Click "Next"
7: Navigate to backup of bookmarks.html
8: Click "Open"
9: Click "File"
10: Click "Close"

---

### Post by lakelovers on 2007-08-22
I tried importing bookmarks backup but each time I put the path into the second drive to the backup "bookmarks.html," Firefox crashed. So, I went into Simple Backup restore and restore the bookmark backup to a folder in "Home." Then I went the import route and thought it was working (the computer ground away for awhile, but the file didn't import.

When I look at the backup files on a text editor, I noticed that the bookmark.html has a header titled Netscape. So you suppose I could just copy the file in "Home" and paste it to Firefox bookmarks or would that corrupt the Firebox bookmark file?

---

### Post by sumguy231 on 2007-08-22
> When I look at the backup files on a text editor, I noticed that the bookmark.html has a header titled Netscape. So you suppose I could just copy the file in "Home" and paste it to Firefox bookmarks or would that corrupt the Firebox bookmark file?
The backup file should just be a copy of your old one, so nothing should get corrupted. The "Netscape" text is probably there because the bookmark format was carried over from the old days of Netscape. There's actually still plenty of Netscape design laying around Firefox, it would seem.

I do suggest reading and doing IanW's post, since it's a little easier than copying the file directly.

---

