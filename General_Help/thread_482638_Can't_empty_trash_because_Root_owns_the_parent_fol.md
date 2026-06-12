---
title: "Can't empty trash because Root owns the parent folder?"
date: 2007-06-23
forum: General Help
---

### Post by Tsu Dho Nimh on 2007-06-23
I'm baffled, because these folders were created by Windows.

However, some of the files and directories I want to delete show with a lock on them and the owner is "root". 

How can I make it turn loose of my files so I can delete them?

---

### Post by fdrake on 2007-06-23
sudo chown your_username /file/s/path             #change the ownership of the file
rm /file/s/path    #remove file

if u have too many file:
sudo chown your_username -R /folder/path   #Change the ownership of all the content of the folder

---

### Post by topsites on 2007-06-27
> **fdrake said:**
> sudo chown your_username /file/s/path             #change the ownership of the file
rm /file/s/path    #remove file

if u have too many file:
sudo chown your_username -R /folder/path   #Change the ownership of all the content of the folder

Bullcrap, it doesn't work, one of my folders continues to be stubbornly powneded by root.

I FIXED it by logging in as root, that ought to be just plain su- like in Redhat

---

