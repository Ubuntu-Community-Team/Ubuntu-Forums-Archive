---
title: "batch unar"
date: 2008-02-20
forum: General Help
---

### Post by MasterAslan on 2008-02-20
I was wondering.  Is there any program or script that I can use to batch unrar a bunch of files.  For instance I have about 30 folders all with files in multi-rar compressed files.  I want to unrar them all into the folders the rar files are already in.  Then if possible delete the rar files afterwards.

Thanks in advance for any help.

---

### Post by dabang on 2008-02-20
Assuming all those folders are in one parent folder, you might try something like this:

```
cd /parent-folder
for i in $(ls -1); do
cd $i && unrar *.rar && cd ..;
done

```
Handle with care, haven't tested this! If it works, you may replace "unrar *.rar" with "rm 
*.rar" Before testing, make backups!

---

### Post by freelinuxhelp on 2008-02-20
So the rar files are already in various folders? And you want to unrar them into the directory they are in?

This is definately scriptable, but I don't know of a program that will do it for you.
I think I would start my script with something like find . -name *.rar -print
That will give you a list of all rar files in your current directory or subdirectory including the relative path.
You could then use a FOR loop to extract them.

Good luck!

---

### Post by MasterAslan on 2008-02-20
Thanks both.

I am going to have to look at some scripting tutorials cause I want to learn it anyway.  How would I strip the file name off of the output of find so I could just get the directories?

---

### Post by freelinuxhelp on 2008-02-21
I use sed for most text processing in scripts. Other options include awk and calling out to a perl script.

Keep us posted with your progress.

---

### Post by freelinuxhelp on 2008-02-21
I learned scripting almost exclusively from this guide: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by freelinuxhelp on 2008-03-08
How are things going with this?

---

### Post by MasterAslan on 2008-03-08
I've been quite busy with work lately so haven't had a chance to work on this.  Not to mention I had to do a clean install as my hard drive got messed up so the files I had to unrar I no longer have.  It is something I want to work on at some point so thanks for reminding me.

---

