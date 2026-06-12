---
title: "saving data to usb disk, won't"
date: 2021-06-22
forum: General Help
---

### Post by frittered on 2021-06-22
I have a usb disk formatted to ext4.  I inserted it to copy contents of my files to.  It won't let me do this.  What do I need to do get the properties changed on the usb to allow file copy?

---

### Post by sudodus on 2021-06-22
You can

With elevated permissions **sudo**

- check that the file system is mounted, and if not, **mount** it
- create a directory at the top level of the file system in the USB disk.
- change ownership **chown** and/or permissions **chmod** to what you want.

Now it should work to write into the directory (create subdirectories as well as files also as a normal user).

There are other alternatives too, depending on how you intend to use the drive ...

If you want to use the drive for backup, you might have a shellscript (using for example **tar** or **rsync**), that works with elevated permissions, and in that case you need **not** create a directory at the top level and modify its ownership and permissions.

If you want to backup system files, it is important to preserve their ownership and permissions, and you should use elevated permissions for this task, but if you only save personal data (pictures, documents etc) you can simply copy the files.)

---

### Post by frittered on 2021-06-22
thank you.  I made the disk on a separate machine and the new machine wouldn't accept it.  What a PITA!  Seems like they want to destroy sneaker nets

---

### Post by tea for one on 2021-06-22
> **frittered said:**
> I have a usb disk formatted to ext4.  I inserted it to copy contents of my files to.  It won't let me do this.  What do I need to do get the properties changed on the usb to allow file copy?

Did you receive [COLOR="#0000FF"]permission denied[/COLOR] message?

When you first format the drive to ext4, the owner is root and you probably need to change ownership.

[https://www.computerhope.com/unix/uchown.htm](https://www.computerhope.com/unix/uchown.htm)

If your drive is mounted at /media then the command is something like this:-

```
sudo chown -R  username:groupname /media/username/device_name/
```

---

### Post by frittered on 2021-06-23
yes, that was the problem.  The ubuntu laptop wouldn't let me do that either.  I had to take it to the machine where I made it and do it there.  Is there a more generic ownership setting such as anyone:anygroup?  What if I had just traveled 100 miles to use that drive only to find it rendered useless?

---

### Post by tea for one on 2021-06-23
> **frittered said:**
>  The ubuntu laptop wouldn't let me do that either.

Do you not have admin privileges on this laptop?

---

### Post by Impavidus on 2021-06-23
Help page on file permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If you use the ext4 filesystem on a usb drive, all rules about permissions apply. Every file has an owner and a group and a set of permissions: setUID, setGID, sticky bit, read/write/execute for owner, idem for group, idem for others. The owner and group are stored as a numerical user ID and group ID. When you plug the usb drive into a different computer, those numeric user ID and group ID may refer to a different username and groupname, or not to any name at all. On all Linux distros user ID 0 refers to the root user, on all Ubuntu systems user ID 1000 is the user created when installing the system. But you can't rely on the owner and group of a file on a portable drive to be of any use (except when the owner is root). So if you plan to move the usb drive to a different computer where you want to use it under a different user ID, make sure the settings for others (not owner or group) are sufficiently permissive. Or use your admin rights to change owner to whatever userID you happen to use on that other system.

---

### Post by frittered on 2021-06-23
thanks, now all I have to do is remember this

---

