---
title: "Custom Cleanup Script Worked, But Now This..."
date: 2024-09-11
forum: General Help
---

### Post by wyattwhiteeagle on 2024-09-11
This may be specific to Lubuntu, but I'm not sure.

My custom cleanup script worked phenominally on 22.04, but on 24.04 the script removes and purges those things which I install, such as Bleachbit, Kolourpaint, Falkon, etc.

What changed from 22.04 that might cause this?

---

### Post by dragonfly41 on 2024-09-11
If you build optional logging into your custom script that might be a start.

---

### Post by wyattwhiteeagle on 2024-09-11
> **dragonfly41 said:**
> If you build optional logging into your custom script that might be a start.

Optional logging, hmm

Here's the current script, any corrections/suggestions are greatly appreciated.
I run this script with sudo

```


# Delete "orphaned" packages
   deborphan | xargs apt remove --purge -y

# Houseclean over 10 days
   journalctl --vacuum-time=10d

# Delete old logs
   find /var/log -type f -name "*.gz" -delete

# Remove packages that didn&#8217;t install completely
   apt autoclean -y

# Clean your apt-cache
   apt clean -y

# Clear thumbnails
   rm -rfv ~/.cache/thumbnails

# Clear cache
   du -sh /var/cache/apt

# Remove software dependencies that you no longer need
   apt autoremove -y

# Kernel and other Cleanups after Deletions
   apt autoremove --purge -y
```

---

### Post by Rubi1200 on 2024-09-11
I would be tempted to suggest that perhaps the **deborphan **part of your script is responsible for purging packages that you want to keep.

With your current Lubuntu 24.04 setup, **deborphan **might be identifying some critical or installed applications (like Bleachbit, Kolourpaint, Falkon) as orphaned due to changes in package dependencies or configurations.

One possible solution would be to whitelist packages you do not want removed.

For example, create or modify the /etc/deborphan.conf file and add these lines:
```
keep Bleachbit
keep Kolourpaint
keep Falkon

```

Note, I am not a Lubuntu user so this is kind of guesswork on my part.

Let's wait for others to add their thoughts before you make any changes.

---

### Post by TheFu on 2024-09-11
That script makes all sorts of dangerous assumptions.
It doesn't specify the script interpeter to be used on the first line. That is non-standard.

The commands are dependent on the PATH, which can be dangerous.  Best to fully specify the exact, absolute, location for any program used in a script.  For example, "apt" should be "/usr/bin/apt". Find the full path for the other commands too and specify them.

```
# Clear cache
   du -sh /var/cache/apt
```
doesn't actually clear anything.  It just lists the size. Incorrect comments are a maintenance nightmare.  The **/usr/bin/apt autoclean** and **/usr/bin/apt autoremove** options do the cleaning.

Is there a reason you don't just have the journald config file limit log file sizes?  Then you would need the  **/usr/bin/journalctl** command at all. Set it once and forget about it.  There are good reasons to do it in a script, but having the system automatically handle things where it can easily is usually preferred.  You might want to also address the text log files with /etc/logrotate.d/ files to ensure you limit sizes and have appropriate log rotation there too.

---

### Post by wyattwhiteeagle on 2024-09-11
> **Rubi1200 said:**
> I would be tempted to suggest that perhaps the deborphan part of your script is responsible for purging packages that you want to keep.


With your current Lubuntu 24.04 setup, deborphan might be identifying some critical or installed applications (like Bleachbit, Kolourpaint, Falkon) as orphaned due to changes in package dependencies or configurations.


One possible solution would be to whitelist packages you do not want removed.


For example, create or modify the /etc/deborphan.conf file and add these lines:
```
keep Bleachbit
keep Kolourpaint
keep Falkon

```


Note, I am not a Lubuntu user so this is kind of guesswork on my part.


Let's wait for others to add their thoughts before you make any changes.
Good catch. 1+ and thank you.


While not ignoring the very important points from others here, I'll begin with this...


The Deborphan manpage mentions the following...
> FILES
       /var/lib/deborphan/keep
              A newline-separated list of packages to keep. Package names are in  no
              particular order.


Do I put in this "keep" file only the package name as it is listed in "dpkg -l" or is it better to include all pertinent paths to everything that the app, package, program, etc uses and its dependencies?


How might I get a list of all relevant things and also those of the dependencies?

---

