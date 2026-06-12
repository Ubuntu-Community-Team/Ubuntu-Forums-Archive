---
title: "Mounted NFS Permissions."
date: 2024-01-30
forum: General Help
---

### Post by joeadams7782 on 2024-01-30
[COLOR=#1C1C1C][FONT=&quot]Hello Ubuntu Forums! My first post here & I need some help.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]Two linux servers Ubuntu & RedHat, both connected to AD domain for authentication, which works fine.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]I have a nfs export that sits on the Ubuntu "/mnt/folder ip-address/subnet(rw,sync,no_root_squash)"[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]The NFS export gets mounted using fstab on RedHat, but I have a permission problem. When domain user A creates a folder, user B will not be able to craete any files or folders inside that folder, and vice versa, both users are in the same AD group.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]On the Ubuntu, I configured the directory as below, but still no luck[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]sudo chown nobody:nogroup /mnt/folder[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]sudo chmod -R 777 /mnt/folder[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]How can I configure the permissions so that anything created (even in the future) under /mnt/folder will be accessible with rwx permission for all users.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]Thanks a lot![/FONT][/COLOR]

---

### Post by TheFu on 2024-01-30
The POSIX uid and gid (the numbers) need to match across all systems OR you need to run an nfsidmap translation setup (which I've never done).

Why would you have the IP address in a mount directory?  It isn't like **showmount -e** can't quickly provide the information for any client.

If you want 2 users to be able to work together inside the same directory, there's nothing special about NFS vs local users.  The same exact method of working together using a shared POSIX group is required.  It has been a few years since I posted how to do this.  Search these forums for my username and "working together chmod chgrp" to find instructions.

No way should you use nobody:nogroup and never, ever, ever, use 777 permissions.  That's providing a way for attackers to pwn your systems.

>  How can I configure the permissions so that anything created (even in the future) under /mnt/folder will be accessible with rwx permission for all users.
Not a good idea, but place all users into a "users" POSIX group, force the group for the storage areas to be "users" with group write and the setgid bit enabled on the top directory before any subdirs are created.

There is a problem with all of this - files that are **moved** into the directory structure will retain their former group. But any newly created (copied) files will be forced with the group of the setgid directory group.

---

### Post by joeadams7782 on 2024-01-30
Thanks for commenting!

I was using nobody:nogroup and 777 permissions out of desperation, trying to see if anything will work.

I've searched the forum for your username and "working together chmod chgrp" and came across the below post. I've tried it, but no luck, still the same behavior.

[https://ubuntuforums.org/showthread.php?t=2479486&p=14113785#post14113785](https://ubuntuforums.org/showthread.php?t=2479486&p=14113785#post14113785)

---

### Post by TheFu on 2024-01-31
How do I say this nicely.  "Prove it".  Saying it doesn't work, then not showing what you've done is hardly a good way to resolve the issue.  So, prove you did what was suggested. Show all your work.  Often, this will show where a mistake was made.  I don't need to see the commands, just the results that show full directory and file permissions along with proof that the userid's involved are in the same group - use the **id** command.

---

### Post by joeadams7782 on 2024-01-31
Thanks for your help!

Each user A & B logged into the client where the NFS is mounted. Each user created a folder, but user A cannot collaborate in user B folders and vice versa.

Below is ls -l for both folders created by both users, and the groups both users are in.

drwxr-sr-x. 2 userA sudoers 4096 Jan 31 2024 byuserA
drwxr-sr-x. 2 UserB sudoers 4096 Jan 31 2024 byuserB

uid=957201116(userA) gid=957200513(domain users) groups=957200513(domain users) , 957201118 (sudoers)
uid=957201117(UserB) gid=957200513(domain users) groups=957200513(domain users) , 957201118 (sudoers)

---

### Post by TheFu on 2024-01-31
sudoers is a really, really, really bad choice as the group to be shared for disk storage, but it will work.
You just didn't give write access to the group for either of those directories.

Also, usernames need to be all lower-case. Same for groups.  Yes, it shouldn't matter, but eventually, it will because some script created by some one 30 yrs ago doesn't handle mixed case and you'll be screwed.  Best to avoid the issue.

Also, POSIX groups shouldn't have spaces.  This is even more important.  Spaces are commonly used as field separators in Unix.  It will be bad much sooner.  I'm a little surprised that gids over 65K are working at all. That's a surprise to me.

---

### Post by joeadams7782 on 2024-01-31
Thanks for commenting.

The usernames and directories are all lowercase. I only used the A & B for privacy. 

"[COLOR=#000000]domain users"[/COLOR] group is the default active directory group for all users, and it's not something I can change.

I gave the group write access to the parent directory sudo chmod g+rwxs /mnt/folder , isn't that enough?

---

### Post by TheFu on 2024-01-31
> **joeadams7782 said:**
>  I gave the group write access to the parent directory sudo chmod g+rwxs /mnt/folder , isn't that enough?

With a stock Ubuntu install it should be, provided the subdirectories are created AFTER the top level directory is setup.

Additionally, all the users need a umask of 002, but that's the default. You should check that. I don't know what AD might do to it.  Just add 
umask 002 to every user's .profile or other  script automatically run at login.

umask is a built-in for most shells.  From the bash manpage:

```
       &#8226;      the  file creation mode mask as set by umask or inherited from the
              shell's parent

       umask [-p] [-S] [mode]
              The user file-creation mask is set to mode.  If mode begins with a
              digit,  it  is interpreted as an octal number; otherwise it is in&#8208;
              terpreted as a symbolic mode mask  similar  to  that  accepted  by
              chmod(1).   If  mode  is omitted, the current value of the mask is
              printed.  The -S option causes the mask to be printed in  symbolic
              form;  the default output is an octal number.  If the -p option is
              supplied, and mode is omitted, the output is in a form that may be
              reused  as input.  The return status is 0 if the mode was success&#8208;
              fully changed or if no mode argument was supplied, and false  oth&#8208;
              erwise.
```

This stuff is covered in any beginning Unix class.  [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) Chapter 9 (pg 90+) covers permissions, including the umask.

---

### Post by joeadams7782 on 2024-02-01
Thank you so much for your help! Using ACL did the trick.

---

### Post by TheFu on 2024-02-01
> **joeadams7782 said:**
> Thank you so much for your help! Using ACL did the trick.

While you can use ACLs, it is a bad practice when standard permissions will work.  ACLs aren't used often, so normal commands and normal permissions output doesn't show what they are. Further, ACLs override the permissions that are normally displayed, so it is possible to have the file permissions show 1 thing, but have the ACLs prevent them from working as expected.  

In over 30 yrs as an admin, I've needed to use ACLs twice for less than 10 files.  Do yourself a favor and **don't mess up your system with ACL use**, unless it is truly required. In this case, it isn't.

---

### Post by joeadams7782 on 2024-02-01
Thanks for the advise. 

I've tried every single permission I could think of, nothing worked, even the umask (I didn't change it permanently, only after user login).

I will continue to dig around to see if I can get it to work as needed using the right permissions.

---

### Post by TheFu on 2024-02-01
Perhaps showing an example will clarify?

```
$ ll
total 28
**drwxrwsr-x  7 tf jellyfin 4096 Feb  1 09:31 ./**
drwxr-xr-x 12 tf tf       4096 Jan 16 08:49 ../
**drwxrwsr-x  2 tf jellyfin 4096 Jan 31 16:36 A_Real_Bugs_Life-2024/**
drwxrwsr-x  2 tf jellyfin 4096 Jan 28 11:44 Space_Age_NASAs_Story/
```

tf is my account.  
My umask and the umask for the jellyfin account are 002.  
The group is shared with the jellyfin server process account.  I added myself to the jellyfin group and setup the parent directory with the shown permissions before creating any subdirectories or files below.

```
$ id jellyfin 
uid=117(jellyfin) gid=118(jellyfin) groups=118(jellyfin),44(video),109(render)
```

Those last 2 groups are required to allow hardware transcoding with my GPU. Well, there's more setup to do that, but that's unimportant for this thread.

I'm in many more groups, but not beyond the documented NFS limit for the number of allowed groups.

All of this is show in the "how-to work together" posts.  Guess you missed the details.

---

### Post by avidandrew on 2024-02-01
Have you configured /etc/nsswitch.conf as described on [https://ubuntu.com/server/docs/samba-active-directory](https://ubuntu.com/server/docs/samba-active-directory) so your AD users show up when running "id username" or "getent passwd"? If so, are you using NFSv3 or NFSv4 for the mount?

---

### Post by joeadams7782 on 2024-02-02
> **TheFu said:**
> [COLOR=#000000]Perhaps showing an example will clarify?[/COLOR]

[COLOR=#000000]Code:
$ ll
total 28
**drwxrwsr-x  7 tf jellyfin 4096 Feb  1 09:31 ./**
drwxr-xr-x 12 tf tf       4096 Jan 16 08:49 ../
**drwxrwsr-x  2 tf jellyfin 4096 Jan 31 16:36 A_Real_Bugs_Life-2024/**
drwxrwsr-x  2 tf jellyfin 4096 Jan 28 11:44 Space_Age_NASAs_Story/[/COLOR]
[COLOR=#000000]tf is my account.[/COLOR]
[COLOR=#000000]My umask and the umask for the jellyfin account are 002.[/COLOR]
[COLOR=#000000]The group is shared with the jellyfin server process account. I added myself to the jellyfin group and setup the parent directory with the shown permissions before creating any subdirectories or files below.[/COLOR]

[COLOR=#000000]Code:
$ id jellyfin 
uid=117(jellyfin) gid=118(jellyfin) groups=118(jellyfin),44(video),109(render)[/COLOR]
[COLOR=#000000]Those last 2 groups are required to allow hardware transcoding with my GPU. Well, there's more setup to do that, but that's unimportant for this thread.[/COLOR]

[COLOR=#000000]I'm in many more groups, but not beyond the documented NFS limit for the number of allowed groups.[/COLOR]

[COLOR=#000000]All of this is show in the "how-to work together" posts. Guess you missed the details.[/COLOR]

Thanks for taking the time to explain it. I will keep searching the forum for you posts on NFS permissions for shared folders.

---

### Post by joeadams7782 on 2024-02-02
> **avidandrew said:**
> Have you configured /etc/nsswitch.conf as described on [https://ubuntu.com/server/docs/samba-active-directory](https://ubuntu.com/server/docs/samba-active-directory) so your AD users show up when running "id username" or "getent passwd"? If so, are you using NFSv3 or NFSv4 for the mount?


Using NFSv4. 


Yes, if I run "id username" or "getent passwd" on the server or the any of the clients I can query the uid, gid, and the active directory groups that each user is member of.

---

### Post by TheFu on 2024-02-02
The gid is what needs to match. The number.

I've never used AD with this, but I know that LDAP works and local accounts carefully crafted with uid and gids to fit work.  NFSv2, 3, 4 all work. Heck, when other things fail, NFS is still working.  I've used it with WinNT and 12 different Unixen and Linux.  However, the last time I tried to get NFS working with Windows was about 2005. I failed, but think it was more about my lack of having proper MSFT Enterprise licenses at the time and unwillingness to install any 3rd party, free, NFS client.  I'd only used 3rd party commercial NFS tools on MSFT.

I can only guess there's something specific about your environment that is off.  POSIX is POSIX.

---

