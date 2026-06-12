---
title: "Permissions :("
date: 2007-09-21
forum: General Help
---

### Post by iamBevan on 2007-09-21
Once I have enter my username and password upon startup I get the following message: 

"User's $HOME/.dmrc file is being ignored, preventing default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

Would someone be willing to give me some extremely basic help with fixing this?

Also, i have downloaded nzb's that are locked and I am unable to delete - Help with this would be much appreciated too.

Thanks in advance

- Kev

---

### Post by ifconfig on 2007-09-21
Hi Kev.

Run the following commands in a terminal,
'sudo chown YourUsername ~/.dmrc'
add '-R' after chown if it's a directory. This will make YourUsername being the owner of the file/directory.

Then,
'chmod 644 ~/.dmrc'
add '-R' after chmod if it's a directory.
You might need to add 'sudo' infront of chmod, depending on your current permissions. This will make you able to read and write to the file/directory.

Good Luck!

// Magnus

---

### Post by iamBevan on 2007-09-21
Sorry, but what do you mean by "~" - I have only had Ubuntu for several days sorry.

---

### Post by ifconfig on 2007-09-21
> **iamBevan said:**
> Sorry, but what do you mean by "~" - I have only had Ubuntu for several days sorry.

"~" is the same as "/home/YourUsername". Less to type. :)
Example, you have a file somewhere and types,
'cp file ~'
then it's the sames as typing,
'cp file /home/YourUsername'.

---

### Post by JKyleOKC on 2007-09-21
That's the standard way to refer to your $HOME directory. As always in any Linux system though, there are other ways to do it.

If you would be more comfortable with the graphic interface, you can go to your home directory by clicking or double-clicking its icon in the top panel, then right-click on its window background and check the box to show hidden files. This will let you see the ".dmrc" file. Right-click on it and choose "Properties" from the context menu, then the "Permissions" tab of the properties display. You will probably see that you have read and write permission but the group has none and others have none. Use the combo-box arrows on group to see the possible choices and select read-only, then do the same for "others" and you will have cured the problem once you OK out of all the windows.

I had that same problem on my first install but it has not happened on any of the three subsequent installs I've done on other boxes. Apparently the install program does not always set this up correctly.

---

### Post by iamBevan on 2007-09-21
I have done exactly as you both have said, however, i still get the error at start up.

(My .dmrc now has a picture of a lock on it, and all permissions are read only)

The problem with deleting those files is no longer an issue though.


This has all happened since I installed "Hellanzb" if that helps atall.

---

### Post by Trzone on 2007-09-21
I just had the same error after i changed the folder permissions of my home folder

Go to places home folder
and right click the white space click properties
then go to permissions
make sure that you can create and delete files under folder access
groups and others should access files as well
I got the same exact error
hopefully this'll help!

---

### Post by iamBevan on 2007-09-21
> **Trzone said:**
> I just had the same error after i changed the folder permissions of my home folder

Go to places home folder
and right click the white space click properties
then go to permissions
make sure that you can create and delete files under folder access
groups and others should access files as well
I got the same exact error
hopefully this'll help!

I already have those settings.

---

### Post by eph1973 on 2007-09-21
In your terminal, you could type this (or just cut and paste it):

```
chmod 0644 $HOME/.dmrc
```then:

```
chmod 0770 $HOME
```Since you own (or at least you should own) both your $HOME (shell variable name for /home/<username>) and your $HOME/.drmc folder/file, then you should not need to sudo.  That should straighten out that error message.  The previously posted suggestions should work also, I just posted this like this so you could cut and paste into your terminal, if you so desired.

---

### Post by iamBevan on 2007-09-21
Copied it, and pasted it - still get the error :(

---

### Post by eph1973 on 2007-09-21
ok, enter this in your terminal, and paste the results back in your next post:
```
ls -l $HOME/.dmrc
```then this:

```
ls -l /home
```For the first one, the first little bit should look something like this:

```
-rw-r--r--  1  <YourUserName> <YourUserName> ...
```and your home directory in /home should look something like this:

```
drwxrwx--- <SomeNumber>  <YourUserName> <YourUserName> ...
```In the above two examples, "..." is meant to mean the rest of the line, and anything in < > is not meant to be taken literally.

---

### Post by iamBevan on 2007-09-22
```
ls -l $HOME/.dmrc
```-rw-r--r-- 1 bevan bevan 26 2007-09-20 22:30 /home/bevan/.dmrc

```
ls -l /home
```total 8
drwxrwx--- 25 bevan bevan 4096 2007-09-22 02:07 bevan
drwxrwxrwx  7 root  root  4096 2007-09-22 11:09 bevannzb

---

### Post by klytu on 2007-09-22
> **iamBevan said:**
> ```
ls -l $HOME/.dmrc
```-rw-r--r-- 1 bevan bevan 26 2007-09-20 22:30 /home/bevan/.dmrc

```
ls -l /home
```total 8
drwxrwx--- 25 bevan bevan 4096 2007-09-22 02:07 bevan
drwxrwxrwx  7 root  root  4096 2007-09-22 11:09 bevannzb

Try: ```
chmod 755 $HOME
``` 

From the error message you posted in your first post, everything else looks OK except the permissions on your $HOME

---

### Post by iamBevan on 2007-09-22
Hehe - works fine now, thanks guys and sorry for my noobness.

---

