---
title: "How to easily join split 001, 003 and 002 files."
date: 2017-11-16
forum: General Help
---

### Post by lelop15 on 2017-11-16
I want a really easy guide to this preferably not using the terminal, i want to join these three files so i can easily extract them using archive manager.

---

### Post by Impavidus on 2017-11-16
**cat** should be able to do so.```
cat file1 file2 file3 >output_file
```
Avoiding the terminal is the hard way.

FYI, the reverse of this operation is done with **split**. Also see the manual pages with **man cat** and **man split**.

---

### Post by ajgreeny on 2017-11-16
What sort of files are they; you don't tell us?

I presume they're split archives (eg zip or gz files) but without that info and also what you want from the final output file, it is difficult to help you.

Normally you need to start with the first numbered part-archive in the archive manager and after extracting that the archive manager asks for the second, and so on.

I don't think I have seen any such split archives since using Linux, so it is possible that my thoughts are going all the way back to Windows, using Winzip but a quich search found this old thread [https://ubuntuforums.org/showthread.php?t=859596](https://ubuntuforums.org/showthread.php?t=859596)

---

### Post by Holger_Gehrke on 2017-11-16
Or if your dislike of the command line is stronger than your unease at running hard to check proprietary binary blobs you can look for "HJSplit for Linux". It's your choice. I'd just make a new directory, put the files to join in there, right-klick the directory in my file manager, choose "Open Terminal here" and type 'cat * >IJustLoveLongArbitraryAndUselessFilename' and be done with it.

---

