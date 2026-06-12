---
title: "how do i tell if the directory contains the file I just copied to ?"
date: 2021-07-22
forum: General Help
---

### Post by tangara on 2021-07-22
Hi,

Can someone tell me what commands to use to tell if the directory I have copied to contains the file ? cos when I use ls it shows nothing...

Here's the command that I used to copy the file:

root@DESKTOP-SB41UI7:~# cp space "/mnt/c/Users/karen/Udacity And SUSSE Cloud Native"/AWS-Jenkin-Practice/jenkins-master.pem.txt/to/Users/root/jenkins-master.pem" ~/ssh/

---

### Post by dragonfly41 on 2021-07-22
quotations not matched in pairs (one appears to be missing/not matched)
also introduce space between " and /

---

### Post by yancek on 2021-07-22
In addition to the missing matched quote, you don't seem to have a space between the source and destination.  THe command you posted shows you are trying to copy a file with the name:  Udacity And SUSSE Cloud Native to another directory.  The destination path contains a directory named "to" above the Users directory.  Is that correct?  Is this using windows sub-system for Linux?

---

### Post by Impavidus on 2021-07-22
As noted above, there appear to be some errors in your command. But you can indeed use ls to see if it was copied. If the name starts with a dot, the file is hidden and you have to use ls with the -a option. If the copy was unsuccessful, cp will give an error message. If there's no error message and the file doesn't appear to be there, either you copied it to the wrong place or you checked for its presence in the wrong place.

---

