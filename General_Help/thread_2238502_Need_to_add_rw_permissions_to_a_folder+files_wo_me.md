---
title: "Need to add rw permissions to a folder+files w/o messing existing perms"
date: 2014-08-08
forum: General Help
---

### Post by caffewmilk on 2014-08-08
Hi,

I need to add 'read-write' permissions to a folder+files owned by root without messing with root's permissions.

Right now they're:  drwxr-xr-x 2 root root /var/www/html

So I need to add my regular user account to have 'read-write' to that folder and all consecutive files.

Also while preventing others from being to write to that folder.

Is this possible?

Thank you.

---

### Post by Jon_Goiri on 2014-08-08
All I can think of is you can add yourself too the root group and then allow all users on the group root to read and write the file. I don't think it's possible for you to read/write the files as non-root without changing some of the permissions.

Add yourself to root group
```

sudo adduser $USER root

```

Recursively change permissions to allow rwx for root, rwx for users in group root, r-x for everyone else
```

sudo chmod -R 775 /var/www/html

```

---

### Post by bab1 on 2014-08-08
> **Jon_Goiri said:**
> All I can think of is you can add yourself too the root group and then allow all users on the group root to read and write the file. I don't think it's possible for you to read/write the files as non-root without changing some of the permissions.

Add yourself to root group
```

sudo adduser $USER root

```

Recursively change permissions to allow rwx for root, rwx for users in group root, r-x for everyone else
```

sudo chmod -R 775 /var/www/html

```

That's terrible advice.  Root is root.  No user should be able to access root owned files via being part of the root group.  In Debian based distros the group is really just a placeholder and should be left that way.

There is no need to to do that at all.  The others setting allows all user to traverse the  /var/www/html already.  The best way to set up a secure web root is to have the root user create a folder with the user as owner and group owner (user:user) with 775 permissions on the folder.  This will allow only that user to have rw access to the /var/www/html/<user> directory.  Any subsequent files or folders will have the permissions of 775 for the folders and 664 for files as set by the default umask.  Since only the user can traverse the directory that is the root of the web store only that user will be able to modify or add files.

---

### Post by mcduck on 2014-08-08
definitely a +1 to above. 

One common way to deal with the web root permissions if you don't want to have the web root in user's home directory (or if you have many users who all need to be able to edit the web files) is to change group of /var/www to "www-data", make sure group has write permission, and then simply add any user who needs write access there into the www-data group.

So, basically the same result as if adding user to root group, but without any of the security issues as instead making the user all-powerful you are giving the exact permissions needed for the task.

---

### Post by caffewmilk on 2014-08-08
Ok, I had already done the adduser $USER root command and chmod -R 775 /var/www/html.

But have backed the truck up and went with the www-data idea.

Both answers are good and got me to where I wanted to be, though.

Thank you.

---

### Post by bab1 on 2014-08-08
> **caffewmilk said:**
> Ok, I had already done the adduser $USER root command and chmod -R 775 /var/www/html.

But have backed the truck up and went with the www-data idea.

Both answers are good and got me to where I wanted to be, though.

Thank you.
Great!  Actually, once you have experience you will see that @mcduck and my solution are essentially the same.  What was important is that you didn't expose a potential security threat by using the root user for your mortal users needs.

[COLOR="#0000FF"]Edit:  It also is important for newbies to understand that *just because you can do something doesn't always mean you should to it*.  You should always take all advice with a grain of salt.[/COLOR]

If you have solved your problem please mark the thread *solved*.

---

