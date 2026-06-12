---
title: "Rsync option that preserves both link to the directory and directory itself"
date: 2013-04-15
forum: General Help
---

### Post by blwegrzyn on 2013-04-15
Is there an option in rsync to copy the link and at the same time copy the directory the link points to while preserving the link?

Example command:  

    rsync -arv --delete /var REMOTE:/backup/


where var2 is a link to /var2 inside /var directory

With above command var2 is copied as link and /var2 directory never gets copied.

I want both link and the /var2 be copied without specifying var2 as source directory.

---

### Post by schragge on 2013-04-15
Try *rsync -arvK*. See description of *-k/--copy-dirlinks* and *-K/--keep-dirlinks* in the manual page for rsync.

---

### Post by blwegrzyn on 2013-04-15
> **schragge said:**
> Try *rsync -arvK*. See description of *-k/--copy-dirlinks* and *-K/--keep-dirlinks* in the manual page for rsync.

did not work, same behavior, link is copied as link and the directory that it links to is not copied

---

### Post by CaptainMark on 2013-04-15
I don't think this is possible, if I understand what you're asking. If you're telling rsync to sync to the location /path/to/backup it wont be able to start syncing directories to /path/to or /path, recursiveness (if thats a word) only works downwards

---

### Post by blwegrzyn on 2013-04-15
I will just use k option to backup everything, but i will loose the symlinks references.
I wonder if there is an easy way to figure out all the symlinks and include their references in the backup list?

---

### Post by CaptainMark on 2013-04-16
Well you'll just have to include the destination folder/file within the rsync command and copy the contents of it to the correct location in the backup,

---

### Post by blwegrzyn on 2013-04-16
not sure if i understand what you say?
lets sat i want to copy folder /etc
and etc has tons of different symbol links
with command
rsync -arv /etc/ /backup/
/etc will be copied with symbol link references but the actual folders it refers to are lost

with 
rsync -arvk /etc/ /backup/
links are lost but folders are copied

---

### Post by CaptainMark on 2013-04-16
Well consider this problem:
I want to sync the folder (including all contents) "/home/mark/Documents/officework" to "/media/usb_backup/mark/" 
but the directory "officework" contains a link to /usr/share/backgrounds/warty-final-ubuntu.png

If I use the -L (capital) option to follow the links and end up with the file located at "/media/usb_backup/mark/officework/warty-final-ubuntu.png"
or I can use the -l (lower case L) option to sync the sym-link so I have a link at the same location as ^above^ which points to the original location of "/usr/share/backgrounds/warty-final-ubuntu.png" 

You simply cant copy both because they would be put in the same location, if your expecting rsync to copy the link and make a new location for the referred file, where would you expect it to go?

---

### Post by blwegrzyn on 2013-04-16
i totally understand what you say.
I was hoping that this might work like this:

source:
/test
link to /test2 folder
/test2
 test2.txt

destination
test3

rsync -arv /test/ test3/

all links to directories that we want to copy are always full path
and backup test3 would be treated as /

when copy happens /test is copied together with the link and because link points to /test2 rsync knows the location of test2 folder relative to / and test2 folder is created at /test3/test2 and copied with all the the files

so that was my idea
but because it does not work like this we need to tell rsync to copy also test2
the only problem i see is is that i would need to know all locations that symlinks point to to keep both links and locations

and because i am not copying everything from the source that makes it more complicated

---

### Post by CaptainMark on 2013-04-16
I see what you'd like to do but alas you can't do this I'm afraid, at least not in the way you intend, with most command's in unix systems a single command only has direct access to the directory you're pointing it at (and therefore its contents, its contents contents etc.) but this theory only works down the file-tree not upwards.

I think you should experiment with the -R option, this will create empty directories at the destination to mimic a full file tree, so:
```
rsync /home/mark /media/usb_backup/
```
will create the backup at /media/usb_backup/mark but if you change it slightly to:
```
rsync -R /home/mark /media/usb_backup/
```
this will treat the destination folder as if it were the root of the backup so your new backup will be at /media/usb_backup/home/mark
This may seem a small difference but you can then use multiple rsync commands to sync any number of folders to the same location safe in the knowledge that their relative locations will remain the same,

The closest thing to doing this in a single command is to sync your entire root folder but use the --include-from option to only include directories matching certain patterns, see "man rsync" for more details

---

