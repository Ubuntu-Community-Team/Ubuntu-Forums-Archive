---
title: "Seamonkey not swimming"
date: 2008-04-22
forum: General Help
---

### Post by E$P on 2008-04-22
Hi,

Wanted to give Seamonkey a try, went an got it from the Mozilla site, followed the instructions in the readme file, but didn't get far...

Step 3 is: Change to the seamonkey directory (cd seamonkey) and decompress the archive with the following command:

  tar zxvf sea*.tar.gz

So I can change to the Seamonkey directory easy enough, but then I type the  tar zxvf sea*.tar.gz command and this comes up: 

-laptop:~/seamonkey$ tar zxvf sea*.tar.gz
tar: sea*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Have no idea what this means, no idea what to do, any help be much appreciated (by the way, running Gutsy Gibbon on a HP Pavilion dv1000)
Cheers

---

### Post by banished_one on 2008-04-22
well i dont know what tar zxvf command does but im guessing it just unzips the data. If thats the case you can just right click the file and select extract here instead of using that command

---

### Post by lswest on 2008-04-22
the sea* bit is an incorrect use of a wildcard, just replace the "*" with the rest of the filename (hit "tab" to auto-complete after typing "sea")

---

### Post by Snarl on 2008-05-25
> **E$P said:**
> 

  tar zxvf sea*.tar.gz



If anyone's still reading this thread, you can't use tar like that.  The command 'x' (for extract) has to be first.  The rest are options, 'z' to gunzip, 'v' for verbose and 'f' for the file to operate on.

The correct tar command is

  tar xzvf sea*.tar.gz

The wildcard will be expanded by the shell.

---

### Post by kerry_s on 2008-05-25
if you just want to try it, why not just grab it from the repo?
use synaptic or sudo apt-get install seamonkey

---

