---
title: "Concepts of archiving all the user accounts in Ubuntu"
date: 2015-09-04
forum: General Help
---

### Post by damon7 on 2015-09-04
[COLOR=#111111][FONT=Ubuntu]I have given a task to archive all the user accounts for a given batch and delete the user accounts of the students for that batch. Such archiving could be useful for setting up the system for the next batch after the current batch of students left.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Basically for what I have done:[/FONT][/COLOR]

[LIST=1]
[*]I have created multiple user accounts on Ubuntu.

[*]For each user accounts, I created daily backup for the accounts home dir using the code as shown:
0 0 * * * sudo tar -cpzf /backupfolder/user1_backup-$(date +\%Y--\%m-\%d).tar.gz /home/students/user1
[/LIST]
[COLOR=#111111][FONT=Ubuntu]For my current tasks, may I know how should I archive all the user accounts and delete them? I still barely understand the concepts behind of doing so and why it is useful for setting up system for the next batch?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you for your guides![/FONT][/COLOR]

---

### Post by TheFu on 2015-09-04
I wouldn't use tar. It isn't very efficient if you are doing this daily. Plus since these are student accounts, having the backup encrypted might be important.

Check out **duplicity** and I'd backup **all** the HOME storage - not individual HOME directories. I'd backup a copy of the password DB and group DB too - this _may not_ be just the /etc/passwd file - LDAP might be used. Same for the group file.

You didn't say how student accounts are named. If they are generic - user001, user002, user003 ... then you don't need the password entries.  If they are based on names, then you'll need the password entries - NIS, NIS+, AD, LDAP all have ways to grab that data.

Did the requirements say how long to keep this stuff?  Can you get extra storage allocated/purchased just for this need? No is the time to ask, not in a month when there isn't any more storage left.

---

### Post by SeijiSensei on 2015-09-05
Beyond all of /home, I'd back up /etc/passwd, /etc/group, and /etc/shadow since those are the system's authentication files.  If the machine stores mail, then the contents of /var/mail should be archived as well.

One way you can check to see what needs to be backed up for a user is to pick an account name at random, say "hermione", then run the commands
```

sudo updatedb
sudo locate hermione

```
That will list all the files and directories with "hermione" in their names.  It won't find files like /etc/passwd, of course, since that file contains the string "hermione" but the filename does not.

---

