---
title: "Reference filenames on Windows/Samba share from Ubuntu programs"
date: 2013-08-08
forum: General Help
---

### Post by ElmoGonzo on 2013-08-08
I linked to a Windows share from Ubuntu 12.04 using Nautilus.  It appears in the tree with the name **sharename on servername** and the full name is **smb://DOMAINNAME;userid@servername/sharename/** where userid refers to the user in the specified DOMAINNAME in the Windows ActiveDirectory.

I want to be able to access files on that share from an application but I have no idea what the "filename" is or how to reference it so the program can use it.  I can't even get a listing of the folders from the command line.  But Nautilus shows them all to me, so I'm sure there must be a way to do it. 
Any Clues for this Clueless one?

---

### Post by ElmoGonzo on 2013-08-08
I think I have resolved the issue on my own.

I've been poking about and I've gotten a little further.  I used the  SystemMonitor and set it to show all file systems which listed a device **/gvfs-fuse-daemon** and a directory named **/home/elmo/.gvfs** 
I was able to get a list using **ls /home/elmo/.gvfs/****"sharename on servername"/** and was also able to use regular command line utilities like **cp** and **mv** and **rm**  to copy, rename, and remove files on the share.  I was able to create a  Java File object using an existing filename but a check to see if it  exists( ) returns false.

Poking a little harder, I ran a test using a Java FileChooser object which does not display the .gvfs item in the **/home/elmo** folder but when I type it in manually and select it, the contents are displayed as **sharename on servername** and I can drill down into there and select a file which then exists.  

Having a bit of a "D'oh!" moment, I realized that the command line processor requires the quotes to delimit the item with spaces in its name but that the OS is more than happy to use the complete name without the quotes.  All I have to do is know that the hidden item exists and what its name is and then I can use it.

---

