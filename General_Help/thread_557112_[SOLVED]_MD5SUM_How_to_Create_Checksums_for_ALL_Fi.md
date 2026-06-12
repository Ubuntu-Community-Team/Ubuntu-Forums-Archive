---
title: "[SOLVED] MD5SUM: How to Create Checksums for ALL Files and Sub-folders etc?"
date: 2007-09-22
forum: General Help
---

### Post by OzzyFrank on 2007-09-22
I didn't think this would be SO hard to find. I found a "man page" that had options for **md5sum** that looked promising - like **-a** or **--all**, and **-r** for recursive scanning - but they actually come up as unknown options! Am I missing something here?

Anyway, have tried **md5sum *.***, and that just did the files in the root of the folder. I'd like to be able to generate the checksums for all files and folders within the folder in question. That way I could simply verify the burned CD with **md5sum -c md5sum.txt**. Can someone tell me how this can be done? Like how the md5sum.txt file on the Ubuntu CD is created? Cheers

---

### Post by pheeror on 2007-09-22
```
find -exec md5sum "{}" \;
```

---

### Post by OzzyFrank on 2007-09-22
Awesome dude. My next question was going to be is there an option to stop lines like this appearing throughout:

md5sum: ./isolinux: Is a directory

...but md5sum just ignores those lines anyway, so I guess it doesn't matter.

Not enough distros have the "md5sum.txt" file to check the CD. I'm currently in talks with the creator of Elive about getting verification happening (he did try to have it, but it's all messed up and you'd have to check each file individually). Now that i am sussing out some solutions, I will be emailing them to a lot of distros.

So **find -exec md5sum "{}" \;** to generate and **cd /media/cdrom0 && md5sum -c md5sum.txt** to verify works great for Linux, but I've come to realise through looking at freeware apps that this won't be compatible for the vast majority in Windows... due to the backslash. Since some will be Windows users trying Linux for the first time, I reckon it would be a really good idea to include a second file that can be used to verify the CD in Windows.

For this I would suggest the freeware** FileCheckMD5**, as it is free, works in Windows and in Ubuntu (and other distros I imagine) running under Wine. It generates a "FCMD5.md5" which you can rename to "md5sum.md5" if you like. So 2 files with same name but different extensions, one for Linux (you supply the command to verify using "md5sum.txt") and one for Windows (with brief instructions for "md5sum.md5"). One could either supply the link to FileCheckMD5 or just have it as a direct download on your site - it is freeware... or even include it on the CD. I'll be doing this myself for any CD i want to be able to verify in any OS. 

Thanks again. Cheers

---

### Post by pheeror on 2007-09-22
```
find -type f -exec md5sum "{}" \;
```

Look at fedora team's solution for this problem.

---

### Post by pheeror on 2007-09-22
```
find -type f -exec md5sum "{}" \;
```

Look at fedora team's solution for your problem.

---

### Post by OzzyFrank on 2007-09-22
Great stuff. Now I can mark this as solved. If there is a way to get this to generate the file itself (ie md5sum.txt) feel free to post that up, but that's really not that important. I don't mind creating a new text document and pasting the results into that (I can be lazy but not THAT lazy, hehe). Cheers!

---

### Post by pheeror on 2007-09-23
```
find -type f -exec md5sum "{}" \; > b&#382;unda.txt
```
Where b&#382;unda.txt is your file. 
You can do some sedding/perling/awking/even bashing to get it into FreeMD5Checker format.

---

### Post by hanzomon4 on 2007-09-23
Isn't there a faster way to do this using find and xargs?

---

