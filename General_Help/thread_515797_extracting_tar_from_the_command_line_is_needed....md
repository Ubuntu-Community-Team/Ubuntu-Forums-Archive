---
title: "extracting tar from the command line is needed..."
date: 2007-08-02
forum: General Help
---

### Post by yehudaco on 2007-08-02
i have done some fatal errors in my ubuntu 7.04 os and i need to restore it, i have a tar backup which made :  tar -xjvf file.tar.bz2 which is now saved in a ntfs partition - media/sdb3 and i want to extract it to the root / partition to restore every thing and i have to do it from the boot cd from the command line - i've mounted  media/sdb3 in  mnt/ntpart and this is where the file is. what would be the command line to extract it from there to the / partition?

---

### Post by Ek0nomik on 2007-08-02
> **yehudaco said:**
> i have done some fatal errors in my ubuntu 7.04 os and i need to restore it, i have a tar backup which made :  tar -xjvf file.tar.bz2 which is now saved in a ntfs partition - media/sdb3 and i want to extract it to the root / partition to restore every thing and i have to do it from the boot cd from the command line - i've mounted  media/sdb3 in  mnt/ntpart and this is where the file is. what would be the command line to extract it from there to the / partition?

```
tar -xzvf /media/sdb3/file.tar.bz2 /
```

This will untar the file to "/".

If you get a permission error, add 'sudo' in front of the command.

---

### Post by Hospadar on 2007-08-02
I would first copy it to the root with ```
sudo cp /media/sdb3/file.tar.bz2 /
```
and then un-tar it with something like ```
tar -xjvf file.tar.bz2
``` (the actual set of arguments for tar might be a little different, do a ```
 man tar
``` to figure out exactly what you need if that doesn't work

---

### Post by gamble6x on 2007-08-02
If you're booting off a live CD you'll have to mount the NTFS partition with the tar file and the EXT3 partition (I'm assuming) for your linux root.

Once you've mounted both you'll want to navagate to where you've mounted the root partitoin (let's use /mnt/linux for example)

once you're in /mnt/linux you should be able to see all the files of the broken system.  If you're sure you don't want to copy anything out of there first I would remove all of them with:

rm -Rf ./

Be sure you're in the right directory and you use the ./ to tell it only that directory, or you can blow away things you don't want to.

Once the files have all been removed from /mnt/linux, in that folder just type:

tar -xvjf /mnt/ntpart/file.tar.bz2

tar always extracts into your present location.  so it will extract that file into /mnt/linux for you as long as you're in that directory when you issue the command.

Hope that helps.

-Brandon

---

### Post by yehudaco on 2007-08-02
but when i do that from knoppix terminal on most of the files it says 
can'nt open/mkdir: no such file or directory 
or 
that there is not enough space 
i'm getting a little upset here, what can i do to solve this??

---

### Post by Ek0nomik on 2007-08-02
> **yehudaco said:**
> but when i do that from knoppix terminal on most of the files it says 
can'nt open/mkdir: no such file or directory 
or 
that there is not enough space 
i'm getting a little upset here, what can i do to solve this??

Can you post your terminal output?

---

### Post by yehudaco on 2007-08-02
sorry i was out...
it is on the other computer and i not really know how to enter the net from knoppix...
any suggestions?

---

### Post by Ek0nomik on 2007-08-02
> **yehudaco said:**
> sorry i was out...
it is on the other computer and i not really know how to enter the net from knoppix...
any suggestions?

So this command,

```
tar -xjvf file.tar.bz2
```

doesn't work?

---

