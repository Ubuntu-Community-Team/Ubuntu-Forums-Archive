---
title: "How to delete downloaded torrents?"
date: 2014-01-09
forum: General Help
---

### Post by MasterShadow on 2014-01-09
I'm using ubuntu 12.04, and I used transmission to download. The file is a little over 3gigs, and I can't delete it. When I right click it, the option that says "move to trash" is grey. When I try to move it to the trash, it'll say permission denied. It's taking up a lot of space, and I really need to delete it.   Also, a warning keeps popping up saying I have low disk space, but I don't. At least, I shouldn't. Disk analyzer says I have 15 gigs, and a few commands in terminal say I do too. I'm not sure what the problem is.

---

### Post by carl4926 on 2014-01-09
Enable delete in the context menu or hold down SHIFT and delete it

---

### Post by MasterShadow on 2014-01-09
Where is the context menu?

---

### Post by jeanjd63 on 2014-01-09
Hello

Can you do a :
**sudo  ls  -l   *Torrentfile***

---

### Post by MasterShadow on 2014-01-09
I'll type the torrent file name, but it says no such file, or directory

---

### Post by jeanjd63 on 2014-01-09
You have to change directory before this command :
[B]cd  *directory_where_are_downloaded_files*
[/B]and then 
**sudo  ls  -l  *Torrentfile***

---

### Post by carl4926 on 2014-01-09
> **MasterShadow said:**
> Where is the context menu?
IIRC Transmission - when you select delete in the application itself, even when you choose delete and completely remove, it still passes a copy of the delete to the trash

If you delete the downloaded file using your file browser - which is where the context menu comes in - The context menu is the list of option you see when you right click something. If delete isn't there you can enable it in the preferences or select the file and hold SHIFT and press delete on the keyboard.

Deleting a file like this will break the torrent in Transmission, but you should now be able to delete the torrent because all that remains is the torrent

---

### Post by MasterShadow on 2014-01-09
> **carl4926 said:**
> IIRC Transmission - when you select delete in the application itself, even when you choose delete and completely remove, it still passes a copy of the delete to the trash  If you delete the downloaded file using your file browser - which is where the context menu comes in - The context menu is the list of option you see when you right click something. If delete isn't there you can enable it in the preferences or select the file and hold SHIFT and press delete on the keyboard.  Deleting a file like this will break the torrent in Transmission, but you should now be able to delete the torrent because all that remains is the torrent  Now I can press Move to trash, but it'll say permission denied. It has the iso, and a few other files.

---

### Post by carl4926 on 2014-01-09
So you deleted the downloaded file or not?
Now you can't clear transmission?

If you don't mind loosing everything in transmission you could delete the hidden transmission config folders

---

### Post by MasterShadow on 2014-01-09
> **carl4926 said:**
> So you deleted the downloaded file or not? Now you can't clear transmission?  If you don't mind loosing everything in transmission you could delete the hidden transmission config folders  I can't delete it at all. It keeps on saying "Unable to trash file: Permission denied" whenever I try to delete the file with the ISO, and other files.

---

### Post by carl4926 on 2014-01-09
> **MasterShadow said:**
> I can't delete it at all. It keeps on saying "Unable to trash file: Permission denied" whenever I try to delete the file with the ISO, and other files.

I think you are struggling with some basic understanding

Please explain if you have tried deleting via the file browser. Please make sure transmission is closed too.

---

### Post by MasterShadow on 2014-01-09
> **jeanjd63 said:**
> You have to change directory before this command : **cd  *directory_where_are_downloaded_files* **and then  **sudo  ls  -l  *Torrentfile***  When I put in that command it gives ```
total 20 drwxrwxr-x 3 username        debian-transmission 4096 Nov 16  2006 broadcom-wl-4.80.53.0 drwxrwxr-x 2 username        debian-transmission 4096 Jan  8 15:12 Completed drwxr-xr-x 4 debian-transmission debian-transmission 4096 Jan  8 16:37 en_windows_8_x64_dvd_915440 drwxrwxr-x 2 username        debian-transmission 4096 Jan  8 15:12 Incomplete drwxrwxr-x 2 username        debian-transmission 4096 Jan  8 15:12 Torrents
```

---

### Post by MasterShadow on 2014-01-09
> **carl4926 said:**
> I think you are struggling with some basic understanding  Please explain if you have tried deleting via the file browser. Please make sure transmission is closed too.  I'm sorry if I don't understand. I'm new with ubuntu, and transmission. In my downloads folder I right clicked, and selected "move to trash". It just says permission denied. I pressed shift-delete, and it said the same thing.

---

### Post by MasterShadow on 2014-01-09
> **carl4926 said:**
> I think you are struggling with some basic understanding  Please explain if you have tried deleting via the file browser. Please make sure transmission is closed too.  Also, under permissions I can't do anything with folder access. On the bottom it says "You are not the owner, so you can't change these permissions"

---

### Post by jeanjd63 on 2014-01-09
> **MasterShadow said:**
> When I put in that command it gives total 20 drwxrwxr-x 3 username        debian-transmission 4096 Nov 16  2006 broadcom-wl-4.80.53.0 drwxrwxr-x 2 username        debian-transmission 4096 Jan  8 15:12 Completed drwxr-xr-x 4 debian-transmission debian-transmission 4096 Jan  8 16:37 en_windows_8_x64_dvd_915440 drwxrwxr-x 2 username        debian-transmission 4096 Jan  8 15:12 Incomplete drwxrwxr-x 2 username        debian-transmission 4096 Jan  8 15:12 Torrents

This list is illisible and i don't see any torrent file, only directories :o

---

### Post by MasterShadow on 2014-01-09
> **jeanjd63 said:**
> This list is illisible and i don't see any torrent file, only directories :o

Why can't I delete them? It has the ISO, and it's about 3 gigs. I can't delete it.

---

### Post by jeanjd63 on 2014-01-09
Could you post the complete :
**ls -l  isofile **

---

### Post by MrMichaelHill on 2014-01-09
You can open file browser as super user in a terminal by typing

sudo nautilus 


Then browse to where the file is (Make sure transmission is closed completely!)

Then try and delete :)

---

### Post by MasterShadow on 2014-01-09
> **MrMichaelHill said:**
> You can open file browser as super user in a terminal by typing

sudo nautilus 


Then browse to where the file is (Make sure transmission is closed completely!)

Then try and delete :)

It worked. Thanks!

---

### Post by MrMichaelHill on 2014-01-09
No problems! 

Be careful running around in nautilus as super user because you have a lot more power to delete & move things etc.. :D

---

