---
title: "mysqldump works from terminal but not from shell script"
date: 2016-02-08
forum: General Help
---

### Post by utklasad on 2016-02-08
Hello,

When I run this command from my terminal it generates a valid .sql file in my backup folder:

```
mysqldump -u myUser -h myHost -pmyPassword myDatabase > /myPath/backup/mysql-backup.sql
```

When I run this shell script it works (no errors), but it generates a corrupt/nonvalid/unknown .sql file:

```
chmod +x sql-backup.sh
./sql-backup.sh (get the same result using sudo, a created .sql file that's corrupted/unknown)

```

_sql-backup.sh:_
```
#!/bin/bash

NOW=$(date +"%Y-%m-%d_%H%M")

echo timestamp = $NOW

mysqldump -u myUser -h myHost -pmyPassword myDatabase > /myPath/backup/$NOW-mysql-backup.sql

```

Any ideas?

Thanks,
/Blix

---

### Post by ian-weisser on 2016-02-08
How are you running the shell file? Teminal? Cron job? Root prompt? Using sudo?

---

### Post by SeijiSensei on 2016-02-08
```
mysqldump -u myUser -h myHost -pmyPassword myDatabase > myPath/backup/$NOW-mysql-backup.sql
```

You don't have a full path to the backup file, like /home/me/myPath.  As it stands, the script will expect to find a "myPath" subdirectory under the current directory when the script is run.

---

### Post by Habitual on 2016-02-08
/path/to/mysqldump in the script is generally a good idea since cron doesn't have a "$PATH" environment.

---

### Post by utklasad on 2016-02-08
> **ian-weisser said:**
> How are you running the shell file? Teminal? Cron job? Root prompt? Using sudo?

I'm running it with sudo from the terminal. Tried without sudo too, same result. The plan is to run it as a cron job later, if I manage to get it working...


> **SeijiSensei said:**
> ```
mysqldump -u myUser -h myHost -pmyPassword myDatabase > myPath/backup/$NOW-mysql-backup.sql
```

You don't have a full path to the backup file, like /home/me/myPath.  As it stands, the script will expect to find a "myPath" subdirectory under the current directory when the script is run.

Hmm okay. I doubt there is anything wrong with the path since the .sql file gets created at myPath. I just can't open it and the file format is unknown. If you're meaning that I missed the starting "/" before myPath that was just a typo here. Corrected the path in the main post.


Thanks for the help, but it's still not working... Maybe I should try to run it with a cron job and see if it works then?

---

### Post by Dragonbite on 2016-02-08
```
#!/bin/bash

NOW=$(date +"%Y-%m-%d_%H%M")

echo timestamp = $NOW

mysqldump -u myUser -h myHost -pmyPassword myDatabase > /myPath/backup/$NOW-mysql-backup.sql

```

I don't know if you were copy-and-pasting the command, but you need a space between "-p" and "myPassword". ;)

I'm not sure what you are doing with the "echo timestamp = $NOW" portion.  Does it work if you take out that portion and run something more basic from the script?  You shouldn't need to use SUDO unless you are saving the file in a location you don't have access to.  And SUDO will not be used in the running of the mysql code (that's what the username and password fields provide).  ```

#!/bin/bash

msqldump -u myUser -h myHost -p myPassword myDatabase > /home/xyz/backup/mysql-backup.sql

```I usually start with making the most basic command and then add on new things.

On the other hand, I don't think this will make a difference with the corrupt .sql file  Looking at the MySQL page for mysqldimp ([http://dev.mysql.com/doc/refman/5.7/en/mysqldump.html]("http://dev.mysql.com/doc/refman/5.7/en/mysqldump.html")) I wonder if the encoding format could be an issue or anything like this > --compatible=name

Produce output that is more compatible with other database systems or with older MySQL servers. The value of name can be ansi, mysql323, mysql40, postgresql, oracle, mssql, db2, maxdb, no_key_options, no_table_options, or no_field_options. To use several values, separate them by commas. These values have the same meaning as the corresponding options for setting the server SQL mode. See Section 5.1.7, “Server SQL Modes”.

