---
title: "external FAT32 drive, permissions"
date: 2006-11-07
forum: General Help
---

### Post by sintheta on 2006-11-07
howdy all,

Running Ubuntu 6.06

I've got an external USB FAT32 drive that automagically mounts when I plug it in. I'd like to make some of the directories on the drive available to other users on the system.

I was previously running Fedora4, and as root just created a link from within the user's home to the desired directory on the drive (I'm sure there are security concerns with this, but I'm not too worried at the moment).

Creating the links in Ubuntu seemed to work, but the user doesn't have the permissions to cd into them.

chmoding the links to o+r didn't change the permissions, and chowning them to the user didn't change anything either.

I'm pretty sure there's something here that I don't understand.

Thanks!

David

---

### Post by pitkali on 2006-11-07
You should inspect the permissions of the mounted drive instead of links. I've just mounted pendrive to check it and I can see that all the contents have permissions 700 with user and group of my user. You should use go+rx on the contents to make them available to others (note +x - this is necessary to be able to browse directories.)

Regards,

---

### Post by sintheta on 2006-11-07
Hi Pitkali,

Thanks for the help.

I've actually tried to do that, and the permissions of the directory on the drive don't change at all! Very confusing…

D

---

### Post by taurus on 2006-11-07
You CANNOT change permissions for VFAT or NTFS!  It's just not going to work.  So if you want to allow others to read and write to it, then try to mount it with the right permissions from /etc/fstab or by hand, from a command line...

Open a terminal, Applications -> Accessories -> Terminal, and unmount it first.  

```
sudo umount /media/<whatever_the_name_is>
```
Then, edit /etc/fstab as

```
gksudo gedit /etc/fstab
```
and add the following line to it.

```

/dev/sdb1   /media/share   vfat   defaults,umask=000   0   0
(assuming that your USB drive is /dev/sdb1...

```
Now, create a mount point for it and mount the thing!

```
sudo mkdir /media/share
sudo mount -a
df -h  <-- you should see your USB drive on this list, last item
```

---

### Post by givré on 2006-11-08
taurus, don't forget that it's an external drive. If you want plug&play to work properly, you should avoid the use of fstab for it, unless you have good reasons to do so.

---

### Post by givré on 2006-11-08
> **sintheta said:**
> 
Creating the links in Ubuntu seemed to work, but the user doesn't have the permissions to cd into them.
What are the permission/ownership of the link, of the pointed directory ? Is it a symbolic or hard link ?

---

### Post by pitkali on 2006-11-08
> **givré said:**
>  Is it a symbolic or hard link ?
You can't hardlink a directory.

---

### Post by sintheta on 2006-11-08
> **givré said:**
> taurus, don't forget that it's an external drive. If you want plug&play to work properly, you should avoid the use of fstab for it, unless you have good reasons to do so.

Hey, you guys are great!

I was aware that FAT32 doesn't have perms, which makes this all the more confusing.

If I'm to avoid using fstab to keep the plug&play working, is there another option? Or is my only hope to use fstab?

Thanks!
David

---

### Post by givré on 2006-11-08
pitkali, right, stupid me :cool: 

sintheta, i don't understand, did you set up it in fstab ?

All removable device can be handle by gnome-volume-manager, which mount them by pmount. If the device is not in fstab, it mount them with default option which allow r/w support for the user (it grab further information, fs... with hal). That what we call currently the plug&play in linux. 
If the device name is in fstab, it mount it with this information. But since :
- device name (/dev/sda for exemple) is not attach to one drive. 
- people have sometimes hard time to set up there fstab.
It's better to don't set it in fstab, and let plug&play be really plug&play.

---

### Post by dannyboy79 on 2006-11-08
> **givré said:**
> pitkali, right, stupid me :cool: 

sintheta, i don't understand, did you set up it in fstab ?

All removable device can be handle by gnome-volume-manager, which mount them by pmount. If the device is not in fstab, it mount them with default option which allow r/w support for the user (it grab further information, fs... with hal). That what we call currently the plug&play in linux. 
If the device name is in fstab, it mount it with this information. But since :
- device name (/dev/sda for exemple) is not attach to one drive. 
- people have sometimes hard time to set up there fstab.
It's better to don't set it in fstab, and let plug&play be really plug&play.

