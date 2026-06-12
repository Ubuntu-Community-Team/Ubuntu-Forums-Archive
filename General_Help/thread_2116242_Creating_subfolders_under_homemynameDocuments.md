---
title: "Creating subfolders under /home/myname/Documents"
date: 2013-02-15
forum: General Help
---

### Post by cigtoxdoc on 2013-02-15
Using file manager under 12.04, I have created folders under /home/myname/documents/.  For example /home/john/Documents/2013 Docs.  This morning, I wanted to add the following subfolders /home/john/Documents/2013 Docs/January and /home/john/Documents/2013 Docs/February.  Ubuntu won't let me do this.  Why?  Also, it will not get me change permissions for /home/john/Documents/2013 to read/write.

I am only user of this PC.  I am listed as an Administrator.  What is purpose of Ubuntu limiting such operations in my own /home/john/Documents subfolders?

How do I permanently fix this major inconvenience?

John

---

### Post by steeldriver on 2013-02-15
How are you trying to create the subfolders (GUI file manager? terminal?)

If you are doing this in a terminal, remember you will need to escape any spaces in the path (or quote the whole path) e.g.

```
mkdir /home/john/Documents/2013[COLOR=Red]\ [/COLOR]Docs/January
```or

```
mkdir [COLOR=Red]"[/COLOR]/home/john/Documents/2013 Docs/January[COLOR=Red]"[/COLOR]
```To answer your other questions we will need to see the EXACT commands you are giving and the EXACT error message - not just ' Ubuntu won't let me do this'

---

### Post by cigtoxdoc on 2013-02-15
I am using File Manager.  I do not like using the terminal.  It is archaic in today's environment.

John

---

### Post by grahammechanical on 2013-02-15
I have just created a new folder (untitled) in the Documents folder and I can paste and cut files into and out of it. Admittedly, I am running this test on 13.04 as I am not using 12.04 at the moment. I ask this question:

How did you create that folder - 2013 Docs? And the folders January and February? If we create a folder when using Administrator privileges that we may not be the owner of the folder. Root will be the owner.

You can open a terminal. Yes I know it is archaic but, do you want a fix or don't you?

Run

```
gksudo nautilus
```

That will open the Nautilus File Manager with Administrator privileges. Do not close the terminal as that will close the File Manager. Now you should be able to use the file manager to change the permissions on those folders.

When finished close the terminal and Nautilus will close and revert back to being a standard user file manager. And the purpose of these restrictions? To prevent us users from being our own worse enemy.

Regards.

---

### Post by oldfred on 2013-02-15
[ATTACH]231453[/ATTACH]Even with my shared NTFS partitionI learned a while back to stop using spaces. Use CamelCase or under_score or just onelongname. Windows will work without the spaces and it makes things a lot simpler in Linux.

Terminal can be easier for us to explain to do something.
cd /home/john/Documents
ls -l

You should be able  to do this from gui.
From Nautilus edit, preferences and add columns to show permissions & ownership.

---

