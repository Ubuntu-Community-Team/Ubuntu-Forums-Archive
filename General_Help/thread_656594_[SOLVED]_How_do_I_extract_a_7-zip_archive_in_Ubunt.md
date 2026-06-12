---
title: "[SOLVED] How do I extract a 7-zip archive in Ubuntu?"
date: 2008-01-02
forum: General Help
---

### Post by omglol741 on 2008-01-02
I went to applications>add/remove> and installed 7zip, but I don't know how to extract things. There are no specific things when I right click, and it's not listed as a program I can open with. The files all end in .7z.001,.7z.002, etc.

---

### Post by shawnrgr on 2008-01-02
right-click on the first file of the group and select "Extract Here" or "Open with Archive Manager"

---

### Post by omglol741 on 2008-01-02
It says archive type not supported. :(

I just installed 7-zip and it says .7z... And Archive Manager says it supports 7z.

---

### Post by FuturePilot on 2008-01-02
I think you need to put them back together into one file manually. Make a copy of them first in case this doesn't go right, it should though.
Make sure all of the pieces are in the same folder such as ~/Desktop/Files/
Then open a terminal and cd into that directory
```
cd ~/Desktop/Files/
```
Then put them together
```
cat Filename.7z.001 Filename.7z.002 Filename.7z.003 > New_File.7z
```
Make sure you input all of the pieces. Replace "Filename" with whatever the name of the files are and replace "New_File" with whatever you want to call the new file. Then right click on the newly created file and extract it.

---

### Post by DirtDawg on 2008-01-02
Try renaming 'file.7z.001' to 'file.7z' and see if that helps.

---

