---
title: "[SOLVED] Need Serious Help Here !!!!!!!!"
date: 2007-10-20
forum: General Help
---

### Post by jrharvey on 2007-10-20
I recently installed gutsy on an already existing 5G partition to test it out. I have fiesty on a seperate partition and after the gutsy install I get a crazy error when booting fiesty. PLEASE SOMEONE HELP ME GET FIESTY BACK. My IM is jrharvey59232210 if you want to IM me.

*Checking file systems.....
fsck 1.4-WIP (14-Nov-2006)
fsck.ext3: unable to resolve 'UUID=18aaedea-e445-4a8a-9a2a-71d149b3879e'
fsck died with exit status 8
                                                                                [fail]
*file system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
*A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
Give root passwork for maintenance
(or type control-D to continue):

---

### Post by jrharvey on 2007-10-20
bump

---

### Post by jrharvey on 2007-10-20
Please Help!!!!!!

---

### Post by jrharvey on 2007-10-20
1

---

### Post by louieb on 2007-10-20
Did the same to me Gutsy install changed the UUID of its partition. Try cntl+d. It should resume booting Feisty. 
Check /etc/fstab and fix the UUIDs as needed.
[http://louboldt.com/ilinuxmisc.htm#uuid](http://louboldt.com/ilinuxmisc.htm#uuid)

---

### Post by jrharvey on 2007-10-20
Thank you soooooo much for your reply, I hope it works.

---

### Post by jrharvey on 2007-10-20
Im confused about what I should do once I open the UUID. Do I need to change sda7 to something else????

---

### Post by jrharvey on 2007-10-20
this is what I get when I display UUID

jrharvey@jrharvey-desktop:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-10-20 17:00 19793c60-c124-44f6-ab15-b5ee66f5e1cf -> ../../sda6
lrwxrwxrwx 1 root root 10 2007-10-20 16:59 254d9b71-c2ea-400f-b926-f0c6b75bfe09 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-10-20 17:00 2C88743C8874071C -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-10-20 21:00 3F41-17EC -> ../../sdf1
lrwxrwxrwx 1 root root 10 2007-10-20 16:59 406EC89E6EC88E5A -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-10-20 16:59 ebf53312-fd34-4fc6-adeb-5a8da1b85da4 -> ../../sda7

---

### Post by chillman88 on 2007-10-20
there should be a UUID for your drives in each of your /etc/fstab files, i believe that by copying the UUID for your fiesty drive, from your Gutsy install's fstab file to your Fiesty's fstab file, SHOULD be what you need to do. I'm not 100% sure, but it sounds like the most reasonable approach.

Chris

---

### Post by jrharvey on 2007-10-20
Ok im not sure i understand. Copy from gutsy and paste in fiesty???? is that what you are saying???

---

### Post by chillman88 on 2007-10-20
basically, but not the whole file... what drive is your fiesty drive? sda7?

---

### Post by jrharvey on 2007-10-20
im sorry can you walk me through this maybe. this is my fiesty file

---------------------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=406EC89E6EC88E5A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
#UUID=2C88743C8874071C /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=18aaedea-e445-4a8a-9a2a-71d149b3879e /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=19793c60-c124-44f6-ab15-b5ee66f5e1cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

----------------------------------------------------------------------------------------------

this is my gutsy file

-----------------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=254d9b71-c2ea-400f-b926-f0c6b75bfe09 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=406EC89E6EC88E5A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 /media/sda7     ext3    defaults        0       2
# /dev/sda6
UUID=19793c60-c124-44f6-ab15-b5ee66f5e1cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

----------------------------------------------------------------------------------------------------------

---

### Post by chillman88 on 2007-10-20
Weird, they have the same UUID? hmm... let me think about this, maybe someone else will step in here for a minute and solve it while i think about it

---

### Post by chillman88 on 2007-10-20
are you sure you have the correct file order? the top is fiesty, and the bottom is gutsy, right?

---

### Post by jrharvey on 2007-10-20
yes!!! I double checked and it is correct. BTW thanks for your help.

---

### Post by g2g591 on 2007-10-20
try changeing 
UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 /               ext3    defaults,errors=remount-ro 0       1
to
# /dev/sda7
 /dev/sda7 /               ext3    defaults,errors=remount-ro 0       1
its a quick and dirty hack, so if your fiesty changes from sda7, like if you delete /dev/sda1-6, you would have to change it to whatever partation number it is then

---

### Post by chillman88 on 2007-10-20
Try replacing THIS in your fiesty...

# /dev/sda5
UUID=18aaedea-e445-4a8a-9a2a-71d149b3879e /media/sda5 ext3 defaults 0 2

with THIS 

# /dev/sda5
UUID=254d9b71-c2ea-400f-b926-f0c6b75bfe09 /media/sda5 ext3 defaults 0 2

That SHOULD solve it, and btw, i enjoy contributing to the community! :)

---

### Post by chillman88 on 2007-10-20
Try HIS first, that may be best

---

### Post by jrharvey on 2007-10-20
> **g2g591 said:**
> try changeing 
UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 /               ext3    defaults,errors=remount-ro 0       1
to
# /dev/sda7
 /dev/sda7 /               ext3    defaults,errors=remount-ro 0       1
its a quick and dirty hack, so if your fiesty changes from sda7, like if you delete /dev/sda1-6, you would have to change it to whatever partation number it is then

What do you mean a quick and dirty fix??? is there a better way that wouldnt cause me trouble in the future??

---

### Post by jrharvey on 2007-10-20
OMG I love you guys more than anyone else right now :) haha, just kidding but seriously it worked. THank you soooooo much. THis is so stupid though, why would gutsy do this. Grrrrr the more I use gutsy the more pissed off i am. Gutsy works great on my girlfriends laptop but its just a pain for my desktop.

---

### Post by chillman88 on 2007-10-20
just curious, which did you do?

it's not a big deal, just wanted to make sure mine worked if that's the way you did it!

---

### Post by jrharvey on 2007-10-20
no offense to the other guy but i used yours first. I didnt understand the other one.

---

### Post by jrharvey on 2007-10-20
I dont like gutsy right now but i love this forum. Now all i have to do is reinstall my nvidia drivers but thats no biggy. Just curious, How did you know to do this? What did you switch?

---

### Post by chillman88 on 2007-10-20
Honestly, it made sense that gutsy would have made the changes, so i looked for the differences between the two, and had you move the data from gutsy to fiesty! 

BTW: If you compile a new kernel and then try to install the nvidia drivers, you may have problems ( i know i did! )

---

### Post by louieb on 2007-10-21
Glad you got it figured out.
I could have been clearer but the stuff on my web page are just notes to myself on how to fix things I have run across in my 1-1/2 years of using Linux.  
 
Fstab can refer to a partition by device name or uuid
```
 
# /dev/sda7 using the UUID identifier 
UUID=ebf53312-fd34-4fc6-adeb-5a8da1b85da4 /               ext3    defaults,errors=remount-ro 0       1
# or the older more common way 

 /dev/sda7 /               ext3    defaults,errors=remount-ro 0       1

```Ubuntu started using UUID in /etc/fstab starting with Edgy. First noticed that swap wasn't being used after I used hibernation on my laptop. Found that formating or resizing a partition would change the UUID of a partition.  Guess we'll just have to deal with it Don't know if it a bug or if it was designed to work that way.

---

