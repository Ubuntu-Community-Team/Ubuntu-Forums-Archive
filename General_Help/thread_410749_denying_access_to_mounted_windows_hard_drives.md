---
title: "denying access to mounted windows hard drives"
date: 2007-04-16
forum: General Help
---

### Post by JackiePaper on 2007-04-16
I'm kubuntu 6.10 user. I have two winxp hard drives (ntfs) mounted. 
I share this computer with someone else. 

How can I deny access from the other user to those xp-drives?

---

### Post by mac.ryan on 2007-04-16
You need to have admin privileges to accomplish that.

I would do that by editing the /etc/fstab file and namely the column with the options. There are various way you can achieve what you want. I can imagine at least two
[LIST]
[*]making the HD non-automonted so that only a user with root privileges will be able to manually mount them.
[*]setting the umask (file permission) in a way that only a given user / class of users will be able to access the files in the partition.[/LIST]The documentation is quite straightforward. To document yourself on possible options, you can type from shell:

```
man fstab
man mount
```

---

### Post by JackiePaper on 2007-04-16
i don't know how to set a user umask privilegdes (yet).

i.e if /dev/hda1 (xp drive) umask value is "007" according the fstab file. i don't know yet how to modify user's priviledges so that she cannot access in that drive. so,

i end up commenting those drives off in the fstab file. 

thanks.

---

### Post by mac.ryan on 2007-04-16
In my understanding of how umask works, the 007 combination would allow both the owner of the partition and the people belonging to its group to access the files in read/write/execute mode, while no permission (neither to read the files) would be given to other users.

If you like, you can post your full line from the fstab in here, so that we can review it together.

I have however the impression your configuration should already prevent normal users to access those drives (unless they belong to the "root group"). The easiest way would be to log in with the account of the person you share the computer with and check if she/he can or can not access those.

---

### Post by mac.ryan on 2007-04-16
Just an additional reflection...

Unix (not even to mention windows!) is not designed to offer a lot security when using the physical machine the system is installed on. This means that regardless of the mounting options you will assign to your drives, a user who would boot from any linux liveCD or windows recovery disk would be able to access your drives.

So, if your data are that much confidential, you might consider activating an HD password from the bios, or using cryptography, instead...

It might be of some use also to prevent (from the bios) the possibility to boot from CD, floppy, or USB...

---

### Post by JackiePaper on 2007-04-16
OK, here's my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=d293e5a1-ce2e-4e9b-9128-b34c672d34cb / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1
#UUID=F4883C3E883C0222 /media/hda1 ntfs defaults,nls=utf8,umask=007,loop,uid=0,gid=46,noauto,rw,nouser 0 1
# /dev/hda5
# UUID=3C78900C788FC2DE /media/hda5 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda1
# UUID=D63889D13889B0D3 /media/sda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/hdb5
UUID=e7611248-a41e-422c-95c3-f3cfa13c3135 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0

---

### Post by mac.ryan on 2007-04-16
```
 # UUID=3C78900C788FC2DE /media/hda5 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
```

The relevant bits here (the one having effects on permissions) are the following:
[LIST]
[*]**auto** means that this partition will be mounted when a command "mount -a" will be issued. AFAIK, this is what happens at boot time so - from our perspective, this partition will be always mounted, unless you change this parameter in *noauto*. **nouser** means that a normal users of your system (i.e. everybody else but the root user) will not be able to mount this partition. Of course, if a user is given the permission to use "sudo" then this rule is overridden. Its contrary is *user.* (This means that _noauto + nouser would prevent a normal user to even mount_ those partitions).
[*]**UID=0** means that - unless specified differently somewhere else - the files on that partition will be seen as "owned by the user#0". User #0 is the root user.
[*]**GID=46** means that - unless specified differently somewhere else - the files on that partition will be marked as "for the group #46". I don't know exactly how ubuntu sets up the groups. In order to know who is in that group, you should first create the account for the person you share your system with, and then see the content of the file /etc/group and verify if the new user is in the line with group 46 or not.
[*]**umask=007 **is the command that really assign permissions. In conjunction with UID and GID, it means: the owner (root) and the group members (people and processes in group #46) will have full access (reading, writing, executing) to the files, while the rest of the world will not have any permission.[/LIST]From my understanding of your parameters, the other user won't be able to access your partitions unless she/he would be member of group 46.

The easiest way to verify is... to create the account and see if it works or not!

---

### Post by JackiePaper on 2007-04-16
Gid is 1001 and UID 1001. She has access to winxp drives and in linux even to my home directory. Obviously I've done something wrong. When I created that user account, I used that kde tool "user management" in system settings.

---

### Post by namityadav on 2007-04-16
Edit: Nevermind. Wrong thread

---

### Post by mac.ryan on 2007-04-16
> **JackiePaper said:**
> Gid is 1001 and UID 1001. She has access to winxp drives and in linux even to my home directory. Obviously I've done something wrong. When I created that user account, I used that kde tool "user management" in system settings.

I run ubuntu and not kubuntu, so I don't know that tool... yet users and groups are managed at a lower system than the desktop environment, so there should not be any problem with that... just a different interface.

Unless files permissions in your directory are poorly set up (see below), the fact that the new user can access your personal files on the ubuntu /home/yourname directory definitively means something is wrong (as this is not the standard behaviour for a normal user). Yet I don't know how to make a diagnosis from here... Just make sure the new user you created is not member of groups with "superpowers" (normally there should be a pane in your utility, saying which groups she is member of).

To check the files permissions in your home directory, right-click on a file, open "properties" then "permissions" (this is the way it works in gnome, but I assume in kde should work similarly).

Finally, provided that your newly created user doesn't have "superpowers" you might **try **(it might well not work... I never tried myself!) to change your fstab entry like follows:
[LIST]
[*]changing the UID to your own (normally '1000' if you have been the first user created on that system)
[*]changing the GID to the same number[/LIST]This is like to say to the system: this partition belongs to me only, and only members of my personal group can access it.

If the system will still mount correctly the partition but other users will still be able to access them, then you could try a step further with
[LIST]
[*]changing the UMASK to 077[/LIST](This partition is mine, and nobody else can even watch it).

---

### Post by JackiePaper on 2007-04-17
Now it works like it should be! There's no more access from other users to winxp drives and my home folder.

I changed gid to 1000 and uid to 1000 in fstab file as you instructed. I Also changed the permissions of my home folder by double-clicking the home folder icon and changing the permissions.

Thank you very much mac for helping me out!

---

### Post by mac.ryan on 2007-04-17
> **JackiePaper said:**
> Thank you very much mac for helping me out!

My pleasure, really! (Good chance to refine my knowledge of the system... I am not that much expert either...)

Have fun with ubuntu!!! :)

---

