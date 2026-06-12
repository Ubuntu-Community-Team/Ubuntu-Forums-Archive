---
title: "Ext3 Mounted In Windows - Invalid File Names"
date: 2008-01-10
forum: General Help
---

### Post by blaze042 on 2008-01-10
I have an Ext3 formated external USB hard drive that has some 6,000+ files on it under various directories. This was used at home on a Linux machine with no problems. Since then I've copied the files onto a more permanent higher capacity location and thus, I didn't need the USB drive anymore. However, I could use these files on a Windows machine in another location. I installed Ext2Ifs and can mount the drive under Windows. However, there are a lot of files scattered across the drive that have characters that are invalid to Windows, e.g., /\|"?*[]:. Needless to say, the Windows OS won't allow me to rename, view, delete, etc...  the files with these invalid characters.

Here's the question: Is there any way under Windows to easily do a bulk replace of these invalid characters?

If not, then using a Linux boot CD (Ubuntu), is there a utility or package that can be installed through the package manager that will crawl the drive replacing the characters? Note, some of the invalid characters are found not just in the file names, but also the folder names.

TIA

---

### Post by Ocxic on 2008-01-10
yes there is a package you can install from the repositories that will do what you want, I dunno the name tho. and remember windows also limits the length of filenames to 32 characters aswell i think

---

