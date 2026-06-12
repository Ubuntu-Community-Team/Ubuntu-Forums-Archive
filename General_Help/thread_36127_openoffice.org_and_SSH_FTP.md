---
title: "openoffice.org and SSH FTP"
date: 2005-05-22
forum: General Help
---

### Post by xsoldier1911 on 2005-05-22
When I connect to my universities network storage srive (udrive), I have complete access to all my files.  I can copy, paste, and open files, except for openoffice.org files.  For example, I can double click on a .txt file and it will open with gedit.  However, if I double click on a msword doc, I get the openoffice.org splash screen followed by an error box that says:
Error loading document
file:///home/john/sftp://xxxxxx@xx.xxx.xxx.xxx/U-Drive/x/x/xxxxxx/file.doc:
file:///home/john/sftp://xxxxxx@xx.xxx.xxx.xxx/U-Drive/x/x/xxxxxx/file.doc does not exist.

If I right click on a .txt file and select to open it with openoffice I receive the same error.  Does anybody have any idea how to remedy this problem?
Thanks in advance for any help,
John

---

### Post by tread on 2005-05-22
Funny .. I would check three things:
1. Does openoffice work fine on local machines?
2. Does openoffice create temp files in the folder where the original resides?
3. Do you have right access to the network folder?

Beyond these obvious ones, I can't think of anything else at the moment  :???:

---

### Post by xsoldier1911 on 2005-05-22
[QUOTE=tread]Funny .. I would check three things:
1. Does openoffice work fine on local machines?
2. Does openoffice create temp files in the folder where the original resides?
3. Do you have right access to the network folder?

Beyond these obvious ones, I can't think of anything else at the moment  :???:[/QUOTE]

1. Yes openoffice works perfect on local files.
2. As far as I can tell, openoffice does not create temp files.  I observed a folder for hidden files by opening a word file, then refreshing to see if any temp files were created like microsoft word does.  I didn't see any temps created.
3. Yes I have complete access to the network folder, its an SFTP folder that I have to login into.  I can open and edit plain text docs and add or delete files.

Thanks for the help, I am completely puzzled over this one though.
John

---

