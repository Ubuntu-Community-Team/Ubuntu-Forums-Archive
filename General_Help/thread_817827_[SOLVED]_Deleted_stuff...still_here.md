---
title: "[SOLVED] Deleted stuff...still here?"
date: 2008-06-04
forum: General Help
---

### Post by Tibco on 2008-06-04
Hello, i made a backup of my laptop using "simple back up". But the backup turned out to be HUGE, 6.4 GB for my 20gb harddrive, and i couldnt find a way to get rid of it, so i could have the space freed again. So, i probably did something stupid: heres what happend, i used the nautilus (to get admin prevligas) to delete the file. However, the space still isnt freed!!! The file isn't physicanlly there at the backup place, but my comp still shows the same free space as before? what gives?

---

### Post by Aearenda on 2008-06-04
It's in the Garbage bin, in case you want to bring it back!

Right-click on the Garbage Bin icon and choose 'Empty Garbage Bin'.

---

### Post by Rocket2DMn on 2008-06-04
Open a terminal and run
```
gksudo nautilus
```
It should drop you into /root - do CTRL+H to see hidden files and open the .Trash folder.  You can delete the files from there for good.
Otherwise the files can still be in your own trash folder located at /home/<yourusername>/.local/share/Trash

---

### Post by Tibco on 2008-06-04
well. that would certainly make it easy...but the trash can is empty...i even clicked empty garbage, still shows the same about the free space.

---

### Post by Rocket2DMn on 2008-06-04
If the backup you deleted was on another partition, you need to remove it from the Trash folder on that partition.  Go to the mount point in nautilus, like /media/external, and hit CTRL+H.  You will probably see two .Trash folders - .Trash-1000 or .Trash-yourusername (which is for your user name), and another one like .Trash-500 or .Trash-root which is where files go that were deleted by root/superuser.

---

### Post by Tibco on 2008-06-04
> **Rocket2DMn said:**
> Open a terminal and run
```
gksudo nautilus
```
It should drop you into /root - do CTRL+H to see hidden files and open the .Trash folder.  You can delete the files from there for good.
Otherwise the files can still be in your own trash folder located at /home/<yourusername>/.local/share/Trash

OMG i think you might have saved my life! thanks.

---

### Post by Tibco on 2008-06-04
never mind, that didnt go as well as planned. When i do that, my laptop in general becomes slow. Eventually my mouse starts to lag, until it responds no more. I waited like this for 10 minuetes before restarting. Is there any way to do this from the terminal or something?

Also, there is no .trash file, there is a trash can icon on the left pane, and thats what i clicked...

---

### Post by Rocket2DMn on 2008-06-04
Yes, this can be done from the terminal.  First, can you tell me what Trash folder you are in?  Please provide the full path, like
/home/yourusername/.local/share/Trash
or
/root/Trash
or
/media/some_mount_point/.Trash-1000

Also tell me what the name of the file you are trying to delete is.
I will then provide you the correct commands to delete the file(s).

---

### Post by Tibco on 2008-06-04
ok good news i have found where the files are at, but when i click delete, they delete and then 2 seconds later they reappear again... Also, i found this comment on the web:
Just a quick note for anyone using Ubuntu 8.04 Use this in terminal instead.

sudo rm -rf ~/.local/share/Trash/files/*

That should do it.

So i did that but to no avail. Also i followed the path located on there to find the deleted files. They are at /root/.local/share/Trash/files/2008-06-03_20.2.2.00.57.312130.ubulaptop.ful

Also, the path located above is for the folder which contain 6 files which i guess are all backup files

---

### Post by Tibco on 2008-06-04
AHA i did it!!!!

This is what i did. it may be a bit crude, but im a linux nub. i went to the file above the back up, so in this case the /Trash/Files and i deleted the files folder. Then i created a files folder to replace the one i deleted. simple yet effective and did the job :)

---

### Post by Rocket2DMn on 2008-06-04
Yes, that is crude, but it works.  You should have just deleted the files out of the Files folder, that would have permanently removed them.  The purpose of using "gksudo nautilus" was to give you a file browser session with superuser privileges to delete files from the trash that it may have given you Permission Denied with otherwise.
Glad you got it working.

---

