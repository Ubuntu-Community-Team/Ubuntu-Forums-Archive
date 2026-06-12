---
title: "Copying files without permissions"
date: 2016-09-16
forum: General Help
---

### Post by MibunoOokami on 2016-09-16
This rather embarrassing, I've been trying to copy so files onto a new system but they all keep getting locked. I have a note to myself saying use ```
sudo -i
``` then ```
nautilus
``` then change permissions via properties. Trouble is each directory seems to have subdirectories and hundreds of files, and it's too time consuming to change each of them one by one. How can I do this in one hit? Or better yet, how can I copy them without permissions being a problem?

I apologise if I have duplicated this thread, I could swear I made one similar earlier in the year except it's not in my profile's latest threads.

Thanks

---

### Post by TheFu on 2016-09-16
You probably want **sudo -H**, so when root runs nautilus, it doesn't take ownership with a 077 umask of config files. This is important for almost all GUI programs. A better rule is not to use sudo with any GUIs programs. That prevents some nasty issues later.

To manage permissions recursively, use **chmod**.  To manage ownsership and/or groups recursively use **sudo chown**.  To copy files recursively from A to B, which can be on the same or different systems, use **rsync** or **cp -r** or your backup and restore tool.  It is always a good idea to give that setup a workout.  BTW, any *first class* in Linux/Unix tools will teach the use of these commands.  EdX has a class and so does the LinuxFoundation - both are free.  [https://ubuntuforums.org/showthread.php?t=2337205](https://ubuntuforums.org/showthread.php?t=2337205)  There is also a free **[Command Line Linux]("http://linuxcommand.org/tlcl.php")** PDF file/book - easy download, no registration and it is a real book you can buy at any bookstore in dead-tree format. Highly recommended.  Get access to the other 90% of the power your Linux system has - use the CLI.  The stuff you learn in that book will last decades (and probably the rest of your life).

---

### Post by HermanAB on 2016-09-16
The utility find with exec is the way to do recursive changes:

find . -type d -exec chmod 0755 {} \;
find . -type f -exec chmod 0644 {} \;
find . -type d -exec chown yourname: {} \;
find . -type f -exec chown yourname: {} \;

...because exec gloms everything following it, you have to escape the semicolon.

You can do all of that in one line also of course, but I found that limiting the potential damage due to a typo to a single command at a time is usually better...

---

### Post by TheFu on 2016-09-16
@Herman - while that was the way we did things in the old days, the chown doesn't need that. After all, if you change-ownership on both files AND directories (which is most common), then **chown -R** does both.  **sudo chown -R thefu.thefu .** is the same as both 'find's above.

After the chown is completed, the chmod probably isn't needed, since file permissions are likely to be ok.

The chmod with find will always be useful, but chmod added the -X option a while ago that will leave the eXecute bits as needed for directories.  From the manpage: ```
The  letters  rwxXst select file mode bits for the affected users: read
       (r), write (w), execute (or search for directories) (x), execute/search
       only  if  the file is a directory or already has execute permission for
       some user (X), ... <snip>
```
So ... **chmod -R u+rwX .** and **chmod -R g+rwX .** together are probably better than the find commands above. Files with eXecute bits set will be left that way. Directories and files will have the 'x' if it had it before.

For the uninitiated - '.' (the dot alone) is the current directory.  './' is the same thing, if you prefer that or `pwd` will return the current full path, which is effectively the same.  

Those find commands are extremely useful for lots of reasons - even as templates for other 'find' cmds.  Find can be slow when used with exec, so often the output from 'find' will be sent into **xargs** for more efficient handling. Just pointing out there are shorter ways to accomplish the same, and sometimes better, results.

Hope this all makes sense.

---

### Post by MibunoOokami on 2016-09-18
Thanks for the replies. ```
sudo chown -R
``` worked like a dream.  
 It also sounded familiar so I must have asked a permissions question in a thread with a different title as none of my started thread titles (excluding this one) have anything to do with permissions. Although for some reason I never made a note of that command.

---

