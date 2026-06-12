---
title: "Finding file names that conflict with Microsoft naming"
date: 2018-07-11
forum: General Help
---

### Post by anoldguy on 2018-07-11
Is there a tool that looks at Ubuntu file names and outputs the file names that are invalid in Microsoft?  

For example:  [Screenshot from 2018-07-11 15:48:08] 
is invalid because it contains a [:].  

Other invalid characters include:  [ “ / \ | ? * ] and even names ending in period or a space.  

I tried the awesome FSLint, but Bad Names lists most of my files and doesn't seem to consider the above characters. 

I've used Files 3.10.1 (Ubuntu 14.04) Search to look for a character like [:], but it's kinda tough searching for a final space or period.


I have problems when trying to backup files to a Samsung T5 Portable SSD (it uses exFAT). 


There is also the problem that [BANANA] is the same file name as [banana] to Microsoft, but I fear that I will have to pick those out singly.

---

### Post by kazakore on 2018-07-11
[https://stackoverflow.com/questions/19008614/find-files-with-illegal-windows-characters-in-the-name-on-linux](https://stackoverflow.com/questions/19008614/find-files-with-illegal-windows-characters-in-the-name-on-linux)

---

### Post by Holger_Gehrke on 2018-07-11
The CLI-tool find will easily find all of the 'wrong' characters and even those pesky spaces or dots as last characters, as the discussion linked by kazakore shows.

To make the search for file names differing only by case easier, a combination of sort and uniq will help:
```

ls -1|sort -f|uniq -Di

```
will print out all file names in the current working directory that differ only by case.

Holger

---

### Post by anoldguy on 2018-07-11
Thank you Holger, exactly what I was looking for!

---

