---
title: "[SOLVED] Changing permissions doesn't change files in folder"
date: 2007-07-09
forum: General Help
---

### Post by Programmerer on 2007-07-09
Let's say I have installed a program as root, and when I use it is it creating a folder in my home folder with many underfolders and files in it. The permissions for the folder is root, but when I change them to "myname" is all the files and folders in it still root. Nothing happens when I click the "Apply permissions to enclosed files" button either.

Anybody have a solution for this, because I don't want to change permission for every single folder/file.

Ps: I have upgraded to the beta version 7.10.

---

### Post by Waappu on 2007-07-09
Hi

Use terminal command to change owner of folders and files ```
chown -R user_name ~/folder_name
```
Function -R will change all files and sub folders.
Replace "user_name" with your user and "folder_name" at folder you want to change

Edit:
Link to chown guide
[http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)
[http://www.computerhope.com/unix/uchown.htm](http://www.computerhope.com/unix/uchown.htm)

---

### Post by Programmerer on 2007-07-09
Thanks:)


Note: I had to run the command as root, because I hadn't access to change permissions from my account:wink:

---

