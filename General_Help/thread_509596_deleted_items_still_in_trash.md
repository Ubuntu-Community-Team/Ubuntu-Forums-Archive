---
title: "deleted items still in trash"
date: 2007-07-25
forum: General Help
---

### Post by c.yarri on 2007-07-25
I'm pretty new at linux, but have been messing around for around a month now.  

I recently set up a virtual XP machine through vmware.  Long story short, I was trying to shrink my virtual space, but ended up copying my linux system folders.  I was doing this as root, so when I moved the useless files into the trash, I couldn't empty the items in trash as a user.  

I searched around and was able to use
```
sudo rm -rf /home/.Trash-root/*
```
to get rid of the files.  This freed of my disk space, but the folders still show up in the trash file manager.

Finally, when I run 
```
sudo nautilus
```
and go to the trash...nothing is there.  Rebooting doesn't make any difference either.  How can I get those items to not show up in the trash?

---

### Post by c.yarri on 2007-07-25
I forgot to mention I'm using Feisty 7.04

---

### Post by c.yarri on 2007-07-27
Can anyone help me with this??  I still have a bunch of items in my trash...and they won't go away!

---

### Post by dannyboy79 on 2007-07-27
there's more than one .Trash location

i know there's ways to make this all one command but I am not that smart with the find command syntax and xargs yet so try this:

first run
sudo find / -name .Trash\* -print

that should return all folders with .Trash<anythinghere>
**NOTE:** mine returned this
/root/.Trash
/home/.Trash-root
/home/daniel/.Trash
/media/300gb/.Trash-daniel
/media/300gb/.Trash-root
/media/500gb/.Trash-root
/media/500gb/.Trash-daniel
/media/500gb/dapperinstall/home/.Trash-root
/media/500gb/dapperinstall/home/daniel/.Trash
/media/500gb/dapperinstall/home/daniel/300gb-ext3/.Trash-daniel
/media/500gb/dapperinstall/home/daniel/300gb-ext3/.Trash-root
/media/500gb/dapperinstall/root/.Trash
/media/fat32/.Trash-daniel
/media/fat32/.Trash-root
/media/400gb/.Trash-daniel
/media/400gb/.Trash-root
then just run that same command on each trash location. good luck

---

### Post by c.yarri on 2007-07-27
Ok...I did the following

```

cole@cole-linux-work:~$ sudo find / -name .Trash\* -print
/root/.Trash
find: /mnt/micro/bin/unix_tools: Permission denied
find: /mnt/micro/software/.dist/floppies: Permission denied
find: /mnt/micro/software/.dist/ghost: Permission denied
find: /mnt/micro/software/.dist/nt_server_tools: Permission denied
find: /mnt/micro/software/.dist/picture_taker: Permission denied
find: /mnt/micro/software/.dist/veritas: Permission denied
find: /mnt/micro/software/.dist/xwin32: Permission denied
/home/.Trash-root
/home/cole/.Trash
cole@cole-linux-work:~$ sudo rm -rf /home/.Trash-root/*
cole@cole-linux-work:~$ sudo rm -rf /root/.Trash/*
cole@cole-linux-work:~$ sudo rm -rf /home/cole/.Trash/*
```

The /mnt/micro is a server share at my school that wasn't mounted at the time the files were sent to the trash, so I'm pretty sure the only three are the ones I just cleaned out.  Unfortunately, the items are still showing up.  Thanks for the help.  Any more suggestions?

---

### Post by Fallen_62 on 2007-07-27
Once you find all your .Trash locations, you could make a script to run them all at the same time, I believe.  You would need to be in as sudo first, then run the script.  The script would have many lines like this "rm -rf /home/.Trash-root/*" with all the different .Trash locations.

Did that make sense...?

Edit:  Seeing what you just posted, the script wouldnt help you : /  It was more if it worked...  Sorry!

---

### Post by c.yarri on 2007-07-27
Not a problem.  I appreciate the help.  I am really confused by the problem.  It seems like the trash folder is getting cues from some place else besides the .Trash folders but I can't seem to find out where.

---

### Post by rbmorse on 2007-07-27
I have two folders that live inside of:

/home/*myusername*/.local/share/Trash

they are

files
info

I have to manually clear trash files from both folders in order to make the tray icon appear empty.

same thing for /root/.local/trash for files deleted while I'm a root level user.

---

### Post by c.yarri on 2007-07-27
Thanks everyone for the help.  Unfortunately I did not have either of those directories in my folder or the root folder.

---

### Post by aysiu on 2007-07-27
Can you run this command? ```
sudo updatedb
``` and then repeat the process from post #5?

---

### Post by c.yarri on 2007-07-27
I will try that.  Also, I just found that the folders that show up in my trash are my actual system folders.  I put a temp folder in my / directory called trash, and then cut and paste an empty folder (I used /opt) from the trash into that temp folder, and it was erased from the / directory, and no longer showed up in the trash!

I put it back so no harm done, but somehow my whole directory tree is in the trash can, and yet I still access it normally.

Will still try updatedb unless advised otherwise.

---

