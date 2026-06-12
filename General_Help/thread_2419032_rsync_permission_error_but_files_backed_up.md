---
title: "rsync permission error but files backed up"
date: 2019-05-15
forum: General Help
---

### Post by Frank P on 2019-05-15
I'm using rsync in a bash script to backup files from a Ubuntu 16.04LTS server to a local Ubuntu 18.04LTS server.. The rsync statement below
```

[FONT=Verdana]rsync  -azhq --stats --exclude=.* --log-file=backup_myfileserver.log /home/myfileserver /mnt_remote_backup/${backup_destination}[/FONT]

```
I'm getting errors in the log for some files, but all files, even the ones with the error message seem to have been transferred okay. Is this normal? Is there anything I can do to remove the error messages
Thanks
```

[FONT=Verdana]2019/05/15 11:48:41 [3155] building file list
2019/05/15 11:48:41 [3155] rsync: chgrp "/mnt_remote_backup/2019-05-15/myfileserver" failed: Permission denied (13)
2019/05/15 11:48:42 [3155] rsync: chgrp "/mnt_remote_backup/2019-05-15/myfileserver/personal" failed: Permission denied (13)
2019/05/15 11:48:42 [3155] rsync: chgrp "/mnt_remote_backup/2019-05-15/myfileserver/personal/personal" failed: Permission denied (13)
2019/05/15 11:48:42 [3155] rsync: chgrp "/mnt_remote_backup/2019-05-15/myfileserver/personal/photography" failed: Permission denied (13)

```
[/FONT]

---

### Post by TheFu on 2019-05-15
If the userid isn't a member of the group and the groups don't exist on both systems, yes.
rsync is only an effective backup tool if the files are all owned by 1 userid and that userid is the one running the rsync command.

Of course, the storage needs to be Linux on a file system, not NTFS nor FAT-whatever. Those don't support Unix-style permissions through the available drivers.

BTW, why not use **rsync -avz local-source/ userid@remote-IP:/target/directory/ **for the command to see what the issues are a little better, then once things are working, you can remove the -v and put in the -q.

From a security standpoint, backups should be pulled by the backup server using non-remote mount protocols.  rsync fits that nicely.  By using network mounts (it appears you are) and mounting on the client machine, then malware can totally destroy all the backups.  With the backup server pulling data and not allowing the client machine(s) direct access to that storage, you've just protected your backups from crypto-locker-type attacks.

Is there a reason not to use a real backup tool that handles versioning for you?  They are crazy efficient these days and the command looks pretty much like an rsync command, but provides so much more capability for almost zero extra effort and less than 10-15% more storage.  Just a thought.

If you are doing HOME directory backups, not using root (or a root-equiv) userid is fine.  If you are doing backups for systems, then using root really is the only method that can also be secured.

I'm happy to explain anything above if it isn't clear.  Excellent, versioned, backups are really easy these days.

---

### Post by Frank P on 2019-05-15
Thanks for the detailed answer. I have a few questions
```

[LEFT][COLOR=#000000][FONT=Ubuntubeta]If the userid isn't a member of the group and the groups don't exist on both systems, yes.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]rsync is only an effective backup tool if the files are all owned by 1 userid and that userid is the one running the rsync command.[/FONT][/COLOR][/LEFT]

```[LEFT]
[/LEFT]
I think I have a problem with one user/userid but I can fix that. But for now are my backups okay in spite of the error messages
```

[LEFT][COLOR=#000000][FONT=Ubuntubeta]Of course, the storage needs to be Linux on a file system, not NTFS nor FAT-whatever. Those don't support Unix-style permissions through the available drivers.[/FONT][/COLOR][/LEFT]

```[LEFT]
[/LEFT]
Yes it's on a Linux file system - ext4
```

[LEFT][COLOR=#000000][FONT=Ubuntubeta]BTW, why not use [/FONT][/COLOR]**rsync -avz local-source/ userid@remote-IP:/target/directory/ **[/LEFT]
for the command to see what the issues are a little better, then once things are working, you can remove the -v and put in the -q.

```
I was using the v but the output was overwhelming so I tried the q to see if it was easier to understand
```

From a security standpoint, backups should be pulled by the backup server using non-remote mount protocols.  rsync fits that nicely.  By using network mounts (it appears you are) and mounting on the client machine, then malware can totally destroy all the backups.  With the backup server pulling data and not allowing the client machine(s) direct access to that storage, you've just protected your backups from crypto-locker-type attacks.
```
I agree and will change it
```

Is there a reason not to use a real backup tool that handles versioning for you?  They are crazy efficient these days and the command looks pretty much like an rsync command, but provides so much more capability for almost zero extra effort and less than 10-15% more storage.  Just a thought. If you are doing HOME directory backups, not using root (or a root-equiv) userid is fine.  If you are doing backups for systems, then using root really is the only method that can also be secured.
```
Its a hobby site and I'm using bash and rsync as a learning experience.

Thanks again for your help

Frank

---

### Post by SeijiSensei on 2019-05-16
One solution is to run the command as root with sudo.  I write all my backups as root so I don't need to worry about permissions.

---

### Post by Frank P on 2019-05-16
Thanks for the suggestion. 
I decided to take this opportunity to straighten out the owner/groups permissions for all the files. That seemed to get rid of the errors.
Frank

---

### Post by TheFu on 2019-05-16
In general, I really appreciate 'code tags', but not when quoting others. ;) Makes reading the paragraph hard when it doesn't wrap.  "quote tags" would be great above.

> Its a hobby site and I'm using bash and rsync as a learning experience.
Good enough.  We all have to start somewhere and mastering rsync **is** an excellent use of your time.

I agree with SeijiSensei about using root/sudo for backups to retain permissions. For local backups to local storage, this is the easy method.  For network-based backups, there are some added complexities in using sudo/root between Ubuntu systems.

Anyways, the rdiff-backup tool uses librsync and provides versioning.  The most recent backup is just like an rsync mirror, plus it keeps track of file permissions changes over time, unlike rsync.  rsync only knows the last permissions for a file/owner/group.  rdiff-backup knows whenever they change and stores that data in the versioning.  For backups of files all owned by the same userid, like just a single HOME directory, this isn't too important.  But for whole system backups, retaining the correct permissions is absolutely critical.

```
$ sudo rdiff-backup --exclude-special-files --exclude=.*  /home/myfileserver /mnt_remote_backup/${backup_destination}
```
should work.  I'd need to look at the --exclude, since globbing in rsync/rdiff-backup don't work like normal file system globbing does.  Both rsync and rdiff-backup follow the same rules, however.  I wouldn't exclude all .files like that, since Unix uses them to store configurations for many, many, different programs. These are usually stored in $HOME, but sometimes they are stored elsewhere - like .gitignore, .vimrc, and other $PWD specific tools.  If you want to exclude .cache/ directories, --exclude=**/.cache is how I'd do it.   Of course, there are 50 different ways to handle this. Whatever works is good.

---

### Post by Frank P on 2019-05-16
I'll check out the rdiff-backup
Thanks
Frank

---

