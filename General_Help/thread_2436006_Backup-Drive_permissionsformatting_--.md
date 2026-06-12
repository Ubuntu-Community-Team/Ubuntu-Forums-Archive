---
title: "Backup-Drive permissions/formatting --"
date: 2020-01-29
forum: General Help
---

### Post by ishmael3 on 2020-01-29
I have been trying to learn about backups and would like to do this in proper Linux fashion. I want to backup the  /home folder (containing several user accounts) so that in event of a serious failure those files can be easily restored to a new Ubuntu installation.
 
 I plan to use Grsync. (Sorry, I know purists will avoid a GUI but I am still learning.)   
 
 I've read/watched a number of tutorials. The few that even mention formatting state that ext4 is the best choice for backup drive. That, of course, introduces the issue of drive ownership, and no tutorials that I've seen address how to handle permissions for the backup-drive, or permissions required in restoring to a new Ubuntu install.   
 
 My question(s): If I set the ext4 backup-drive so it is owned by the admin account of the machine being backed up, what must I expect or be aware of, as far as permission issues, when I go to recover those files to a fresh installation?
 
 I'm unsure whether a new Ubuntu  installation -- on, perhaps, a new computer -- will allow me (Grsync) to even access the backup drive (owned previously by the admin account of the dead installation). And  if I have to take ownership I'm unsure how I might be corrupting the permission settings for the accounts I'm backing up and recovering.  
 
 Maybe I'm making it too hard. Guidance from anybody who's dealt with this would be appreciated -- please explain as if you are talking to someone who grew up with Windows and NTFS.  

 Many thanks.

---

### Post by TheFu on 2020-01-29
Backing up HOME directories is bonehead simple.
a) use a real backup tool, not rsync or grsync.
b) run it from a crontab - root is the account.
c) when root runs a backup tool, permissions are handled.  They will be retained automatically both when doing the backup and when restoring.  
d) Be certain to backup /etc/ and the list of manually installed packages too.

Yes, using ext4 is a reasonable choice if you don't have any specific reason to use some other type.
```

#!/bin/bash

# Create the list of manually installed packages - use apt-mark showmanual and store that output somewhere that gets included in the backups.  I put it into /root/backups/
/usr/bin/apt-mark showmanual > /root/backups/apt-mark.manual
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

######
# Clean up garbage inside all the HOME directories before doing the backup.  No need for cache or trash files, for example.

# mount the backup disk as needed; best not to leave it mounted.
/bin/mount /Backups

# Ensure backups are by hostname, so multiple hosts can use the same backup storage
mkdir  -p /Backups/$(hostname)

# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \
                                            --exclude '**'    /       /Backups/$(hostname)

# Remove really old backup sets - say 90 days old.
/usr/bin/rdiff-backup --force --remove-older-than 90D    /Backups/$(hostname)

# umount the backup disk
umount /Backups
```

Simple.  Put that into a file, make the permissions +x, then put that file /path/name into root's crontab to run daily.
More rdiff-backup examples: [http://rdiff-backup.nongnu.org/examples.html](http://rdiff-backup.nongnu.org/examples.html)

---

### Post by Impavidus on 2020-01-30
Your root user copies the backups to a ext4 filesystem. So, all ownership and permissions are kept the same. That's good. When you copy everything back to a new Ubuntu install, ownership and permissions are still the same. The root user is the same, so that's no problem. The root user is always userID 0, so the new system will correctly see that the /home directory on the backup drive is owned by root.

The main caveat is that you must make sure that on your new install the same usernames get associated with the same userIDs as on the old system. Suppose that on your old system user alfred has userID 1000, betsy has userID 1001 and charles has userID 1002, as that was the order in which you created the accounts. But on the new system you first create user alfred (userID 1000) during installation, next you create charles (userID 1001) and finally betsy (userID 1002). Now the system will think that the backup of betsy's home directory is owned by charles and the backup of charles' home directory is owned by betsy. They are still named correctly, so they will be restored correctly, but Betsy and Charles won't be able to login and if they could, would find all their files owned by the other. It's not very hard to fix, but it's best to simply create the users in the same order.

---

### Post by TheFu on 2020-01-30
> **Impavidus said:**
>  The main caveat is that you must make sure that on your new install the same usernames get associated with the same userIDs as on the old system. Suppose that on your old system user alfred has userID 1000, betsy has userID 1001 and charles has userID 1002 .... 
<snip>


This is partially why backing up /etc/ is required.  Having the passwd and group files will let the person doing the restore see the old relationships between uid/gid and the names.

**rdiff-backup** can be forced to keep the numbers for uid/gid in the backups, or it can use a mapping file between old and new systems.  More information in the manpage.
```
       --group-mapping-file filename
              Map group names and ids according the the group mapping  file  filename.   See  the
              USERS AND GROUPS section for more information.
...
       --user-mapping-file filename
              Map  user names and ids according to the user mapping file filename.  See the USERS
              AND GROUPS section for more information.
...
USERS AND GROUPS
       There can be complications preserving ownership across systems.  For instance the username
       that  owns  a  file  on  the  source system may not exist on the destination.  Here is how
       rdiff-backup maps ownership on the source to the destination (or vice-versa, in  the  case
       of restoring):

       1.     If  the --preserve-numerical-ids option is given, the remote files will always have
              the same uid and gid, both for ownership and ACL entries.  This  may  cause  unames
              and gnames to change.

       2.     Otherwise,  attempt to preserve the user and group names for ownership and in ACLs.
              This may result in files having different uids and gids across systems.
....
```
This is just another reason to use a real backup tool that supports versioning.  BTW, I used rsync for years.  rdiff-backup is faster, has more features to handle backup stuff, and mostly looks like rsync.  The most recent backup looks just like an rsync mirror too, it is just the older versions that are diff.gz files.  Run a little test backup and check out the target area, see what's there.  You'll say "ahhhh, that's smart."

---

### Post by ishmael3 on 2020-01-30
TheFu:  
 Thank you for the response. And thank you for the code example. I'm going through it and searching the parts I don't understand. (from my point of view "bone-head simple" is Win-7 "create system image" ;)) I see that some others agree with you that rdiff has some advantages over rsync -- I don't know enough yet to understand the differences. And if I understand what "crontab" is, a way to automate updates, it's a complication I don't need right now -- happy to run manually whenever I feel it is necessary.  I very much appreciate your long response and I am still digesting it. Especially thanks for stating value of backing /etc directory!
 
 Impavidus:
 That is some very useful information. It's the sort of info that I can't believe isn't addressed in tutorials for doing backups in Linux -- and there are hundreds of such tutorials available! Thank you! Thanks especially for the explanation of "root" and the importance of userIDs and how they are created. Your explanation leads me to ask a couple more questions I wouldn't have thought to asked before:
 
 1) How do I copy or restore as root user? Grsync has a box to check for "run as super-user," so that seem obvious. But if using command line to run rsync or rdiff, none of the examples I've seen prefix with "sudo." Does this have something to do with having my backup drive owned by root? -- if so, how do I do that?
 
 2) I seem to have a misunderstanding regarding recreating userIDs on the new machine: I would have thought that if I restored the /home directory AND /etc directory to the new machine then the user names and userIDs would all be restored correctly at that time. In other words, I would not need to recreate them individually.  Where am I mixed up?  
 
 Thanks to both of you for the very thoughtful responses.

