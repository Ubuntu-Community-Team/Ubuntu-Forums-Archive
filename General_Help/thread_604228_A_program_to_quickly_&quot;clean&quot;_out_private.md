---
title: "A program to quickly &quot;clean&quot; out private / personal temp. data(similiar to CCleaner)?"
date: 2007-11-05
forum: General Help
---

### Post by enthusaroo on 2007-11-05
I used a program for Windows called "CCleaner", which is a "cleaning" program for Windows that would wipe out cached data, browser cookies (I use Firefox AND Opera), browser history, temp files, recent documents, etc..etc.. with the touch of a button.

Is there a similar application for Ubuntu that can wipe out all temporary private / personal data under Ubuntu with the touch of a button? I have tried searching the repos using search terms like "cleaner", and such, but I can't find any thing like I'm seeking. Sometimes I share my labtop with my co-workers, so that's why I'd like to easily get rid my data confidential.

---

### Post by mpierce on 2007-11-05
I'm familiar with CC Cleaner, but under preferences in both Firefox and Opera, you have the option to delete all personal info and history when you close the browser. 

You can write a simple script and put it in /usr/local/bin to erase all folders that you want the content delete in. You could then put that file at the end of /etc/init.d/bootmisc.sh and whenever you started up your machine, it would run and delete the contents of the folders as long as the file was owned by root with 666 permission. 

Easy...
Hope this helps...

---

### Post by daengbo on 2007-11-06
Do you share accounts? If not, you have your own data that is separate from theirs. Simply change the permissions on your home folder (right click in the Nautilus file browser) to "create and delete files." Set group and other access to "none." Apply permissions to enclosed files and you are done. No one can look at your files but you (and the admin).

If you share the account with someone else (a bad idea WRT privacy), you can create a shell script that runs automatically on logout. Locate the files you want to delete. The easiest way to do this is to 
find ~/ > before.txt # This will put a list of your files into a text file
<Do your cleanup>
find ~/ > after.txt # This will put a list of your cleaned-up files into a text file
diff before.txt after.txt # This will compare the two files and show you what disappeared.

Write a script to delete those files (or everything in a directory, if it looks appropriate, set it executable, and put it in /etc/gdm/PostSession/

Hope that helps.

Daeng

---

### Post by Lektorvis on 2008-06-13
GtkOrphan is a helpfull small program that keeps track on packages that are downloaded, it has too a filter function that sort out orphanen files no longer in use.

---

