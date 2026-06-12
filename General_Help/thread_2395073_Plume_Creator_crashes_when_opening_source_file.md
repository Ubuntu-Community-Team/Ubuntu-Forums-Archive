---
title: "Plume Creator crashes when opening source file"
date: 2018-06-26
forum: General Help
---

### Post by Captaingracekidd on 2018-06-26
Hi everyone,

I have searched for a fix for my problem online but cannot find it, so I really really hope you can help me solve this issue as I am working on a manuscript that needs to be finished at the end of summer, and now it seems that Plume Creator has hijacked my text. :frown:

Basic dats: Ubuntu 14.04 64bit with Plume Creator Version 0.66.1.
After opening Plume Creator and attempting to open the source file the program instantly crashes. In terminal: 

```
~$ plume-creator
Running on Gnome 
QuaZipFile::open(): zip does not have current file
Segmentation fault (core dumped)
```

I can create new projects that open fine in Plume Creator.
Corrupt .plume file?

Alternatively: Is there a way of getting the text out of a .plume file?

(To be mentioned, the source file is save onto a different partition, I did read that segmentation errors can be due to the program not having permission to access certain areas, but I attempted to copy and place the file in the home directory and open it from there but it does not change anything. Also I had the file saved like this and working on it the last 3 months without a problem. The user permissions for the file is set to read and write for the user.)

---

### Post by spjackson on 2018-06-26
A .plume file is actually a zip archive. Can you unpack it with unzip? If so, you should be able to recover the text from the constituent documents. If it is corrupt in a way such that unzip can't open it then that's a harder problem.

---

### Post by Captaingracekidd on 2018-06-26
Hi Spjackson,

I opened the file with Archive Manager which showed me a folder called Text, it was empt. I extracted the file and it was still empty. Since the Plume file is barely a bit more than 1kb in size can it be that it is just redirecting to another hidden source file? Or has the program in some strange way deleted all the data in the file... I hope not. Thanks for the help!

---

### Post by spjackson on 2018-06-26
> **Captaingracekidd said:**
> 
I opened the file with Archive Manager which showed me a folder called Text, it was empt. I extracted the file and it was still empty. Since the Plume file is barely a bit more than 1kb in size can it be that it is just redirecting to another hidden source file? Or has the program in some strange way deleted all the data in the file... I hope not. Thanks for the help!
It appears that an empty .plume document is about 4kb. So at 1kb it would appear to be destroyed. Do you have a .plume_backup file, or any other backup?

---

