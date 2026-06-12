---
title: "undeletable corrupted files"
date: 2007-07-29
forum: General Help
---

### Post by rousselm on 2007-07-29
Hello,

I'm quite new at Ubuntu. Recently I have changed one of my partition coding to utf8 as I had some trouble with accentuated filenames. Anyway, I don't know if it's linked but last week I've seen that I have a folder in this partition ("documents") containing corrupted files. I tried to delete it without too much success until I deleted the whole folder containing it. Now it's in the trash can of the "document" partition and I can't seem to be able to get rid of them. I tried several things like the "sudo rm -rf /home/username/.Trash" (which does nothing) and I found out the folder is in /home/username/documents/.Trash-username .
So I then did "sudo rm -rf /home/username/documents/.Trash-username" which returns "error, read only file system". I tried to go through gksudo nautilus without more success.
I can see the folder containing the corrupted files in /home/username/documents/.Trash-username but if I try to open it kind of freeze. Nautilus says the folder is containing more than 40000 items which is just weird as there should have been at most 20.
I also tried the command line by starting in recovery mode, to that the computer answers in several lines : "fileystem panic" then "invalid access to FAT (entry 0x7dc57070)" then "File system has been set to read-only" and finally errors saying the files I'm trying to delete are read-only.
I also tried to delete them from Windows (I have both Ubuntu and Windows on my computer) and that does not help, I can the same kind of errors.
I have used all the things I could find in the forums.... please help!
Thanks in advance,

Marie

---

### Post by jwcgator on 2007-07-29
Sounds like file-system corruption to me.  Can you boot into a live-cd and delete the files?

---

