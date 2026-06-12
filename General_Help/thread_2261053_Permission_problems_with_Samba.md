---
title: "Permission problems with Samba"
date: 2015-01-16
forum: General Help
---

### Post by p2ranger on 2015-01-16
I thought I understood permissions well, but apparently there is something I still don't understand.

I have a samba share running on my Ubuntu 14.04.1 server. 

The intention is to use this for my family at home to use. I created a user called myfamily in a group called family. I put the usernames of the people in my family including myself in the group family.

The directory, share, has these permissions for the sake of troubleshooting: drwxrwxrwx

I would prefer drwxrwxr-x

It is owned by the myfamily username and is in the family group.

I can connect with my computer (OSX) to the samba server with my username and with the myfamily username.

All directories and files within the share folder have the following permissions:
drwxrwxr-x

If I try to write a file to a directory owned by myfamily in the share while logged in as my username, I don't have permission to write but can read.
The same results for if I am logged in to the share as myfamily and I try to write to a folder owned by me.

The way I understood it is if a user is a part of a group and permissions are set 775, then users of that group can write to folders in that group regardless of the owner.

My the part of my /etc/samba/smb.conf file for this:
```

[share]
        comment = Family share on server
        create mode = 775
        writable = yes
        directory mode = 775
        public = yes               
        path = /media/raid1/share

```
Thanks for any help.

Jason

---

### Post by SeijiSensei on 2015-01-16
If you don't care about identifying which person placed which file in the shared directory, you can use the "force user" and "force group" directives in Samba.  In your case 
```

[share]
        comment = Family share on server
        create mode = 775
        writable = yes
        directory mode = 775
        public = yes               
        path = /media/raid1/share
        force user = myfamily
        force group = family

```
Now all files will be written by the Linux user myfamily and belong to group family.

---

### Post by p2ranger on 2015-01-18
The problem I see with this is a guest user browsing. Would they then be able to write to the folder?

Thanks

Jason

---

### Post by SeijiSensei on 2015-01-19
If you have "guest ok = yes" then yes, they can.  The "force" parameters determine the Linux user and group Samba uses to read and write to the share.  They can reference a user/group that isn't one of the Samba users but exists as a Linux user.

---

