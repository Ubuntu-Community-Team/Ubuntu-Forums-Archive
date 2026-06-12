---
title: "Sudo not working after trying to set up samba permissions"
date: 2006-11-29
forum: General Help
---

### Post by Karbonik on 2006-11-29
Ok, so I'm trying desparately to somehow get my linux laptop to talk with my linux samba fileserver, so I can actually transfer files to the server without having to boot into windows or use the sneakernet option.

I've been trying Smb4k, no luck, so I figured maybe Komba would work.  Still no luck - in both of them I can see the workgroup (MSHOME), and the shares on the various machines around our happy little home - mostly XP boxes, but also the samba Shared folder I set up with Edgy Server.

I followed the instructions from the Komba help explicitly, found here:
[INDENT]
Komba2 as user
The use as non root user should be the normal case. It's recommended not to use Komba2 with su. It creates security holes. In this case Komba2 starts other programs with root permissions (for example Konqueror).
If you start Komba2 as a normal user you have not enough permissions to mount and unmount shares at first.
You have to change the permissions on smbmount and smbumount. Please note, it can open a security lack on your machine. So be carefull!
It would be enough to change the bit SETUID on smbmnt and smbumount. If this bit is set the programs start with the permissions of the owner (in this case root). Now all users can mount and unmount smb shares.
We tell you now how to set the permissions only to group of users. For following commands you must be root. At first you add a group to your system. 
% groupadd sambamount

Now you add the users to the new group. 
% usermod -G sambamount username

Change the group on smbmount und smbumount to sambamount. 
% chgrp sambamount smbumount
% chgrp sambamount smbmount

At least you set the permissions that only users of the group (and root) can run smbmount and smbunmount and set the SUID bit 
% chmod 4750 smbumount
% chmod 4750 smbmount

Now you can use Komba2.

[/INDENT]I have previously changed the Sudo password, so if I go with the option of rebooting into the recovery mode, and doing

root@laptop:~%[FONT=Courier New]adduser karbonik admin[/FONT]

and something weird has happened - I'll have to use the live cd like the instructions here: [http://ubuntuforums.org/showthread.php?t=286553&highlight=password+root](http://ubuntuforums.org/showthread.php?t=286553&highlight=password+root)
but I haven't tried that one out yet and don't know for sure if it works.

In any case, once that issue is taken care of - I'll still have to deal with getting the original problem done, which is being able to mount Samba Shares on the local network.

Am I just an idiot? Or is it more difficult to *read* Windows shares than it is to *set them up* under linux?

---