Correct givre, but you have to remember, plug-n-play linux doesn't work for EVERYONE, for some odd reason, this is a problem lately, people are plugging in their external usb drives and if they are automounting, they aren't writable and they are owned by root and that's even if it's automounting! some peoeple can't even get it to automount. so, instead of sounding like a broken record and repeating the same thing, can you point out to us what we are suppose to do if when we plug in an external usb drive it automounts WITHOUT write permissions? (and yes, there is NO reference to the drive anywhere in FSTAB) if you do a search on this, you'll find tons of people who can't write to removable devices, so gvm and pmount aren't working I guess for these people so THEN WHAT DO THEY DO????? that's when I suggest the fstab entry, if not, then what.

---

### Post by givré on 2006-11-08
> **dannyboy79 said:**
> Correct givre, but you have to remember, plug-n-play linux doesn't work for EVERYONE, for some odd reason, this is a problem lately, people are plugging in their external usb drives and if they are automounting, they aren't writable and they are owned by root and that's even if it's automounting! some peoeple can't even get it to automount. so, instead of sounding like a broken record and repeating the same thing, can you point out to us what we are suppose to do if when we plug in an external usb drive it automounts WITHOUT write permissions? (and yes, there is NO reference to the drive anywhere in FSTAB) if you do a search on this, you'll find tons of people who can't write to removable devices, so gvm and pmount aren't working I guess for these people so THEN WHAT DO THEY DO????? that's when I suggest the fstab entry, if not, then what.
It's highly impossible that the drive gets owned by root, if you can point me to those people, i'd glade to talk to them, and help them.
I'm sorry if i could sound to you like i broken record, but lot's of developper works hard to make plug&play a reality in linux, and this is something that just works. And i'd like that users thinks that linux just works. If they have to make an fstab entry for anything, if they have to make an udev rules to not make conflicts, i'm sorry, that's not something that just works.
That said, something you forgot is that if it's automount with an fstab entry, it can automount without it, and with the good options (like i said, you don't have the choice, r/w for the user, but of course not for ntfs)
Now if it don't automount at all, this is an other problem.
- You may look at dmesg to see if there is not a problem with the kernel
- You may try to mount it manually with pmount-hal.
- You may check that pmount is setuid (something really important)

But anyway, point me to those people, i'll try to help.
And if you want to advice fstab for removable device, no problem, i'm not an anti-fstab, just be sure that it's necessary.

---

