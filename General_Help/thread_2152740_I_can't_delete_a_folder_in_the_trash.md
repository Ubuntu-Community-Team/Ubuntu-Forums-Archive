---
title: "I can't delete a folder in the trash"
date: 2013-06-08
forum: General Help
---

### Post by Bao2 on 2013-06-08
I run a script that created a folder with this name "~" (yes, the shortcut used for your /home/username folder, the script instead created a folder named with that "~" symbol).
The script was run as root so I could not delete the folder as a normal user. So I launched a nautilus as root and deleted the file.
But the file was to the Trash. I can see the folder is in the trash but as a normal user I can't delete it. And as root I can't empty the trash.

So my question is: Where in the FileSystem disk is the trash so I can enter and delete the files there using the terminal. I don't see any .Trash  file on the FileSystem disk (in other disks that folder appears and then you can delete it for example).

---

### Post by TNFrank on 2013-06-08
Would it be possible to pull it out of the trash and rename it to something so you can delete it?

---

### Post by Bashing-om on 2013-06-08
[COLOR=#000000]Bao2; Hi ![/COLOR]

drs305's informative tutorial;
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

If and in worst case, copy and paste into terminal to remove with admin authority ....[INDENT=2]
where there is a will there is a way

[/INDENT]

---

### Post by Bao2 on 2013-06-08
Found it.
sudo nautilus
and now go to the .local/share/Trash   folder and now delete the file

Thanks for the answers and your time guys.

---

### Post by Bashing-om on 2013-06-08
[COLOR=#000000]Bao2;

Hey; Quite welcome.
[/COLOR][INDENT=3][COLOR=#000000]We are all in this together 

[/COLOR][/INDENT]

---

