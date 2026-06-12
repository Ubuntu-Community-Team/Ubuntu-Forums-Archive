---
title: "Please Help! Iv Locked Myself Out Of A Folder!"
date: 2006-11-03
forum: General Help
---

### Post by Sheepish on 2006-11-03
I know, i know this sounds stupid but i was trying to enable permissions to USR/SHARE/PIXMAPS  ,following some advice elsewhere on the site, so i could add some icons, but it all went pearshaped. i wanted to give myself all permissions to this folder, but now it says that i dont have sufficient privilages. please help. im using gnome if its any help

---

### Post by nikhilk on 2006-11-03
I guess the owner of "/usr/share/pixmaps" should be root (cant check now, I am on a window$ machine). Just see what are the current attributes of that folder using
```
ls -l /usr/share/pixmaps
```

---

### Post by Sheepish on 2006-11-03
thanks for replying, but thats the point, it says access denied!

---

### Post by Roobert on 2006-11-03
If you're trying to move files into the PIXMAPS folder, try 
```
sudo chmod -R 755 /usr/share/pixmaps
```

Even though root is the owner, and the group is root as well, you'll have read permissions enabled.

---

### Post by Sheepish on 2006-11-03
thanks for replying, but thats the point, it says access denied!

---

### Post by Sheepish on 2006-11-03
hmm sorry ,it double posted for some reason

---

### Post by Roobert on 2006-11-03
If the permissions are set up so that only root has read,write,execute (i.e., the permissions of the folder look like this: ```
drwx------
```, then no, you won't be able to do 'ls -l'  - you'll get *permission denied*

Try ```
sudo ls -l /usr/share
``` and post the permissions listed for folder pixmaps.

---

### Post by Sheepish on 2006-11-03
thanks a lot roobert that works :) will this work for any file?
cheers

---

### Post by dbott67 on 2006-11-03
The owner should be root:root (according to my computer).  Try **sudo su** at the command prompt and then cd to /usr/share/pixmaps to see if you can access.

If you've buggered up the ownership, then try this:
```
chown -R root:root /usr/share/pixmaps
```

Type exit a couple of times to get out of **sudo su** (i.e. root mode).

Then use Rooberts suggestion of:
```
sudo chmod -R 755 /usr/share/pixmaps
```

---

### Post by Roobert on 2006-11-03
You can change the permissions of any file or folder, even if you or your group aren't the owner, by using the ***chmod*** command. For folders and files owned by root (basically, everything *outside* of your /home directory), you can change permissions so that you have read access, no write access, and permission to execute programs by using the chmod octal code '755', like so:

```
sudo chmod 755 *filename*
```

Or, change permissions of a directory, sub-directories, and all files inside:

```
chmod -R 755 foldername
```

The -R flag means change the permissions *recursively*; that is, go through every directory and subdirectory of *foldername* and apply the same permissions listed as the argument to the chmod command.

**CAVEAT:** Don't ever chmod of any file or folder to 666 or 777; these two permissions allow others read/write access (for code '666') and read/write/execute access(for '777') over your files; consequently, these two codes are considered security weaknesses.

---

