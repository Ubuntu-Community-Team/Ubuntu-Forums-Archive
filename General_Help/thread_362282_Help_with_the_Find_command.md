---
title: "Help with the Find command"
date: 2007-02-15
forum: General Help
---

### Post by crypticstatic on 2007-02-15
Hello All,

I wondering if someone can assist me with the find command.

Basically what I want to do is search a directory and it's subdirectories for a file called file.log and zip the files to a compressed file called file.log.zip

If someone can assist me with the correct syntax it would be greatly appreciated.

Thanks in advance!

---

### Post by anaconda on 2007-02-15
First go to the directory where you want to do the search and then type:
find -name file.log

it will search all the subdirectories too.. you can also add the directory to the command like this:
find /home/anaconda -name file.log 2>/dev/null
this would search all directories starting from /home/anaconda and all its subdirectories.. the "2>/dev/null" part is useful. It means that move all error messages to /dev/null, which means ignore all error messages.

You can get more info with
man find

cant help you with the zip part, but it would go like this:

find /home/anaconda -name file.log 2>/dev/null | zip whatever wherever
look at 
man zip
for more help.

PS. I know manpages are hard to read, and dont like to tell anyone to use man..

---

