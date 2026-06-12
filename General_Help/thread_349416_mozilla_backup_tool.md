---
title: "mozilla backup tool?"
date: 2007-01-30
forum: General Help
---

### Post by bcs on 2007-01-30
Hello,
I am looking for a tool that easily backs up Thunderbird mail/settings and firefox bookmarks.  I have used [MozBackup]("http://mozbackup.jasnapaka.com/download.php") for windows and it worked very well...quick to backup and even quicker to restore.  Does a similar tool exist for linux?

---

### Post by p!=f on 2007-01-30
> **bcs said:**
> Hello,
I am looking for a tool that easily backs up Thunderbird mail/settings and firefox bookmarks.  I have used [MozBackup]("http://mozbackup.jasnapaka.com/download.php") for windows and it worked very well...quick to backup and even quicker to restore.  Does a similar tool exist for linux?
Couldn't find anything similar but
```

cd ~
tar cjvf mozilla-backup.`date +%F`.tar.bz2 .mozilla

```
works too :)

---

### Post by bcs on 2007-01-30
what does that command do?

---

### Post by p!=f on 2007-01-30
> **bcs said:**
> what does that command do?
Backups .mozilla directory in your /home and creates something like this
mozilla-backup.2007-01-30.tar.bz2 in your /home

---

### Post by bcs on 2007-01-30
Great; thanks.  did it for .mozilla and .mozilla-thunderbird.  In backing up, I realized that I actually didn;t need to...I wanted to backup a copy to my home, forgetting that FF and Thunderbird are already there by default!  But good to know a new command nonetheless.  By the way, what is "cjvf " part of the command for???

---

### Post by p!=f on 2007-01-30
> **bcs said:**
> By the way, what is "cjvf " part of the command for???
```

man tar
tar --help

```
:)

---

### Post by bcs on 2007-01-30
thanks :)

---

### Post by agibby5 on 2007-07-18
How would one then restore such a backup?

---

### Post by HermanAB on 2007-07-18
$ man tar

tar -c == compress
tar -x == extract

---

### Post by bigboy_pdb on 2007-07-18
I don't know about backing up anything in Thunderbird because I don't use it.

To backup your Firefox bookmarks you can do the following:
Go to "Places -> Home Folder". Press Ctrl-H to see the hidden files and folders. Go into the ".mozilla" folder, then into the "firefox" folder, and then there should be a folder which is some characters followed by ".default". Go into that folder. Copy the file called "bookmarks.html" to wherever you want it saved.

You could also do the following to backup your Firefox bookmarks:
In Firefox go to "Bookmarks -> Organize Bookmarks..." then in the "Bookmarks Manager" go to "File -> Export...". Use the file browsing window to save the bookmarks to a file.

To restore your Firefox bookmarks you can do the following:
In Firefox go to "Bookmarks -> Organize Bookmarks..." then in the "Bookmarks Manager" go to "File -> Import...". Select "From File" and click "Next". A window for browsing for a file will appear. Go to the folder where you saved the backup file that contains your bookmarks, select the file, and click "Open".

By the way, it isn't a good idea to import your bookmarks when same bookmarks are in the list because you'll get two copies of the bookmarks.

---

### Post by jsacks on 2008-05-23
Hi,
I'm switching over from WindowsXP to Ubuntu.  How do I transfer all my Firefox settings (bookmarks, extensions, etc) from one to the other?

I have the mozilla backup tool but it seems like it only works for windows to windows...

any advice? (and i'm a newbie to ubuntu so please make it simple)

---

