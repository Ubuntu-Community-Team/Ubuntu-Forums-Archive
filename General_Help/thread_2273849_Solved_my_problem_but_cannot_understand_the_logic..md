---
title: "Solved my problem but cannot understand the logic.  Can anyone explain please?"
date: 2015-04-16
forum: General Help
---

### Post by KayeNg on 2015-04-16
Hi guys!

Two desktop computers.  One running Windows XP, the other Lubuntu.  There is a folder in the XP computer that can be accessed from the Lubuntu computer, via the Lubuntu file manager PCManFM.

Using PCManFM, the contents of said folder can be copied (to the Lubuntu computer).  But renaming files, deleting files, copying/moving files into said folder cannot be done.  

However, if I go to terminal and type gksu pcmanfm,  I could do all that--renaming, deleting, creating, etc.

Can anyone explain why this is so?  

Thank you!

---

### Post by Holger_Gehrke on 2015-04-16
Looks like the permissions allow reading and writing of the files but not the directory. File names are not stored in the files but in the directories. To rename or delete a file or copy and move a file into a directory you need write permission for the directory. Using gksu you temporarily assume the role of root, and root is allowed to write everywhere. The only thing that surprises me about the situation is that it's happening on a folder shared from XP, since file permissions work differently in windows. I assume that the client (whatever PCManFM uses to access CIFS/SMB-shares, possibly gvfs ?) does some translating of permissions.

---

