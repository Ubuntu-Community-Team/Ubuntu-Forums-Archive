---
title: "Need help trying to install wine on a primary Vfat partion."
date: 2005-07-18
forum: General Help
---

### Post by Omnios on 2005-07-18
Hi I have a strange lay out my main drive is devided into two primary partitions one ntfs with my hardly used XP and another drive that is mainly for my documents such as my music stc shared with Ubuntu. I just downloaded the backport wine and am trying to set up wine so the fake windows is on the vfat partition mainly because its got 52gigs of space as apposed to my 34 gigs of free space on my Linux partion. (I must be closterfobic lol). Anyways I tryed confifing wine to install and it gave me a it cant write to it though it did deposit a wine and program files folder there. The main problem is im trying to mount it in root and the users where groups one time and root the other with full read write permitions. I also tryed to install it on the drive as an exzisting partition but it gave me a warning that it wanted to errase everything on the partition. 

 Enclosed is my fstab is there a way of setting it up so wine can install. I think I have to have me as user to do this.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2       /media/vfat     vfat    rw,users,gid=users,umask=000,       0       0
``` 

 Any help would be apreciated. This set up worked well showing a drive in my computer etc.

---

### Post by amohanty on 2005-07-18
After you install wine, look at the wine.conf file, usually in your ~/.wine/config/

There you can add another fake windows drive to it. Link to man page for wine.conf:

[http://www.die.net/doc/linux/man/man5/wine.conf.5.htm](http://www.die.net/doc/linux/man/man5/wine.conf.5.htm)

HTH

AM

---

### Post by Omnios on 2005-07-18
While trying to install wine on a seperate vfat partition I got an Idea and created a wine file on the partition trying to emilate the home directory by changing the owner and user to my user name in root. It gave me a you do not have privilages to rename owner and group. If I could get a wine file with ownership and group to my user name I should be fine. Think its the way I set up fstab to have a drive icon in Computer causing the problems as owner is root and user is groups. Any help would be greatly apreciated.

---

### Post by amohanty on 2005-07-18
--
by changing the owner and user to my user name in root. It gave me a you do not have privilages to rename owner and group.
--

I think you are not allowed to run chown and chgrp as a normal user. You have to sudo it.


And try this in your fstab in the place of what you already have:
/dev/hda2       /media/vfat     vfat    rw,users,auto,gid=users,umask=0200,       0       0

This will automount the drive and also allow users to write and create files. Also make sure that you belong to the users group. By default Ubuntu creates a new group by the username and that is your primary group not 'users'

--
created a wine file on the partition trying to emilate the home directory by changing the owner and user to my user name in root.
--

What do you mean by this? Did you create a wine.conf in the drive that is mounted to be fake_windows.. ???


HTH

AM

---

### Post by Omnios on 2005-07-18
Using /usr/bin/winesetup (the old .wine.config is no longer used) there is an option of using an exsisting windows drive or making a fake windows. The using an exsisting drive comes with a warning that is will erase the contents of that drive so I desided to make a fake windows on my vfat drive.

 ALso it will not allow me to change the ownership and group of directories within the Vfat drive which is a problem as I will have to do a lot of changes within wine. (tryed changing a wine directory to mu username -not the drive file but a file within it)

---

### Post by Omnios on 2005-07-18
> And try this in your fstab in the place of what you already have:
/dev/hda2 /media/vfat vfat rw,users,auto,gid=users,umask=0200, 0 0 

 This didnt work but is step in the right direction. Basicly I think I have to mount vfat the same as a home directory that is on its own partition to accomplish what I am trying to achieve. This will actualy be better for me as my vfat primary partition is supposed to be a sort of mixed /home, My Documents file system and not for systems though I would like to get wine working on it. Thanks for the help so far though.

---

### Post by amohanty on 2005-07-18
The thing is that vfat does not have any idea of ownership so everything is mounted as root. Also permissions are directory based and since the root mount is something it does not know about (linux mounts it, has nothing really to do with vfat) permissions are sort of meaningliess. Linux essentially fakes it. 

If you mount it the way I mentioned, then people belonging to the users group will be able to rw to it. If you are the only user you probably should set the uid too.

Also keep in mind that by default you do not belong to the users group, you belong to a group by your own username. You can reset that to users via System->Administration->Users and Groups.

Finally if you want to do some permissions stuff on the vfat drive, for some reason, sudo doesnt seem to work. Login as root (ie in a term, do su and then do your operations).

HTH
AM

---

### Post by Omnios on 2005-07-18
Thanks! In wine setup you have to do it as your username as it will config and install the files under root. The problem was that it would not intall all the fake windows as such. Which boils down to write permitions. Ill try it with the user mod and see how it works.

 Edit: Whent over the error I have to be the owner of the file to install the fake windows in Vfat

---

### Post by amohanty on 2005-07-18
> Thanks!  

No problem. Let me know how it all works out...

AM

---

### Post by Omnios on 2005-07-18
Is there anyway of mounting the vfat directory with username as the owner?

---

### Post by amohanty on 2005-07-18
IN fstab instead of this:
/dev/hda2 /media/vfat vfat rw,users,auto,gid=users,umask=0200, 0 0
put this:
/dev/hda2 /media/vfat vfat rw,users,auto,uid=XXX,gid=users,umask=0200, 0 0

where XXX is your userid. To look up your userid goto System.->Administration->Users and Groups.

One done, unmount the vfat drive:
>> sudo umount /media/vfat

then reload fstab:

>> sudo mount -a

This will mount all files and dirs in /meda/vfat with you as owner.

HTH
AM

---

### Post by Omnios on 2005-07-18
That did the trick! Thanks. But one little problem Now I am the owner but it booted as a no exe wich means I can't run executables as owner on the drive which was ok when it was owned by root as the exe is only affecting the owner.  Also I couldn't unmount even with sud it ran the unmount in sudo but nothing happened. Seems it only wan't to do changes with reboots, which isnt realy that big of a problem for me as long I get it working.

---

### Post by amohanty on 2005-07-18
add exec to the list of options in column 4 rw,users,exec....
also a complete explanation of fstab options:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

if it does not allow a umount as sudo, in a teminal type:
>> su

it will respond:
Password:

type in password and then do your mount an unmount. Also as a precaution, I have setup my root password differently than my usual password by:
>> sudo passwd

and I do all things via the method mentioned above. There are certain things you cannot do with sudo.

HTH

AM

---

### Post by Omnios on 2005-07-18
Oopsies made a boob I realy must look carefully before I act. It does have exacutable rights it was owner write privelages that it didn't have. Got most of ot solves so far except for the owner which is me not having write privlaages. I looked at the link looks interesting Ill try to figure it but found that web site a bit lacking thenn again its better than nothing lol.

---

### Post by amohanty on 2005-07-18
Look at the umask option. Its the complement of what the permission will be so if umask=0 then all file perms will be 777, a umask of 0200 means it will be 500 which means r-x------ for all files so figure out what you want and set it to that. Also theres an option called dmask for directories.

AM

Edit: oops a umask of 0200 means it will be 500  sorry I mean 577 r-xrwxrwx.

---

### Post by Omnios on 2005-07-18
Thanks a bundle that did the trick. I kind of figured that was the problem but I dont like fiddling to much with stuff I bearly know probably would have tryed putting 777 in it lol.  I laready have about 3 reformats under my belt lol. Anyways thanks!

---

### Post by Omnios on 2005-07-20
Well spent alot of time trying to get my documents drive working with wine but as it turned out wine would not intall a fake drive onto it. Learn't a lot though about mounting drives though.

---

