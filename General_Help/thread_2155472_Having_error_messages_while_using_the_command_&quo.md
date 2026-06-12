---
title: "Having error messages while using the command &quot;sudo nautilus&quot;"
date: 2013-06-18
forum: General Help
---

### Post by tushar21nov on 2013-06-18
[h=5]I am using Ubuntu 12.04 LTS (32 bit). When I run "sudo nautilus" command in the Terminal, this output appears:
 
 tushar@tushar-G41M-Combo:~$ sudo nautilus
 [sudo] password for tushar:
 Initializing nautilus-gdu extension
  Nautilus-Share-Message: Called "net usershare info" but it failed: 'net  usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares. Error No such file or directory
 Please ask your system administrator to enable user sharing.
 
 But still I can edit the folders and files in the "File System". After closing the window this output appears in the terminal:
 
 tushar@tushar-G41M-Combo:~$ sudo nautilus
 [sudo] password for tushar:
 Initializing nautilus-gdu extension
 Nautilus-Share-Message: Called "net usershare info" but it failed: 'net  usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares. Error No such file or directory
 Please ask your system administrator to enable user sharing.
 
 Shutting down nautilus-gdu extension
 tushar@tushar-G41M-Combo:~$
 
 What is the reason for this error message ? Why the messages with "Failed" and "Error" ? How to fix this error ?[/h]

---

### Post by CatKiller on 2013-06-18
It's saying that it can't find any Windows shares, which is OK because you don't have any Windows shares.

Using sudo with graphical applications is a bad plan. Use gksudo instead.

---

