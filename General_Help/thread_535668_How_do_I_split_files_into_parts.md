---
title: "How do I split files into parts?"
date: 2007-08-26
forum: General Help
---

### Post by s3a on 2007-08-26
Hi, when I was a Windows user (two days ago, lol) I had the ability to use Winrar to not only compress a file but split it into parts. I need to do this in Ubuntu Linux now because I need to send files by email and I can't send a file the size of what I want to send. Can someone point me to a freeware program that does this in Ubuntu Linux?

Thanks in advance!

---

### Post by freebeer on 2007-08-26
Maybe this might help?  [http://www.cgi-interactive-uk.com/splitting_large_files.html](http://www.cgi-interactive-uk.com/splitting_large_files.html)

---

### Post by mali2297 on 2008-02-04
You can install **rar** from the multiverse repository (use Synaptic). To create a split archive of a file or folder, let's call it  *foo*, use the command
```

rar a -v100M foo.rar foo

```
In this example, each part of the archive would be max 100MB.

If you don't like the terminal, try this [graphical tool]("http://ubuntuforums.org/showthread.php?t=556756").

---

