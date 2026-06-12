---
title: "Cannot change ownership of /windows drive even in root mode! Help!"
date: 2005-06-15
forum: General Help
---

### Post by Mr.Auer on 2005-06-15
Im a totally new user to Ubuntu. I have dual OS installed, XP on other HD, Ubuntu on the second hd. I have one partition on the second HD thats using FAT 32, and this partion is visible both in windows and Ubuntu. But I cant change the ownership of this folder, and i cant allow writing to this disk even when im logged in as root user. I can see the Permission tab, but if i click on the Write allow, the check just disappears. When trying sudo chown <user> /windows it just says cant change ownership. And im in root mode. Im helpless now, someone please give a hint. I tried everything in the How-to's...

---

### Post by desdinova on 2005-06-15
Is it NTFS?

---

### Post by Mr.Auer on 2005-06-15
No, i set it up as FAT 32, and i can read everything in the drive, and when im logged in as root i can also write in the drive, but i cannot give other users or groups writing rights. So everything works fine when im logged as root: i have read,write and execute, but it wont allow me to change the settings for other users/groups. I can see the option box for write too, but if i try to check it it wont allow. edit: i have 30 gb hd with XP on it, formatted to fat32. Then i have 2nd hd 120gb, split to 20 gb Linux, 10 gb swap, and 90 gb FAT 32. Windows sees this 90 gb drive and can use it correctly. I have simple file sharing on in XP and i havent changed any ownerships from win, and I created all the partitions on 120 gb drive with Ubuntu installers partitioner.

---

### Post by desdinova on 2005-06-15
can you list your /etc/fstab

---

### Post by Mr.Auer on 2005-06-15
how do i do that...  ](*,)

---

### Post by desdinova on 2005-06-15
[QUOTE=Mr.Auer]how do i do that...  ](*,)[/QUOTE]
 from a console

sudo cat /etc/fstab


highlight it with the mouse - cut and paste

---

### Post by Mr.Auer on 2005-06-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /windows        vfat    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0

the drive in question is hdb6. /windows

---

### Post by desdinova on 2005-06-15
[QUOTE=Mr.Auer]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /windows        vfat    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0

the drive in question is hdb6. /windows[/QUOTE]
 For this line

 /dev/hdb6       /windows        vfat    defaults        0       0

change it to

 /dev/hdb6       /windows        vfat users,rw        0       0

---

### Post by Mr.Auer on 2005-06-15
Uh..i directly change the file /etc/fstab? with a text editor? and then save again?

---

### Post by desdinova on 2005-06-15
[QUOTE=Mr.Auer]Uh..i directly change the file /etc/fstab? with a text editor? and then save again?[/QUOTE]
 Yep easiest way would be 

sudo gedit /etc/fstab

---

### Post by Mr.Auer on 2005-06-15
Now i get this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /windows        vfat    users,rw        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

but i still cant seem to get the Write options on :( did the edit and saved the file..Huoh..it aint easy to begin with this :/

---

### Post by Mr.Auer on 2005-06-15
Ive been fiddling with this 12 hours now...need some coffee..real coffee :D

---

### Post by desdinova on 2005-06-15
[QUOTE=Mr.Auer]Ive been fiddling with this 12 hours now...need some coffee..real coffee :D[/QUOTE]
 umount /dev/hdb6
then
mount /dev/hdb6

and try to write again

---

### Post by Mr.Auer on 2005-06-15
i cant unmount it, it says Device is busy twice..Now the HD appears in my Computer too as 90 gb HD (it didnt before, it only showed in File system/windows/), but still no luck with the write permission. I even logged in again and tried the umount/mount again.

Is there some reason i couldnt always log on as root, then i wouldnt need to change the permissions? Since root has all privileges already? Does this pose a security risk or something? Im the only person using this comp..

---

### Post by desdinova on 2005-06-15
Logging on as root all the time is a big security risk - its so easy to damage all your files

try changing the "users" to "user"

 /dev/hdb6       /windows        vfat    user,rw        0       0


   user   Allow  an  ordinary user to mount the file system.  The name of the mounting user is written to mtab so that he can unmount the file system again.  This option implies the
                     options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line user,exec,dev,suid).

              users  Allow every user to mount and unmount the file system.  This option implies the options noexec, nosuid, and nodev (unless overridden  by  subsequent  options,  as  in  the
                     option line users,exec,dev,suid).

---

### Post by desdinova on 2005-06-15
The equivalent line on my other pc for my wife is

*/dev/hdb6  /windows  vfat  rw,user,owner,suid,exec,umask=0000  1 2* Also 

sudo chmod 777 /windows

---

### Post by Mr.Auer on 2005-06-15
still no bonus.... :( :(

---

### Post by desdinova on 2005-06-15
[QUOTE=Mr.Auer]still no bonus.... :( :([/QUOTE]

I get a feeling you may need to reboot as it said it couldn't un mount it - therefore it cannot re-mount it with the changed options...

---

### Post by Mr.Auer on 2005-06-15
will try complete reboot. brb or i hope not :)

---

### Post by Mr.Auer on 2005-06-15
nope, reboot didnt help..any other suggestions..does it matter that its /windows, what if is selected /dos when partitioning it? would it matter?

---

### Post by Mr.Auer on 2005-06-15
Seems i cant get it to work..i tried all your instructions, no help..no way can i get write permission for other than root user.. :( I suppose ill just have to login as root every time then and be careful not to delete system files :D
But if someone has an idea, plz tell me..and keep it simple so a newbie to linux can understand..Ive never used OS that needs a lot of command line configuring..All my experiences are c64, atari STFM (until a year ago!) :) and XP..not that i like the way xp handles things either, thats why i installed this ubuntu..I suppose ill have to spend a few days reading..this just feels a lil odd, i suppose your directions should have worked? Just feels like the changes to the fstab file had no effect at all, had no rights even after adding the line instructed..

---

### Post by desdinova on 2005-06-15
Did you reboot after - just to force the new settings to take effect?

---

### Post by Takis on 2005-06-15
Try changing it to this (this is exactly what I have. BTW, ff you browse using Nautilus or Konqueror (or something similar) and browse to that drive, graphical programs tend to forget to advise the vfs once they've finished. Hence, umount keeps complaining that something's using it. You'll typically need to reboot to do this remount.):
```

/dev/hdb6       /windows  vfat    defaults,umask=000      0       0

```

---

### Post by Mr.Auer on 2005-06-15
Yeah, now it worked! Pasted just that line there in place of the original hdb6 one, rebooted and now it lets me change the Write on allow... :) Thanks for help!
(i just have a feeling im gonna be having an interesting time with this..now i cant get mp3 support done..and i thought this would make life easier..guess not! back to reading the fine manuals - since when did that f mean fine?!?)

---

### Post by desdinova on 2005-06-15
And thats why we enjoy using linux ;-)

---