### Post by wyattwhiteeagle on 2024-09-11
This post wasn't actually needed.
It was something for me to put together a personal file.

Somewhere I believe there should be a "delete post" option for the person posting to delete unneeded posts.
Maybe there's the option to enable that feature in my profile...I don't know.

---

### Post by Rubi1200 on 2024-09-11
To my knowledge, you can add any program you want to keep using its common name.

For example,

```
bleachbit
falkon
python3
```

No need for the full path and also no need to put them in any particular order.

Note this was just an example, you need to add the program name as shown in the package manager.

---

### Post by Rubi1200 on 2024-09-11
> **wyattwhiteeagle said:**
> This post wasn't actually needed.
It was something for me to put together a personal file.

Somewhere I believe there should be a "delete post" option for the person posting to delete unneeded posts.
Maybe there's the option to enable that feature in my profile...I don't know.

As far as I know, this option does not exist.

Only an admin can delete posts but that means you would need to PM them.

Or I guess you could use the Report Post button at the bottom of the post and request it there.

---

### Post by wyattwhiteeagle on 2024-09-11
For now...

> **TheFu said:**
> Is there a reason you don't just have the journald config file limit log file sizes?  Then you would need the  **/usr/bin/journalctl** command at all. Set it once and forget about it.  There are good reasons to do it in a script, but having the system automatically handle things where it can easily is usually preferred.

Where would I find the journald config file?
What is it's file name?
What are the proper commands to effectively limit log file sizes?

---

### Post by TheFu on 2024-09-12
> **wyattwhiteeagle said:**
> For now...
Where would I find the journald config file?
Teaching you how to fish for yourself ....

Use **locate** to find files on your computer.  If it isn't installed, install whatever package APT says you need. The package name has changed a few times in the last 20 yrs, so I never remember it.

> **wyattwhiteeagle said:**
> What is it's file name?
Whenver I need to know the name of a config file for any process or daemon, I take a few guesses and use **locate** to find them.
For a config file for the "journald" daemon, I'd guess "journald.conf" as my first guess and I'd expect it to be somewhere under /etc/ ... if not in /etc/ itself, in a sub-sub-sub directory ... but it doesn't matter because locate would know already.  If the filename journald.conf isn't found, I'd remove the 'd' and locate on "journal.conf".  If that didn't work, I'd look in the manpages for the command line tool, journalctl in this case, and at the very bottom, there's a "See Also" section which normally would list other commands and config files related to the topic.  So, on my system, the **journalctl** manpage has this:
```
SEE ALSO
       systemd(1), systemd-journald.service(8), systemctl(1), coredumpctl(1), systemd.journal-fields(7),
       [COLOR="#FF0000"]journald.conf[/COLOR](5), systemd.time(7), systemd-journal-remote.service(8), systemd-journal-upload.service(8)
```
Which shows that my first guess (which I would have already found) also has a manpage.
```
$ man journald.conf
JOURNALD.CONF(5)                                     journald.conf                                     JOURNALD.CONF(5)

NAME
       journald.conf, journald.conf.d, journald@.conf - Journal service configuration files

SYNOPSIS
      [COLOR="#FF0000"] /etc/systemd/journald.conf[/COLOR]

       /etc/systemd/journald.conf.d/*.conf

       /run/systemd/journald.conf.d/*.conf

       /usr/lib/systemd/journald.conf.d/*.conf
....
```

> **wyattwhiteeagle said:**
> 
What are the proper commands to effectively limit log file sizes?
The are settings and documented in both comments inside the files and inside the manpages.

Next up, logrotate .... where are the config files for it? What settings can those accept?  Where are the answers to the question asked?  Hint, the answers are probably in the manpage for logrotate and the config files for logrotate.  You have 4+ methods to find the answer provided above.  BTW, logrotate config files are usually split by each log file to be managed/limited, so there should be 20+ examples of the settings for 20 different text-based log files on your system.  If you create a script/program that sends output to a log file, you can create a logrotate config file just for your custom script/program to rotate the logs from time to time based on size, age, or a few other considerations.  You can tell it to keep 2 or 200 log files and to compress them all or just the ones that aren't currently in use.  Logrotate is a mature tool. It has been around longer than I've been using Unix and it was mature when I started.

If you want a fancy GUI to read manpages, not a terminal interface, use **xman**.

