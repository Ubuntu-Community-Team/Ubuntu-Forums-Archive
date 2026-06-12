---
title: "ftp question"
date: 2007-03-14
forum: General Help
---

### Post by ncappel1 on 2007-03-14
Hi everyone, I am trying to figure out how to send files over the command line to a remote machine with ftp. I am fine with sending single files, but is there a way to send an entire folder's contents and subfolders and their content too?

ive been reading man pages and other things too, but I just can't figure it out, it's bugging me!

---

### Post by useResa on 2007-03-14
> **ncappel1 said:**
> Hi everyone, I am trying to figure out how to send files over the command line to a remote machine with ftp. I am fine with sending single files, but is there a way to send an entire folder's contents and subfolders and their content too?

ive been reading man pages and other things too, but I just can't figure it out, it's bugging me!
IIRC: When you want to transfer 1 file you use the PUT command.
If you want to transfer multiple files you can use the MPUT command.
With MPUT you can use wildcards like *.* to transfer all files in a directory (I am not sure if subfolders get submitted as well)

Hope that this somewhat helps.

---

### Post by ncappel1 on 2007-03-14
i've tried using the mput command, but the subfolders don't get sent. in fact nothing gets sent, this is what happens:

```
ftp> mput ~/Desktop/blog/*.*
mput ~/Desktop/blog/add.php [anpqy?]? [here i type "y']
227 Entering Passive Mode (62,149,140,82,195,112)
553-Can't open that file: No such file or directory
553 Rename/move failure: No such file or directory
```

any ideas?

---

### Post by oneofth3m on 2007-03-14
Try writing a script file which can recursively browse through a folder and when ever it finds a file it uploads using ftp.

---

### Post by useResa on 2007-03-15
> **ncappel1 said:**
> i've tried using the mput command, but the subfolders don't get sent. in fact nothing gets sent
Hmmm ... no not sure why it not gets sent.
Maybe it is a too obvious question, but I assume that you do have the rights to copy that file?
 
Regarding MPUT
Googled somewhat around and don't think you made any mistakes there (except that most samples use * instead of *.*).
Furthermore I came across some links that may be of interest:
**1. [Essentials for using Linux FTP]("http://www.reallylinux.com/docs/autoftp.shtml")** (this page contains a sample of a script to copy an entire directory)
**2. [Linux/Unix command ftp]("http://linux.about.com/od/commands/l/blcmdl1_ftp.htm")** What struck me on this page was the following
> Note: **mget** and **mput** are not meant to transfer entire directory subtrees of files. That can be done by transferring a [[COLOR=black]tar[/COLOR]]("http://linux.about.com/library/cmd/blcmdl1_tar.htm")(1) archive of the subtree (in binary mode). 

---

