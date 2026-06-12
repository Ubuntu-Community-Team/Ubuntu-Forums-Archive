---
title: "recover ntfs files deleted in ubuntu"
date: 2007-11-16
forum: General Help
---

### Post by brar on 2007-11-16
Hi

I have dual boot system with ubuntu and windows xp.  I was trying to share my thunderbird profiles in windows system (C:\ Documents and Settings\***\Application Data\Thunderbird\Profiles\xxxxxxxx.default)  with ubuntu but accidently deleted the profiles folder :( (which was more than 1GB in size). I have tried couple of file recovery utilities in windows but they are unable to detect the folder. I also tried ntfsundelete in ubuntu but it doesnt detect the deleted files/folders. Could somebody please help me out with this.

FYI
Ubuntu (gutsy gibbon installed on ext3 partition)
Windows xp sp2 on NTFS partition.

Thanks in advance

---

### Post by TidusBlade on 2007-11-16
I think theres a .trash-***** folder on the C: drive, I found it when I deleted stuff from my NTFS partition using Linux.

---

### Post by brar on 2007-11-16
there is no .trash folder in c: drive. I checked diskspace and files have been actually deleted.

---

### Post by TidusBlade on 2007-11-16
Oh, sorry then, I guess theres no way to get them back, unless you have some type of backup :( OR maybe someone else got a solution

---

### Post by erginemr on 2007-11-16
> **brar said:**
> there is no .trash folder in c: drive. I checked diskspace and files have been actually deleted.

Hello,

Did you check the command "Ctrl+H" in Nautilus when you are in the root folder of your Windows drive? "Ctrl+H" makes nautilus show hidden files and there should be a .Trash-yourname file in your Windows root directory.

---

### Post by brar on 2007-11-16
> **erginemr said:**
> Hello,

Did you check the command "Ctrl+H" in Nautilus when you are in the root folder of your Windows drive? "Ctrl+H" makes nautilus show hidden files and there should be a .Trash-yourname file in your Windows root directory.

I have checked that as well. As I previously mentioned 1GB space which the folder occupied has been reclaimed. This means that the folder is not there anymore.:(

---

### Post by az on 2007-11-20
ubuntu-rescue-remix.org

use the dls tool to image the unallocated space and then try to carve the files out of that image.

---

