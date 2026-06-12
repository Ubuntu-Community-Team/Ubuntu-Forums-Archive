---
title: "How to backup certain files only?"
date: 2017-04-22
forum: General Help
---

### Post by freeworld4 on 2017-04-22
This is for my home folder I'd like to only keep certain files backed up in all directories. 
I want to backup only audio, web, office and ebooks(epub,pdf,mobi and office formats doc,odf...etc. and web formats html,xhtml,xml...etc.)
How do I accomplish this?
What is your favorite backup tool to use?
I think I really like lucky backup.

This is for a backup drive to save up space on.
What commands can I enter in a terminal that would recursively remove all video formats, disk image formats...etc ?
Also, can you specify how big the files can be to not be removed? like a 1gb limit or so. This is on a drive that I backed up files to but I am willing to keep the small files like office, web and ebook formats as long as they are not over a certain size.

---

### Post by raleigh3 on 2017-04-22
I use a script.

For example:

```
/bin/bash
# 
#  Backup important files  
# 
#  Use gxmessage to show a message
#
gxmessage -fg red -font  'sans 20' -timeout 2 ' BACKING UP FILES FOR UBUNTU_MATE 16.04 (LTS) 64-BIT'
# Backup bookmarks file  
cd /home/andy/.mozilla/seamonkey/4e39n1np.default/
cp -u -f bookmarks.html /media/sdb1/Linux_Files/
zip -u ~/Documents/Ubuntu_Documents.zip *.html
#
cd ~/Documents
zip -u Ubuntu_Documents.zip *.txt *.doc *.rtf *.html *.png *.pdf *.odt *.ods *.odg
cp -u -f Ubuntu_Documents.zip /media/sdb1/Linux_Files/
```

---

