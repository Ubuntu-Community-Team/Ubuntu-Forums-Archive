---
title: "{drive:} refers to unavailable location"
date: 2008-02-10
forum: General Help
---

### Post by robb234 on 2008-02-10
yesterday i download some files and save it into my ubuntu partition,
and i was able to play/use those files...
then i move those files into my D: drive (windows partition), and when i tried to play the file, it says :

{drive:} refers to a location that is unavailable. It could be on a hard drive on this comp or on a network. blablabla

i have never encountered this problem before,
i mean i often download files at ubuntu and then move it to windows partition and still able to play it.
but now i can't seem to do so anymore
i have browsing around and googling, but no luck

anyone has any ideas about this ?
please share

thx :)

P.S. : I run a dual-boot of xp and ubuntu on the same single hdd

---

### Post by ajgreeny on 2008-02-10
Sounds as if your windows partition is not mounted.  Show us the output of ```
cat /etc/fstab
``` and we can possibly help you get it mounted and usable again.  What did you do to make the difference to the way things were?

---

### Post by robb234 on 2008-02-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2fd5f8eb-fb6e-42b2-8241-842a71b07d88 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=10C43442C4342C7A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=F21014C4101491A9 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=8796c2b5-fccb-4c95-8ed9-2f5285f55dc9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

i didn't make any changes to ubuntu or windows lately,
in fact, i have not logon to my ubuntu for quite some time.

---

### Post by ajgreeny on 2008-02-11
Well, if the UUID for the disks is correct, then your windows partition should be mounted and the files should be playable with most things, but not, I believe amarok, as it needs write permission.  If that is the program you are using to play them, try another.

Sorry, but I don't think I can help any more, though I  agree it seems strange that you can't play the files when you used to be able to.

---

### Post by robb234 on 2008-02-12
maybe i forget to mention this,
the folder containing that particular files is not even accessible,
let alone seeing the files...
i mean the properties of that folder in xp says it's : 0 bytes of data (folder is empty)
so whenever i double-click on it, it says that unavailable location blablabla

any idea about this ?

it seems like formatting might fix it, but until it can be fixed, formatting will be my last choice :)

---

### Post by ajgreeny on 2008-02-12
So do you mean it's an ntfs folder/partition that even windows XP can't read, or do you really mean it's empty/no files in it?

---

### Post by robb234 on 2008-02-14
> **ajgreeny said:**
> So do you mean it's an ntfs folder/partition that even windows XP can't read, or do you really mean it's empty/no files in it?

yes, i guess

so it's like this,
my windows D: drive including all folder inside it is accessible from ubuntu,
now there's this mp3 folder, which was created when i was logon in ubuntu
and of course is accessible from ubuntu
but when i logon into windows, it cant read that mp3 folder, which is unusual

i never encounter this before, i dont know if this has something to do with my xp having this error recently :

"generic host process for win32 service error"

btw, i really appreciate your trying to help me  :)

---

### Post by skibukow on 2008-06-16
> yesterday i download some files and save it into my ubuntu partition,
and i was able to play/use those files...
then i move those files into my D: drive (windows partition), and when i tried to play the file, it says :

{drive:} refers to a location that is unavailable. It could be on a hard drive on this comp or on a network. blablabla


I got this same thing also on a Ubuntu/Xp dual boot and found that the name of the directory was the issue.  

In this case "M.I.A." wrote incorrectly (due to the periods I assume) but worked fine when I rewrote it as "MIA".  Now in order to delete it I think I just have to go through Ubuntu.  

Is this technically a bug or what?  Possibly Ubuntu should do some truncating of illegal filenames. 

-Skibukow

---

