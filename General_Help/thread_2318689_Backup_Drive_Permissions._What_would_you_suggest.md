---
title: "Backup Drive Permissions. What would you suggest?"
date: 2016-03-28
forum: General Help
---

### Post by mikodo on 2016-03-28
Hi,

All backup drives are formatted to Ext4 FS's. I am the only user:user on this system. What would you suggest for the backup drives' permissions?

I know little about permissions and tend to depend on octal notations for my backup drives. Maybe, I need to change things a little but, I dunno. 

Today, I decided to change the permissions of my backup drives to chmod 777. To make them much less restrictive for "my user" easy access from, if needed.

For backing up of / I will use **sudo** rsync. I was just going to it. Then, wondered if the permissions should be different for that backup drive than, any other?

 When I check my install's / permissions I get this. 
 ```
mikodo@mikodo:~$ stat /
  File: &#8216;/&#8217;
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d    Inode: 2           Links: 23
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2016-03-27 11:44:49.327906686 -0600
Modify: 2016-03-26 11:33:37.749252546 -0600
Change: 2016-03-26 11:33:37.749252546 -0600
 Birth: -
mikodo@mikodo:~$ stat -c %a /
755
mikodo@mikodo:~$ 

```

Thank you!

---

### Post by TheFu on 2016-03-28
Wow. Just Wow.

Using 777 permissions is a very, very, very, bad idea on a system with networking.  Learn about Unix directory and file permissions before starting out. This knowledge is the core to all Unix system security. Without this knowledge, you've just defeated 95% of the security on the system, not just the storage.

There are all sorts of different backup tools. Without knowing which you are using and how you are using it exactly, it is impossible to make any additional suggestions.  Some backup tools don't care what the storage file system is. For others, the backup file system is integral to the backup.

In general, nobody should see anything on the backup storage they cannot see on the regular storage. Further, if the backup storage is portable, it must be encrypted, to prevent "just anyone" to have access to the backup data.

Don't have any idea why stat was posted. Don't generally see that used outside of programming calls ( stat() or fstat() ).

---

### Post by mikodo on 2016-03-28
All right.

I'll go back to my much more restrictive permissions on my backups. I didn't like it because when I looked at them, with my user I was locked out. But, the backups worked.

Hopefully, my oops of my those permissions today, will not cause a breach of my security until, I change out this one computer. Then, dd the drive. Fingers crossed.

Thank you.

---

### Post by ajgreeny on 2016-03-28
I also use rsync to backup my /home partition to an external HDD which has an ext3 partition.

I have labelled the external disk partition as "Backup" so when I connect the drive it is mounted in my system automatically to /media/*username*/Backup.
Your disk/partition will mount to another named folder, but do as I did which was to run command ```
sudo chown -R *username:username* /media/*username*/Backup
```which will give you ownership of the partition and allow you to read and write to it.  Use your own system mountpoint and your own username, of course.

---

### Post by TheFu on 2016-03-28
Backing up with rsync provides 1 mirror.  Almost the exact same command with rdiff-backup can make efficient, versioned, backups which take very little added storage. [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) quickly, simply, explains.

chown -R is fine for HOME directory backups.  Not very useful for system backups.  That's a good way to end up with a system that doesn't work.

---

### Post by mikodo on 2016-03-28
> **ajgreeny said:**
> I also use rsync to backup my /home partition to an external HDD which has an ext3 partition.

I have labelled the external disk partition as "Backup" so when I connect the drive it is mounted in my system automatically to /media/*username*/Backup.
Your disk/partition will mount to another named folder, but do as I did which was to run command ```
sudo chown -R *username:username* /media/*username*/Backup
```which will give you ownership of the partition and allow you to read and write to it.  Use your own system mountpoint and your own username, of course.

Thank you. I saw that last night:

