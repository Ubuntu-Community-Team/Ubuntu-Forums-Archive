---
title: "Truecrypt Permissions Problem"
date: 2016-05-28
forum: General Help
---

### Post by carlmacgentey on 2016-05-28
I have installed Truecrypt on Ubuntu 16.04 LTS from Stefan Sundin's ppa with no problems. I can mount the volume with no problems. Unfortunately, I cannot move files or folders into the container. I keep getting error messages about permissions issues.
I tried to run "sudo visudo" as described by Mister Sundin just below.

 "To automatically grant TrueCrypt root privileges to mount volumes, run `sudo visudo` and add this to the end of the file:
your_username ALL=(ALL) NOPASSWD:/usr/bin/truecrypt" (omit the quotes)

I am not able to add the required line of code to the end of the file. I can add the line of code to the beginning of the file. Unfortunately. I cannot figure out how to save the file with the required changes. Advice? Suggestions?

---

### Post by SuperFreak on 2016-05-28
It is dangerous to change ownership of any system directory but if this is a data partition use

```
sudo chown -v -R user:user /media/partition/
```

where user is the user you want to have ownership and /media/partition/ is the directory of the partition

Permissions should be modifiable from Nautilus by left clicking on directory

---

### Post by Dennis N on 2016-05-28
> I can mount the volume with no problems. Unfortunately, I cannot move files or folders into the container. I keep getting error messages about permissions issues.

My comments: You can't add anything directly to the container. Truecrypt mounts the decrypted container as a folder under /media (probably now it's under /media/<username>). That is what you open and add files to. 

Example I took from Ubuntu 10.04 (obsolete, but the only instance of truecrypt I have):

coins and stamps are two truecrypt containers stored in the ~/hobbies folder:
```
dmn@Roxanne:~/hobbies$ ls -l
total 180224
-rw------- 1 dmn dmn 67108864 2016-05-28 09:43 coins
-rw------- 1 dmn dmn 33554432 2011-07-11 07:31 stamps

```
Start truecrypt. Select a slot from the list in the main window (let's say I choose 5). Then: Select the container file to use. Provide the password to the container. Provide your user password. 
Truecrypt then mounts the decrypted container at /media/truecrypt5*. A shortcut to it is added for truecrypt5 to the desktop as well for quick access. Open and browse with file manager. You should have all needed permissions (as shown here) to modify the contents.

```
dmn@Roxanne: cd /media
dmn@Roxanne:/media$ ls -l
total 1
drwxr-xr-x 17 dmn dmn 1024 2013-09-19 11:15 truecrypt5
```

On close, unmount and exit - all the stuff in this folder is again encrypted and saved to the container file, and the folder disappears.

*on a newer system, probably at /media/<username>

---

