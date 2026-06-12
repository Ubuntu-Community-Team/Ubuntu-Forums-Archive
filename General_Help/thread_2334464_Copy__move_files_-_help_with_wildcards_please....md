---
title: "Copy / move files - help with wildcards please..."
date: 2016-08-19
forum: General Help
---

### Post by pat4 on 2016-08-19
Hi,
I am having trouble copying or moving files from one directory to another using terminal and the cp or mv command.

I have a directory with a large number of assorted document files of various extensions. I am trying to copy files of extension *.txt and *.pdf to another directory.  This is the command I am using:

$ cp /home/pat/t1/*.txt *.pdf /home/pat/t2/

where the originating directory is named t1 and the destination is t2.  Note the spaces - *.txt[space]*.pdf[space]/.......

I am getting the message:      cp: cannot stat '*pdf': No such file or directory.

I can list the files using the ls command and the files are definitely there....  I have tried rewriting the command but whichever extension I list secondly is the one rejected whether it be pdf or txt.    If I try to copy (or move) the files using individual separate extensions one after the other I don't have a problem.

I have searched various solutions and I am unable to see my error.   Can anyone help me with correct syntax please?

Many thanks.

---

### Post by howefield on 2016-08-19
Try..

cp /home/pat/t1/{*.txt,*.pdf} /home/pat/t2/

---

### Post by montag dp on 2016-08-19
The problem is that you did not specify a directory for the pdf files, so it is looking in your working directory. Either use howefield's solution or this:

```
cp /home/pat/t1/*.txt /home/pat/t1/*.pdf /home/pat/t2/
```

---

### Post by pat4 on 2016-08-19
Thanks for the replies...  Both those solutions tried and OK.  It seems I have a lot to learn.

I appreciate your help.

Kind regards,  Pat.

---

