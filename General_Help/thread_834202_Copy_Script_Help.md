---
title: "Copy Script Help"
date: 2008-06-19
forum: General Help
---

### Post by esullivan on 2008-06-19
I am running Ubuntu Desktop, with LAMP.  I have a site where users can download files.  I have two files on a Windows server that I edit a lot (extension list), and I want a script to run every night that replaces the files on the Ubuntu box, with what's on the Windows box (so the file list is up to date every night.

I was going to have a .bat file run on the server, and copy to a share, but I can't get Ubuntu to NOT ask to authenticate.

Any thoughts on a better way to do this?

---

### Post by bingoUV on 2008-06-19
Isn't the filesystem of the windows box mounted on the Ubuntu box? Why don't you write a script on Ubuntu to copy from the windows box to Ubuntu box?

---

### Post by justleen on 2008-06-19
isseuing the commands on the ubuntu side would be easier, since linux comes with cron, the perfect scheduler for things like this...

if you do want to use it on windows, i'd suggest scp (ssh) with a generated key pair to "by pass" the security...

---

### Post by esullivan on 2008-06-19
New to Linux, what's the Windows Batch file equivalent for Linux

---

### Post by beckols on 2008-06-19
A shell script.  Like Windows, anything you type into a terminal can be put into a script.  Unline Windows, Linux is CLI-oriented, so you have much more power and versatility when writing scripts.

If you want to learn to write basic scripts here are some links:
[http://ubuntuforums.org/showthread.php?t=73885&highlight=log+file+locations]("http://ubuntuforums.org/showthread.php?t=73885&highlight=log+file+locations")
[www.linuxcommand.org]("www.linuxcommand.org")

The first one is a terrific post by Kyral, it is probably one of the best simple explanations for beginning to use the terminal.  The second is a site with very easy to understand tutorials as well, and has a section just on writing shell scripts.

---

### Post by esullivan on 2008-06-19
Thanks guys!

---

