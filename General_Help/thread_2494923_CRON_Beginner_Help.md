---
title: "CRON Beginner Help"
date: 2024-01-31
forum: General Help
---

### Post by unbuntunewbie02 on 2024-01-31
I have created a bash script that checks of updates and returns a value if any and notes the data and time.

Ideally I would like this to run every hour and using CRON it is installed and is active but my CRON job does not run "/home/webserver/Desktop/Bash_Script/Updates.sh: Permission denied"

I can run a terminal and manually run the script by browsing to the folder the script is located in with no sudo which works correctly.

running ls -l on the script gives me:

rw-rw-rw- 1 webserver webserver 382 Jan 31 15:10 Updates.sh

Which is the user i am running the CRON 

What am I missing

---

### Post by TheFu on 2024-01-31
```
chmod +x /home/webserver/Desktop/Bash_Script/Updates.sh
```

The execute permission is required for scripts to run.  Additionally, the userid running the script needs to have read access on the file.
In general, placing cron scripts in a HOME directory is a poor choice for a number of reasons. I'd put it elsewhere.

Additionally, the username "webserver" could lead to confusion since on Ubuntu web servers run under the www-data user and group.  For files to be accessed by that process, you need to ensure that through file permissions.  

There are lots of tutorials for Unix permissions.  Those tutorials provide the information, but they won't make it "click" in your mind.  For that to happen, plan on spending an hour with 3 terminals, mixing and matching groups with users to see what permissions, owners, groups can and cannot do things with text files, scripts, programs, directories.  What I did was to create a subdirectory under /tmp/ to play around.  Then I literally used every possible combination of permissions then checked which other test usernames I'd created could and couldn't do things with those files.  I started with 000, 100, 200, 300, 400, 500, 600, 700, 010, 020, 030, .... up to 777.  You get the idea.  Don't forget to to the same for directories with files inside them.  That can be really eye opening.  

With 8 octal characters, we've ignored the special flags that the 4th octal provides. 90% of the time, that isn't important. I don't have the values for octal special flags memorized after 30 years.  I use the symbolic methods, but for the main 3 octals, after this effort, you'll probably have them memorized.  644, 664, 640, 755, 750, and 751 are very typical, much used values.

---

### Post by unbuntunewbie02 on 2024-01-31
If I run  chmod +x the text file doesn't show anything only the last time i ran the file in the directory.

---

### Post by TheFu on 2024-01-31
> **unbuntunewbie02 said:**
> If I run  chmod +x the text file doesn't show anything only the last time i ran the file in the directory.

Sorry, I don't understand what you are trying to say.

What does the crontab line show?
Which crontab are you using?
Which userid do you want this script to run under?

There are differences between the environment that cron provides with the environment that an interactive GUI session provides.  Under cron, it is minimal so many environment variables aren't set. This means that if any are being assumed, but don't exist, then the script won't work.  You can see the difference by creating 2 scripts.
```
#!/bin/bash

env > /tmp/interactive.env
Run this from any terminal session you have.


``````
#!/bin/bash

env > /tmp/cron.env

```
Have this as a file and have cron run it.

Now, compare those two files.  /tmp/cron.env   and /tmp/interactive.env  Note the differences?  I'd use the **meld** program for this, but you can use diff, sdiff, or some other tool, if you prefer.

Oh, and the fix for missing environment variables is to set them inside your script.

---

