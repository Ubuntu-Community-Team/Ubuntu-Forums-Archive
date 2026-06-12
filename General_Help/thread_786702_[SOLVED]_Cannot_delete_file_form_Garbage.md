---
title: "[SOLVED] Cannot delete file form Garbage"
date: 2008-05-08
forum: General Help
---

### Post by Piccy on 2008-05-08
Hi

First post, so thanks for having me

Running 32bit Hardy amd getting an error when I try do delete a file from the garbage bin

Error while deleting.
There was an error deleting file.XXX
Error removing file: Permission denied

This a file in a directory from a DVD which I copied down do my HDD (on the desktop) and then deleted. The problem is its a 3gb directory and I only have a 30gb drive

It was copied down under my user name but wont let me delete

BTW
I do not have a .Trash directory in my home drive. Is that normal?

---

### Post by perlluver on 2008-05-08
> **Piccy said:**
> Hi

First post, so thanks for having me

Running 32bit Hardy amd getting an error when I try do delete a file from the garbage bin

Error while deleting.
There was an error deleting file.XXX
Error removing file: Permission denied

This a file in a directory from a DVD which I copied down do my HDD (on the desktop) and then deleted. The problem is its a 3gb directory and I only have a 30gb drive

It was copied down under my user name but wont let me delete

BTW
I do not have a .Trash directory in my home drive. Is that normal?

The trash folder is located at ./local/share/Trash/files/.  Most likely that folder you copied over locked when it was moved.  To delete press Alt+F2 and type gksu nautilus in that box that pops up, then press control+h in your home directory and you will find ./local/.

---

### Post by akhil.t on 2008-05-31
I have a similar problem. I tried to copy the .dat files in a VCD and ended up with two empty locked folders on the desktop that refuse to go. I tried the suggestion above but could not remove them. I am on Hardy Heron.

Any help?

---

### Post by jocko on 2008-05-31
> **akhil.t said:**
> I have a similar problem. I tried to copy the .dat files in a VCD and ended up with two empty locked folders on the desktop that refuse to go. I tried the suggestion above but could not remove them. I am on Hardy Heron.

Any help?

CD and DVD file systems are read only file systems, so if you copy a file from a cd or dvd it will usually still be read only.
To fix it, right click the file or folder, go to the permissions tab and make sure it's set to "read and write" and that you are the owner.
Another way could be:
```
 sudo rm -rf [COLOR=Blue]/path/to/folder/file[/COLOR]
``` (But be very careful with this command, make sure you type the correct and complete path to a file you know it's safe to remove)

---

### Post by 6205 on 2008-05-31
You can always run Nautilus like root typing into terminal [COLOR="DarkRed"]sudo nautilus[/COLOR] and then navigate to your .trash folder into your home directory or desktop folder and delete any files you want...

---

### Post by akhil.t on 2008-05-31
> **jocko said:**
> CD and DVD file systems are read only file systems, so if you copy a file from a cd or dvd it will usually still be read only.
To fix it, right click the file or folder, go to the permissions tab and make sure it's set to "read and write" and that you are the owner.
Thanks Jocko. I managed to delete them using the following command: 

sudo rm -r ~/Desktop/mpegav

Found it [here]("http://ubuntuforums.org/showpost.php?p=3906980&postcount=2")

Cheers!

---

### Post by neur0 on 2008-05-31
Open Applications > Accessories > Terminal
Type:
```
cd ~/Desktop
```

Then make sure those folders are there
```
ls -l
```

If you see the folders you want to delete in the list do
```
sudo rm -r <name_of_the_folder>
```
Enter your log-in password, and repeat last step for the other folder

Make SURE the name of the folder you want to delete is correct

To delete undeletable files from flash do the same as above, except in the first step do
```
cd ~/.local/share/Trash/files
```

---

### Post by pro003 on 2008-08-07
> **perlluver said:**
> The trash folder is located at ./local/share/Trash/files/.  Most likely that folder you copied over locked when it was moved.  To delete press Alt+F2 and type gksu nautilus in that box that pops up, then press control+h in your home directory and you will find ./local/.

**[COLOR="Navy"][SIZE="6"]this one definitely helped![/SIZE][/COLOR]**

---

### Post by ford074 on 2008-08-14
+1 on the "Thank You" this helped big time!

---

### Post by KhanTG on 2008-08-16
> **6205 said:**
> You can always run Nautilus like root typing into terminal [COLOR="DarkRed"]sudo nautilus[/COLOR] and then navigate to your .trash folder into your home directory or desktop folder and delete any files you want...

I had a similar problem when removing a "user" from my system.  Thanks for the "sudo nautilus" command, I didn't have this information previously and it works for ANY locked file. Thanks again!

---

