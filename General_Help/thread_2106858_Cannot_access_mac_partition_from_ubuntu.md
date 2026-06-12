---
title: "Cannot access mac partition from ubuntu"
date: 2013-01-20
forum: General Help
---

### Post by AlexEttels on 2013-01-20
My Mac installation crashed, never mind about that..But I need to get some files from it, and I try to get to it with
cd /media/user1/Lion/Users/user1/
I get to the user folder without any problems, but as soon as I try to cd to "Documents" folder it tells me I have no premission. Naturally, I append a "sudo" before "cd Documents"
and it gives me a weird error: 
[HTML]sudo: unable to open /var/lib/sudo/alex/0: Read-only file system
sudo: cd: command not found
[/HTML]
I have no idea what that is..so I try to use root access, I use "sudo -i" I manage to get to the desired folder, but then my filesystem turns in read-only..I can't make any files at all..not from the root user and not from my own user.

Can anybody help me with that?

Thank you!

EDIT: To summarize the problem: when I mount the mac partition, it makes the filesystem read only

---

### Post by AlexEttels on 2013-01-20
bump

please guys, I have really important files on that partition, I have to get them some how!

---

### Post by rawlins02 on 2013-01-20
How is the MAC partition being mounted? Are you doing this at command line or is it mounted automatically?  This is a bit out of my level of expertise, but I see that the mount command has an option (--rw) for mounting a file system read/write. What does ls -l tell you when in the Mac directory or one of its parent directory?

---

