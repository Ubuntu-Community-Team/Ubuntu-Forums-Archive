---
title: "Cant see NAS files from Programs"
date: 2013-12-26
forum: General Help
---

### Post by yocomprocosas on 2013-12-26
So,
I can see my NAS drive read and write no issue. Now when ever i try to use a program, Transmageddon, Mixx, ect.. and I try to access my NAS it wont show up, not even the mapped folders in that drive. Its like it doesnt exist, But if i click on " Recently Used " it will show files in the NAS which i accesed before but when i click them nothing happens wont pull them into the program.
So im clueless as what the problem could be.
Any ideas?

---

### Post by tgalati4 on 2013-12-26
When you use Nautilus (the file manager) to navigate a network share, a special directory link is created.  Not all applications (especially older ones) can recognize this link.  So a work-around is to create a local directory and make a hard mount to your NAS.

Although this is a lot of reading to accomplish a simple task, it gives you the background for how mounting works:  [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

If you are clever, you can find the Nautilus mounts in ~/.gvfs typically.

For instance, after clicking on my NAS music share from Nautilus, I could navigate to my share as follows:

cd "/home/tgalati4/.gvfs/freenas1 on freenas/MUSIC"

So in your program you would have to navigate to the hidden .gvfs directory.  Not all programs allow you to navigate to hidden directories.  Hit Control-H in the dialog box to see if hidden directories show up.  If not, then you would have to create a local mount as shown in the link above.

---