Now you know how to fish for answers yourself and get them from authoritative sources, not random people (like me) on the internet.

Hope this is helpful and will help you for the next 50+ yrs, not just for 15 minutes today.

---

### Post by wyattwhiteeagle on 2024-09-12
Wow...A LOT of very useful and helpful info there.

A lot to go through and a lot to learn.

Thank you so very much.

> **TheFu said:**
> Teaching you how to fish for yourself ....

Use **locate** to find files on your computer.  If it isn't installed, install whatever package APT says you need. The package name has changed a few times in the last 20 yrs, so I never remember it.


Whenver I need to know the name of a config file for any process or daemon, I take a few guesses and use **locate** to find them.
For a config file for the "journald" daemon, I'd guess "journald.conf" as my first guess and I'd expect it to be somewhere under /etc/ ... if not in /etc/ itself, in a sub-sub-sub directory ... but it doesn't matter because locate would know already.  If the filename journald.conf isn't found, I'd remove the 'd' and locate on "journal.conf".  If that didn't work, I'd look in the manpages for the command line tool, journalctl in this case, and at the very bottom, there's a "See Also" section which normally would list other commands and config files related to the topic.  So, on my system, the **journalctl** manpage has this:
```
SEE ALSO
       systemd(1), systemd-journald.service(8), systemctl(1), coredumpctl(1), systemd.journal-fields(7),
       [COLOR=#FF0000]journald.conf[/COLOR](5), systemd.time(7), systemd-journal-remote.service(8), systemd-journal-upload.service(8)
```
Which shows that my first guess (which I would have already found) also has a manpage.
```
$ man journald.conf
JOURNALD.CONF(5)                                     journald.conf                                     JOURNALD.CONF(5)

NAME
       journald.conf, journald.conf.d, journald@.conf - Journal service configuration files

SYNOPSIS
      [COLOR=#FF0000] /etc/systemd/journald.conf[/COLOR]

       /etc/systemd/journald.conf.d/*.conf

       /run/systemd/journald.conf.d/*.conf

       /usr/lib/systemd/journald.conf.d/*.conf
....
```


The are settings and documented in both comments inside the files and inside the manpages.

Next up, logrotate .... where are the config files for it? What settings can those accept?  Where are the answers to the question asked?  Hint, the answers are probably in the manpage for logrotate and the config files for logrotate.  You have 4+ methods to find the answer provided above.  BTW, logrotate config files are usually split by each log file to be managed/limited, so there should be 20+ examples of the settings for 20 different text-based log files on your system.  If you create a script/program that sends output to a log file, you can create a logrotate config file just for your custom script/program to rotate the logs from time to time based on size, age, or a few other considerations.  You can tell it to keep 2 or 200 log files and to compress them all or just the ones that aren't currently in use.  Logrotate is a mature tool. It has been around longer than I've been using Unix and it was mature when I started.

If you want a fancy GUI to read manpages, not a terminal interface, use **xman**.

Now you know how to fish for answers yourself and get them from authoritative sources, not random people (like me) on the internet.

Hope this is helpful and will help you for the next 50+ yrs, not just for 15 minutes today.

---

### Post by wyattwhiteeagle on 2024-09-13
> **TheFu said:**
> That script makes all sorts of dangerous assumptions.
It doesn't specify the script interpeter to be used on the first line. That is non-standard.

The commands are dependent on the PATH, which can be dangerous.  Best to fully specify the exact, absolute, location for any program used in a script.  For example, "apt" should be "/usr/bin/apt". Find the full path for the other commands too and specify them.

```
# Clear cache
   du -sh /var/cache/apt
```
doesn't actually clear anything.  It just lists the size. Incorrect comments are a maintenance nightmare.  The **/usr/bin/apt autoclean** and **/usr/bin/apt autoremove** options do the cleaning.

