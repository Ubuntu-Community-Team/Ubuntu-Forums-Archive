---
title: "What is $RECYCLE.BIN on my External Hard Drive"
date: 2015-06-06
forum: General Help
---

### Post by gr8 on 2015-06-06
My NTFS external hard drive has a $RECYCLE.BIN directory I think Linux placed on it. What is it? Some psuedo recycle bin?

---

### Post by sotiris2 on 2015-06-06
Actually windows placed it there. It's your windows recycle bin. Windows probably doesn't show it to you since it special to it but to linux its just another directory so it gets shown.

Linux does create .Trash-number folders for recycle bins in my (fat format) usb flash drive, so that would be the case if ubuntu puts something on a recycle bin on your ntfs partition.

---

### Post by gr8 on 2015-06-06
When I delete a file in Windows does it just get moved to this $RECYCLE.BIN directory and not actually removed?

Same questions for Ubuntu, when I "move to trash" is it just moving files to this $RECYCLE.BIN directory?

Thank you!

---

### Post by sotiris2 on 2015-06-06
More details for how windows handles recycle bin [here](http://superuser.com/questions/368890/how-does-the-recycle-bin-work).

No I don't think ubuntu will put stuff in $RECYCLE.BIN because as I said before it's not special to it. I told you what it does in my fat32 formatted usb flash drives, it makes it's own .trash-1000 folder and puts it there. Folders that start with a dot . are hidden files in linux (not normally shown). When I put that flash drive on my windows install the .trash-1000 folder is just another folder because it means nothing to windows. 

In my actual ntfs hard drive partitions ubuntu doesn't support a recycle bin at all. It gives me a warning that it can't send it to recycle bin and asks for confirmation for PERMANENT deletion. 

Finally to round up this trashy business your ubuntu recycle bin (for files in your ubuntu home partition) is in ~/.local/share/Trash
~ is your home folder. To see hidden folders just press ctrl+H . You will see that the recycle bin isn't really any "mystical" place but just another directory.

---

