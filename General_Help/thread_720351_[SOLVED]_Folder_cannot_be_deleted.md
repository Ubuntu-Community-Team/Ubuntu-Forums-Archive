---
title: "[SOLVED] Folder cannot be deleted"
date: 2008-03-10
forum: General Help
---

### Post by Rytron on 2008-03-10
Hi,
I have an external hdd (ntfs formatted).
There is an empty folder that I cannot delete. A message says it is corrupt. I logged in as root but even from there I was unable to delete it.
Also I have a dual boot pc (Xp is other OS) - I tried deleting it from my Windows Xp side - still no luck.
I even tried using the freeware  tool 'unlocker' in windows.

Does anyone know of a command / method to delete a stubborn folder?

Thanks.

---

### Post by Oldsoldier2003 on 2008-03-10
> **Rytron said:**
> Hi,
I have an external hdd (ntfs formatted).
There is an empty folder that I cannot delete. A message says it is corrupt. I logged in as root but even from there I was unable to delete it.
Also I have a dual boot pc (Xp is other OS) - I tried deleting it from my Windows Xp side - still no luck.
I even tried using the freeware  tool 'unlocker' in windows.

Does anyone know of a command / method to delete a stubborn folder?

Thanks.
run scandisk on the volume to repair the file system then try deleting it

---

### Post by phrawzty on 2008-03-10
> **Rytron said:**
> I have an external hdd (ntfs formatted).  There is an empty folder that I cannot delete. A message says it is corrupt. 

How, exactly, are you attempting to delete the directory?  I suspect you're using the GUI - if this is the case, you may wish to try removing the file via the shell :

```
rm -v <file>
```

The "-v" will enable verbose mode, which may give you further insight into why the file cannot be removed.

---

### Post by ATIuser on 2008-03-10
in linux try 
```

sudo chmod a-r filename
rm -ri filename

```
in windows xp cli I believe its something to the effect of:
```

attrib -r filename
del filename

```

---

### Post by Rytron on 2008-03-11
I tried commands above.
No luck. 

I opened terminal, put the commands above (individually) and then pasted the path to the invincible folder.

Also it is a folder and not a file that I need to delete - do I need a different command to delete a folder?

---

### Post by Oldsoldier2003 on 2008-03-11
> **Rytron said:**
> I tried commands above.
No luck. 

I opened terminal, put the commands above (individually) and then pasted the path to the invincible folder.

Also it is a folder and not a file that I need to delete - do I need a different command to delete a folder?
rm -r will delete a folder and its contents rmdir deletes directories, but they have to be empty.

---

### Post by Rytron on 2008-03-11
Thank you. I will try that very soon.

:mrgreen:

---

### Post by unutbu on 2008-03-11
Could you please post the output to commands we have suggested, so we can look for clues?

Here are a few more that might help
```

ls -l <directory>
stat <directory>
/bin/rm -rf <directory>

```

---

### Post by Rytron on 2008-03-17
> **unutbu said:**
> Could you please post the output to commands we have suggested, so we can look for clues?

Here are a few more that might help
```

ls -l <directory>
stat <directory>
/bin/rm -rf <directory>

```

[COLOR="DarkGreen"]Here is some output:[/COLOR]

```
name@Tron:/media/500GB/Linux/Games-Linux/Emulators$ stat "/media/500GB/Linux/Games-Linux/Emulators"  File: 

`/media/500GB/Linux/Games-Linux/Emulators'
  Size: 0               Blocks: 0          IO Block: 4096   directory
Device: 

821h/2081d      Inode: 5282        Links: 1
Access: (0777/drwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 

2008-03-09 13:35:46.000000000 +0000
Modify: 2008-03-09 13:35:45.000000000 +0000
Change: 2008-03-09 13:35:45.000000000 +0000
name@Tron:/media/500GB/Linux/Games-Linux/Emulators$ ls -l
ls: reading directory .: Input/output error
total 0
name@Tron:/media/500GB/Linux/Games-Linux/Emulators$ 
name@Tron:/media/500GB/Linux/Games-Linux/Emulators$ /bin/rm -rf 

"/media/500GB/Linux/Games-Linux/Emulators"
/bin/rm: reading directory `/media/500GB/Linux/Games-Linux/Emulators': 

Input/output error
name@Tron:/media/500GB/Linux/Games-Linux/Emulators$ 
```

---

### Post by forrestcupp on 2008-03-17
Did you try to change to the Games-Linux directory first, then remove the folder?
```
cd /media/500GB/Linux/Games-Linux
rm -v ./Emulators
```

Try that and post the output if it doesn't work.  Let us know what the solution is when you figure it out.

---

### Post by unutbu on 2008-03-17
Thanks for the output.

Notice the error:
```

name@Tron:/media/500GB/Linux/Games-Linux/Emulators$ ls -l
ls: reading directory .: Input/output error

```

I think Oldsoldier2003 had the right idea. The filesystem is corrupt. 
Run scandisk as Oldsoldier2003 suggested. 

You might also try this on the linux side:

```

sudo umount <device name>
sudo fsck.vfat <device name>

```
If you don't know the device name, run
```

sudo fdisk -l

``` and post the output.

On XP, you could try:
```

Start->Run->Open->cmd
chkdsk VOL:/r

```
where VOL should be replaced with the volume name.

---

### Post by Rytron on 2008-03-19
Hi, I solved the problem by booting into XP and using disk check. I then deleted the corrupt folder without any problems. Thank you. :D

Also it took about 2.5 hours as the external hdd is 500GB in size.

---

