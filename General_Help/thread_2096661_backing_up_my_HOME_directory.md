---
title: "backing up my HOME directory"
date: 2012-12-20
forum: General Help
---

### Post by Nuitblanche on 2012-12-20
Hi, my laptop is malfunctioning.
After it boots to login screen then the screen goes black.
I tried using a live cd to log in - it still doesn't work.
All I can do is get to the command username@username:~$ (by CTRL-ALT-F1). I have the Mount Passphrase of my encrypted HOME folder. How can I back up my HOME folder to my external hard drive by using just commands at the username@username:~$  ? I plan to do a fresh install after I recover my files.

Thanks much for your help anyone!

---

### Post by pierceTN on 2012-12-20
> **faginp said:**
> Hi, my laptop is malfunctioning.
After it boots to login screen then the screen goes black.
I tried using a live cd to log in - it still doesn't work.
All I can do is get to the command username@username:~$ (by CTRL-ALT-F1). I have the Mount Passphrase of my encrypted HOME folder. How can I back up my HOME folder to my external hard drive by using just commands at the username@username:~$  ? I plan to do a fresh install after I recover my files.

Thanks much for your help anyone!

look at this thread:

[http://ubuntuforums.org/showthread.php?t=1774562](http://ubuntuforums.org/showthread.php?t=1774562)


-Pierce

---

### Post by Nuitblanche on 2012-12-20
Thanks alot for the link Pierce, will try to do it.

Will get back tomorrow to let you know if I've succeeded.

---

### Post by Nuitblanche on 2012-12-22
Hi, I have been following instructions on the link. I mounted my external drive in the directory I made called "seagate".

Then to browse it, I type "cd /media/seagate"
But instead of getting a list of all the folders in my seagate external drive, I get this instead - "username@username:/media/seagate$"

What does that mean?

Thanks anyone. I'm really new and haven't a clue.

---

### Post by Nuitblanche on 2012-12-22
okay nevermind my above post. I just figured it out.

but I have a new question - I typed:
sudo cp -r /home/username/* /media/seagate, when I pressed enter, nothing happens. just a flashing underscore.

Is it in the process of copying or is there something wrong?

I sure hope someone can help.

---

### Post by vanadium on 2012-12-22
It may be copying indeed. By default, manu bash commands are "discrete", i.e., they will only throw out messages if soemthing goes wrong. To have more info on an ongoing process, you would need to add the -v (--verbose) option.

You can also tell from the led of your drive whether there is disk activity going on.

---

### Post by Nuitblanche on 2012-12-22
Thanks Vanadium.

It was in fact in the process of copying.

My back up is completed. PHEW!

Thanks again you guys!!

---

### Post by ayenack on 2012-12-22
You'll need to be patient. Depending on how much data you have in your home directory this can take ages.

We're talking 10's of hours here if you're copying to a USB drive and there's a good whack of data on the home partition.

Bit late with this.

---

### Post by Wim Sturkenboom on 2012-12-22
```

cd /media/seagate

```
will take you to 'the drive'. You can do a listing of files with _ls -l_ (that is, EL ES minus EL)
```

wim@aa0:/media/PENDRIVE$ **[COLOR="Red"]ls -l[/COLOR]**
total 258080
-rwxr-xr-x 1 wim root  67461732 Jun 20  2012 12771K.mpg
-rwxr-xr-x 1 wim root  17290736 May 13  2011 150640K.mpg
...
...
-rwxr-xr-x 1 wim root     39424 Dec  5 14:13 xls2scd.x64.exe
-rwxr-xr-x 1 wim root       541 Oct 22 07:56 xxxmvldb.ipconfig.txt
-rwxr-xr-x 1 wim root    171008 Dec  4 21:28 zMoviePlayer.exe

```

You can create a backup directory with _mkdir backup_; make sure that you are on the seagate disk.
```

wim@aa0:/media/PENDRIVE$ **[COLOR="Red"]mkdir backup[/COLOR]**

```
or if you're not in the seagate disk, 
```

wim@aa0:~$ **[COLOR="Red"]mkdir /media/PENDRIVE/backup[/COLOR]**

```
To check the available space on the drive, use _df_
```

wim@aa0:/media/PENDRIVE$ **[COLOR="Red"]df -h[/COLOR]**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.0G  3.0G  3.6G  46% /
tmpfs                 246M     0  246M   0% /lib/init/rw
udev                  239M  200K  239M   1% /dev
tmpfs                 246M  4.0K  246M   1% /dev/shm
/dev/sdb1             3.9G  1.9G  2.0G  50% /media/PENDRIVE

```
In the above example there is 2GB available on /media/PENDRIVE.

Move back to your home directory
```

wim@aa0:/media/PENDRIVE$ **[COLOR="Red"]cd ~[/COLOR]**

```
Next check how big your home directory is with _du_; after 'max-depth=' is the number one, not the letter i or lowercase L
```

wim@aa0:~$ **[COLOR="Red"]du -h --max-depth=1 /home/wim[/COLOR]**
964K	/home/wim/.Skype
1.3M	/home/wim/.thumbnails
256K	/home/wim/.gconf
4.0K	/home/wim/testje
36K	/home/wim/.pki
...
...
4.2M	/home/wim/images
12K	/home/wim/documents
92M	/home/wim/.local
957M	/home/wim

```
The last line give the size

Next copy the files with _cp_
```

wim@aa0:~$ **[COLOR="Red"]cp -R /home/wim/* /media/PENDRIVE/backup/[/COLOR]**
cp: cannot create symbolic link `/media/PENDRIVE/backup/images/wallpapers/shared': Operation not permitted
wim@aa0:~$ 

```
There is one error; it can be ignored.

Next check the result
```

wim@aa0:~$ **[COLOR="Red"]ls -l /media/PENDRIVE/backup/[/COLOR]**
total 704294
drwxr-xr-x 2 wim root      2048 Dec 22 17:28 backup
drwxr-xr-x 2 wim root      2048 Dec 22 17:28 bin
drwxr-xr-x 2 wim root      2048 Dec 22 17:28 Desktop
-rwxr-xr-x 1 wim root       260 Dec 22 17:28 df.afterinstall.txt
...
...
drwxr-xr-x 3 wim root      2048 Dec 22 17:28 x
-rwxr-xr-x 1 wim root 721121280 Dec 22 17:31 zenlive-7.0.iso
-rwxr-xr-x 1 wim root        50 Dec 22 17:31 zenlive-7.0.md5
wim@aa0:~$ 

```

You can check a bit more, e.g. I have a directory Misted
```

wim@aa0:~$ **[COLOR="Red"]ls -l /media/PENDRIVE/backup/Misted/[/COLOR]**
total 4
drwxr-xr-x 2 wim root 2048 Dec 22 17:28 gtk-2.0
drwxr-xr-x 2 wim root 2048 Dec 22 17:28 openbox-3
wim@aa0:~$ **[COLOR="Red"]ls -l /media/PENDRIVE/backup/Misted/openbox-3/[/COLOR]**
total 20
-rwxr-xr-x 1 wim root  133 Dec 22 17:28 bullet.xbm
-rwxr-xr-x 1 wim root  136 Dec 22 17:28 close.xbm
-rwxr-xr-x 1 wim root  157 Dec 22 17:28 desk_toggled.xbm
-rwxr-xr-x 1 wim root  133 Dec 22 17:28 desk.xbm
-rwxr-xr-x 1 wim root  142 Dec 22 17:28 iconify.xbm
-rwxr-xr-x 1 wim root  154 Dec 22 17:28 max_toggled.xbm
-rwxr-xr-x 1 wim root  130 Dec 22 17:28 max.xbm
-rwxr-xr-x 1 wim root  130 Dec 22 17:28 shade.xbm
-rwxr-xr-x 1 wim root 2195 Dec 22 17:28 themerc
wim@aa0:~$ 

```

Lastly unmount the drive
```

wim@aa0:~$ **[COLOR="Red"]sudo umount /media/PENDRIVE/[/COLOR]**
[sudo] password for wim: 

```
And checkif it's indeed unmounted
```

wim@aa0:~$ **[COLOR="Red"]mount[/COLOR]**
/dev/sda1 on / type ext4 (rw,noatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)

```
/media/PENDRIVE is no longer there

Note:
you need to replace 'PENDRIVE' with 'seagate'

---

### Post by Wim Sturkenboom on 2012-12-22
Hmm, I should not take that long working out the example. Hopefully useful for somebody else.

Congratulations on solving the puzzle ;) Please mark your thread as solved using the thread tools just above the first post on this page.

---

### Post by Nuitblanche on 2012-12-22
Thanks everyone and Wim for taking the time to put all that explanation out.

Someone will surely need to use it in the future.

I couldn't have done it on my own.
Happy Holidays!!

---

