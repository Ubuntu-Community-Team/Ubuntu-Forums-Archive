---
title: "Copying Files to Router Connected HD"
date: 2018-04-22
forum: General Help
---

### Post by jay30 on 2018-04-22
I am backing up (copying) files via the cp command from one HD to another (I use a ubuntu desktop).  The vast majority of the files are photos.  I have had both the HD's connected in to my home network via the usb ports on the router.  I have liked this option because then the files can be accessed from any pc on the network.  I have found something peculiar happening which is beyond my simple understanding of folders, files etc.

I use the cp command to copy an entire structure of folder/files from one HD to another.  The format of my command is as follows:[INDENT]cp -vru *[source] [target]*[/INDENT]
When I compare the results following the copy by checking the properties of each folder (# items, size) I find that most folders match, however, I periodically find a folder where the numbers of files do not match what was in the source.  Specifically, one folder in the source has 943 files yet in the target it has 905 files.  I identified the files that were not copied and via the ubuntu desktop copy them from the source folder to the target folder.  When I do so I am told they already exist in the target yet I do not see them through the desktop or even when I go to the terminal and list the folder contents.  It still shows only 905 files in the target yet it seems to know the missing files are there when I try to copy them over.  Now, when I disconnect the target HD from the router and connect it directly to the ubuntu desktop then I can easily see the missing files.

Would someone please be able to explain to me what might be happening in this case?  Why do these files easily show up on the HD when it is connected directly to the desktop but not show up when the HD is connected to the router (although seems to know about them)?  Is it a bad idea to connect your HD to your network router (for the record I use a TP-Link 1750)?  Any comments or suggestions are very much appreciated.  Thank you.

---

### Post by HermanAB on 2018-04-23
Well, you are using some sort of network file system, probably a buggy version of Samba.  Since you now know that the underlying software is unreliable, yet you don't want to change, you should at least use a reliable copy method when copying large numbers of files, such as rsync or unison, not ordinary cp.

---

### Post by jay30 on 2018-04-23
Thank you HermanAB.  I have all my drives now directly attached to my Ubuntu desktop and things seem much better (except for the access part).  Based on your suggestion I think I will look at switching from cp to rsync for the regular copying.

---

