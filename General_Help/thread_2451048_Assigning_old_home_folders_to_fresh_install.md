---
title: "Assigning old home folders to fresh install"
date: 2020-09-25
forum: General Help
---

### Post by theroha on 2020-09-25
I just upgraded my hardware for the first time with a new SSD to use as a boot drive and dedicate my old HDD as a storage unit. The old HDD has user Home folders that I would like to retain in place and assign as Home folders for the users on the new drive.

My research pointed to editing /etc/passwd, but I'm not sure how the HDD needs to be listed as reading the directory properties of the old folders shows the drive mounted under my current user.

I'm on Ubuntu 20.04 and the old HDD was an install of 18.04.

Any help or direction to relevant tutorials would be appreciated. Thank you.

---

### Post by TheFu on 2020-09-25
More detailed facts please. Less abstract ideas needed.

There are 3 considerations.
[LIST=1]
[*]fstab mount location
[*]passwd entry for each userid (or if using ldap user management, getent passwd)
[*]file and directory ownership for each userid
[/LIST]

The /etc/fstab controls where and how storage is mounted. You can put it anywhere, but the unofficial standard location would be /home/.  Recently, Canonical has decided that this was less than optional, breaking 40+ yrs of Unix standards around home directories.  To my knowledge, only snap packages care. If you don't use snaps, then you don't need to care either.  You can use /u/user1, /u/user2, /u/user3 if you like.

The passwd entry for each userid specifies where the HOME directory is located for that userid. It is used at login and to set the HOME environment variable at login. It just needs to be correct and shouldn't matter where it is mounted at all.

File and directory ownership of the HOME is typically for the primary userid and primary group for that userid. In Ubuntu systems the last 15 years, that would be the same userid/groupid. The numbers usually start from 1000 for both the uid and gid. They increment by 1 for each new uid and gid created.  If you create the multiple users in the same order as on the other system, then they should line up uid-to-uid with the same numbers. You could use the old passwd file from the old system to get the uid and gid for each user on the new system.
But if you don't, it isn't a big deal provided the main uid is correct.  Then you can use **chown -R** on each userid HOME directory to force the correct userid+groupid recursively.  Home directory files are almost always owned by the userid and primary groupid for that userid.  Clear as mud?

The relationship between the passwd --> shadow and group --> gshadow files in /etc/ isn't hard to understand.  There is a manpage for each of those files which outlines what each field means. It is simple and elegant.  On the file system, it is 100% about the uid/gid - the numbers.  Those numbers are set in the passwd and group files, period. As long as the numbers are correct everyone will be happy.

---

