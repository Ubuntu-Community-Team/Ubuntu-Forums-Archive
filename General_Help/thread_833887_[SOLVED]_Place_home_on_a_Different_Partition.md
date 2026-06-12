---
title: "[SOLVED] Place /home on a Different Partition"
date: 2008-06-19
forum: General Help
---

### Post by 1467 on 2008-06-19
i was stumbling and fond this web site [http://hehe2.net/linux-general/the-7-habits-of-highly-effective-linux-users/]("http://hehe2.net/linux-general/the-7-habits-of-highly-effective-linux-users/") and i am trying to do number 3-Place /home on a Different Partition clicked on this link [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") and i cant get passed this part 

find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome/
and i get this 

cpio: You must specify one of -oipt options.
Try `cpio --help' or `cpio --usage' for more information.

  what do i do ?

---

### Post by forestpixie on 2008-06-19
If you look at psychocats page on the same thing the first 2 cpio options should be preceded with -- not -

so there the command reads

cpio --null --sparse -pvd

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

That page worked for me when I tried it last year.

---

### Post by 1467 on 2008-06-19
o thank you

---

### Post by forestpixie on 2008-06-19
welcome - can you mark thread solved

---

### Post by 1467 on 2008-06-19
ok np

---

### Post by 1467 on 2008-06-19
lol i broke it i cant run any thing  now and i cant open any thing ?

---

### Post by 1467 on 2008-06-19
k i moved the home to my new hard drive and mounted it and it told me to edit a /dev/ file but i was not able to open any thing or open firefox so now i am on my other computer and i cant find my live cd

---

### Post by forestpixie on 2008-06-19
If you have to edit a file and cann't start - try to use recovery mode. In gutsy if I remember correctly it drops you to a root prompt, hardy gives you a menu in which you can choose to use a root prompt.

You will need to use nano to edit the file - syntax is

nano /path/tofile

That will open the file for editing - to save the file Ctrl+O and enter, to exit Ctrl+X

If you get errors you need to try and post them

---

### Post by 1467 on 2008-06-19
ok i moved my /home to /dev/sdb1 cant i gust move it back and if so how?

---

### Post by forestpixie on 2008-06-19
Well I guess you could use the same commands as before changing them to suit the new location.

Other than that I can't help, if you haven't done much to your system maybe it would be worth reinstalling and leave the home where it is.

---

### Post by 1467 on 2008-06-19
i lost my live cd and this computer has no cd burner the only cd burn i have is in the computer that i am trying to fix i can mover the cd burner to this computer 


o well thanks for the help i dont think i will ba able to use my other computer for a week or so 


np i this one is fine

---

### Post by forestpixie on 2008-06-19
What /dev/file was it wanting to edit? Did you try to edit it?

---

### Post by 1467 on 2008-06-19
dev/fstab and no i did not edit it yet

---

### Post by forestpixie on 2008-06-19
Sure it wasn't /etc/fstab - that is the file which tells the system where to mount stuff.

For instance there will be a line for /home in there - if you have changed where /home was then it won't be able to find it.

---

### Post by 1467 on 2008-06-19
now in recovery mode i get this could not start the x server ( your graphical enviroment) due to some internal error

---

### Post by 1467 on 2008-06-19
yea it was etc/fstab

---

### Post by forestpixie on 2008-06-19
You can check a few things from the root prompt and make sure that they agree

use this command to get the UUID for each partition - you need the UUID for your new /home partition

```
blkid
```

This command will show you your current fstab

```
cat /etc/fstab
```

Check that the line, if you have one, that corresponds to /home has the right UUID.

If it doesn't change it to the new number - be careful with case.

If it doesn't have a line for your new /home put one in, this is mine without the uuid

```
UUID=puthteuuidyougetfromblkidhere /home  ext3  relatime  0  2
```

---

### Post by forestpixie on 2008-06-19
> **1467 said:**
> yea it was etc/fstab

thought so - try this above

---

### Post by forestpixie on 2008-06-19
Don't worry about x server for the moment, lets try and get /home mounting first.

I need to know if you are using which version of ubuntu you are running.

Id you are at all unsure of any of these commands ask before you go to recovery mode again.

---

### Post by 1467 on 2008-06-19
ok i got this after blkid
/dev sda5: uuid "89516682-947a-438f-9ffd-32f4597366 "type=ext3"

/dev/sdb1: uuid='825ef296-ceo3-4ee5-bbpf-odaa3p3266"type="ext3"

---

### Post by 1467 on 2008-06-19
i am using 8.04

---

### Post by forestpixie on 2008-06-19
What are the uuid's actually for, to me they are just the uuids for two partitions - do you know which relates to the new partition - was there a line in the fstab for your home or was there not one there?

I'm quite happy to help you - but you are giving little bits of information. My post 17 shows how to edit the fstab file - did you do it?

---

### Post by 1467 on 2008-06-19
#/etc/fstab 
#
#<file system> <mount point> <type> <options>     <dump> <pass>
proc            /proc         proc   defaults      0       0    
# /dev/sda5   
UUID=89516682-947a-438f-9ffd-32f4597366 /          ext3   relaytime.error

---

### Post by 1467 on 2008-06-19
/dev/sda5 is ubuntu 
/dev/sdb1 has /home on it

---

### Post by 1467 on 2008-06-19
no /dev/sdb1 was not in the fstab file

---

### Post by forestpixie on 2008-06-19
Ok I assume then that sdb1 is where you have put your new home partition, if that is not the case let me know the result of this command

```
fdisk -l
```

Boot into recovery mode and drop to a root prompt.

open the file to edit it after it has been backed up - 

```
cp /etc/fstab /etc/fstab.1906
```

```
nano /etc/fstab
```

File will now be open for editing, add these lines to the end

```
#dev/sdb1
UUID=825ef296-ceo3-4ee5-bbpf-odaa3p3266 /home  ext3  relatime  0  2
```

then close the file and reboot

Ctrl+O, enter
Ctrl+X

reboot

Make sure you copy the file as it is written, for example you gave me 

> UUID=89516682-947a-438f-9ffd-32f4597366 / ext3 relaytime.errorrelaytime should be relatime :) - I know you are writing these things down to post them but make sure you write commands from me down correctly :D

---

### Post by 1467 on 2008-06-19
k

---

### Post by 1467 on 2008-06-19
and it works thank you vary much !!!!!

---

### Post by forestpixie on 2008-06-19
No problem - glad to be a help.

---

