---
title: "I have 1 laptop and 1 PC How to synchronize the files before ubuntu installation"
date: 2007-10-29
forum: General Help
---

### Post by faraz_k86 on 2007-10-29
Hello,

I use a PC and a laptop, both have windows installed in it.


now i want my laptop to convert completely to ubuntu so i'll be doing a full hard disk partition.

now i have files on both of the systems, some of the new files are on my laptop and some are on my PC , depending on what i am using at that time.

all of my important files are placed in 1 folder, the folder has the same name on both systems,

now can anyone please tell me how can i synchronize the files to my PC, like it copies the new files the ones that are latest modified and skips the files that already exist or the the ones that are identical


i hope i explained properly. any suggestions, is there any opensource for this??

---

### Post by margori on 2007-10-29
There is an package called rsync. It's included with ubuntu default instalation.

There is an syncronization daemon too, but I haven't seen it yet.

---

### Post by faraz_k86 on 2007-10-29
no im still using windows and i want to save all my files to a single place.

any suggestions?

---

### Post by faraz_k86 on 2007-10-29
bump

---

### Post by Fidgel on 2007-10-29
If you have Windows XP on both systems, look in the Programs/Accessories/System Tools/File & Settings Transfer Wizard.  Connect an Ethernet Cable between the two computers and run the wizard on both machines.  I forget which one is supposed to load first, but check it out.

This will move all your "My Documents" files, bookmarks, mail settings and other stuff to the new computer.

JOhn ><>

---

### Post by faraz_k86 on 2007-10-30
thx but this does not synchronize,  it assumes one is an old computer and the other is new. so it only transferes files

---

### Post by faraz_k86 on 2007-10-30
bump

---

### Post by Fidgel on 2007-10-30
Network the two together:
on your laptop map a drive letter (like F) to the destination folder on your desktop

Suppose the local dir is called "documents" or wherever it is (probably something like c:\documents and settings\username\my documents but for simplicity sake.  You will have to navigate to the appropriate folders.

Go to a DOS prompt, click Start/Run then type CMD and [enter]

type:
cd c:\documents [enter]
xcopy *.* F:\*.* /e/s/v/d/y [enter]

/e/s - will cause subdirectories even empty ones to be copied
/v - will verify that it did it right
/d - will copy only newer files
/y - is not necessary, but it keeps xcopy.exe from asking if you really want to do it.

or

In Windows Explorer copy and paste all of the items in your laptops folder NOW this is the tricky part.  NO NOT click the "Yes to All" button.  Compare the files dates on each file before you overwrite the destination file.

The first option is probably the easiest and most fool proof if you understand navigating via the DOS prompt.

Good Luck!
Fidgel ><>

---

### Post by Eskil Trivia on 2007-11-16
There's a program called SyncToy from Microsoft, it should do what you want. Not many features but it works good, I've used it for the exact same operation myself several times. You can find it at MS' home page under downloads.

---

