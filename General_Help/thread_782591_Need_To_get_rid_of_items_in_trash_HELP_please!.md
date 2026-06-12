---
title: "Need To get rid of items in trash HELP please!"
date: 2008-05-05
forum: General Help
---

### Post by amyfan on 2008-05-05
i have items i deleted in the trash can but the icons are still in it when i click on the icons it tells me ```
Couldn't find "trash:///home_doug_Desktop_stuff_.Trash-1000_______".
``` also there is a document int he trash i click on it it opens and i can not get it to delete it came with a .zip file i got the rest gone but that one wont delete from the trash can

---

### Post by Rocket2DMn on 2008-05-05
Try deleting from terminal.  If you are in Hardy, do
```
cd ~/.local/share/Trash/files
rm -rf *
```
If you are in Gutsy or older, do
```
cd ~/.Trash
rm -rf *
```
Be VERY VERY careful with the rm -rf command, it CANNOT be undone and is dangerous if you use it incorrectly.  Make sure that you are in your trash directory before using that command as it will recursively delete everything from your current directory.

---

### Post by amyfan on 2008-05-05
did not help the icons are still in the trash can

---

### Post by amyfan on 2008-05-05
i am cd into the trash can i do ls it shows nothing in it.
but the icon on my tool bar shows there is three icons in it if i open .trash it shows nothing.

---

### Post by Rocket2DMn on 2008-05-05
Are the files from another partition on your computer or an external drive?  If so, you need to change to the mount point of those partitions, then open the .Trash-1000 or .Trash-yourusername folder (deprecated as of Hardy).  You may need to use sudo on the rm command, just PLEASE be very careful.

---

### Post by amyfan on 2008-05-05
im in hardy 64bit gnome and i did ls -la in the trash dir and one . and one .. showed up and no same partition ....

---

### Post by Rocket2DMn on 2008-05-05
That means that if the files are actually in your trash, they are in a trash folder somewhere else, like on another partition.  You can try deleting them under nautilus with root permissions by running
```
gksudo nautilus
```
CTRL+H will allow you to see hidden files/folders.

---

### Post by amyfan on 2008-05-05
ok i done that and i hit delete they go away for a min then two seconds later pop back in that folder....

---

### Post by Rocket2DMn on 2008-05-05
LOL, try Shift+Del at the same time, that will allow you to permanently delete them.

---

### Post by amyfan on 2008-05-05
ok that fixed those but well now the icons are still in the trash can...

---

### Post by Rocket2DMn on 2008-05-05
Can you please post a screenshot?

---

### Post by Bubba64 on 2008-05-05
> **Rocket2DMn said:**
> LOL, try Shift+Del at the same time, that will allow you to permanently delete them.

This works on thumb drives as well but you have to highlight or right click on what you want to remove. On a thumb drive or usb stick this deletes bypassing the on board trash. I have used it as shift then hit the delete key

---

### Post by amyfan on 2008-05-05
sorry for the clutter on the pic

---

### Post by Rocket2DMn on 2008-05-05
That is very strange, it seems like those folders aren't actually there.  Although rebooting is rarely needed in linux, you may want to give it a try (blasphemy, I know!).  It could be that the file system is acting up, you may even consider running fsck on the filesystem from a LiveCD or forcing it to scan on the next boot by running
```
sudo touch /forcefsck
``` then rebooting.

---

### Post by amyfan on 2008-05-05
sorry just hit me to post pics of .local/trash and the reg trash can

---

### Post by Arasfang on 2008-05-05
I have the same problem. The files I need to remove are located in ./Trash-1000 folder on another harddrive. When I try delete them from that folder with shift+delete I get the following error.

Im running Ubuntu Hardy 8.04 64-bit.

---

### Post by Rocket2DMn on 2008-05-05
> **Arasfang said:**
> I have the same problem. The files I need to remove are located in ./Trash-1000 folder on another harddrive. When I try delete them from that folder with shift+delete I get the following error.

Im running Ubuntu Hardy 8.04 64-bit.

That could be because it doesn't like the file name, you might try renaming the file first, then deleting it.  Have you tried deleting it from terminal?

---

### Post by amyfan on 2008-05-05
ok i am going to go do the disk check i will report back here when i am done.

---

### Post by legend2440 on 2008-05-05
It may be permissions problem
[http://ubuntuforums.org/showthread.php?t=759544](http://ubuntuforums.org/showthread.php?t=759544)

---

### Post by amyfan on 2008-05-05
ok i did the term by hiting cntrl+alt+f6 for my set up and i did sudo touch /forcefsck it went straight to another line of david@doug.

---

### Post by Rocket2DMn on 2008-05-05
That is normal, you have to reboot the system for it to run the disk check.  Right now I am going to bed since it's 2:30am, so I'll check up on you in the morning, hopefully by then you can sort it out.  Good luck!

---

### Post by amyfan on 2008-05-05
night and i did reboot the system i was in the terminal outside X...

---

### Post by Arasfang on 2008-05-05
> **Rocket2DMn said:**
> That could be because it doesn't like the file name, you might try renaming the file first, then deleting it.  Have you tried deleting it from terminal?

Ah. I tried from terminal before but on the regular trash-folder in my Home. Now I tried terminal on correct folder and it worked :)

Thank you ^^

---

### Post by amyfan on 2008-05-06
i fixed it by wiping my computer and reinstalling 32 bit hardy gnome lol
got tired of all the bugs in 64bit hardy.

---