### Post by dannyboy79 on 2007-07-28
have you tried to restart lately. something is amiss. it sounds like you're saying that your trash folder is your highest within the directory structure? that's not good. is it possible that you used sudo to run nautius and accidentally dragged the / folder into the trash? can you please show me the output from ALL the trash locations. thanks. just run a ls -la on each location.

---

### Post by c.yarri on 2007-07-30
I have restarted many times, but I believe your second comment may be hitting close to the point.  In my first plea for help I mentioned that I was doing some vmware disk management stuff, and I in trying to copy my virtual hard drive, I did something to my actual hard drive.  Anyways, that is how I got to this point.  Here is a snapshot of my trash folders right now.

```
root@cole-linux-work:/home/cole/.Trash# ls -al
total 8
drwx------  2 cole cole 4096 2007-07-30 09:43 .
drwxr-xr-x 52 cole cole 4096 2007-07-27 17:25 ..
root@cole-linux-work:/home/cole/.Trash# cd /home/.Trash-root
root@cole-linux-work:/home/.Trash-root# ls -al
total 8
drwx------ 2 root root 4096 2007-07-27 16:54 .
drwxr-xr-x 6 cole root 4096 2007-07-27 17:28 ..
root@cole-linux-work:/home/.Trash-root# cd /root/.Trash
root@cole-linux-work:~/.Trash# ls -al
total 12
drwx------  3 root root 4096 2007-07-27 17:32 .
drwxr-xr-x 29 root root 4096 2007-07-27 17:00 ..
drwxr-xr-x  7 root root 4096 2007-07-27 17:32 var (copy)
```

---

### Post by c.yarri on 2007-07-30
Thanks everyone for the help.  I am also having some xgl-compiz-ati problems, so I am going to do a fresh install and that should take care of it anyways.  Thanks.

---

### Post by mommebu on 2007-08-10
Looks like this bug:
[https://bugs.launchpad.net/gnome-vfs/+bug/85608](https://bugs.launchpad.net/gnome-vfs/+bug/85608)
I had a similar problem, not with the system tree /, but with a partition mounted on /archive.
Deleting .trash_entry_cache resolved it for the moment...

---

### Post by dannyboy79 on 2007-08-10
thanks for the tip, I'll try to find a cache file named that.

---

### Post by mommebu on 2007-08-10
I found it at
~/.gnome/gnome-vfs/.trash_entry_cache

---

### Post by hugh_h_chen on 2008-05-19
i have a similar problem: i have a file in the gnome panel trash located in the panel in the right bottom corner of screen next to the workspace swticher. in this trash, i can't delete the file as it says i don't have the permission to do so.

when i use sudo nautilus to open the trash, there is nothing in there.

i tried to find the trash location using your code: sudo find / -name .Trash\* -print, it returned this :

find: /home/chenhua/.gvfs: Permission denied

and then nothing comes up. do you know what's wrong with this? can you help?

---

### Post by hugh_h_chen on 2008-05-20
Just an update:

the find code didn't do the work, though i found out the .gvfs is something to do with trash. it comes back when your trash is used even it is deleted.

1. however, i the find did return a new location /.Trash-0. i believe this is the highest level of trash. it is empty by the way, so it is not the problem

2. i read some where on this forum that trash can be in /home/chenhua/.local/share/Trash. so i found my file that i didn't have permission to empty. and i deleted without problems, as i was in root privilege.

3. then, the file went to  the  /root/.local/share/Trash folder, i had to empty from there too. i guess i was using root profile, so it puts my deleted stuff  to the root trash.

4. now, i know that i need to be careful when i use different account to do the deletion, as they will be put in different trash.

thanks for this thread and previous replies.

---

### Post by stinkinrich88 on 2008-06-25
ahh ~/.local/share/Trash/ was where my problem was

oh, you already said that. I swear I tried what you said! Maybe it was the reboot that made them show up. Yeah, try a reboot (anyone else with this problem)

---

### Post by aNgGaCKt on 2008-07-15
> **stinkinrich88 said:**
> ahh ~/.local/share/Trash/ was where my problem was

oh, you already said that. I swear I tried what you said! Maybe it was the reboot that made them show up. Yeah, try a reboot (anyone else with this problem)

Me :lolflag: , i was having the same problem and it's really killing me. The symptoms are :

1. I can't empty the trash as a user, always saying i do not have the privilege to do so. 
2. Every time i tried to delete it as a root in terminal, the cpu goes 100%.
3. Opening Nautilus as a root and tried to empty the trash force me to force quit nautilus
4. Every other method i tried failed, including the chown or the chmod method.

And there you go, telling your problem is at : ~/.local/share/Trash/ . I tried to go there with my desperation, delete all the files in there, and, voila. Problem Solved :)

Thanks :guitar:

---

### Post by stinkinrich88 on 2008-07-16
ahh, good stuff, aNgGaCKt. I know what you mean about opening "Deleted items" as root in nautilus! I tried it a few times and my RAM would start filling up until all 2GB were full, then it moved onto my swap! I cold rebooted it because I panicked :oops:  I'm pretty sure I reported it as a bug, though

---

