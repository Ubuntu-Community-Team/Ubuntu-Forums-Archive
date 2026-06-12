---
title: "permission denied when trying to add files to archive"
date: 2017-05-07
forum: General Help
---

### Post by wyndlass on 2017-05-07
i've been having probs with adding files to archives that i've previously made. i get 'an error occurred while adding files to the archive, you don't have the right permissions', this only happens if i try to add files by dragging them to the archive  but if i open the archive and drag and drop it works. what can i do to fix this? naut says i have full permission for the archive and files that i'm trying to add and so does ls -al using 16.04 on a hp pavilion g7 6 gb ram 650 gb hdd. thanx also it doesn't matter what else i have going on at the time either.

---

### Post by TheFu on 2017-05-07
Please show the **ls -al **output for the file AND the directory it is inside. Use 'code tags' when posting so things line up and are readable here. Too hard otherwise.

---

### Post by wyndlass on 2017-05-13
this is the output of ls -al;

```


total 23740
drwxrwxr-x 11 jadaja jadaja     4096 May 12 02:02 .
drwxrwxrwx 13 jadaja jadaja     4096 Apr  8 15:31 ..
-rw-rw-r--  1 jadaja jadaja 24256646 May  4 18:35 anthony.7z
drwxrwxr-x  2 jadaja jadaja     4096 Apr 22 08:36 aton
drwxrwxr-x  2 jadaja jadaja     4096 Apr 22 04:46 battle
drwxrwxr-x  2 jadaja jadaja     4096 Apr 22 04:48 bio
drwxrwxr-x  2 jadaja jadaja     4096 Apr 22 04:51 cluster
drwxrwxr-x  2 jadaja jadaja     4096 Apr 19 20:33 geodessy
drwxrwxr-x  2 jadaja jadaja     4096 Apr 22 04:55 immortality
drwxrwxr-x  2 jadaja jadaja     4096 Mar 19 23:37 manta
-rw-rw-r--  1 jadaja jadaja      749 May 12 02:02 piers.txt
drwxrwxr-x  2 jadaja jadaja     4096 Apr 22 04:58 rud
drwxrwxr-x  2 jadaja jadaja     4096 May  4 10:51 xanth


```

anthony is the archive for this example. dragging and dropping into this w/o opening first gives this;

[IMG]/home/jadaja/Pictures/Screenshot from 2017-05-13 14-29-08.png[/IMG]

didn't mean to double post that last post. the pic doesn't seem to pop up, let me try the pic as an attachment;

[ATTACH=CONFIG]275097[/ATTACH]


there it goes.

---

### Post by TheFu on 2017-05-13
If you are logged in as jadaja, then the issue isn't with permissions.  Perhaps 7z doesn't support modifying existing archives or the archive has a password to prevent modifications, but allows reading?  IDK.

Of course, this all assumes the disk isn't full and all the inodes haven't been used.  **df** and **df -i** will show that.

Besides those things, I have no idea.  I don't use 7z.

---

### Post by wyndlass on 2017-05-13
i have, currently, 53 gb left on hdd. df/df -i give this

```


Lord jadaja:~$ df 
Filesystem                  1K-blocks      Used Available Use% Mounted on
udev                          2981104         0   2981104   0% /dev
tmpfs                          600392      9320    591072   2% /run
/dev/mapper/ubuntu--vg-root 608852424 525874988  52026424  91% /
tmpfs                         3001956    380072   2621884  13% /dev/shm
tmpfs                            5120         4      5116   1% /run/lock
tmpfs                         3001956         0   3001956   0% /sys/fs/cgroup
/dev/loop0                     193664    193664         0 100% /snap/stellarium-plars/4
/dev/loop1                      80256     80256         0 100% /snap/core/1577
/dev/loop2                      81408     81408         0 100% /snap/core/1689
/dev/sda1                      240972    108686    107403  51% /boot
cgmfs                             100         0       100   0% /run/cgmanager/fs
tmpfs                          600392        96    600296   1% /run/user/1000
Lord jadaja:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
udev                          745276    560   744716    1% /dev
tmpfs                         750489    909   749580    1% /run
/dev/mapper/ubuntu--vg-root 38674432 690306 37984126    2% /
tmpfs                         750489    177   750312    1% /dev/shm
tmpfs                         750489      6   750483    1% /run/lock
tmpfs                         750489     18   750471    1% /sys/fs/cgroup
/dev/loop0                      3346   3346        0  100% /snap/stellarium-plars/4
/dev/loop1                     13536  13536        0  100% /snap/core/1577
/dev/loop2                     13689  13689        0  100% /snap/core/1689
/dev/sda1                      62248    309    61939    1% /boot
cgmfs                         750489     14   750475    1% /run/cgmanager/fs
tmpfs                         750489     45   750444    1% /run/user/1000


```

no password on the archive and i can add to it once i open it.

---

