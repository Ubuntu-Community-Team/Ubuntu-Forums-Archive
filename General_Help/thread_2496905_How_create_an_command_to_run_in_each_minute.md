---
title: "How create an command to run in each minute ?"
date: 2024-04-16
forum: General Help
---

### Post by aug7744 on 2024-04-16
Thanks for reading my topic.
Have an software (rpcs3 emulator) create an file using extension map. That file is about performance log. When closing the software that file is removed and not is important to run the software.
The problem is when happen an crash the file will continue in /tmp and the user try start again the software so another map will be created. If happen another crash another map file is in /tmp
Sometimes has several map files in /tmp using much space above 150 MB.
The simple solution is run an command to remove any map files in /tmp. That command can run in each minute so I not need remove manually that file.
Is possible create an command to do it ? How create it ?

Have an nice week.

---

### Post by yancek on 2024-04-16
Create a cron entry for it.  Doing that and creating various cron jobs is explained at the link below .

[https://blog.iron.io/how-to-run-cron-jobs-every-5-minutes-10-minutes-or-15-minutes/](https://blog.iron.io/how-to-run-cron-jobs-every-5-minutes-10-minutes-or-15-minutes/)

To quote from that page:  an asterisk in the minute field will make the cron job repeat every minute.

---

### Post by TheFu on 2024-04-16
crontab -e   # this will edit your username's personal crontab.
Add a nice commented, header to the crontab, so you don't have to wonder about the columns in the file. Here's one:

```
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command --arg1 --arg2 file1 file2  > /tmp/log.file  2>&1
# m h  dom mon dow   command
```

Add 1 line for each command to be run, following the timespec.  Output will be spooled to the local email account of the username, so if you don't have email setup on the system to forward emails somewhere else, you may fill the HDD with unread emails. This isn't good.
Example lines for a crontab ... 
```
31 4 * * * /u/thefu/bin/backup_to_rom
```
At 4:31 am, run /u/thefu/bin/backup_to_rom every day.  Use military time for PM times.

To run a command every minute, use * in that field, so the following command will delete a specific file, every minute, every hour, every day, every month with the privileges of your userid.
```
*  *  *  *  *  /usr/bin/rm  /path/to/file/to/delete
```

Caveat, NEVER, EVER, EVER, trust the PATH for any commands run from any crontab. Always specify the complete, full, path, to every program AND to every input or output or log file.  Never assume any CWD/PWD, since it won't be set.  Cron tasks don't have the same environment that we have in a normal terminal window.  If you need any environment variable to be set, you must set it yourself.

You may want to selectively redirect stdout and stderr to specific files. That is left for you to setup.  I'll often send stdout to /dev/null, but let stderr hit my MTA, so I'm notified of cron errors.

---

### Post by aug7744 on 2024-04-16
Thanks for all replies.
I want create that command not doing logs or other activity loging simply to avoid written in disk.
Is possible create an cron not using logs ?
In moment trying create an command using Zeit.

---

### Post by Holger_Gehrke on 2024-04-17
Wouldn't it be simpler to write a small wrapper script for your program that checks for left-over .map files after the program has run and removes them ? Instead of calling rpcs3 directly you'd start the script and that would remove any .map files afterwards.

Holger

---

### Post by TheFu on 2024-04-17
> **aug7744 said:**
> Thanks for all replies.
I want create that command not doing logs or other activity loging simply to avoid written in disk.
Is possible create an cron not using logs ?
In moment trying create an command using Zeit.

If you don't want anything written to disk from a specific command, you could setup an temporary overlay file system that lasts for the length of that command. When the command finishes, the overlay would end and any files created would disappear, without ever touching any physical storage.  There are lots of ways to do it, but the easiest is probably to run it in a **firejail --private** sandbox.

For example, 

```
firejail --private bash
```
will start a bash shell. You can look around to see what it can and cannot access.  Basically, nothing, though a few skeleton .dotfiles  files will exist in your HOME. Files outside of the HOME will have access following normal Unix access/permissions for the userid involved.  Firejail allows custom control over which directories can be seen/accessed through the use of profiles.  In general, /tmp/ is available for all users in the normal, expected, way. If that isn't desired, you'll need a custom profile.

Or you could setup a chroot.

On my media center, TV shows can be recorded using an antenna.  Every 30 minutes, I change the owner/group for newly recorded (actually all files) in the default recorded show locations, since the media center runs under a different userid than I'd like to be the owner of the files.  The group is fine, just the owner isn't ideal.  I could be more selective and do all sorts of scripting, but it is just easier and does no harm to run  
```
/usr/bin/chown  -R thefu:jellyfin /TV/Recordings
```
from the root crontab. I don't need the exact names of the files stored there.  Also, the directories get set with 
```
drwxrw[COLOR="#FF0000"]s[/COLOR]r-x 2 thefu    jellyfin     4096 Apr 17 08:10 ./
```
permissions so any newly created files in those directories (like thumbnails and .nfo files) retain the correct group and group write is allowed/forced.  This is how multiple users can share edit/modification controls over the same files.

As I said, lots of methods are possible.

---

### Post by TheFu on 2024-04-17
> **Holger_Gehrke said:**
> Wouldn't it be simpler to write a small wrapper script for your program that checks for left-over .map files after the program has run and removes them ? Instead of calling rpcs3 directly you'd start the script and that would remove any .map files afterwards.

Holger

+100!   This makes the most sense, if you can get into the software chain that runs the program(s).

---

