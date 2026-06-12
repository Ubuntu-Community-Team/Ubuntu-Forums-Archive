---
title: "Added a 2nd drive-need to give full access to all users"
date: 2006-07-29
forum: General Help
---

### Post by Hurons on 2006-07-29
Hello All,

I have an old PC that I loaded dapper on and for the most part it works. Since the OS is loaded on a 10GB drive, I added a 2nd 30GB drive and I need to give full permissions to all users without using sudo. Is this possible? Its for my teenagers that live 30 miles away, so I want to get this right before giving it to them.

Thank you in advance.

Regards,

Husrons

---

### Post by jefffq on 2006-07-29
You can just change the permissions for the point that the HDD is mounted to. If you want all users to have all permissions on the whole drive then you can do this:

sudo chmod 777 /path/to/mount-point

If you already have stuff in the mount point that you also want to ensure universal access to, you'll want it to run recursively, so:

sudo chmod -R 777 /path/to/mount-point

The owner:group of the mount point won't matter much with those permissions.

But any new files and folders created by these users will have their ownership and their umask settings for the permissions. So if Davey makes a folder, depending on your setup, Susie may not be able to access it.

---

