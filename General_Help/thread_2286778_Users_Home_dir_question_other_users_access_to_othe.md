---
title: "Users Home dir question other users access to others home dir"
date: 2015-07-14
forum: General Help
---

### Post by phs2004 on 2015-07-14
Hi, When I add user to my server they can access other users home dir and download files. How can I change it so day can see files but dont download whit out chroot them in home dir? 

Chmod 644? Or wich one chmod 700? Get som access error if using does. 

Using chroot now for users but i want one user to get access to /media folder to or maby do a link in fstab mount it to 

```
/media/ /home/<user>/media auto bind
``` Tryed this but dont work (edit now it works forgot to mkdir media in users home dir)


Using Ubuntu Server 14.04

Tanks!

---

### Post by sudodus on 2015-07-14
If the directory has read and execute permissions for 'others' the files can be listed alias 'seen'.

If the files lack permissions (read, write, execute) for 'others', they cannot do anything with them (not read, not copy etc).

---

### Post by phs2004 on 2015-07-14
And how to sett the right permissions? Maildir has chmod 700 and they cant access it luckely. Have tested alot of chmod options.

Edit ```
chmod 0750 /home/<user> 
```seems to work

---

### Post by sudodus on 2015-07-14
***Warning:*** This can be dangerous - done in the wrong place, the following command can destroy your Ubuntu system. ***Backup*** your system before doing it.

Are different users in the same group or in different groups? Keep the users from each other's groups and turn off permissions for 'others'.

Do this only in the ***home directory*** of each user, remove the read, write, execute permissions for 'others'.

```
sudo find . -type f -exec chmod o-rwx {} \;
```

It is very important to keep the permissions for the owner ('user'), otherwise the user's system will be borked.

And do *not* do this with any files or directories that belong to the linux system.

With this method new files will be (or at least might be) given such permissions, that they can be not only seen but also readable (and possible to copy) by other users.

-o-

I think it would be easier and safer too, to make it impossible to list the files too (by changing the access for 'others' of each user's home directory recursively). This way new files will also be impossible too see.

```
sudo chmod -R o-rwx /home/*
```

-o-

Finally, ***test that it really works as intended*** before you start using it with real users !!!

---

### Post by nerdtron on 2015-07-14
I don't think you need to change the permissions on all files/folders inside each of the home directories.
You just need to set the parent folder (e.i. /home/user1) to be rwx for the user that owns it.

For example, user1 with home directory /home/user1. You'll just need the following so that other users can't access his home directory.
```
chown user1.user1 /home/user1
chmod 700 /home/user1 
```

Now only user1 can go inside the /home/user1 folder. Also, you don't have to worry for the permissions inside the /home/user1 folder since all files/folders created will be owned by user1 (because he's the only one who can access the folder, unless you are root of course).

---

### Post by sudodus on 2015-07-14
Thanks nerdtron, that makes it easier :-)

(I thought it was necessary to change the permissions of the whole directory tree with files.)

---

### Post by phs2004 on 2015-07-15
Ok most users have chmod 700 and my own has to be 750. chmod 700 makes my subomain stop working. 

and added this to adduser.conf in /etc

```
# If DIR_MODE is set, directories will be created with the specified# mode. Otherwise the default mode 0755 will be used.
DIR_MODE=0700

```

---

### Post by sudodus on 2015-07-15
Have you tested and all user accounts work as you want them to work? In that case please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

---

### Post by phs2004 on 2015-07-15
Yes everying works great now.  Forgot about the SOLVED, fixed :)

---

