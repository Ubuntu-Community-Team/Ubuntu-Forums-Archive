---
title: "permissions"
date: 2008-06-16
forum: General Help
---

### Post by mrmustardman on 2008-06-16
I dislike how I cannot move files among users or play other user's files without being root. I am an administrator, why is it that to do any of this, I need to actually sign into Root to move files or play music from another user. Is there any way to make my account root so I do not have to deal with it?

---

### Post by Mr Chimp on 2008-06-16
Hi, sorry to threadjack a bit but I am having the same problem. I am trying to install Joomla to the /var/www/ folder and I can't access it or any system folders.

Is there a simple way of setting up my user as an "almost root" account. I have tried using chmod and several other ways mentioned on here but to no avail. I do have Ubuntu 8.04 server but don't fancy the lack of GUI.

---

### Post by oldos2er on 2008-06-16
[https://help.ubuntu.com/community/RootSudo?highlight=(rootsudo](https://help.ubuntu.com/community/RootSudo?highlight=(rootsudo))

---

### Post by Mr Chimp on 2008-06-16
> **oldos2er said:**
> [https://help.ubuntu.com/community/RootSudo?highlight=(rootsudo](https://help.ubuntu.com/community/RootSudo?highlight=(rootsudo))

Thanks, I did try this but it didn't seem to work. I logged in as root and changed the privileges of the /Var. Logged back in as me and it worked fine. I know the root account should not be used but needs must.

Arran

---

### Post by cariboo on 2008-06-16
Why not just ask your users for copies of the files you want ot tinker with

Jim

---

### Post by iaculallad on 2008-06-16
Edit the /etc/sudoers file, with your name settings below (Giving you a "root" user account"):

> Your_UserName  ALL=(ALL) ALL

```
sudo visudo
```

---

### Post by nix4me on 2008-06-16
Permissions are what makes Linux secure.  Now it might be a pain sometimes, but there are easy ways to alleviate the inconvenience yet still be secure.

Such as, use groups.  You can add a group called users for instance and add all your user accounts to that group, including yourself.  Then you would have access if the permissions were set right.  There are many ways to accomplish what you need.  Research users and groups and Linux file permissions and I'm sure you will see some possibilities.

---

### Post by mrmustardman on 2008-06-19
well Im the only user, but my first account got all skrewed up from messing around with compiz. I had to make a new account, or else I would have had to re-add all of the panel items. But I wasnt expecting to not be able to play all the music files I had on my old account. I cant seem to get the visudo thing working... I changed the file, but I still cant access the files.

---

### Post by sisco311 on 2008-06-19
> **mrmustardman said:**
> well Im the only user, but my first account got all skrewed up from messing around with compiz. I had to make a new account, or else I would have had to re-add all of the panel items. But I wasnt expecting to not be able to play all the music files I had on my old account. I cant seem to get the visudo thing working... I changed the file, but I still cant access the files.
Don't change the permissions. Change the owner:
```
sudo chown -R $USERNAME. /home/old-home
```[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by sisco311 on 2008-06-19
> **Mr Chimp said:**
> Hi, sorry to threadjack a bit but I am having the same problem. I am trying to install Joomla to the /var/www/ folder and I can't access it or any system folders.

Is there a simple way of setting up my user as an "almost root" account. I have tried using chmod and several other ways mentioned on here but to no avail. I do have Ubuntu 8.04 server but don't fancy the lack of GUI.

You can setup a new location for /var/www in your home folder.
```
mkdir ~/www
``````
sudo nano /etc/apache2/httpd.conf
```add this:
> <VirtualHost *>
  ServerName **ServerNameHere(localhost by default)**
  DocumentRoot /home/**YourHomeFolderHere**/www
</Virtualhost>
Ctrl+o, Enter to save the file, Ctrl+x to exit.
restart apache:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by mrmustardman on 2008-06-20
> **sisco311 said:**
> Don't change the permissions. Change the owner:
```
sudo chown -R $USERNAME. /home/old-home
```[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

this worked! thanks.

---

