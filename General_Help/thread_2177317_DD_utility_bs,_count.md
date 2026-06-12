---
title: "DD utility: bs, count"
date: 2013-09-28
forum: General Help
---

### Post by 7t6dLGB on 2013-09-28
Hello,

I just trying to rewrite files.

I have "dd if=/something of=file bs=1 count=FILE_SIZE"
It is very SLOW.
If I try "dd if=/something of=file bs=512 count=FILE_SIZE/512"
It is very FAST. But it is not exactly file size. It may be less or more.

Therefore I want use second command, but I don't know if it doesnt rewrite something important after file. How can I rewrite file, with bs=512, and dont damage other files?

Or how it will be working with "dd ......... bs=FILE_SIZE count=1" ?

Thanks for clarifying.

---

### Post by sudodus on 2013-09-28
***dd*** is used to read or write block devices, typically cloning an installed system or flashing an iso file to a USB pendrive. And it is risky, so I recommend to used it with some kind of help program to avoid destroying your system, 

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

***dd*** can also be used for regular files, but there are better alternatives for that ...

But to answer your question: ***bs*** is the block size, how many bytes that are read or written each time. The default block size is 512 bytes. ***count*** is the number of blocks that are copied.

I have found that bs=4096 makes dd work fast in many situations. If you intend to write a whole file or device, you need not use count, dd will continue until either there is nothing more to read or no more space to write.

But for normal copy operations I use ***cp***, and for more advanced operations (backup and syncing) I use ***rsync***.

Read the manual pages or find tutorials on the internet.

```
man dd
man cp
man rsync
```

---

