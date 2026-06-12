---
title: "Directory Name Spaces and SFTP"
date: 2007-05-25
forum: General Help
---

### Post by dpsguard on 2007-05-25
Hi all,

I am new to Linux. Just installed Ubuntu desktop. 

I had created a directory named "My Documents" in GUI and it accepted it. It is shown as correct under the pathname as /home/dpsguard/My Documents/ but from terminal I was getting errors. I read around and was able to figure out a fix for this. So I type /home/dpsguard/My\ Documents and it is then accepted.

Now I am trying to sftp to a work server ( I used to use a GUI client on windows XP but can not find one in LInux, tried Gftp but can not figure out sftp working, FTP/ Options / SSH is confusing, so I left it there only) . 

I can connect to work server successfully from terminal by typing like "sftp dpsguard@12.34.56.78 and get  to sftp>. When I try to upload some files from my local directory My Documents I get errors that this directory does not exist

Tried all combinations, it truncates directory to "My" and stops with error

 sftp>put /home/dpsguard/My Documents/test.txt

 sftp>put /home/dpsguard/My\ Documents/test.txt

 sftp>put /home/dpsguard/"My Documents"/test.txt

 sftp>put /home/dpsguard/"My\ Documents'/test.txt

It does appear to be shell issues but as I said I am novice and am looking for some guidance as to how to resolve specifying directory names with spacs in them, in sftp as pathnames. All works fine with directory names as single word with no spaces.

Appreciate any help,

Thanks

---

### Post by mbradlcu on 2007-05-25
what about?
```
sftp>put "/home/dpsguard/My Documents/test.txt"
```

commentary here,,, spaces in filenames and dirs are a pain to deal with, "My_Doucments" IMHO looks nice and doesn't cause all the problems.

---

### Post by dpsguard on 2007-05-25
Excellent. That did the trick. I am so glad to find resolution to my problem so quick at this forum.

So to clarify, I should always enclose the whole pathname in quotes for dealing with spaces in directory / filenames. And I do agree to not use, wherever possible, any spaces in these names.

Appreciate again for your help.

---

### Post by dpsguard on 2007-05-25
I am also able to now use gFTP for SFTP. Requires selecting SSH2 and port 22, while I had only port 22 and ftp selected and it was not working thus.That is why I tried to use terminal. 

gFTP becomes a single FTP/SFTP client for file transfer applications for me to use on Ubuntu Desktop. Thanks to this forum, I learnt quite a bit about Linux just in two days, being always a windows user before. The only issue now I need to resolve is running some windows applications thru WINE.

---

