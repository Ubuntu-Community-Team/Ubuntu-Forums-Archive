---
title: "Cannot move file to trash from /var/www"
date: 2007-11-09
forum: General Help
---

### Post by abrichr on 2007-11-09
I recently switched from Feisty to Gutsy on my laptop.  I use this machine for web development, but not hosting.  I installed the LAMP package, and took ownership of /var/www, and even chmod 777'd it.  Still, when I cannot move files from this directory to the trash from nautilus:

"Cannot move file to trash, do you want to delete immediately?"

from the command line, it just deletes it immediately.

The folder permissions are drwxrwxrwx, but I cant' seem to go any further with file permissions than -rw-rw-rw-.

I'm could always resort to development in a public_html in my home directory, but I'm curious as to why this is happening.  Any help would be appreciated.

---

### Post by amitst on 2007-11-09
I guess you haven't assigned a recursive ownership to the /var/www  folder. You need to do "chown -R <user>:<pass> /var/www" for this. Also the 777 permissions need to be give recursively "chmod -R 777 /var/www".

Hope this helps

---

### Post by abrichr on 2007-11-09
aye, i've done this, using the octal permissions as well as rwx, still no go.

---

### Post by djrobthaman on 2007-11-09
I don't see why that didn't work.  But why not view the folder in nautilus as super user and then change the permissions using the gui there.  That seems to work for me whenever I need to do something like that.

Hit Alt+F2
Type "gksudo nautilus" in the text box
Then nautilus will show up and anything you do using that window is law as far as ubuntu is concerned because you'll be administrator

---

### Post by abrichr on 2007-11-09
that didn't work either.

/var/www has owner, group, and others set to create and delete files.  the owner and group are both my user name.  file access, however, is set to "---" for all three, and when i change it tp "read and write", it's back to "---" after i close the dialogue and reopen it.

i've also clicked on "apply permissions to enclosed files",

if i right-click a file in /var/www, the owner and group are both me, and owner, group, and others have permissions set to read and write.

but the file permissions are still the same.

---

### Post by djrobthaman on 2007-11-09
What about execute permissions?  Are those set?

---

### Post by abrichr on 2007-11-09
no.  i don't want to execute anything here.  there's just php and js includes, as well as some images.

edit; i tried setting them just for giggles, but it still won't send to the recycle bin.

---

### Post by djrobthaman on 2007-11-09
I get you, but I figure it can't hurt to see if that's the problem.  If not I've got no clue what else you could do.  Maybe just change your web root folder.

---

### Post by chrisccoulson on 2007-11-09
Is /var/www on the root filesystem, and on a different filesystem to /home? If so, when you delete a file using Nautilus, it will try to create '.Trash-<*your_user_name*>' on the root filesystem (if there isn't already one), to put the deleted files in to. Because you don't have permissions to write to the root filesystem ('/'), Nautilus will fail.

Try creating a hidden '.Trash-<*your_user_name*>' on your root filesystem '/', or on whatever filesystem /var/www is on (if it's on a different filesystem). Make sure you chown the folder to yourself and give yourself write permissions to it. Nautilus will then behave as you expect.

---

### Post by geirha on 2007-11-09
```
df $HOME /var/www
``` is a quick way of determining what partitions these directories are located in

---

### Post by abrichr on 2007-11-21
> **chrisccoulson said:**
> Is /var/www on the root filesystem, and on a different filesystem to /home? If so, when you delete a file using Nautilus, it will try to create '.Trash-<*your_user_name*>' on the root filesystem (if there isn't already one), to put the deleted files in to. Because you don't have permissions to write to the root filesystem ('/'), Nautilus will fail.

Try creating a hidden '.Trash-<*your_user_name*>' on your root filesystem '/', or on whatever filesystem /var/www is on (if it's on a different filesystem). Make sure you chown the folder to yourself and give yourself write permissions to it. Nautilus will then behave as you expect.

You got it: /var/www is on the root filesystem, and /home is on a different partition.  I did what you suggested:

```
$ sudo mkdir /.Trash-<myusername>
$ sudo chown -R <myusername>:<myusername> /.Trash-<myusername>
$ sudo chmod -R 755 /.Trash-<myusername>
```

The permissions on the folder are drwxr-xr-x, and I am the owner, but I am still getting the error message in Nautilus.

If this helps:

```
$ df $HOME /var/www
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             60476068  11366432  46652016  20% /home
/dev/sda1             20184644   5563528  13595772  30% /
```

Any other ideas?

---