[http://ubuntuforums.org/showthread.php?t=2014846&highlight=usb+flash+drives](http://ubuntuforums.org/showthread.php?t=2014846&highlight=usb+flash+drives)


> **TheFu said:**
> Backing up with rsync provides 1 mirror.  Almost the exact same command with rdiff-backup can make efficient, versioned, backups which take very little added storage. [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) quickly, simply, explains.

Thank you. rdiff-backups are in my future from, your earlier suggestions.

> chown -R is find for HOME directory backups.  Not very useful for system backups.  That's a good way to end up with a system that doesn't work.

I am seeing that. I am using a data partition, that is symlinked from my ~. For my one and only computer to usb nodes.

I have gone back (for now) to this, after an afternoon of reading on chown and chmod:

```
For setting chmod for /mnt/data:

 mikodo@mikodo:~$ sudo chmod -R a+rwX /mnt/data
```
See Morbius1's explanation:[ http://ubuntuforums.org/showthread.php?t=1795369]("http://ubuntuforums.org/showthread.php?t=1795369")  

For backup nodes, I have gone back to (example):

```
sudo chown mikodo:mikodo /media/mikodo/FlashBackup1

sudo chmod -R a+rwX /media/mikodo/FlashBackup1   **<- I missed that line earlier here**

rsync -av --delete /mnt/data/ /media/mikodo/FlashBackup1 
```

That sent me in a "tail spin" last night, when I thought I would see what my backups looked like from a live cd.

All I saw where the sub-directories. No data in them. I thought what the ? and went to that foolish and unsafe way so I could see my data from a live cd????

```
sudo chmod 777 /media/mikodo/FlashBackup1   and all the other nodes
```

What I found today from reading man chown && chmod:

chown

-R gives recursive permissions on all files. 

chmod

This  a = for  all users; + = attaching to all users = r (read), w (write), = X execute (execute/search  only if  the file is a directory or already has execute permission for       some user)  from man chmod.

execute, (search for directories)

execute = run a binary. Typically an (.file like .exe) like programs or possibly malicious code.

That is I guess why in the live cd I couldn't see, what was in my backup files beneath the sub-directories from, rsync backed up nodes.


I will test later on being able to return my data partition back from backups safe and secure, again. 


Thank you, so much.

---

### Post by TheFu on 2016-03-28
From reading what you wrote, it appears you've misunderstood Unix file/directory permissions.
Don't use 777 permissions.  Don't use a+rwX either. Same thing.  I suspect I'm not making my point clearly. Sorry for my failure.  Maybe I'm making a bigger deal about this than others because I manage multi-user systems and these permissions are the cornerstone for all system security.

"Other" shouldn't usually have any write permissions and read permissions only on files you'd want on the front page of the New York Times.

I wouldn't mind if you use **chmod -R ug+wrX** - it really is the "other" part  that is at issue.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by mikodo on 2016-03-28
> **TheFu said:**
> 

I wouldn't mind if you use **chmod -R ug+wrX** - it really is the "other" part  that is at issue.
*I read up on that*. I'll do as you say. I see the value of having the **ug.**

Thank you, for the hand-holding.

---

### Post by ajgreeny on 2016-03-29
> **TheFu said:**
> chown -R is fine for HOME directory backups.  Not very useful for system backups.  That's a good way to end up with a system that doesn't work.
But as I said I backup my /home only; I can reinstall the OS so quickly that it seems pointless to me to bother backing up that as well.

Of course that may well depend on what you use your computer for; perhaps you have some important personal information or databases in the filesystem that you must backup, whereas I do not.

---

### Post by mikodo on 2016-03-29
> **ajgreeny said:**
>  - snippet - I can reinstall the OS so quickly that it seems pointless to me to bother backing up that as well.Sure. I can too. I've had to do it lots when I was earlier in my learning process. I tend to modify my desktop given Xfce being so modular though. And things like my symlinks to my data partition that I also of course, backup. It would be interesting to see how much of a "bit for bit", comes back from an installation of it all from, a sync of it, though. It was more of a "scratching of an itch" than, any serious backup for  protecting data. I just thought it would be cool to try it. 

Though, I need to re-consider given, what TheFu has warned. And to, learning more important aspects of administrating my Linux install first.
  
Now, to attending to chmod of my nodes and other security practices. I am using the chmod as TheFu suggested  with, no ill effects on my install.

Thank you.

---

### Post by TheFu on 2016-03-29
If you only backup the HOME, then having your userid as the owner for all files is fine.  A liveCD can fix that later, during a restore, if needed.  Symbolic link backups gets the links alone, unless you specifically ask for them to be followed. I don't.  I backup file systems (not as separate backup jobs). Find that safer and easier to restore.  I suppose doing it by following links would only risk having multiple copies if you also backed up the other storage too.  But how would you restore putting the linked data to that alternate disk?  See my point?

However, I'd encourage you to also backup a list of installed packages, so reinstalling them isn't a chore later and the system settings in /etc/ - there are lots of tiny things there that are a pain to remember. Having a backup of those areas too will make life much easier.  It isn't like the list of packages is big or all of /etc/ either.  Of course, /etc/ has very specific ownership AND permissions, so you'll need/want to be careful.  A normal userid cannot successfully backup /etc/.

I've been optimizing my backups for 15 yrs now.  Like to think I have it down pretty solid - just enough to get everything back within an hour.  Not so complex so that someone else with "general Unix administrative knowledge" couldn't restore it too.

And just to be very clear, @ajgreeny's methods do make perfect sense for many average end-users using the system only as a desktop, without **any** modifications, or system tweaks.  

I think I've posted my backup-script-template somewhere in these forums - but it has been a few years since I've modified it in any serious way.  Don't have time to clean/sanitize the scripts for others to view now, but  ... [http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup](http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup) from 2009 is  relevant still.  I've switched over to perl for the script too - needed some better parsing than sh/bash can handle.  I do network backups on most systems, so ssh-keys are setup between the systems as needed. That part isn't important. Local backups on the backup server do not use ssh.  I use a separate backup userid (root equiv, but not root) to perform the backups.  The first HowTo link (?kira.net?) for rdiff-backup is really how I'd do it today, if starting from scratch, but I would still do all of the pre-backup tasks as my article shows.  If you are going to do backups, why not make the restore process as painless as possible, within the practical storage limitations available?

---

### Post by mikodo on 2016-03-29
> **TheFu said:**
> Symbolic link backups gets the links alone I apologize. I was* not* clear. I wouldn't want to follow the links in the backup of / or rather, my plan then, to backup / either. Initially, I was planning to test this by syncing my / to a backup (second) drive and keep it current with **sudo rsync -av --delete**. Then, when I had the time for this, sync a copy to a (third) "test" drive. Use **tune2fs** to change the test internal drive's UUID in its' /etc/fstab that was synced over. Then, match UUID specifications in the file **/boot/grub/grub.cfg** to the new test install's. Install Grub2 in it in a chroot environment. Sync over a copy of my Data partition, to the "test" drive and with its' partition and change its' Label and Boot into the new test drive and see if the symbolic links from new install's ~ for my Documents, etc. had followed to my "data" partition correctly that, is mounted in mnt/data (LABEL) after changing the name in /mnt/LABEL to match. But, I'll will have to see when, I try it. A lot of this detail, ie. change the UUID with **tune2fs**; for /etc/fstab in my / partition and **/boot/grub/grub.cfg** and other stuff came from the tutelage of **sudodus** in another thread of mine. I hope I have that right and clear enough to follow. I am kinda mixing ideas as I type here.

> However, I'd encourage you to also backup a list of installed packages, so reinstalling them isn't a chore later and the system settings in /etc/ - there are lots of tiny things there that are a pain to remember. Having a backup of those areas too will make life much easier.  It isn't like the list of packages is big or all of /etc/ either.  Of course, /etc/ has very specific ownership AND permissions, so you'll need/want to be careful.  A normal userid cannot successfully backup /etc/.  I will be looking into this, sometime. I have heard of others doing this too. I have some more learning about that I see.

> I've been optimizing my backups for 15 yrs now.  Like to think I have it down pretty solid - just enough to get everything back within an hour.  Not so complex so that someone else with "general Unix administrative knowledge" couldn't restore it too. It is apparent and, I am not that self-centered to think that you are writing this just for my benefit. But, for all readers, I'll take the liberty to say, Thank you!

> And just to be very clear, @ajgreeny's methods do make perfect sense for many average end-users using the system only as a desktop, without **any** modifications, or system tweaks. Just to highlight this point. 

> I think I've posted my backup-script-template somewhere in these forums - but it has been a few years since I've modified it in any serious way.  Don't have time to clean/sanitize the scripts for others to view now, but  ... [http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup](http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup) from 2009 is  relevant still.  I've switched over to perl for the script too - needed some better parsing than sh/bash can handle.  I do network backups on most systems, so ssh-keys are setup between the systems as needed. That part isn't important. Local backups on the backup server do not use ssh.  I use a separate backup userid (root equiv, but not root) to perform the backups.  The first HowTo link (?kira.net?) for rdiff-backup is really how I'd do it today, if starting from scratch, but I would still do all of the pre-backup tasks as my article shows.  If you are going to do backups, why not make the restore process as painless as possible, within the practical storage limitations available?Again, thank you. Now, about my experience. I am in my early 60's and started with this my first computer in the latter half of my 50's. I am slowing down. At work today, I got called into my immediate supervisor's office for a friendly inquiry in to how I am doing as I hadn't looked well lately. I had to tell her that I had been messing with this stuff too much and was running on 4 - 5 hours sleep each night for the last while. With that I need to eat supper and try to sleep better tonight.

Oh, all my drives are working well using [B]sudo chmod -R ug+wrX 
[/B]
Thank you.

---

