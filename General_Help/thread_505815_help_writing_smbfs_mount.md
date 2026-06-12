---
title: "help writing smbfs mount"
date: 2007-07-20
forum: General Help
---

### Post by cjlindem on 2007-07-20
I have set up a permanent mount of a windows 2003 server share using fstab.

I have followed the guide and everything works except I am unable to write any files without being logged in as root.  When I try to give anyone else write access, it immediately reverts back to file access only.

here is my mount from fstab:
//192.168.0.xxx/data /mnt/myserver smbfs username=myuser,password=mypasswd,gid=myserverchangers 0 0


my user id is a member of the group 'myserverchangers' which is supposed to give me write access to the drive based on the guide I read here:

[http://ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares](http://ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares)

I have also tried to give access using chmod at the command line.  It goes through with no errors, but a check of the folder rights reveals nothing has chanced, and still only owner (root) has write access.

Any help is appreciated.  Thanks!

---

### Post by bernied on 2007-07-20
Are you sure that the gid value is right (even assuming that the extra space is a typo)?
I do this using cifs, not smbfs, and gid is a the group id number, not the name.

It's easy to try anyway, to find the number, you can:
```
sudo cat group | grep myserverchangers
```

---

### Post by cjlindem on 2007-07-20
I doublechecked there is not a typo in my group id, I'm not sure why it pasted into the forums that way.  However, the tutorial I linked above does not say to use the group number, it demonstrates with the groupname.  Perhaps the syntax for cifs is different?

Also, I get this when I type the sudo cat command:

cat: group: No such file or directory

Thanks for any additional help.

---

### Post by cjlindem on 2007-07-21
I was able to get this working correctly with cifs.  Reading up on it, sounds like it is to replace smbfs mounting anyways.

Here is the entry in /etc/fstab that gets it to do what I want:

//192.168.0.xxx/data  /mnt/servername  cifs  username=uname,password=passwd,iocharset=utf8,gid=1001,file_mode=0770,dir_mode=0770 0 0

Though I did get an error at shutdown which seems to be a known issue and I was able to correct it with info from this thread:
[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

Thanks for the help!

---

