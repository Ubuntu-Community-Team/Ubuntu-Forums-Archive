---
title: "Copy/Paste Not Working"
date: 2021-11-03
forum: General Help
---

### Post by bostonman on 2021-11-03
Hello,

I'm new to this board, so bare with me if I'm posting in the wrong section (and I apologize in advance).

I'm using Ubuntu 20.04.3 and suddenly it seems trying to copy a file and pasting it to a thumbdrive or another internal drive doesn't work. I'm able to select 'copy', however, when I go to my destination drive and click 'paste', it's dark (i.e. I'm unable to select it).

I've tried rebooting, checking permissions (per stuff I've read online, and so far I'm at a loss. It seems a bug exists, but that's while trying to 'cut' a file and pasting it.

Does anyone know why this is happening and how to get around it?


Thanks.

---

### Post by vanadium on 2021-11-04
Can you copy to files/folders under your home folder? Can you copy on a different way, e.g. by drag and drop? Are there error messages/error dialogs? If yes, what is the message?

---

### Post by yancek on 2021-11-04
>  suddenly it seems trying to copy a file and pasting it to a thumbdrive or another internal drive doesn't work

 The word 'suddenly' jumps out as it implies this was done and done successfully before.  Are you copying a file from your /home/user directory where you should have read/write/delete permissions a wll as ownership to all files?  Are you them trying to copy these files to another USB or other drive where you had NO ownership permissions..  To 'cut a file is NOT the same as to 'copy' it, 'cut' ,means to move which also means to delete  You need to ascertain the owner:group and permissions you want to copy "TO" as well as the owner:group and permissions from which you want to 'cut'.

---

### Post by bostonman on 2021-11-04
I'm not getting an error message, and yes, I can copy within Ubuntu.

Drag and drop never worked, it always pulls the file back to its original location. I always have to right click and select copy and then paste. The thumbdrive is just plugged in as I had been doing in the past. Also, I try accessing an internal (Windows) drive as I normally did, and also unable to paste a file there.

So when I right click in the destination, the word 'paste' is dark and doesn't allow me to select it.

Since it worked before, I'm assuming an update changed something.

---

### Post by TheFu on 2021-11-05
So, I'll take a guess that the USB storage isn't using a native Linux file system.  It probably has exFAT or FAT32 or NTFS?  For those to be read-write, the mount options need to allow that for the current userid.  By default, at least on all my systems the last 20 yrs, that doesn't happen without manual effort.

You can test this by trying to create a new text file in the target directory. Does that work or not?
Also, you can see the file system used by running:
**df -Th** while the USB storage is 'mounted'.  That will show the file system used, which is the first step in understanding which, if any, mount options are necessary.

---

### Post by pantazi on 2021-11-05
Does ctrl+C and ctrl+V  work?

---

### Post by ActionParsnip on 2021-11-05
Have you checked the file system on the USB to make sure it is healthy? You can use fsck if it is a Linux file system or for NTFS you should use Windows

---

### Post by bostonman on 2021-11-07
I'll check the thumbdrive but this is also not working on an internal hard drive that's WinXP based.

This all worked before at some point because I was copy/pasting files either by CTRL C/V or right clicking and selecting accordingly between Ubuntu and the XP internal hard drive. I'm only guessing, but would say this problem began after an update, however, Ubuntu seems to have updates almost daily.

At the moment, using CTRL C/V doesn't work, and the 'paste' option in the drop down menu (right clicking) is greyed out. I also tried copying/pasting from the XP drive to Ubuntu and the same thing. I just realized that I placed a PDF onto Ubuntu from the XP drive on 11/2 (at least that's what the permissions show as the last access time - I'm guessing that's when I moved it because I know it was recent). So sometime around 11/2 something changed and I don't use this computer often, so I there is little I would have changed in Ubuntu.

Also, I can download a file from the Internet and save it to the XP drive if I select that as a location - so Ubuntu is capable of saving files to another drive - just not pasting.

If it has any connection, I know at one point I couldn't open a PDF on Ubuntu that I copied/pasted from the XP drive. It would open just fine if I opened it while it was still on the XP drive, but once I copied/pasted it onto Ubuntu, it wouldn't open.

---

