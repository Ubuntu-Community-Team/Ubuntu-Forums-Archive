---
title: "Partition Fat 32"
date: 2006-08-12
forum: General Help
---

### Post by Donnut on 2006-08-12
Hi.  I am trying to add fat 32 writing to users, and nautilus wouldn't do it, I opened it in sudo and got the following error:

** (nautilus:5716): WARNING **: Hit unhandled case 24 (Operation not permitted) in fm_report_error_setting_owner

What do I do?

---

### Post by jordilin on 2006-08-12
> **Donnut said:**
> Hi.  I am trying to add fat 32 writing to users, and nautilus wouldn't do it, I opened it in sudo and got the following error:

** (nautilus:5716): WARNING **: Hit unhandled case 24 (Operation not permitted) in fm_report_error_setting_owner

What do I do?

You can write to fat32 out of the box with any Linux, so I don't understand when you say 
> I am trying to add fat 32 writing to users

---

### Post by ifokkema on 2006-08-12
If you mean that the partition isn't mounted rw for you, take a look at the umask, uid or guid settings you can provide in /etc/fstab. See `man mount`.

---

### Post by Donnut on 2006-08-13
Well, as sudo, I can write to fat32, but only as a user I can't.  You know if I put in the command "sudo nautilus" it will write, but without being the super user it won't.

---

### Post by njzillest on 2006-08-14
use chmod.. Im not sure if this will help.. I belive the file is owned by root.

```
root@root-laptop:/media/hda1# chmod +r+rw+x+w /media/hda1
chmod: changing permissions of `/media/hda1': Read-only file system
```

From what i understand, this may not work. If not.. set the permission in the /etc/fstab 

show us what it looks like

you might need to use umask=0222

Hope this helped

---

### Post by ifokkema on 2006-08-14
> **njzillest said:**
> use chmod.. Im not sure if this will help.. I belive the file is owned by root.
Could be the case: use the uid and umask settings in /etc/fstab. See `man mount`.

> **njzillest said:**
> ```
root@root-laptop:/media/hda1# chmod +r+rw+x+w /media/hda1
chmod: changing permissions of `/media/hda1': Read-only file system
```
What are you trying to do?
You need to use chmod -R to recurse into all directories. The rest of the syntax looks really weird. What you probably mean is
```
chmod -R +rwx /media/hda1
```

But seriously, Donnut, you need to have the disk mounted under your username, and with write privileges for you. See /etc/fstab and look for the line describing your hard drive. Now add the uid and umask options. See `man mount` and look for "mount options for vfat" for more info on these.

---

### Post by MarinaraOfDeath on 2006-08-17
There could be two problems. The first would be that root owns the directory you have your FAT32 partition mounted on. The second could be the umask you have set in /etc/fstab for that directory. Since you can read and write using *sudo nautilus*, I would bet that the problem is the first. I also had this at one point, and here's what I did to solve it.

[LIST=1]
[*]The first thing to do is 
```
System --> Administration --> Disks
```
In the window that pops up, click on the tab labeled *Partitions*. Make sure that the partition is unmounted (i.e., click the button that says *Disable* if the partition is enabled).

[*]Check who owns the directory you are using to mount the FAT32 partition. In my case, this directory is called /winshare, and it is located at the top level of the file system along with /home, /usr, and all the other directories created just under / during installation.
> ls -al /
...
drwxr-xr-x  24 aramis aramis  16384 1969-12-31 18:00 winshare/
...
From left to right, the things you need to know are the permissions, the owner, the group, and the name of the directory. Originally both the owner and the group were root, which is what causes the behavior you are trying to get around.

[*]Next up change ownership of the directory (this is why it's important that the partition be unmounted before this). The version I used for mine is ```
chown -R aramis:aramis /winshare
```
For more info, type man chown in a teminal window and read the man page before doing this; once inside the man page, type q to exit. I may eventually change the group to users, but I haven't decided yet.
[*]Now alter /etc/fstab to match.
[LIST]
[*]Backup: sudo cp /etc/fstab /etc/fstab_backup
[*]Open file for editing: sudo gedit /etc/fstab
[*]Make a copy of the line that gives instructions for mounting your partition, comment the original by putting a # in front of it, and start editing the permissions on the partition. Here's what the entry for one of the partitions I use in both windows and Ubuntu looks like
> /dev/hda7 /oldIDL vfat defaults,utf8,umask=000,uid=1000,gid=46,auto,rw,users 0 1
#/dev/hda7 /oldIDL vfat defaults,utf8,umask=007,uid=1000,gid=46,auto,rw,user 0 1
This is where it pays to figure out unix permissions and umasks. Let's say you start off with 777 for a file (a code in octal math that says owner:group:everyone else can read/write/execute). The umask subtracts off of that (again, in octal) to get the actual permissions, which is why umask=0222 lets owner:group:everyone else read and write. In the case of a directory, such activities correspond to creating or editing a file in the directory.
[*]Save /etc/fstab and exit gedit.
[/LIST]
[*]Now repeat the first step to pop up the disk administration window, but that this time click to button that says *Enable* for your FAT32 partition.
[/LIST]

You shouldn't even have to reboot. Good luck.

---

