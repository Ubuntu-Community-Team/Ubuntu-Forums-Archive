---
title: "Can't change directory name, copy to it, or from, USB drive."
date: 2015-10-15
forum: General Help
---

### Post by l6griffin on 2015-10-15
I have a HP SimpleSave 320 gb usb drive I want to backup files to. When 15.04 comes up it creates 2 directories in media, HPLAUNCHER and HP SimpleSave. A filer manager will find the directories and the files in them. File manager will copy to and from the directories. Unfortunately I want to copy home directory for backup and all I get with file manager is permission denied. If I try from the command line the HP SimpleSave does not seem to be recognized. If I try and change the directory name the space in the name seems to get in the way. There must be a work around.

---

### Post by grahammechanical on 2015-10-15
What home folder? There are two. The file manager will show us a home folder that is actually / and is owned by root. Open that folder and you will see another folder with your user name. That is /home and that is owned by ME. Which is you the user.

Right click on folders and select Properties and then Permissions tab to see who owns folders and what access groups and users have.

Regards.

---

### Post by l6griffin on 2015-10-15
The Directory is in /media/larry/HP SimpleSave, the files I want to backup are /home/larry/*.*. What happens when I try to copy from the command line file into HP SimpleSave is;
 larry@larry-HP-2000-4ID2:/media/larry/hp$ cp -r /home/*.* /media/larry/HP SimpleSave
cp: target &#8216;SimpleSave&#8217; is not a directory

larry@larry-HP-2000-4ID2:~$ ls /media/larry/HP SimpleSave
ls: cannot access /media/larry/HP: No such file or directory
ls: cannot access SimpleSave: No such file or directory
larry@larry-HP-2000-4ID2:~$ ls /media/larry/HP
ls: cannot access /media/larry/HP: No such file or directory

The directory is set r/w but that shouldn't be an issue using sudo from the cmd line.

---

### Post by ajgreeny on 2015-10-15
The space in the folder name **HP SimpleSave** is the problem.

Either use an escape character, ie a backslash, **HP\ SimpleSave** or enclose the pathway in quotation marks, **"/media/larry/HP SimpleSave"**

In future it is going to make life a lot easier to avoid spaces in file or folder names; replace the space with a dash or underscore.  Also worth using autocomplete in terminal to fill folder and file names, so start typing the pathway with first character or two and hit tab.  If there is only one name option available it will fill it in for you; if more than one is available, hit tab twice and the list of possible entries will be shown.

---

### Post by yancek on 2015-10-15
> cp -r /home/*.* /media/larry/HP SimpleSave

Doing this from a terminal will require quotes due to the space between HP and SimpleSave as it is seen as two different directories so try:

> cp -r /home/*.* "/media/larry/HP SimpleSave/"

If that fails with a permissions error, precede the command with sudo.

---

### Post by l6griffin on 2015-10-15
Thanks for jogging my memory I couldn't see the forest for the trees. I replaced the space between with a wildcard such as HP*SimpleSave.

Best Regards, Larry

---