### Post by dannyboy79 on 2006-11-09
i may have mispoke, i don't believe it's owned by root but his problem is that he can't write to it according to this post:  Originally Posted by jalefkowit  View Post
Yes, as I mentioned above it mounts automatically, but in read only mode.  the thread is here: [http://www.ubuntuforums.org/showthread.php?t=289366](http://www.ubuntuforums.org/showthread.php?t=289366). he has posted his pmount -d and it appears as though it is terminating with status 32 so hopefully you can help. i gogled this and found nothing exciting. i am not meaning to get upset it's just that it's frustrating for you to say, it just works, when it clearly DOESN'T for people and as I said, useing the search function with something like write to usb drive or similar will show you all the people having problems.

mount point directory locked
spawnv(): executing /bin/mount '/bin/mount' '-t' 'udf' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000,umask=000,iocharset=utf8' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'udf' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000,umask=000' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'iso9660' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000,iocharset=utf8' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'iso9660' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'vfat' '-o' 'nosuid,nodev,user,quiet,shortname=mixed,async,atime,noexec,uid=1000,gid=1000,umask=077,iocharset=utf8' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 0
unlocking mount point directory
mount point directory unlocked

---

### Post by givré on 2006-11-09
> **dannyboy79 said:**
> i may have mispoke, i don't believe it's owned by root but his problem is that he can't write to it according to this post:  Originally Posted by jalefkowit  View Post
Yes, as I mentioned above it mounts automatically, but in read only mode.  the thread is here: [http://www.ubuntuforums.org/showthread.php?t=289366](http://www.ubuntuforums.org/showthread.php?t=289366). 
Thanks.
> **dannyboy79 said:**
> he has posted his pmount -d and it appears as though it is terminating with status 32 so hopefully you can help. 
pmount didn't really terminate with status 32. pmount guess the fs of the device by trying different ones, and it continue until it succeed, which is the case for vfat (status 0). The difference between pmount & pmount-hal (which is in fact the command use) is that pmount-hal will get the fs by hal.

---

### Post by sintheta on 2006-11-09
Maybe I should restate what my problem is, hopefully that'll clear some things up.

[LIST]
[*]The external USB drive mounts automagically.
[*]I, as the root user, can read/write to it just fine.
[*]There is another user, called "public", who I would also like to be able to read/write to it.
[*]public can't read/write to the drive—only I, as the root user, can access it
[*]declaring the mount in fstab would apparently fix the problem, but would screw up the plug&play nature of the USB drive (or so someone posted in this thread)
[/LIST]

So, I guess, how can I make the drive read/writable to public without using fstab?

I have the feeling that I'm just going to have to use fstab…

---

### Post by givré on 2006-11-09
sintheta, ok, your problem is different :
you want the drive to be accessible by two different users (i don't know why you would like to log as root, but i don't care), but , that is impossible with the current default option of pmount, because it set umask=077, so only the user who mount the drive have rw, the others have nothing (even if they are in the same group)(note also that if the other user umount & mount again the drive, he would have rw support)

So in that case, setting it in fstab is a good idea. When i said that it could screw up plug&play, it's because your external drive is not always map to /dev/sda (or whatever). It's more probable when you have multiple external drive, but it could also happens when you have only one.

Solutions :
- If you use edgy, use UUID= instead of /dev/sd*. To know the uuid, just check 'ls -l /dev/disk/by-uuid/'
- Create an udev rules.
- You can live without all this, but be prepare that wrong mapping could happens.

Better but long terme solution :
- Fill a bug against pmount to use umask=007 instead of umask=077. I think stupid to set a so restrictive permission.

---

### Post by Linuturk on 2006-11-13
I'd like to put my two cents in here.

I currenty have a external USB drive. It automounts nicely, but I've found I haven't been gaining disk space as I delete things. I took a look at the hidden files on the root of the drive, and found a .Trash-root on the drive (I was having problems removing files, so I opened a sudo nautilus to remove them) Apparently, nautilus is creating a .trash directory just like the one on my ~ directory.

I've tried going back in as root and deleting this .Trash-root directory, but I get lots of error messages saying I can't delete them because they are read only: (Keep in mind that as a normal user, I can read and write to this drive just fine, until I try to remove that .Trash-root directory.)

here is the output of "mount" at terminal
```
linuturk@NAABAL:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda3 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=linuturk)
/dev/sda2 on /media/WD300GB type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)


```

The last entry on this list is the external that auto mounts.

Also, I somehow managed to delete a .Trash-linuturk, but it only removed it to .Trash-root . . .

So, my question is two fold. 

a) How do I remove that .Trash directory while still maintaining plug & play?
b) How do I stop nautilus or anything from creating that .trash directory on external drives? When I remove something from them, I want it gone completely.

---

### Post by pitkali on 2006-11-14
> **Linuturk said:**
> a) How do I remove that .Trash directory while still maintaining plug & play?
You need to do it from the terminal using rm command or you could select it in nautilus and press Shift+Del - that should also work.

> b) How do I stop nautilus or anything from creating that .trash directory on external drives? When I remove something from them, I want it gone completely.
Use Shift+Del. Or edit the preferences under Edit->Preferences->Behaviour in file browser window and check the box 'Include the Delete command that bypasses... bla' and then use  the Delete command found in context menu (available after right-clicking any item).

Regards,

---

### Post by Linuturk on 2006-11-14
a) I have tried deleting the .Trash-root directory that way, and the drive reverts to a read-only state, saying nothing can be deleted. Before I try deleting it, the drive is read/write.

b) Thanks, got that.

---

### Post by dannyboy79 on 2006-11-14
> **Linuturk said:**
> a) I have tried deleting the .Trash-root directory that way, and the drive reverts to a read-only state, saying nothing can be deleted. Before I try deleting it, the drive is read/write. 
and is this after you switch to the root user? do sudo -i, enter your password and you're now logged in as root so be careful, then just rm -rf .Trash-root and bye-bye, there she goes! don't forget to type in exit so you are back to the normal user mode within that terminal session

---

### Post by Linuturk on 2006-11-17
> rm: cannot remove `.Trash-root//.Trash-linuturk/Lily Navon System Backup/Lily Navon/Local Settings/Temporary Internet Files/Content.IE5/KPGFSN8J/trans_pixel[2].gif': Read-only file system
rm: cannot remove `.Trash-root//.Trash-linuturk/Lily Navon System Backup/Lily Navon/Local Settings/Temporary Internet Files/Content.IE5/KPGFSN8J/TYPE%3~1.HTM': Read-only file system
rm: cannot remove `.Trash-root//.Trash-linuturk/Lily Navon System Backup/Lily Navon/Local Settings/Temporary Internet Files/Content.IE5/KPGFSN8J/vg[1].gif': Read-only file system

That's what I get when following your method . . .

---

