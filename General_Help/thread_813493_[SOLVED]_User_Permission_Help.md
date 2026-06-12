---
title: "[SOLVED] User Permission Help"
date: 2008-05-30
forum: General Help
---

### Post by HunterThomson on 2008-05-30
Aloha,

Well, I just found the ever so cool SuperKaramba and now I have my logfiles on the screen. 

My problem is that after I played around with a few Karamba themes now when I close Dauphin I get a error message saying it can not save to the Bookmarks file. I don't know if this is related to my playing around with Karamba or not but I do know that the drive/partition is not full at all(14GB are free) I guess it must be a permission problem according to what he error message tells me. What do you think the problem mite be? How would I fix this problem?

Thank you in advance. 

See, screen shot below.

Mahalo

---

### Post by HunterThomson on 2008-05-30
What dose this bookmarks file do anyway?

---

### Post by MrFSL on 2008-05-30
For starters you can post the output of the following command:

```
ls -l ~/.kde/share/apps/d3lphin/
```

Odds are you don't have permissions to edit the file because perhaps at one point you ran the application using sudo.

F.Y.I.
Permissions can be changed with chmod command:
```
ex.
chmod -R cruzer:cruzer ~/.kde/share/apps/d3lphin
```

---

### Post by HunterThomson on 2008-05-31
-rw-r--r-- 1 root root 1555 2008-05-27 01:14 bookmarks.xml
-rw-r--r-- 1 root root 1555 2008-05-27 01:14 bookmarks.xml.bak

So, it seems root is the only usr or group with read/write permission to bookmarks. Is this how it should be? Should I change the permission of bookmarks instead of d3lphin?

---

### Post by MrFSL on 2008-05-31
Hidden folders in your Home folder are supposed to contain YOUR settings for applications... not for roots.

I would take ownership of everything in my home folder. In your case this command:
```
sudo chmod -R cruzer:cruzer /home/cruzer/.kde/share/apps/d3lphin
```
changes the ownership to your user and your user group on the entire contents of the d3lphin folder.

of course you could always do:
```
sudo chmod -R cruzer:cruzer /home/cruzer
```
and reclaim ownership of every folder and file in your home directory if you would prefer.

---

### Post by HunterThomson on 2008-05-31
The "chmod" comand doesn't work on my system. Thanks to your knowledge on who should own the home folder I used these command's form my ever so useful "Linux Phrasebook":

chgrp -R cruzer /home/cruzer

and

chown -R cruzer:cruzer /home/cruzer

I still have no clue how the ownership got changed:confused:

Maybe I am not the only one who owns my box:lolflag:

---

### Post by MrFSL on 2008-05-31
if you ran an application using sudo ... odds are that this is how root got ownership.

Furthermore - 
chown -R - means change ownership recursively 
cruzer:cruzer - means to the user cruzer and group cruzer

for this reason chgrp -R is not needed.

---

### Post by HunterThomson on 2008-05-31
> **MrFSL said:**
> if you ran an application using sudo ... odds are that this is how root got ownership.

Furthermore - 
chown -R - means change ownership recursively 
cruzer:cruzer - means to the user cruzer and group cruzer

for this reason chgrp -R is not needed.

I was thinking that... but I found the group command first.... Owe well cruzer is the only user in this group anyway. 

Star for the help:)

Awwwww... There is that command write after the chown.... "chown user:group" changes the owner and the group of the file or directories. "-R" changes the ownership of all the files and directories with in the directory except for hidden files (files that start with a ".")....

---

