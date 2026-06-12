---
title: "I'm curious how Linux deletes its files in /home partiiton"
date: 2016-02-01
forum: General Help
---

### Post by Grigoriy on 2016-02-01
Hello,

I've got Ubuntu 14.04 Desktop and recently I deleted a pretty big file.  Its size was 7 GB. It wasn't in a trash bin. The file was physically in  my Downloads folder. So I thought that it had disappeared from the  system altogether after the deletion. BUT... Couple of things...
a) In GParted I still saw that my /home partition usage was big enough, like I included that big file;
b) When I tried a backup of my /home partition, I saw that file in some mysterious .trash directory.
That all was yesterday. Today after I turned on my computer, the file  actually did disappear (Thanks God!) and everything got back to normal.  And I couldn't even find that strange .Trash folder anywhere in my /home  partition.

---

### Post by Habitual on 2016-02-01
Next time have a look for and/or at ~/.local/share/Trash

---

### Post by grahammechanical on 2016-02-01
Imagine a physical filing cabinet with many paper files each with an index number and at the front of the filing cabinet draw is a special index recording the location of every file in the cabinet. Remove the record of a file from the index and in a sense the file is deleted but actually the file is still there in cabinet.

With a computer OS removing the index location to a file is a form of deletion. The data is still on the disk. And this is what makes it possible to restore a "deleted" file or recover data from a "deleted" file. 

When we send a file to the trash bin the file is not moved. The index location of the file is changed to record the file as being in the trash bin. The data is still on the disk and taking up space.

When we empty the trash bin the data is not wiped from the disk but it can now be over-written and cannot be retrieved except by specialist utilities. So, emptying the trash seems to create space and it does create space that the OS can use.

Regards.

---

### Post by pfeiffep on 2016-02-01
I generally highlight a file and use the delete key vs moving a file to trash. I believe this actually removes the file and the space recovery is immediate. While the data is still on the disk using this method it's not readily recoverable.

---

### Post by Nuno_Abreu on 2016-02-01
> **pfeiffep said:**
> I generally highlight a file and use the delete key vs moving a file to trash. I believe this actually removes the file and the space recovery is immediate. While the data is still on the disk using this method it's not readily recoverable.
SHIFT + DELETE does this - it does not redirect to the trash bin.

---

### Post by Vladlenin5000 on 2016-02-01
> **Nuno_Abreu said:**
> SHIFT + DELETE does this - it does not redirect to the trash bin.

+1

Delete alone is the same as moving to trash.

---

### Post by Grigoriy on 2016-02-01
Okay, thank you all for your replies!

---

