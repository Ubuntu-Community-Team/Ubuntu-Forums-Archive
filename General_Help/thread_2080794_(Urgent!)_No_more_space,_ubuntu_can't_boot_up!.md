---
title: "(Urgent!) No more space, ubuntu can't boot up!"
date: 2012-11-05
forum: General Help
---

### Post by grimslider75 on 2012-11-05
I have maxed out my HDD space somehow, even though I deleted about 30gb of files prior to a warning message which popped up to, well, warn me. 

Now, I can't even boot up. Grub comes up, then the boot sequence stops midway, (usually around that TiMidity++ message). 

As you may be able to tell, I am not knowledgeable about linux or how computer systems work in general, so I would really appreciate a nudge in the right direction.

This also is happening conveniently before a project is due. I have 1 day before it's due, so this is fairly urgent. 

PS: I'm posting this from my windows partition. Comes in handy in times like these . . . :icon_frown:

THANKS in advance!

---

### Post by decrepit on 2012-11-05
Did you empty the trash? If you didn't that's where the 30gb is, still on the disk.

I think you need a live cd, and check just what's happening.

---

### Post by Wim Sturkenboom on 2012-11-05
Boot into recovery mode and select the option to drop to a (root) shell. Navigate to your home folder and check where the most space is used.

```

cd /home/yourusername
du -h --max-depth=1 /home/yourusername

```

If it's the trash, you will find that the directory .local is quite big. You can find the trash in /home/yourusername/.local/share/Trash/files and /home/yourusername/.local/share/Trash/info

```

cd /home/yourusername/.local/share/Trash/files
rm *
cd /home/yourusername/.local/share/Trash/info
rm *

```

Next run _df -h_ to check your free space.
Reboot with _shutdown -r now_

PS
Warning: you're root and have more powers than you ever want; so make sure that you don't delete the wrong stuff.

---

### Post by grimslider75 on 2012-11-05
> **Wim Sturkenboom said:**
> Boot into recovery mode and select the option to drop to a (root) shell. Navigate to your home folder and check where the most space is used.

```

cd /home/yourusername
du -h --max-depth=1 /home/yourusername

```If it's the trash, you will find that the directory .local is quite big. You can find the trash in /home/yourusername/.local/share/Trash/files and /home/yourusername/.local/share/Trash/info

```

cd /home/yourusername/.local/share/Trash/files
rm *
cd /home/yourusername/.local/share/Trash/info
rm *

```Next run _df -h_ to check your free space.
Reboot with _shutdown -r now_

PS
Warning: you're root and have more powers than you ever want; so make sure that you don't delete the wrong stuff.


```
[B]df-h
[/B]Filesystem     Size     Used    Avail    Use%    Mounted on
/dev/sda2      298G   284G         0     100%    /
```**ls** in my trash shows there to be no files there to be removed

trying to remove any files produces this message:

```
 rm: cannot remove 'file_name': Read-only file system
```confusion persists . . . . .

Even while trying to access the trash using a live cd, I get the same read-only file system message when I attempt to open it.

Please note: This is no longer urgent, I got the file I needed to finish my project, but I would still prefer to get ubuntu up and running sooner than later. 

Thanks for your help thus far, I really appreciate it :)

---

### Post by grimslider75 on 2012-11-05
Extra info:

I also moved a 50GB virtualbox .vdi and associated files/folders to my windows partition using a live ubuntu cd, but that made no difference, even though **df-h** shows that there is nothing in my VirtualBox VM's folder.

I should also add that this problem happened right after I tried shutting down a virtualbox sesson, so I think that had something to do with it. Other than that, I had recently added some video files to my HDD, but I clearly had 6GB free prior to the random 100% capacity problem, so I really don't know how that would have caused this, seeing that I've had as little as 100MB remaining on a fully functioning system.

---

### Post by Wim Sturkenboom on 2012-11-06
Time to start digging

```

wim@wim-desktop:~$ **[COLOR="Red"]sudo du -h --max-depth=1 /[/COLOR]**
[sudo] password for wim: 
484K	/dev
168K	/root
60K	/tmp
7.3M	/sbin
du: cannot access `/home/wim/.gvfs': Permission denied
12G	/home
7.9M	/bin
4.0K	/cdrom
400M	/lib
2.0G	/usr
4.0K	/media
8.0K	/srv
4.0K	/mnt
399M	/var
0	/sys
15M	/etc
4.0K	/selinux
16K	/lost+found
du: cannot access `/proc/7250/task/7250/fd/3': No such file or directory
du: cannot access `/proc/7250/task/7250/fdinfo/3': No such file or directory
du: cannot access `/proc/7250/fd/3': No such file or directory
du: cannot access `/proc/7250/fdinfo/3': No such file or directory
0	/proc
49M	/boot
4.0K	/opt
15G	/

```
Find the largest directory and repeat the process on the largest directory (in above example it's /home)
```

wim@wim-desktop:~$ **[COLOR="Red"]sudo du -h --max-depth=1 /home[/COLOR]**
16K	/home/lost+found
12G	/home/filemanager
du: cannot access `/home/wim/.gvfs': Permission denied
799M	/home/wim
12G	/home
wim@wim-desktop:~$ 

```
Again find the largest directory (in this case /home/filemanager) and drill further.
```

wim@wim-desktop:~$ **[COLOR="Red"]sudo du -h --max-depth=1 /home/filemanager/[/COLOR]**
12G	/home/filemanager/filemanagertest
12M	/home/filemanager/testje
12M	/home/filemanager/testje2
4.0K	/home/filemanager/.cache
12G	/home/filemanager/
wim@wim-desktop:~$ 

```
Keep on going till _du_ does not show something special. Run an _ls -lS_ on that directory to find the large files (they will be at the top)
```

wim@wim-desktop:/home/filemanager/filemanagertest$ **[COLOR="Red"]ls -lS[/COLOR]**
total 11549068
-rw-r--r-- 1 filemanager filemanager 8589934592 2012-10-19 11:12 8GBfile.devzero
-rw-r--r-- 1 filemanager filemanager 3221225472 2012-10-19 12:09 3GBfile.devzero
-rw-r--r-- 1 filemanager filemanager    3046137 2012-10-24 08:39 cc_rfs_20071206_0837.sql
-rw-r--r-- 1 filemanager filemanager     408136 2012-10-24 08:39 cc_rfs_20071207.tar.gz
-rw-r--r-- 1 filemanager filemanager      63488 2012-10-24 08:52 Thumbs.db

```

If I'm not mistaken, you can remount your filesystem to be writeable but I'm not sure how. A live CD / USB is the alternative.

Notes:
you don't need sudo if you're root ;)

---

