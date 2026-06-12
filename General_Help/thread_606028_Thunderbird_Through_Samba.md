---
title: "Thunderbird Through Samba"
date: 2007-11-07
forum: General Help
---

### Post by metalcoat on 2007-11-07
I have a Kubuntu Desktop that is used as a media server mostly, and is always on.  I also have a laptop that runs Windows XP that is not always on.  Right now thunderbird will only work on the ubuntu computer if I resubmit changes to permissions to files, so if the xp user uses it the ubuntu can't.  What i mean by can't use it is that it allows reading of all files but no changes, such as mark as junk, delete, etc. I suspect windows is doing something to the permissions on the ubuntu machine no longer giving it use. I have read all the forums but none tend to explain this.

Side Note: I would also like to use extensions such as lightning but they require different versions of the extension, one for windows the other linux. I can live without this though.

Both are using the same versions of thunderbird and the extensions.

---

### Post by kellemes on 2007-11-07
But isn't the locking of data what you want? I mean.. it seems rather wise to not let multiple users use the same data..
Or do you mean to say you can't even have write-access from ubuntu when XP isn't on?

Did I misunderstand your question?

---

### Post by metalcoat on 2007-11-08
it only allows one user that xp asks for the login each time it starts to mount the network drive so security isn't really an issue.  But the fact that I have to change permissions to delete emails, etc. when im on ubuntu is a pain.  Like I said I think XP is changing the permissions or something on the ubuntu system. Is there anyway to have ubuntu lock in the permissions or what not? ...Yes when xp isn't on ubuntu still can't delete emails etc (Xp isn't always accessing the data, only if i leave thunderbird on, which i rarely do)

I hope I explained it better, thanks for the reply.

---

### Post by mahousaru on 2007-11-08
Check the rights of the mounted directory with ls -l and make sure that the current user is owner and has write rights to the folder.  To set rights with samba you need to mount using something like following option flags...

```
uid=username,gid=groupname,file_mode=0640,dir_mode=0750,iocharset=utf8
```

Change the username and groupname to what ever you want the share to be.  The file mode and dir mode will set directories to be

drwxr-xr-x

and files to be:

-rw-r--r--

Remember the rights are something that samba fudges over each time it mounts a share.

*Edit*
Just to let you see the full mount line

```

mount -t smbfs //server/share /somedirectory -o username=username,password=passwd,uid=username,gid=groupname,file_mode=0640,dir_mode=0750,iocharset=utf8

```

---

### Post by metalcoat on 2007-11-09
Actually the thunderbird profile is hosted on the Ubuntu machine and I connect to it via an XP Laptop.

---

### Post by metalcoat on 2007-11-17
bump

---

