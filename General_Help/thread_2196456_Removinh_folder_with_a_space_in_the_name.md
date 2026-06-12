---
title: "Removinh folder with a space in the name"
date: 2013-12-29
forum: General Help
---

### Post by ibates on 2013-12-29
Inadvertently, I have created a folder name with a space in the name.  (Ubuntu 12.04 LTS updated).

I now wish to remove that folder and its contents (permissions for asministrator only), but rm does now recognise the "xxxxx yyyyy" folder name.  It goes into cyber confiusion attempting to find the folder with the part of the name before the space.

So I thought, cleverly, that I would simply rename the folder with no space.  But when executing the command line instruction to do that, it once again goes off into cyber fairyland looking for the folder with the name of the part before the space.

Can't rename; can't remove.  Looks like I am stuck with that waste of disk space forever.  Unless .....

Any thoughts?

---

### Post by Toz on 2013-12-29
If the folder's permissions are set such that the administrator (root) is the owner and no-one else has [s]read/write permissions[/s] access to remove the directory, then to delete the folder you will need to use the sudo command:
```
sudo rm "xxxxx yyyyy"
```
Make sure you are sitting in the correct directory when you enter the command or you'll have to specify the complete path.

More info about sudo [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by steeldriver on 2013-12-29
You can escape the space with a backslash, or enclose the whole name in quotes (either single or double quotes will do)

```

m -rf xxxxx\ yyyyy

rm -rf "xxxxx yyyyy"

rm -rf 'xxxxx yyyyy'

```

FYI 'tab completion' is very useful for stuff like this, it will fill in the escape characters provided you type enough of the name to identify it uniquely --> [http://tldp.org/LDP/abs/html/tabexpansion.html](http://tldp.org/LDP/abs/html/tabexpansion.html)

---

### Post by Iowan on 2013-12-29
Have you tried surrounding the name with single or double quotes?

DRAT - out typed again... and you even got the escaped version!

---

### Post by sisco311 on 2013-12-29
> **Toz said:**
> If the folder's permissions are set such that the administrator (root) is the owner and no-one else has read/write permissions, then to delete the folder you will need to use the sudo command:
 

Nope. That's not how Unix/Linux file permissions are working.   

You don't have to be the owner of a file (directory/regular file/link/pipe/socket/device...) or have write permission on it to rename or delete it!  You only need write permission on the directory that contains the file.


[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by Toz on 2013-12-29
> **sisco311 said:**
> Nope. That's not how Unix/Linux file permissions are working.   

You don't have to be the owner of a file (directory/regular file/link/pipe/socket/device...) or have write permission on it to rename or delete it!  You only need write permission on the directory that contains the file.


[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

You are correct, I didn't type that out right. My mind and fingers are thinking different things today. I'll edit my post.

---

