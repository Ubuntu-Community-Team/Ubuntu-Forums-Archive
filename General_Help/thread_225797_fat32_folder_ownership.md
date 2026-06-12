---
title: "fat32 folder ownership"
date: 2006-07-30
forum: General Help
---

### Post by Martango on 2006-07-30
How do I change the ownership of my fat32 formatted partition /media/fat32/ so I will be the owner? The file owner is set to root file group is set to plugdev. When I try to change one of them with the sudo nautilus I get the error: "The owner could not be changed. Sorry, couldn't change the owner of "fat32" / You do not have the permissions necessary to change the group of "fat32".

---

### Post by kinematic on 2006-07-30
sudo chown -R yourusername:yourusername /media/fat32
sudo chmod -R 755 /media/fat32
that should do it if i remember correctly but i don't know if it'll work because fat32 doesn't preserve permissions in the file system like a linux file system does.

---

### Post by Martango on 2006-07-30
Thanks, but the

> **kinematic said:**
> sudo chown -R yourusername:yourusername /media/fat32

returns:

> :~$chown: changing ownership of `/media/fat32': Operation not permitted

for every file on the partition.

---

### Post by RAOF on 2006-07-30
The answer, of course, is that you **can't**.  FAT32 doesn't support ownership/permissions.

So, what you're after is the effective permissions that get set by mount.  Check out /etc/fstab - there'll be a line something like
```
/dev/hda3    /media/fat32   vfat   defaults   0   0
```
And you want to change "defaults" (or whatever that bit looks like, it could be "rw, somethingelse, etc" (and only that bit)), to have "uid=*your_numeric_userid*".  Your userid is **probably** "1000", but you should be able to get it by typing "id" at a terminal.

---

### Post by RRS on 2006-07-31
Change your fstab to;
```
/dev/..............vfat  umask=000,uid=1000,gid=1000  0  0
```

This should make you the owner.

---

### Post by Martango on 2006-07-31
Thanks!

I checked my userid and it's 1000, the line in fstab look like this
```
/dev/sda5       /media/fat32     vfat    defaults,utf8,umask=007,gid=46 0       1
```

Should I change that to

```
/dev/sda5       /media/fat32     vfat umask=000,uid=1000,gid=1000  0  0
```

I'm a newbe so I can not decipher all the codes, "defaults", "utf8" etc. and what about the number of spaces, is that important?

---

### Post by RRS on 2006-07-31
Here's mine:
```
/dev/hda6       /media/common vfat iocharset=utf8,umask=000,uid=1000,gid=1000 0 0
```

Just substitute "sda5" and "fat32" for "hda6" and "common".

I think as long as there is a space where one is shown I don't think the number of spaces matter, I often reduce 5 or 6 to 1 or 2 in order to keep everything "looking orderly"

Also, since my typing skill is marginal at best, for things like this I often copy and paste an entire line and then just change the individual characters as needed.

And don't forget to comment out or delete the original entry for sda5.

edit:typos

---

### Post by Martango on 2006-07-31
Great thanks!

It's working fine, but that made a new problem. Now when I change the permissions on the fat32 drive in the GUI my settings will not be saved and when I reboot they will change back to default (all persmissions marked).

---

### Post by RRS on 2006-07-31
So, can I take it you don't normally want the partition to have all permissions, just occasionally?

Since I'm the only user on my machines it doesn't matter but I'm guessing you may have multiple users and only want full permissions for yourself.

I'm sure you can change the uid and gid numbers to only you but I can't help you with the correct entry.

Another less convenient method would be to edit you fstab when needed. 

If you commented the original line rather then deleting when you changed it to the suggested line, simply uncomment it and comment the new one, then remount.

Whenever you need to write to the drive just change which line is commented.

Though a rather clumsy way to do things, if you only occasionally want full permissions it might be the easiest.

Seems likely someone else could suggest a more elegant solution but this should work till then.

---

### Post by RAOF on 2006-07-31
> **Martango said:**
> Great thanks!

It's working fine, but that made a new problem. Now when I change the permissions on the fat32 drive in the GUI my settings will not be saved and when I reboot they will change back to default (all persmissions marked).

You **can't** change permissions on the fat32 drive.  FAT32 has **no concept** of file permissions.  The only permission settings you can change are those in the fstab:
1) umask - the octal values of the permissions to **not** give all files.  
   1 = execute 
   2 = write
   4 = read

Add them up, and you have your digit.  So 7 = no permission, 1 = read+write, 3 = read, etc.  The three digits are, in order, user-group-others.
So umask=027 gives: all permissions to the owner.  Read+execute permissions to the group.  No permissions to everyone else

2) uid= - The numeric identifier of the user who will own all the files
3) gid= - The numeric identifier of the group who will own all the files.

---

### Post by RRS on 2006-07-31
> **RAOF said:**
> You **can't** change permissions on the fat32 drive.  FAT32 has **no concept** of file permissions.  The only permission settings you can change are those in the fstab:
1) umask - the octal values of the permissions to **not** give all files.  
   1 = execute 
   2 = write
   4 = read

Add them up, and you have your digit.  So 7 = no permission, 1 = read+write, 3 = read, etc.  The three digits are, in order, user-group-others.
So umask=027 gives: all permissions to the owner.  Read+execute permissions to the group.  No permissions to everyone else

2) uid= - The numeric identifier of the user who will own all the files
3) gid= - The numeric identifier of the group who will own all the files.

Thanks for the explanation. 

As a sole user it's not a subject I've looked into deeply so hopefully this will help Martango solve his problems.

I'll also add it to my own note collection.

---

### Post by Martango on 2006-08-01
That was exactly what I was looking for, but didn't know how to do it. There are multiple users on my system, and I want to be the only one to have access to the fat32 partition.

Thanks a lot! :D

---

### Post by Steven_B on 2006-08-02
> 1) umask - the octal values of the permissions to not give all files.
1 = execute
2 = write
4 = read

Add them up, and you have your digit. So 7 = no permission, 1 = read+write, 3 = read, etc. The three digits are, in order, user-group-others.
So umask=027 gives: all permissions to the owner. Read+execute permissions to the group. No permissions to everyone else

Isn't it the other way around?  If I recall correctly, 7 grants all permissions, 0 grants none.

---

### Post by carlosqueso on 2006-08-02
> **Steven_B said:**
> Isn't it the other way around?  If I recall correctly, 7 grants all permissions, 0 grants none.

For chmod commands you are correct.  However, in the fstab file, it's backwards for some reason so 0 is all, 7 is none.

---

### Post by RAOF on 2006-08-02
> **carlosqueso said:**
> For chmod commands you are correct.  However, in the fstab file, it's backwards for some reason so 0 is all, 7 is none.

Furthermore, I belive that these meanings depend upon **which** filesystem type you're mounting :(.

---

