---
title: "Firefox won't start"
date: 2013-05-06
forum: General Help
---

### Post by penguinslide on 2013-05-06
Hi, I have returned to Ubuntu (13.04) after a long time on Cinnamon Mint and am enjoying Ubuntu this time around, but I think I broke Firefox, I believe it was after failing to properly install Chrome (but accept there maybe a different reason),
 
I accidently loaded 32 bit chrome debs instead of 64 bit and then Ubuntu said that that too was the wrong packages for my system so I gave up installing Chrome and have been using Chromium since. I use Firefox for a couple of things I can't do on other browsers, so please help. 

I have tried installing and uninstalling via both terminal and ubuntu app centre. I can get the icon in the unity launcher, I click it, it flashes and the cursor does the loading indication but then it stops after about 10 seconds and nothing happens

Probably not related to the first issue but am also a bit frustrated that Ubuntu keeps forgetting my keyboard shortcuts!! Thanks in advance

---

### Post by Yellow Pasque on 2013-05-06
Start it from the terminal and see what it says:
```
firefox
```

You can also try safe mode:
```
firefox -safe-mode
```

If you don't mind losing your FF bookmarks, cache, etc., then you can delete your user's mozilla profile:
```
 rm -r ~/.mozilla/
```

---

### Post by ajgreeny on 2013-05-06
No, don't **remove** the hidden .mozilla folder, just **rename** it as .mozillabackup, then you can use some of the files and folders from that in the new .mozilla folder that will be made, to get back your bookmarks etc etc.

---

### Post by penguinslide on 2013-05-06
Ok, tried your suggestions:

m@m:~$ firefox


(process:7017): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Could not create gnome accelerators directory `/home/m/.gnome2/accels': Permission denied
m@m:~$ 

Then

m@m:~$ firefox -safe-mode


(process:7023): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Could not create gnome accelerators directory `/home/m/.gnome2/accels': Permission denied
m@m:~$ 

Haven't loaded my ff bookmarks yet so did the


rm -r ~/.mozilla/

so I believed it was a clean slate, but:

m@m:~$ rm -r ~/.mozilla/
m@m:~$ sudo apt-get install firefox
[sudo] password for m: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
m@m:~$ 

?

---

### Post by penguinslide on 2013-05-06
Sorry, am Australian and it's time to get some sleep, will respond in 8hrs

---

### Post by Impavidus on 2013-05-06
The **rm -r ~/.mozilla** deleted your user configuration, not firefox itself, so there's no need to reinstall it. There's no need to delete it either. The problem is in your /home/m/.gnome2/accels. When you're awake again, can you post the return of this command?```

ls -al .gnome2/
```

---

### Post by penguinslide on 2013-05-06
m@m:~$ ls -al .gnome2/
ls: cannot open directory .gnome2/: Permission denied
m@m:~$ sudo ls -al .gnome2/
[sudo] password for m: 
total 16
drwx------  3 root root 4096 Apr 26 19:00 .
drwxr-xr-x 26 m    m    4096 May  7 05:42 ..
drwx------  2 root root 4096 Apr 26 18:57 accels
-rw-r--r--  1 root root   53 Apr 26 19:00 firestarter
m@m:~$

---

### Post by Bashing-om on 2013-05-06
penguinslide ; Hi !


Impavidus Is spot on. Here is my output:
> sysop1@1204-a:~$ ls -al .gnome2/
total 28
drwx------  5 sysop1 sysop1  4096 Aug 31  2012 .
drwxr-xr-x 29 sysop1 sysop1 12288 May  6 15:17 ..
drwx------  2 sysop1 sysop1  4096 Nov 19 21:40 accels
drwx------  2 sysop1 sysop1  4096 Aug 31  2012 keyrings
drwxr-xr-x  2 sysop1 sysop1  4096 Aug 31  2012 nautilus-scripts
sysop1@1204-a:~$ 
 As to how deep the miss-directed file ownerships in your situation go, presently we do not know. I am hesitant about advising to change the ownership recursively to all files in your home directory. Wait for Impavidus's continued advisement.
I also note that nautilus-scripts directory is non-existent in your output, perhaps required for Fire Fox scripts to also be able to run ?
     [INDENT]
just my 2 cents worth in an effort to help

[/INDENT]

---

### Post by Impavidus on 2013-05-06
There shouldn't be any files in your home directory not owned by you. There may be a few files in your home directory not belonging to your group, but you would know if that were the case. Try a recursive chown:```

sudo chown -R m:m .gnome2/

```
The "nautilus-scripts" directory is present but empty on my system. It doesn't matter, if it's needed it will be created.

---

### Post by ajgreeny on 2013-05-06
You may even need to use chown on all your /home with ```
sudo chown -R m:m /home/m
```

---

### Post by penguinslide on 2013-05-07
After reading the whole ownership topic I thought I would try sudo firefox, asked for password and it worked.

```
sudo chown -R m:m /home/m
```

That has fixed it can now launch from unity bar, thank you all very much, now I guess it will save my keyboard shortcuts now it recognizes ownership

---

