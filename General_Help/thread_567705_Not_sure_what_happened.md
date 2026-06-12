---
title: "Not sure what happened"
date: 2007-10-04
forum: General Help
---

### Post by Mastrchief on 2007-10-04
Unsolved:

When I try to open certain pages or download semi large files, my entire computer freezes up.

Solved:

Ok, so I used wubi installer earlier today to install kubuntu. Everything works fine, but I go back to windows too delete things for space. I try to go back to kubuntu and I get an error which is something about alternate installer not found, please run the installer again. So I log back into windows and run the installer. It tells me I need to uninstall it, so I do, but I make the backups it asks me if I want to make. My problem now is Wubi won't uninstall and now I am getting errors saying system.virtual.disk is corrupt and I can't do ANYTHING with it. Does anyone know how I can get wubi uninstalled so I can reinstall it, system.virtual.disk deleted, and everything running fine again?

The internet was working (sort of) the first time I installed wubi, but then I had other problems and had to reinstall it. Now I had the internet work one time and have the settings correct, yet it doesn't connect. Ago has given me a solution, but I am having problems writing to the folder, as it will no allow me to, no matter what I try.

---

### Post by ago on 2007-10-05
Chances are you might have deleted some file you should have not. 

To uninstall wubi manually see the WubiGuide, essentially remove the wubi folder, edit boot.ini to remove the wubi line and remove the windows key.

---

### Post by Mastrchief on 2007-10-05
Sorry for not keeping this thread up to date. I have fixed my earlier problem using microsofts help ([http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)), now I only get a few minor problems when I boot onto kubuntu. First is the internet seems to go out at times, and I have it set up correctly. Second is when set the computer to shut off, it just idles with a blank screen and I have to manually hold the button down on my computer.

---

### Post by Mastrchief on 2007-10-06
Would anyone care to elaborate my internet problems?

---

### Post by ago on 2007-10-06
See if you have a file called /etc/init.d/fixsendsigs. That should be symlinked into /etc/rc6.d and /etc/rc0.d

---

### Post by Mastrchief on 2007-10-06
Symlinked?

---

### Post by Mastrchief on 2007-10-06
Although I don't know what symlink is, I have found fixsendsigs and found where to put them, I just need to know how to set the folder permissions to write so that I can get them in.

---

### Post by eph1973 on 2007-10-06
symlink is a symbolic link (vice a hard link), which if you really want to know what's what, there is info on that [here]("http://en.wikipedia.org/wiki/Symbolic_link").

If you are really sure you want to write to that file or directory, you could change the permissions by typing ```
sudo chmod u+w (target)
```  You might consider restoring the permissions after you are done by typing```
sudo chmod u-w (target)
```

Of course, those commands go in the terminal.

To my knowledge, you can't have a symlink pointing to more than one file or directory (of course a file or directory can have multiple links pointing to it).

---

### Post by Mastrchief on 2007-10-07
The command didn't seem to work. I even tried setting my user's primary group as root.

---

### Post by eph1973 on 2007-10-08
It would be helpful to diagnose what you are trying to do if you provided some information.  First off, as to the directory or file you are trying to write to, use the command:
```
ls -l (/path/to/file/or/directory)
```the "-l (that's the lower case letter "L", not the number "1") means to show the long form of the directory listing.  The first part of that listing shows the permissions for the file or directory.  Also, note that if you are trying to display the permissions for the directory itself, it would be better to use:
```
ls -l (path) | grep (directory name)
```Where the path is the path to the directory, without the name of the directory, but you would put the name of the directory after the grep.  So in the case of you want to check the permissions of the directory /etc/init.d you would use ```
ls -l /etc | grep init.d
```For each case, post both the command you entered, and the results of the command.  And try to describe what exactly you are trying to do within the directory you are working in.  If you see something like this:
```
drwxr-xr-x  (number) root   root      4096 (some date) (some time) init.d
```(for the case of the directory /etc/init.d), and you see any w's in that first part of the listing, then your issue isn't permissions to the file or directory, it lies elsewhere.

---

### Post by Mastrchief on 2007-10-08
I logged in to kubuntu just a little while ago to try what eph1973 suggested, and surprisingly, I had internet. Now my only problem is why my computer freezes during downloads.

---

