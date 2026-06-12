---
title: "Backups question re: standard backup"
date: 2014-12-05
forum: General Help
---

### Post by dtree46 on 2014-12-05
Using the backup that came in 14.04LTS.
Is it possible to see individual files in the backup folder?
Restore, Delete, etc.

Thanks,
dlw2

---

### Post by bashiergui on 2014-12-07
Yes this tutorial will get you started
[http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

---

### Post by dtree46 on 2014-12-07
Thank you for replying.

I do not understand.
There are only 'duplicity' files in the backup folder.
Opening them in 'archive manager' only gives  'difftar' files.
Archive Manager will not open 'difftar' files.

dlw

---

### Post by mcduck on 2014-12-08
You can't see individual files in the backup loation, since Duplicity doesn't work by storing new copies of the file again and again but instead stores delta backups (the changes between each version of a file). This means it's a lot quicker, and uses lots less space, allowing you to restore different versions of each file without needing ridiculous amounts of drive space for your backups. Also, the backup data is encrypted.

However you *can* restore individual files, if you look at the page bashiergui linked, all you need to do is browse to where the file should be, and from the file manager's right-click menu select "Restore Missing Files".

---

### Post by amanchesterman on 2014-12-08
If you actually want to see individual files in the backup folder (which is what you asked for) rather than restore files to your system, then Duplicity won't do it, for the reason mcduck has given. (For example, if you want to open the backup folder and read individual files on another machine -- even on another OS.) To do that you need a program which creates simple copies of the files (i.e. does not compress them). The program I use is ukopp, which is in the Software Center. I find it fast and reliable, but because there is no compression the backup size is as large as the original.

---

### Post by dragonfly41 on 2014-12-08
Like DropBox .. SpiderOak allows backups to a cloud account (up to 2 GB free).

Download the SpiderOak client from here ..

[https://spideroak.com/help/](https://spideroak.com/help/)

After installing launching SpiderOak client, click on the BACK UP tab.

You can choose Basic backup (e.g. Desktop, Documents).

But for your need choose Advanced and select the files to backup.

The files will be encrypted so it is very important that you write down in some notepad (not on your PC) your password to SpiderOak account in case your PC crashes and you cannot recover the backed up, encrypted data.

You can also SHARE your files with other users (including yourself accessing from another platform).

---

