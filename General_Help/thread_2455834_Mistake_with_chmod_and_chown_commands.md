---
title: "Mistake with chmod and chown commands"
date: 2020-12-28
forum: General Help
---

### Post by jay30 on 2020-12-28
I have setup a Ubuntu server (18.04) with PHPBB (along with apache2 and mysql etc).  Everything was up and running fine until I needed to go in an add a few files to one of the directories on the server to be able to enable an extension.  When I tried to do so I didn't have access to place files into the /var/www directory.  Did some research and found the suggestion to run the following 2 commands (which I did):

sudo chmod -R 757 /var/www
sudo chown -R myid:myid /var/www

Since I have done this I get some warnings/errors with I go into PHPBB and the system is not allowing me to make certain changes to the forum setups within PHPBB.  I am assuming it has to do with the 2 commands I issued.  Did these commands mess up the PHPBB software ability to write changes or something?  Have I messed myself up badly?  Any suggestions?  Thank you in advance.

---

### Post by TheFu on 2020-12-28
Probably.
Probably.
Solution: restore any directories you altered from the backup you made just prior.

Those are some funky permissions. I wouldn't consider those safe on the internet.
File and directory permissions are the front-line for all Unix security.

---

### Post by jay30 on 2020-12-28
I hadn't done a backup yet.  Any commands i can issue on that directory to open the access as it should be

---

### Post by TheFu on 2020-12-28
> **jay30 said:**
> I hadn't done a backup yet.  Any commands i can issue on that directory to open the access as it should be

There isn't any "undo" - so if you don't know what the owner, group, permissions, ACLs, and xattrs were BEFORE you did those commands, then no.  The data isn't sufficient for backups. The data plus all those other things are required FOR EACH FILE and DIRECTORY.

Whatever you do, first step is to get that system off the internet ASAP. As the permissions are now, it is just scary.  Anyone not in the group has full access to do anything to the files and subdirectories there.

If it was me, I'd assume it had already been compromised and wipe the system, start over, reload from scratch using my notes, and MAKE A GOOD system-level backup, before putting it onto the internet.

There are ways to make snapshots using advanced file system capabilities, but these are beyond someone new to Unix systems. They would cause more problems than they would solve at this point, unfortunately.  They must be installed BEFORE the file system is created since they are between the hardware and the file system.  Most people get by with daily, automatic, versioned, backups just fine.  If running a server, those are not optional. They are mandatory.  The higher risk to the server, the more mandatory they are and getting those backups to a different system is even more important.

Probably the best you can do now is to learn from these few, easily made, mistakes, so they don't ever happen again.

---

### Post by jay30 on 2020-12-28
Thank you kindly for your help.  Thankfully the system is not yet on the internet - it is just running on a Ubuntu server within my home at the moment - no access from outside.  I was using the server to trial the setup of a forum using phpbb.  If there is nothing I can really do to repair the access to that directory then I may just start again from scratch.

---

### Post by TheFu on 2020-12-28
Allowing access is easy, but php webapps need very specific permissions, owners, groups. acls to provide exactly the level of access needed, but not any more.  Learn Unix permissions.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Perhaps someone with an existing install of that software could help? Alas, the software name isn't in the thread title, so unlikely they would see this thread.  Every webapp has different requirements, so there isn't any simple, generic, answer.  The website for the webapp project may have specific information on the permissions. Have you checked there?

---

### Post by jay30 on 2020-12-29
Thanks for that tip.  I did a search on phpbb file permissions and did find something in the phpbb forum and located some documentation on chmod permissions required for phpbb.  It indicates the values noted below.  Does it therefore seem reasonable that I go through the noted files/directories and adjust the chmod values for those directories/files?

[COLOR=#800040]**Correct Chmod Values**[/COLOR] 
[LIST]
[*]config.php
[LIST]
[*]666 before installation
[*]644 after installation
[/LIST]

[*]All other files - 644
[*]All directories - 755
[LIST]
[*]There are some exceptions when it comes to directory permissions,
[LIST]
[*]The ***files*** directory - 777
[*]The ***cache*** directory - 777
[*]The ***store*** directory - 777
[*]The ***images/avatars/upload*** directory - 777
[/LIST]
[/LIST]
[/LIST]

---

### Post by jay30 on 2020-12-29
Actually, disregard my last note - I have found/realized now that I didn't actually execute that chmod command.  I did, however, execute the chown command.  So that is probably what has cause the issue.  I will check phpbb documentation to see if there is anything on ownership settings for folders.

---

### Post by TheFu on 2020-12-29
777 directory permissions is for lazy people or people who don't understand permissions and should only be used when you want to be hacked, imho.  Worry whenever instructions for an installation suggest those.  it means they decided to be lazy, not secure.

Learn about Unix permissions, ownership, and process effective userids so you can create better, more secure settings, than the 777 suggested above.  I'd guess that having www-data as the owner of those 777 directories above would allow tighter 700 permissions.

---

