---
title: "Libreoffice. Why are some .odts locked for editing by unknown user"
date: 2016-06-20
forum: General Help
---

### Post by mikodo on 2016-06-20
Hi,

LibreOffice suite 1:5.1.3, in new install of Xubuntu 16.04. Sharing a data partition with Xubuntu 14.04, with an earlier version of LibreOffice.

This has happened before. Then, with bringing .odts from backup to new installs. Very annoying.

Some (luckily only a small percentage) of the .odts will not open in 16.04. Give the message that they are, "locked for editing by unknown user".

I can open and edit them, but then have to save them as another .odt name and delete the old one or, I wind up with two copies of the same .odt.

I am the only user. The permissions are the same.

Has anyone else had this problem? What causes it?

Did you find a fix for it besides, changing names and deleting the old ones?

Thanks.

---

### Post by howefield on 2016-06-20
Try the easy solution first, navigate to the folder where the document is stored and press Ctrl+h to show hidden files, then search for a file similar to your document file name but that starts with .~lock and remove it.

---

### Post by mikodo on 2016-06-20
> **howefield said:**
> Try the easy solution first, navigate to the folder where the document is stored and press Ctrl+h to show hidden files, then search for a file similar to your document file name but that starts with .~lock and remove it.

Thank you sir.

I've been doing that now and it is working really well.

Pray tell, what am I doing? And why are they locked?

---

### Post by ajgreeny on 2016-06-20
Normally those ~lock files are deleted from the folder when the LO file is closed and saved back to disk.  However if you did not close the LO file and then shutdown the OS, or perhaps the application used in LO crashed in some way, the ~lock file may still be present; not deleted by the system.

Could that have happened in your case?

---

### Post by mikodo on 2016-06-20
> **ajgreeny said:**
>  - what you said - 

Yes, in both instances.  I went through it all, with the way howefield explained and there was a lot less than I thought. Maybe ten files. And most of them were files I often have open. I just installed 16.04 yesterday and I had a situation where something filled up my ~/.cache in a hurray. Firefox safe browsing and upstart were the culprits. I couldn't shut it down in any normal way. No tty, no mouse, key presses, nada. My whole 25GB install was full. I most likely would have had some of those files open at that time. I had to shut it down hard. In the morning, I saw what happened from 14.04 and enlarged the 16.04 partition and mv the cache out. I've since had no problems.

Thank you, for the explanations.

---

### Post by gregg3 on 2016-11-19
> **howefield said:**
> Try the easy solution first, navigate to the folder where the document is stored and press Ctrl+h to show hidden files, then search for a file similar to your document file name but that starts with .~lock and remove it.

I add my thanks. (same problem) :D Thanks a lot.

---

