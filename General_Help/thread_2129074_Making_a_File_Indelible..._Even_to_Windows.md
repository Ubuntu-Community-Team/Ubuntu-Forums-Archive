---
title: "Making a File Indelible... Even to Windows?"
date: 2013-03-25
forum: General Help
---

### Post by kenizl86 on 2013-03-25
How can I make a file in Xubuntu (or any ubuntu) indelible, or at least unreadable (if not undeleteable)? And is there a way to make this extend to Windows? I tried running the 'sudo chattr +i file.ext' command, but it did not work (the Terminal returned an error line).

The reason I ask this is that, one my computer (my Windows one), I extract Brutus from it's Zipped folder, but right after I place it in a folder, Windows XP immediately removes it. I have no idea why. I figured that maybe (since Unix has more editability) I could fix this issue on my Xubuntu box. It (being my Windows computer) also does it to other EXEs, not just Brutus (albeit certain ones).

Any ideas?

---

### Post by slickymaster on 2013-03-25
I can't assure you that this will work on windows, since I've never tried it, but I can assure you that works on Linux systems.

_Making immutable/indelible a file_
```
sudo chattr +i file_name
```
and the file "file_name" will become immutable. If instead you want to restore it, type:
```
sudo chattr -i file_name
```

_Making immutable/indelible a folder_
```
sudo chattr -R +i folder_name
```
and the folder "folder_name" become immutable. If instead you want to restore it, type:
```
sudo chattr -R -i path_of_the_directory
```

---

### Post by Cheesemill on 2013-03-25
Could it be that your Windows anti-virus software is deleting your files because it believes they are viruses?

---

### Post by LewisTM on 2013-03-25
The chattr command won't work on files in NTFS partitions which is what you have on Windows. The tools to edit NTFS in Linux are limited since it's a proprietary format. You would be better off seeking help in a Windows forum.

Cheers!

---

### Post by Mark Phelps on 2013-03-25
Brutus is a remote password cracker -- so, of course, Windows AV products will see this as malware and remove it!

---

### Post by QIII on 2013-03-25
Because Brutus is a password cracker and cracking/hacking subjects are not supported here, this thread is closed.

---

