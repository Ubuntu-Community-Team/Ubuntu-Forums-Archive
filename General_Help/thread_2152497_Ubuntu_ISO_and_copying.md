---
title: "Ubuntu ISO and copying"
date: 2013-06-08
forum: General Help
---

### Post by anon_private on 2013-06-08
I downloaded a ubuntu iso file to the pc, but when I try to copy it to a pendrive (4GB) I get the mesage that there is not enough space. I have remove all the files, but still get this message.

I think there must be a lot of hidden files/directories on the drive.

How can I see them and remove them ( detailed instructions please).

Thanks

---

### Post by 2F4U on 2013-06-08
Could it be that there is more than one partition on the drive? You could see this through the partition editor, for example.

---

### Post by CatKiller on 2013-06-08
How is the drive formatted? Also, if you simply deleted the files in a file manager then you'll also need to empty the Trash (if you deleted them in Ubuntu) or the Recycle Bin (if from Windows).

Ctrl-h is the keyboard shortcut to show hidden files in the Ubuntu file manager.

---

### Post by 3rdalbum on 2013-06-08
> **anon_private said:**
> I downloaded a ubuntu iso file to the pc, but when I try to copy it to a pendrive (4GB) I get the mesage that there is not enough space. I have remove all the files, but still get this message.

I think there must be a lot of hidden files/directories on the drive.

How can I see them and remove them ( detailed instructions please).

Thanks

Press Control-H in the file manager to show hidden files. Or you can just format the flash drive (right-click, Format)

Have you checked the size of the ISO? IIRC there is a large Ubuntu DVD image that fills a single-sided DVD, and it's full of language packs. Obviously, it'll be about the 4.1 gig mark and won't fit on a 4 GB flash drive.

If you've instead got the regular Ubuntu disc (that's around a gigabyte), you might have a faulty or modified pendrive. Some cheap pendrives from China are low capacity, but have a higher capacity printed on them and also have their circuits modified to read as being the higher capacity. If you bought it from a local market stall or directly from China online, it might be one such scammed drive.

---

### Post by anon_private on 2013-06-08
The pendrive that I wanted to clean up in preparation for a new livependrive had masses of hidden files.

I found that many files, and virtually all the space, was being used by .Trash-999.

I have got rid of this directory (using a Vista pc) and now hope to be able to install another UBUNTU live pendrive.

At present, I am running a UBUNBTU livependrive (another pendrive), and wonder about the .trash-999 file that must be there and using increasing space.

Can I stop it taking up the penbdrive space?

_________

You mention the file manger. Is this called the file manager?

Thanks

---

### Post by CatKiller on 2013-06-08
Ctrl-h will show hidden files, as mentioned above. Shift-Delete will delete files rather than moving them to Trash.

---

### Post by 3rdalbum on 2013-06-08
The file manager is the window that allows you to browse the contents of your home directory, hard disk or other disks. If you click the folder icon in the Launcher bar or double-click a folder or disk on your desktop, you get a file manager window.

Usually there should be nothing in any of the .Trash folders, unless you drag something from your USB to the trash and forget to empty it. You probably can't prevent the creation of a .Trash folder.

---

### Post by anon_private on 2013-06-08
Can I see the hiddden files in a window - see all files?

The .Trash-999 on my pendrive contained numerous files (very large). I did not drag any files. I think this folder was made and populated autocatically. How can it be emptied, bear in mind that this file os on the pendrive.

---

### Post by coffeecat on 2013-06-08
> **anon_private said:**
> 
The .Trash-999 on my pendrive contained numerous files (very large). I did not drag any files. I think this folder was made and populated autocatically. How can it be emptied, bear in mind that this file os on the pendrive.

The .Trash-999 folder was created when you used the delete key in your live desktop session. As others have said, to empty it you simply need to empty the trash.

---

### Post by anon_private on 2013-06-09
> **CatKiller said:**
> Ctrl-h will show hidden files, as mentioned above. Shift-Delete will delete files rather than moving them to Trash.

So I view a page hit ctrl-h and all hidden files appear
Shift delete on the page will delete the files

> **coffeecat said:**
> The .Trash-999 folder was created when you used the delete key in your live desktop session. As others have said, to empty it you simply need to empty the trash.

I assume that you mean the 'Trash' on the desktop and not Trash-999

---

### Post by CatKiller on 2013-06-09
It's all the same thing. When you move a file to trash it gets put in the hidden Trash directory belonging to your user on the partition that contained the file. The Trash user interface collates together the files in that user's Trash directories and Empty Trash gets rid of all of them.

---