This option does not guarantee compatibility with other servers. It only enables those SQL mode values that are currently available for making dump output more compatible. For example, --compatible=oracle does not map data types to Oracle types or use Oracle comment syntax.

Sorry I'm not more up on it.  I am working with PostgreSQL on FreeBSD so things are a little different.

---

### Post by SeijiSensei on 2016-02-08
> **Dragonbite said:**
> [I'm not sure what you are doing with the "echo timestamp = $NOW" portion.
It's used to create the unique name for the timestamped backup file.

As for the "-ppassword" item, the man page for mysqldump reads:

"If you use the short option form (-p), you cannot have a space between the option and the password."

OP, if you open the resulting file with a text editor like nano, gedit or kate, what do you see?

---

### Post by Dragonbite on 2016-02-08
> **SeijiSensei said:**
> It's used to create the unique name for the timestamped backup file.

I don't know if it is completely different in Linux but what I use for adding date to the filename is ```

NOW=$(date + "%Y-%m-%d")                                  #formats as yyyy-mm-dd

FILENAME="/home/me/backup/postgres_$NOW.sh"   #or I could put it into the actual command

```and then output to $FILENAME.  Being PostrgreSQL the actual command is different so I'm not putting it here because it'll cause too much confusion.

Just trying to understand the use of "echo timestamp" and putting it to a variable.  I would think it would be more like "echo timestamp > NOW" but even that doesn't make sense.  Putting "NOW=$date" also works, but the format gets pretty wonky.

EDIT: Nevermind, now I see that the NOW is being used the same way as I do (mostly), the echo is just displaying it in terminal and doesn't actually perform a function in the backup process.

I agree, what does the output look like in a text editor?

---

### Post by Habitual on 2016-02-08
```
/usr/bin/mysqldump -u myUser -h myHost -pmyPassword myDatabase > /myPath/backup/$(date +"%Y-%m-%d_%H%M")-mysql-backup.sql
```

---

### Post by utklasad on 2016-02-09
> **SeijiSensei said:**
> 
OP, if you open the resulting file with a text editor like nano, gedit or kate, what do you see?

Hmm, I saw something strange now. I tried to open **2015-02-08_0740-mysql-backup.sql** with **nano**, then it just tried to create a new one (like it didn't found it).

Then I ran the **ls** command and found out that the sql-file got a question mark at the end. If I **nano** that file it's containing the sql query, but I can't save it since "the file does not exists".

If I run **ls** it shows the file with a question mark at the end:

```

ls
2015-02-08_0740?-mysql-backup.sql?

```

The name of the file should be: **2015-02-08_0740-mysql-backup.sql** (without the ?) and that's the name it gets when I run the mysqldump-command from the terminal directly. Seems like the shell script add these question marks and messes upp the file? Same result if I remove the $NOW part and only use hardcoded file name.

@Dragonbite I'm pretty sure there should not be a space between -p and password. If I try to use a space the command fails.

---

### Post by utklasad on 2016-02-09
Solved!

I had an empty line after the mysqldump-command in the shell script. Unbelievable how I could miss that... Removing that empty line solved everything. Thanks for the help!

/Blix

---

### Post by Habitual on 2016-02-09
But a lot of shell scripts have "empty lines"...?

---

### Post by SeijiSensei on 2016-02-09
More likely there was a trailing non-printing control character accidentally added to the end of the line.

OP, you didn't create this file in Windows or DOS first, did you?  They terminate lines with a "return" and a "newline."  Unix only uses the latter.  So if you create the file with something like Notepad in Windows, you'll have extraneous return characters at the end of every line which can confuse the Bash shell.

---

### Post by utklasad on 2016-02-12
I created the file in Windows, therefor the empty line got formatted wrong. Noticed this later when I needed to add more code to the script. Created it with Linux instead and everything was working!

---