Is there a reason you don't just have the journald config file limit log file sizes?  Then you would need the  **/usr/bin/journalctl** command at all. Set it once and forget about it.  There are good reasons to do it in a script, but having the system automatically handle things where it can easily is usually preferred.  You might want to also address the text log files with /etc/logrotate.d/ files to ensure you limit sizes and have appropriate log rotation there too.
Does this look somewhat better...I mean...at least a little bit?
Are there growing logs for each of those programs?
```
#!/bin/bash

# Wyatts-Cleanup-Script.sh

# Change permissions
# $   chmod a+x /home/wyatt/Desktop/Wyatts-Cleanup-Script.sh

# To run the script
# $   sudo /home/wyatt/Desktop/Wyatts-Cleanup-Script.sh

###########################################################

# This script does the following...

# Clear IMVU Cache
# Delete "orphaned" packages Note: DebOrphan needs to be installed before running this command.
# Replace packages mistaken as "orphaned"
# Houseclean over 10 days
# Delete old logs
# Remove packages that didn&#8217;t install completely
# Clean your apt-cache
# Clear thumbnails
# Clear cache
# Remove software dependencies that you no longer need
# Kernel and other Cleanups after Deletions
# Update & Upgrade

###########################################################

# ClearIMVU Cache
#   /usr/bin/find /home/wyatt/.wine/drive_c/users/wyatt/AppData/Roaming/IMVU/HttpCache/* -type f -delete
#   /usr/bin/find /home/wyatt/.wine/drive_c/users/wyatt/AppData/Roaming/IMVU/HttpCache/* -type d -empty -delete
#   /usr/bin/find /home/wyatt/.wine/drive_c/users/wyatt/AppData/Roaming/IMVU/PixmapCache/* -type f -delete
#   /usr/bin/find /home/wyatt/.wine/drive_c/users/wyatt/AppData/Roaming/IMVU/PixmapCache/* -type d -empty -delete
#   /usr/bin/rm /home/wyatt/.wine/drive_c/users/wyatt/AppData/Roaming/IMVU/_buddyState.pickle
#   /usr/bin/rm /home/wyatt/.wine/drive_c/users/wyatt/AppData/Roaming/IMVU/productAuth.pickle
#   /usr/bin/rm /home/wyatt/.wine/drive_c/users/wyatt/AppData/Roaming/IMVU/localstorage.pickle
#   /usr/bin/rm /home/wyatt/.wine/drive_c/users/wyatt/AppData/Roaming/IMVU/productInfoCache.db

# Delete "orphaned" packages
#   deborphan | xargs apt remove --purge -y
   /usr/bin/deborphan | /usr/bin/xargs /usr/bin/apt remove --purge -y

# Replace packages mistaken as "orphaned"
#   /usr/bin/apt install -y kolourpaint

# Houseclean over 10 days
   /usr/bin/journalctl --vacuum-time=10d

# Delete old logs
   /usr/bin/find /var/log/* -type f -name "*.gz" -delete
   /usr/bin/find /var/log/* -type f -name "*.old" -delete

# Remove packages that didn&#8217;t install completely
   /usr/bin/apt autoclean -y
   /usr/bin/apt-get autoclean -y

# Clean your apt-cache
   /usr/bin/apt clean -y
   /usr/bin/apt-get clean -y

# Clear thumbnails
#   /usr/bin/rm -rfv ~/.cache/thumbnails
   /use/bin/rm -rfv /home/wyatt/.cache/thumbnails/*

# Clear cache
#   /usr/bin/du -sh /var/cache/apt

# Remove software dependencies that you no longer need
   /usr/bin/apt autoremove -y
   /usr/bin/apt-get autoremove -y

# Kernel and other Cleanups after Deletions
   /usr/bin/apt autoremove --purge -y
   /usr/bin/apt-get autoremove --purge -y

# Update & Upgrade
#   /usr/bin/apt update
#   /usr/bin/apt upgrade -y

###########################################################
```

---

### Post by TheFu on 2024-09-13
You don't need both **apt** and **apt-get** commands.  apt says it shouldn't be used in scripts, so I'd use apt-get.  apt is meant for manual use in a terminal.

There's a technique used in scripting where we set variables to the full paths of programs, then use the variables inside the scripts. In this way, only 1 line needs to be modified if the location of a program changes.

```
APTGET=/usr/bin/apt-get

$APTGET update
```

is an example.  That's why you see things like that at the start of most sh/bash scripts. Makes maintenance easier.
I wouldn't delete any log files in this script.  I'd setup journald.conf and logrotate to better manage them.  Deleting all .gz files seems like a bad idea.

I run autoclean and autoremove AFTER I patch and wait a day to ensure there aren't issues.  I suppose running it a week after patching would be fine too.  IMHO, patching too often is a liability and leads to an unstable system, so no way would I patch daily - really once a week is all I want to patch so I get multiple days of a stable system.

I like the other changes.

---

