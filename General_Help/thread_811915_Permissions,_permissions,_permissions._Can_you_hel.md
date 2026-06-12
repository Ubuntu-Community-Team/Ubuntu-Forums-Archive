---
title: "Permissions, permissions, permissions. Can you help?"
date: 2008-05-29
forum: General Help
---

### Post by ruipedroca on 2008-05-29
Hi,

How can a folder be configured so that ALL files/folders/subfolders created inside it, in the future, can be read/write/deleted by ALL users, even those users accessing it via nfs sharing?

I've been around concepts like: chmod, chow, setfacl, setgid and others.
But, i'm a linux newbie and need some expert guidance. 
Can you help? 

Thanks in advance!

---

### Post by WRDN on 2008-05-29
I haven't tried this, so can't guarantee it will work, but if you right click a folder, select Properties then Permissions, you can set options.

Under the "Others" heading on the Permissions form, select the values you want.
You could also ensure all users are under the same user group.

---

### Post by ruipedroca on 2008-05-29
Hi,

I've already tried that, but it doesn't work only for future files/folders.

Regards

---

### Post by bingoUV on 2008-05-29
umask affects the permissions of future files and folders. Before creating files/directories here, run 
```

umask 0

```

It may not work if you are creating files/directories here using some editor/application that does not respect your umask setting.

---

### Post by ruipedroca on 2008-05-29
I've tried the umask aproach and it worked!

I had to edit /etc/profile, and change the default umask 022 to 000 to make changes permanent to users.

Regards!

---

### Post by Zimmer on 2008-05-29
[http://www.tldp.org/LDP/intro-linux/html/sect_03_04.html](http://www.tldp.org/LDP/intro-linux/html/sect_03_04.html)

[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

As I se it, from a layman's view, not an expert, a directory with permissions  777 would be accessable by anyone.
By default as a user you create a new directory with permissions 755. The umask set is 022 for a user (777 -022 =755). 
However,  accessing files from a remote client: (a Windows computer? maybe via a network) when I set up Samba shares a long time ago I recall adding a SAMBA user and I used the same name and password as my Windows login and password. I do not recall any bother with accessing files created on my shared folders on the Ubuntu machine from Windows.
There is also help on one of the community documents about sharing folders the easy way. I will look it up and edit this post later.

I hope this info helps you in deciding a reasonable course of action for your particular problem. A direct answer to your question is probably this:
A chmod command on a directory with the -R option acts recursively.( see: man chmod).
And I believe that means it will go through the directory files and sub directories applying the given permissions, but don't take my word for it, have a check on that elsewhere (I may just experiment with a folder later... :)  )

EDIT:  [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server)

---

