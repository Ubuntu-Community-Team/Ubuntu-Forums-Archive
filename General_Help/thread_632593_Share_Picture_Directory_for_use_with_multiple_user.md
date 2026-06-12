---
title: "Share Picture Directory for use with multiple users"
date: 2007-12-05
forum: General Help
---

### Post by pjman on 2007-12-05
I'm looking for some advice to share picture directory with multiple users.

We use F-Spot to manage our pictures and have F-Spot set to copy images to the picture directory (/data/photos) on import. ([SIZE="1"]All users use the [-b option]("http://f-spot.org/User_Guide/Organize") in their shortcut to force F-Spot to use /data/photos/photos.db as the path for the database.[/SIZE])

I want to be able to share (read and write access) the /data/photos/ directory between multiple users on my machine along with all subdirectories and any newly created files/subdirectories.

I've spent a lot of time searching on how to do this this and I've seen posts pointing to using Access Control Lists (ACL). I've tried that route but that doesn't help since F-Spot set's permissions during import to:

644 - new files
755 - new directories

The only option I can come up with is creating a cron job to change the permissions on all the files/directories every few minutes/hours. 

I'm looking for ideas. Anyone??

---

### Post by metalheart on 2007-12-06
Those permissions F-Spot is using are probably controlled by the umask value (sets default permissions for all files and directory's, created by the user). It's value is stored in file /etc/profile (default, set for all users) and in file in your home directory .profile (to override the default). You can change this value, but this means that **all** files and directories are created with those permissions.

You can create special user and run f-spot as this user, with appropriate usermask.

---

### Post by pjman on 2007-12-06
> **metalheart said:**
> Those permissions F-Spot is using are probably controlled by the umask value (sets default permissions for all files and directory's, created by the user). It's value is stored in file /etc/profile (default, set for all users) and in file in your home directory .profile (to override the default). You can change this value, but this means that **all** files and directories are created with those permissions.

Good to know. I'll read up on umask.

> **metalheart said:**
> You can create special user and run f-spot as this user, with appropriate usermask.

I like this idea. In the Windows world there is a "run as" option when you right click a file or shortcut. Is there any way to change a shortcut to run the application as this special user?

Thanks!

---

### Post by metalheart on 2007-12-06
In  Linux is a thing like su. If you enter
```
su username -c 'command &'
```
'Username' is this users name, with who's permissions you want to run 'command'. If you run program from the terminal, the '&' will put the program to the background (releases the terminal prompt). Command must be put in quotes.

---

