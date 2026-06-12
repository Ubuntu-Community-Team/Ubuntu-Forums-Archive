---
title: "Using mkisofs command"
date: 2007-04-08
forum: General Help
---

### Post by MacPC on 2007-04-08
Hello,

I am trying to use the mkisofs command to make a iso backup of my Win98 partition on my multi-boot machine. 

I created a /tmp/ directory on my desktop, I copied all files from the Win98 partition, put them in the /tmp/win98copy/ directory. I named the output file /tmp/win98bk.iso, 

I typed in :  mkisofs -o /tmp/win98bk.iso /tmp/win98copy/ 
then I got this message:

INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: No such file or directory. Invalid node - /tmp/win98copy/

 What did I do wrong? What does the UTF-8 mean and how do I correct it?

Btw, I use Ubuntu 6.0.6 dapper.

Thanks in advance.


MacPC

:guitar:

---