---

### Post by TheFu on 2020-01-30
a) rdiff and rdiff-backup are not the same thing. Best not to confuse people by not using the full name.

b) the scripts would be run with sudo OUTSIDE the script, not inside it.  All the commands inside would be running as root already, so sudo isn't needed/wanted, inside.

c) crontab is a way to automate non-GUI programs on any Unix-like OS.  They can run as root or as any userid on the system. The timing for when something runs can be controlled to the minute with the built-in capabilities, but to the second by using a sleep-delay.  Getting a non-GUI program to run daily, weekly, monthly when you don't care exactly what time it runs is easier with anacron. The only requirement is that the computer be powered on sometime that day, week, month, or year, so the task can run.  I almost always want backups to happen at specific times that I'm not using the computer.

d) userids don't have to have a HOME directory.  Also, the location of a userid's HOME can be any where.  There is nothing special about /home/ at all.  The entry in the passwd file or LDAP passwd database controls the userid, username, and HOME directory for that userid.  **getent passwd** will show both local and LDAP accounts.  Usually, on a home system, LDAP isn't used. If someone didn't go out of their way to install and configure LDAP, it isn't used.

e) if you want image-based backups like used typically on Windows, then you should check out fsarchiver or clonezilla or dd on Linux. I find these solutions to be extremely inefficient for storage and time compared to rdiff-backup.  Daily rdiff-backup sets require 2-4 minutes to finish and having 90 days of versioned backups really doesn't take all that much storage, maybe 1.3x the original size.  With image-based backups, every version is about the same size as the prior backup version. Want 3 versions, then we need 3x the storage. Each image backup requires at least an hour, perhaps multiple hours to create.

With image backups, how will a restore to different hardware work?

In these days of malware, crypto-ware, and just dumb mistakes made by humans, having daily, versioned, backups really isn't an option. It is a **requirement**.

IMHO.

---

### Post by Impavidus on 2020-01-30
> **ishmael3 said:**
> 
 2) I seem to have a misunderstanding regarding recreating userIDs on the new machine: I would have thought that if I restored the /home directory AND /etc directory to the new machine then the user names and userIDs would all be restored correctly at that time. In other words, I would not need to recreate them individually.  Where am I mixed up? 

If you also backup and restore /etc, you'll also restore all user accounts, passwords etc. That's very useful. The one thing you have to be careful about is that you don't restore the reason why you reinstalled. And you can't use that trick when you move from one release of Ubuntu to the next.

---

### Post by ishmael3 on 2020-01-31
TheFu:
 Thanks for the correction on rdiff vs. rdiff-backup. I wasn't meaning to advocate image backups; the reference to the Win-7 procedure was only meant as an example of what I'd call "bone-head simple." I very much appreciate your advice and suggestions. Thanks for taking the time.
 
 Impavidus:
 Thanks for the clarification on /etc.. Also, thanks for taking the time. Much appreciated.
 
 I'll have to do some experimenting and reading to learn more about ownership issues. Then maybe I can ask  more specific questions.  

 Great forum. I hope I'll be able to add something useful one of these days!

---

