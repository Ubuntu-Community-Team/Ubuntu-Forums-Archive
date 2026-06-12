---
title: "Rdiff Backup Script Needs Work...Please help"
date: 2022-02-15
forum: General Help
---

### Post by wyattwhiteeagle on 2022-02-15
What am I doing wrong?
What in the script do I need to change for it to work properly?


It works but it has some issue's.


I chose TheFu's simple rdiff backup script for 18.04 (Bionic Beaver) as a learning tool for practice.
[https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432)

/media/wyatt/D05C37195C36FA34 is a usb flashdrive.

Here is my progress so far...
```
#!/bin/bash


# Ensure backups are by hostname, so multiple hosts can use the same backup storage
mkdir  -p /media/wyatt/D05C37195C36FA34/Backups/$(hostname)


# Create the list of manually installed packages - use apt-mark showmanual and store that output somewhere that gets included in the backups.  I put it into /media/wyatt/D05C37195C36FA34/Backups/
/usr/bin/apt-mark showmanual > /media/wyatt/D05C37195C36FA34/Backups/apt-mark.manual
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade


######
# Clean up garbage inside all the HOME directories before doing the backup.  No need for cache or trash files, for example.


# mount the backup disk as needed; best not to leave it mounted.
/bin/mount /media/wyatt/D05C37195C36FA34/Backups


# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \
                                            --exclude '**'    /       /media/wyatt/D05C37195C36FA34/Backups/$(hostname)


# Remove really old backup sets - say 90 days old.
/usr/bin/rdiff-backup --force --remove-older-than 90D    /media/wyatt/D05C37195C36FA34/Backups/$(hostname)


# umount the backup disk
umount /media/wyatt/D05C37195C36FA34/Backups
```


When running that script, the terminal gives the following output...
```
wyatt@wyatt-Aspire-E1-532:~$ /home/wyatt/Desktop/MyBackupScript
mount: /media/wyatt/D05C37195C36FA34/Backups: can't find in /etc/fstab.
ListError: 'etc/.pwd.lock' [Errno 13] Permission denied: b'/etc/.pwd.lock'
ListError: 'etc/NetworkManager/system-connections/WIN_201145.nmconnection' [Errno 13] Permission denied: b'/etc/NetworkManager/system-connections/WIN_201145.nmconnection'
ListError: 'etc/brlapi.key' [Errno 13] Permission denied: b'/etc/brlapi.key'
ListError: 'etc/cups/ssl' [Errno 13] Permission denied: b'/etc/cups/ssl'
ListError: 'etc/cups/subscriptions.conf' [Errno 13] Permission denied: b'/etc/cups/subscriptions.conf'
ListError: 'etc/cups/subscriptions.conf.O' [Errno 13] Permission denied: b'/etc/cups/subscriptions.conf.O'
ListError: 'etc/gshadow' [Errno 13] Permission denied: b'/etc/gshadow'
ListError: 'etc/gshadow-' [Errno 13] Permission denied: b'/etc/gshadow-'
ListError: 'etc/polkit-1/localauthority' [Errno 13] Permission denied: b'/etc/polkit-1/localauthority'
ListError: 'etc/ppp/chap-secrets' [Errno 13] Permission denied: b'/etc/ppp/chap-secrets'
ListError: 'etc/ppp/pap-secrets' [Errno 13] Permission denied: b'/etc/ppp/pap-secrets'
ListError: 'etc/security/opasswd' [Errno 13] Permission denied: b'/etc/security/opasswd'
ListError: 'etc/shadow' [Errno 13] Permission denied: b'/etc/shadow'
ListError: 'etc/shadow-' [Errno 13] Permission denied: b'/etc/shadow-'
ListError: 'etc/ssl/private' [Errno 13] Permission denied: b'/etc/ssl/private'
ListError: 'etc/sudoers' [Errno 13] Permission denied: b'/etc/sudoers'
ListError: 'etc/sudoers.d/README' [Errno 13] Permission denied: b'/etc/sudoers.d/README'
ListError: 'etc/ufw/after.init' [Errno 13] Permission denied: b'/etc/ufw/after.init'
ListError: 'etc/ufw/after.rules' [Errno 13] Permission denied: b'/etc/ufw/after.rules'
ListError: 'etc/ufw/after6.rules' [Errno 13] Permission denied: b'/etc/ufw/after6.rules'
ListError: 'etc/ufw/before.init' [Errno 13] Permission denied: b'/etc/ufw/before.init'
ListError: 'etc/ufw/before.rules' [Errno 13] Permission denied: b'/etc/ufw/before.rules'
ListError: 'etc/ufw/before6.rules' [Errno 13] Permission denied: b'/etc/ufw/before6.rules'
ListError: 'etc/ufw/user.rules' [Errno 13] Permission denied: b'/etc/ufw/user.rules'
ListError: 'etc/ufw/user6.rules' [Errno 13] Permission denied: b'/etc/ufw/user6.rules'
ListError: 'root' [Errno 13] Permission denied: b'/root'
No increments older than Wed Nov 17 11:20:11 2021 found, exiting.
umount: /media/wyatt/D05C37195C36FA34/Backups: not mounted.
wyatt@wyatt-Aspire-E1-532:~$ 
```

> mount: /media/wyatt/D05C37195C36FA34/Backups: can't find in /etc/fstab.
What does that mean and how do I correct it?


When I change permissions to / or /root, things start not working properly.
What am I doing wrong here?
The command I used is...
```
sudo chmod -R a+rwx /
sudo chmod -R a+rwx /root
```

---

### Post by coley9225 on 2022-02-15
I have used thefu's script myself. The 1 thing I see is you are not running as root. Try again with sudo and see if that helps. AFAIK, the mount and unmount are not needed for a thumbdrive, they are to prevent an accidental mistake if it is able to be accessed all the time. I backup to an external drive that is always connected and listed in fstab, not sure how to handle this with a thumbdrive. It should automount when you plug it into your computer, and trying to mount again maqy be the issue with that. Try commenting out the mount and umount lines and run it that way. Good luck.

---

### Post by deadflowr on 2022-02-15
> 
When I change permissions to / or /root, things start not working properly.
What am I doing wrong here?
The command I used is...

```
sudo chmod -R a+rwx /
sudo chmod -R a+rwx /root
```
That just broke everything.
Some files and directories require specific permissions and rights.
The changes of making everything everything breaks that and causes programs to not run.

Also 
```
# mount the backup disk as needed; best not to leave it mounted.
/bin/mount /media/wyatt/D05C37195C36FA34/Backups
```
This issue is about the fact that the mount command as written can only mount a file system listed within the fstab file.
Since you do not have an fstab entry for your backup system in fstab the command fails.

I think TheFu sets the /backups entry in fstab with the noauto option which keeps it from automatically mounting at boot,
but also allows for simple mounting whenever needed.

---

### Post by wyattwhiteeagle on 2022-02-15
> **coley9225 said:**
> I have used thefu's script myself. The 1 thing I see is you are not running as root. Try again with sudo and see if that helps. AFAIK, the mount and unmount are not needed for a thumbdrive, they are to prevent an accidental mistake if it is able to be accessed all the time. I backup to an external drive that is always connected and listed in fstab, not sure how to handle this with a thumbdrive. It should automount when you plug it into your computer, and trying to mount again maqy be the issue with that. Try commenting out the mount and umount lines and run it that way. Good luck.

Not sure if it worked, but following coley's suggestions, here is the terminal output...
```
wyatt@wyatt-Aspire-E1-532:~$ sudo /home/wyatt/Desktop/MyBackupScript
[sudo] password for wyatt: 
No increments older than Wed Nov 17 13:52:32 2021 found, exiting.
wyatt@wyatt-Aspire-E1-532:~$ 

```

---

### Post by coley9225 on 2022-02-15
Install the thumbdrive and open in file manager, and see if anything is there. If everything shows up, your in good shape, if not, the script needs more work than my limited abilities can help with.

---

### Post by wyattwhiteeagle on 2022-02-15
I've reserved the flashdrive for my backups.
I don't plan to leave the flashdrive plugged in.

What recursive line needs to be in the script to enter my password when it asks for it?

How would I have the script clean out "garbage" before doing the backup?

Is there a way to have the script create and maintain a changelog?

> **deadflowr said:**
> [QUOTE=wyattwhiteeagle;14081402]
When I change permissions to / or /root, things start not working properly.
What am I doing wrong here?
The command I used is...
```
sudo chmod -R a+rwx /
sudo chmod -R a+rwx /root
```
That just broke everything.
Some files and directories require specific permissions and rights.
The changes of making everything everything breaks that and causes programs to not run.[/QUOTE]

Yeah...after I did a fresh reinstall...I didn't change any permission's.
I made a note to change the script...not the permissions.

> Also
```
# mount the backup disk as needed; best not to leave it mounted.
/bin/mount /media/wyatt/D05C37195C36FA34/Backups
```
This issue is about the fact that the mount command as written can only mount a file system listed within the fstab file.
Since you do not have an fstab entry for your backup system in fstab the command fails.

I figured that.
I took out the mount and umount lines.

> I think TheFu sets the /backups entry in fstab with the noauto option which keeps it from automatically mounting at boot,
but also allows for simple mounting whenever needed.

I believe I need to keep a copy with the mount and umount lines...just in case.

---

### Post by kevdog on 2022-02-16
You have to run the script as root or as the sudo uses.  You need to make sure your mount command is correct.

---

### Post by wyattwhiteeagle on 2022-02-16
> **kevdog said:**
> ...You need to make sure your mount command is correct.

Ok, can you instruct on how to do that?

The current script doesn't include the mount and umount commands, but they are...
> # mount the backup disk as needed; best not to leave it mounted.
/bin/mount /media/wyatt/D05C37195C36FA34/Backups

...

# umount the backup disk
umount /media/wyatt/D05C37195C36FA34/Backups

Though I believe coley and deadflowr touched on that.

The current script:

```
#!/bin/bash

# Ensure backups are by hostname, so multiple hosts can use the same backup storage
mkdir  -p /media/wyatt/D05C37195C36FA34/Backups/$(hostname)

# Create the list of manually installed packages - use apt-mark showmanual and store that output somewhere that gets included in the backups.  I put it into /media/wyatt/D05C37195C36FA34/Backups/
/usr/bin/apt-mark showmanual > /media/wyatt/D05C37195C36FA34/Backups/apt-mark.manual
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

######
# Clean up garbage inside all the HOME directories before doing the backup.  No need for cache or trash files, for example.

# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \
                                            --exclude '**'    /       /media/wyatt/D05C37195C36FA34/Backups/$(hostname)

# Remove really old backup sets - say 90 days old.
/usr/bin/rdiff-backup --force --remove-older-than 90D    /media/wyatt/D05C37195C36FA34/Backups/$(hostname)
```

---

### Post by TheFu on 2022-02-16
@coley9225 is correct. Backup scripts need to run as root. Mine all run from root's contrab. I don't run them interactively. You shouldn't be entering any password.

I'd add a TGT variable to the top, since it seems some of your stuff is inconsistent.
```
TGT="/media/wyatt/D05C37195C36FA34/Backups"
```
Then replace all references to that inside the script. This way, when you decide that backups don't belong under /media/ (and I think they DO NOT), then only 1 line will need modifying.  
Plus, I doubt you really want the apt-mark.manual file where it is in the script currently.  Things mounted automatically by some GUI tool often (usually) don't have the best performing, options.  However, ext4 seems to get mounted fine, regardless, so if other file systems are used, that's really where my warning goes.

@deadflowr is correct about my fstab for that partition. noauto. Well, actually, I use a client/server architecture for my backups, but on the backup server, the backup storage isn't normally mounted. This is an important security decision.

A flash drive really makes a not-so-great backup storage device, just because of limited writes. If it was me, I'd get a $40 USB3 external HDD, partition it with ext4 (lacking any good reason to choose some other file system) and use that for backups.

To clean garbage is completely dependent on which programs you run. Each has different places for junk files.  A start would be to remove the trash for the DE you run. There are CLI tools for this, if you use a file manager. I do not use file managers, so I don't have trash directories.  I do wipe the Firefox cache area and that for thunderbird for each userid.  Basically, just delete the files you don't need anymore.  Or you can use --exclude options.  I do that too. Some examples:
```
**--exclude-special-files**
--exclude **/.gvfs
--exclude **/.local/share/Trash
--exclude **/.cpan
--exclude **/.cache
--exclude **/.cache2
--exclude **/.mozilla/firefox/*/chrome/sagetoo
--exclude **/.mozilla/firefox/*/sessionstore
--exclude **/.mozilla/firefox/*/Cache
--exclude **/.adobe
```
I use a '**heredoc**' for these and have a little merge_lines function so they get put onto a single line in the command. My script is actually perl, not bash, so it doesn't posting it doesn't help. Bash and perl are too different.  Knowing how to use *heredocs* is a basic scripting skill for all languages. Very useful. Google it.

Changelog? rdiff-backup does that. Learn to use the command and look at the files it creates for each backup set.  Every morning, I get an email with a summary of the backups for every system - start time, end time, and how many bytes were transferred. For example:

```
=== Time for Backups to wallabag ===
StartTime 1644991295.00 (Wed Feb 16 01:01:35 2022)
EndTime 1644991300.47 (Wed Feb 16 01:01:40 2022)
ElapsedTime 5.47 (5.47 seconds)
TotalDestinationSizeChange 1019 (1019 bytes)

=== Time for Backups to vpn ===
StartTime 1644991304.00 (Wed Feb 16 01:01:44 2022)
EndTime 1644991304.52 (Wed Feb 16 01:01:44 2022)
ElapsedTime 0.52 (0.52 seconds)
TotalDestinationSizeChange 953 (953 bytes)

=== Time for Backups to hadar ===
StartTime 1644991310.00 (Wed Feb 16 01:01:50 2022)
EndTime 1644991332.52 (Wed Feb 16 01:02:12 2022)
ElapsedTime 22.52 (22.52 seconds)
TotalDestinationSizeChange 5541259 (5.28 MB)
```

Those are just an egrep command for lines that ... heck ... here's the command:
```
for D in $SRVS ; do
nice egrep 'TotalDestinationSizeChange|StartTime|EndTime|ElapsedTime' \
          $SOURCE_DIR/$D/rdiff-backup-data/session_statistics.$TODAY*.data
done
```

You can fill in the variables.

Weekly, I ask rdiff-backup to generate reports for how much storage is used by each host.  *--list-increment-sizes* is the option. It takes a while to run, so it is also a crontab script ... that runs on Sunday mornings, early.  Waiting for me to see the output.  I keep a few months of those reports for each backed up system. Old versions are removed by the same script.  The 'find' command makes that trivial. For example, 
TODAY=(/bin/date "+%F")
Clearly, backups cannot start until after midnight, so 'today' will be 'today' when this report egrep runs.  It runs after all the server backups are run, without delay, before the backup storage gets umount'ed.

The point of my script postings were to keep it simple for beginners, so they could get some backups going relatively easy.  The real backup script(s) that I use are about 20 interdependent files with significant setup required to have a remote backup userid that can support the 'pull' backup model. This requires a little ssh knowledge and some knowledge about how userids really work. Not any secrets, but I've never seen any book do anything similar.  The simple script initially provided was something I slapped together in a few minutes, referencing some other scripts, and then tested quickly on a system with very little data. Think the initial run was 20 seconds.

---

### Post by erind on 2022-02-16
One way to run your script as root is to enter the following line at the top of the script and adding this script into the SUDOERS file:

```
#!/bin/bash

[COLOR=#0000ff][ $(whoami) = root ] || exec sudo $0[/COLOR]

# Ensure backups are by hostname, so multiple hosts can use the same backup storage
mkdir  -p /media/wyatt/D05C37195C36FA34/Backups/$(hostname)

## The rest of the code goes below ...
```

---

### Post by TheFu on 2022-02-16
@erind, while checking against 'root' can work, it doesn't work always.  Best to **always** compare the uid, not the username.
root (and root-equiv accounts) will have a uid of 0.  Comparisons of integers are are better than string comparisons too. Many, many, fewer failure modes.

Plus, backups really need to be 100% automatic. Best to fail from the crontab ASAP, so steps can be taken to correct the issue.

$(/usr/bin/id -u) returns the integer uid.  Never trust the PATH in any script, unless you set it yourself OR fully specify the absolute path to each command. Trusting the PATH is one technique that crackers use to take over systems. Best to never learn the habit.

---

### Post by wyattwhiteeagle on 2022-02-16
Ok, I modified the script a bit.
How does it look...

The script
```
#!/bin/bash

# Clean up garbage inside all the HOME directories before doing the backup.  No need for cache or trash files, for example.

#Remove packages that didn&#8217;t install completely
apt autoclean -y

#Remove software dependencies that you don&#8217;t need
apt autoremove -y

#Clean your apt-cache
apt-get clean -y

#clear thumbnails
rm -rfv ~/.cache/thumbnails

#clear cache
du -sh /var/cache/apt

#Kernel and other Cleanups after Deletions
apt autoremove --purge -y

#update
apt update -y

#Full-upgrade
apt full-upgrade -y

# Ensure backups are by hostname, so multiple hosts can use the same backup storage
mkdir  -p TGT="/media/wyatt/D05C37195C36FA34/Backups/$(hostname)/Date=$(/bin/date +%Y-%m-%d-%b-%s)"

# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \
                                            --exclude '**'    /       TGT="/media/wyatt/D05C37195C36FA34/Backups/$(hostname)/Date=$(/bin/date +%Y-%m-%d-%b-%s)"
--exclude **/.gvfs
--exclude **/.local/share/Trash
--exclude **/.cpan
--exclude **/.cache
--exclude **/.cache2
--exclude **/.mozilla/firefox/*/chrome/sagetoo
--exclude **/.mozilla/firefox/*/sessionstore
--exclude **/.mozilla/firefox/*/Cache
--exclude **/.adobe

# Remove really old backup sets - say 90 days old.
/usr/bin/rdiff-backup --force --remove-older-than 90D    TGT="/media/wyatt/D05C37195C36FA34/Backups/$(hostname)/Date=$(/bin/date +%Y-%m-%d-%b-%s)"

# Create the list of manually installed packages - use apt-mark showmanual and store that output somewhere that gets included in the backups.  I put it into TGT="/media/wyatt/D05C37195C36FA34/Backups/$(hostname)/Date=$(/bin/date +%Y-%m-%d-%b-%s)"
/usr/bin/apt-mark showmanual > TGT="/media/wyatt/D05C37195C36FA34/Backups/$(hostname)/Date=$(/bin/date +%Y-%m-%d-%b-%s)"
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

######
```

---

### Post by TheFu on 2022-02-16
It won't work - or it shouldn't work as written. The TGT use isn't correct and the --exclude options cannot be used as I provided them, they need to be merged into a single line AND they need to be placed in the correct order in the rdiff-backup command.  At the end breaks rdiff-backup. Order of arguments matters.

A beginning bash scripting tutorial will clear up some of these things. Here's how it works:
```
TGT="/media/wyatt/D05C37195C36FA34/Backups/$(hostname)"
mkdir  -p "$TGT"
```

From that point on, "$TGT" can be use as a replacement for that long directory path, in this script/processes. This is how environment variables work. Nothing special.  At a bash prompt, type 'env' to see the already set environment variables in your login session.  That list changes based on the type of login, if you are local or remote, and which GUI is being used.  We have complete control over these things.

Also, I'd strongly (_***extremely strongly***_) recommend _***AGAINST***_ putting any package management commands into a script that gets run daily.  There are so many things that can go wrong with APT, and unfortunately, things often do go wrong.  Running those types of commands more than once a week is asking for trouble, IME.  I've been burned a few times, as have many others by updating too quickly and too often.

---

### Post by wyattwhiteeagle on 2022-02-17
> **TheFu said:**
> It won't work - or it shouldn't work as written. The TGT use isn't correct and the --exclude options cannot be used as I provided them, they need to be merged into a single line AND they need to be placed in the correct order in the rdiff-backup command.  At the end breaks rdiff-backup. Order of arguments matters.

A beginning bash scripting tutorial will clear up some of these things. Here's how it works:
```
TGT="/media/wyatt/D05C37195C36FA34/Backups/$(hostname)"
mkdir  -p "$TGT"
```

From that point on, "$TGT" can be use as a replacement for that long directory path, in this script/processes. This is how environment variables work. Nothing special.  At a bash prompt, type 'env' to see the already set environment variables in your login session.  That list changes based on the type of login, if you are local or remote, and which GUI is being used.  We have complete control over these things.

Also, I'd strongly (_***extremely strongly***_) recommend _***AGAINST***_ putting any package management commands into a script that gets run daily.  There are so many things that can go wrong with APT, and unfortunately, things often do go wrong.  Running those types of commands more than once a week is asking for trouble, IME.  I've been burned a few times, as have many others by updating too quickly and too often.

Just to let you know, I'm not using the GUI version of rdiff-backup.
Please don't assume that I am.

What is needed for the --exclude options to be merged into a single line in the correct order?

About the TGT, you mean like this?

The Script
```
#!/bin/bash

# Clean up garbage inside all the HOME directories before doing the backup.  No need for cache or trash files, for example.

# Ensure backups are by hostname, so multiple hosts can use the same backup storage
TGT="/media/wyatt/D05C37195C36FA34/Backups/$(hostname)/Date=$(/bin/date +%Y-%m-%d-%b-%s)"
mkdir  -p "$TGT"

# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \
                                            --exclude '**'    /       /media/wyatt/D05C37195C36FA34/Backups/$(hostname)

# Create the list of manually installed packages - use apt-mark showmanual and store that output somewhere that gets included in the backups.  I put it into "$TGT"
/usr/bin/apt-mark showmanual > "$TGT"
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

######

# Remove really old backup sets - say 90 days old.
/usr/bin/rdiff-backup --force --remove-older-than 90D    "$TGT"

```

---

### Post by TheFu on 2022-02-17
> **wyattwhiteeagle said:**
> Just to let you know, I'm not using the GUI version of rdiff-backup.
Please don't assume that I am.

What is needed for the --exclude options to be merged into a single line in the correct order?

About the TGT, you mean like this?


I didn't see any mention of GUI.  Didn't know that there was a GUI for rdiff-backup. Is there?

rdiff-backup has a how-to guide. It is called a manpage on Unix-like systems. It should be on your computer already, waiting to be read.  In there are details about the command, options, and caveats.  It spells out the order of options and what the order means.  You should read and understand that to ensure you achieve the desired results.

As for using $TGT ... I think you missed a spot.  Also, it really should be "$TGT", so that any paths with odd characters get handled correctly.  This is normal bash scripting and how quoting works.  You can read up on that in any bash scripting guide.  There's nothing special about TGT. I just didn't feel like spelling out TARGET.  I follow a nomenclature that is a little old - I use CAPS for local variable names. The new kids do it different. Nothing special at all with the name I picked, other than I wanted to ensure it doesn't conflict with other programs or built-in bash commands.

---

### Post by dragonfly41 on 2022-02-17
There is this GUI which I found in studying rdiff-backup

[https://www.debianhelp.co.uk/rdiffbackupgui.htm](https://www.debianhelp.co.uk/rdiffbackupgui.htm)

I am following this current thread with interest, And other threads referring to rdiff-backup.

So far I have not used rdiff-backup mainly because I adopted a rather daft convention to 
rename project folders to change their pecking order. Just as TheFu uses a convention to use CAPS for local variable names, I used a folder naming convention like _PROJECTNAME

Of course any dabbling with folder and file names will screw up rdiff-backup so I am first renaming folders to return them  to a reasonable order. This is proving more difficult than it seems to reverse since folder paths are embedded in "recently used files" menus in applications. The die has been cast.

Then I will use a self built GUI just to hold the rules for applying rdiff-backup scripts.

I fall into the camp of not being able to remember many commands, particularly if we look at the multitude of cli commands in applications and cloud services. I think that there is room for a middle of the road approach between raw commands and GUI's.

---

### Post by TheFu on 2022-02-17
That link for a GUI to rdiff-backup is bad. Doesn't go anywhere and quick attempts to guess the correct URL failed.
GUIs tend to be 20% solutions, missing 80% of the tool's capabilities.
GUIs are very hard to automate. CLI commands work easily in cron.  I probably have 150 different crontab tasks running at least once a day to deal with things automatically, so I don't have to point-n-click 10 times for each one.
I only need to solve the command options issue once, put it in a script (I have thousands of scripts) and then forget it. The script is my record.

All backup tools will have the same issue if filenames and directory names are changed. Not rdiff-backup specific. It is how they all work - all-of-them.  I ignore 'recently used' stuff in the GUIs. Find it nearly useless. Either a file/directory has been processed or it hasn't.  I do change aliases to be able to quickly access different projects as those bubble to the most-important status.  I also tweak my cdpath variable to make getting around fast.

>  Then I will use a self built GUI just to hold the rules for applying rdiff-backup scripts.
You've lost me.  Put the script call in a crontab to run as you like and be done with it.  BTW, may want to backup all the crontabs on a system for every account too. I do in my real backup scripts - this is part of my pre-backup, daily, information gathering commands.

I don't remember all the options for every command either. Between having my scripts with plenty of examples, commented in a way that I can find later (grep the files), most already-solved patterns are easily solved again. IF not, every system has the manpages right there to explain how a command works.  Learn to use the **apropos** command to find which command to use.  Read through all the programs in /bin/ and /usr/bin/ once - what do you think each does? It requires active-learning in the exercise.  If you don't know that a command exists, you'll never think to use it.  We want our toolboxes full of options, not just 1 hammer and no nails. ;)

I don't use cloudy services hosted outside my LAN, so none of that matters. The closest I come to that is a nextcloud instance on the LAN which is mainly used to provide file access to phones and tablets, not much else.  It keeps shopping lists, todo lists, and assorted text notes.  Last month, I setup a sync for 1 file into nextcloud using DAVFS. What a pain. DAV sucks and has been known to have far too many security failures. Alas, there isn't a better method that I know to push my password db to a place that will automatically sync on Android, at least not in my environment.

---

### Post by wyattwhiteeagle on 2022-02-17
> **TheFu said:**
> rdiff-backup has a how-to guide. It is called a manpage on Unix-like systems. It should be on your computer already, waiting to be read.  In there are details about the command, options, and caveats.  It spells out the order of options and what the order means.  You should read and understand that to ensure you achieve the desired results.

```
wyatt@wyatt-Aspire-E1-532:~$ manpage
manpage: command not found
wyatt@wyatt-Aspire-E1-532:~$ rdiff-backup manpage
Fatal Error: Switches missing or wrong number of arguments
See the rdiff-backup manual page for more information.
wyatt@wyatt-Aspire-E1-532:~$ rdiff=backup manual
manual: command not found
wyatt@wyatt-Aspire-E1-532:~$ 

```

If it is INDEED on my computer already.
How do I read it?

---

### Post by deadflowr on 2022-02-17
manpages go by the command ```
man <command-name> 
```
replace <command-name> with the command or name of program.
and man has it's own man page see
```
man man
```

---

### Post by wyattwhiteeagle on 2022-02-17
> **dragonfly41 said:**
> There is this GUI which I found in studying rdiff-backup

[https://www.debianhelp.co.uk/rdiffbackupgui.htm](https://www.debianhelp.co.uk/rdiffbackupgui.htm)

I am following this current thread with interest, And other threads referring to rdiff-backup.

So far I have not used rdiff-backup mainly because I adopted a rather daft convention to 
rename project folders to change their pecking order. Just as TheFu uses a convention to use CAPS for local variable names, I used a folder naming convention like _PROJECTNAME

Of course any dabbling with folder and file names will screw up rdiff-backup so I am first renaming folders to return them  to a reasonable order. This is proving more difficult than it seems to reverse since folder paths are embedded in "recently used files" menus in applications. The die has been cast.

Then I will use a self built GUI just to hold the rules for applying rdiff-backup scripts.

I fall into the camp of not being able to remember many commands, particularly if we look at the multitude of cli commands in applications and cloud services. I think that there is room for a middle of the road approach between raw commands and GUI's.

rdiff-backup doesn't have a GUI.
That url is misleading.
It leads to everything rdiff-backup but never presents a GUI version.
So the user who follows that link is never going to find a rdiff-backup GUI, because it doesn't exist.
If it ever existed, it has discontinued or it's still only an idea.

---

### Post by wyattwhiteeagle on 2022-02-17
> **deadflowr said:**
> manpages go by the command ```
man <command-name> 
```
replace <command-name> with the command or name of program.
and man has it's own man page see
```
man man
```

o ok...wow, my brain forgets things sometimes

@TheFu...the manual mentions target, but nothing about "$TGT".
It never mentions anything about caveats.
Must be terminology only in perl tutorials and guides.

There's an online version...(didn't know it was an online version until I seen in the terminal)
[https://rdiff-backup.net/docs/rdiff-backup.1.html](https://rdiff-backup.net/docs/rdiff-backup.1.html)

It seems to aim for confusing the reader instead of actually helping the reader understand.

One part I read...under the --include and --exclude...gives the idea that --include can be used instead of --exclude and whatever is specified to include will be excluded.

See...

> For instance,

rdiff-backup --include /usr --exclude /usr /usr /backup

is exactly the same as

rdiff-backup /usr /backup

because the include and exclude directives match exactly the same
files, and the **--include** comes first, giving it precedence.

So...let's compare that to the script.
```
[FONT=Verdana]/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \[/FONT]
```
The script has a line that says "--exclude" and on the same line it has "--include" 3 times.
Makes me wonder if it is actually excluding that which is specified to include due to --exclude's precedence.
If I turn it around where the includes are before the exclude, here again...precedence.

Don't worry...that's not what's happening.
That script line is ok.
It's the manual that leaves the user confused.

That info seems more confusing to me than helpful.
And the manual doesn't seem to clear my confusion.

If that manual is more of a "do you believe everything you read" joke...then it's an aweful bad joke, because now I'm more confused than before I read the manual.

Will somebody please "dummy-it-down" for me?

---

### Post by Quarkrad on 2022-02-18
A basic principle that many on this forum use (following advice from TheFu) when using rdiff-backup is to *exclude* everything and then *include* what you want to backup.  So ... logically, it makes sense that you can have a number of *--include .... *items on a line following an *--exclude.....*

---

### Post by wyattwhiteeagle on 2022-02-18
> **Quarkrad said:**
> A basic principle that many on this forum use (following advice from TheFu) when using rdiff-backup is to *exclude* everything and then *include* what you want to backup.  So ... logically, it makes sense that you can have a number of *--include .... *items on a line following an *--exclude.....*

Right now, my backups are 3gb each.
TheFu says hook an external HDD or SSD, format it to ext4 and use that.

I tried that.
Anything externally connected to my laptop gets put on /media.
TheFu advises against doing backup on anything /media
It can be a security risk if left plugged in, which I unplug usb connections when not in use.

A flashdrive...2 or 3 things matter...size, write-limits, and how many days to keep.
My largest is 128gb with 119 usable, and the internal is an 80gb and it's already half full...TheFu advises to keep 90days worth.

90days of 3gb each...that takes up 270gb and thats not including the apt-mark.manual.

So I gotta exclude things fast...not people tell me..."here, read this manual and read that guide and maybe I might learn something if I'm lucky"
I just need something now...not after everything fills up to not usable.

One folder that is being included (but everyone is saying exclude it while not telling how to exclude it but sending the user on a bookworm trip) is /home/.cache

"Take care of things now...then go read"

When I specify --exclude or --include following the exact way TheFu wrote that script...
I get the "command not found"

Maybe I should put it in the script like this...

```
rdiff-backup --exclude
``` or ```
rdiff-backup --include
```

---

### Post by Quarkrad on 2022-02-18
I am far far from an expert on rdiff-backup and got most of my advice/info from @TheFu and others on this forum.  Although probably not the most efficient script this is what currently works for me:

```
sudo /usr/bin/rdiff-backup  --verbosity 5 --exclude-special-files \
           --include-globbing-filelist '/usr/bin/includelist.txt' --include /root --include /etc --include /usr/local --include /usr/bin --exclude / --exclude /media \
           --exclude **/.local/share/Trash --exclude **/.cache \
           --exclude **/Cache \
            / /media/dad/backup/rdiffbackup
```

Most of the *personal* things I want backed up is list in my includelist.txt file.  The --verbosity 5 bit allows me to see what is happening in a terminal when rdiff-backup is running - not necessary, but it gives me satisfaction seeing everything happening as it should.  (I run this backup when I shutdown my machine).  I have videos files that are also backed up but I only occasionally do video work - my methodology is to use rdiff-backup for my day-to-day backup and the use rsync for my occasional video work whenever I make file changes.

---

### Post by wyattwhiteeagle on 2022-02-18
> **Quarkrad said:**
> I am far far from an expert on rdiff-backup and got most of my advice/info from @TheFu and others on this forum. Although probably not the most efficient script this is what currently works for me:


Most of the personal things I want backed up is list in my includelist.txt file. The --verbosity 5 bit allows me to see what is happening in a terminal when rdiff-backup is running - not necessary, but it gives me satisfaction seeing everything happening as it should. (I run this backup when I shutdown my machine). I have videos files that are also backed up but I only occasionally do video work - my methodology is to use rdiff-backup for my day-to-day backup and the use rsync for my occasional video work whenever I make file changes.


Your's looks more efficient than mine does.
Did you manually create the includelist.txt?


Your script...
```
sudo /usr/bin/rdiff-backup  --verbosity 5 --exclude-special-files \
           --include /root --include /etc --include /usr/local --include /usr/bin --exclude / --exclude /media \
           --exclude **/.local/share/Trash --exclude **/.cache \
           --exclude **/Cache \
            / /media/dad/backup/rdiffbackup            
```


My script...
```
# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \
                                            --exclude '**'    /       /media/wyatt/d98d1629-adb3-421e-a72a-381bb40b03ce/Backups/$(hostname)
           --exclude **/.gvfs
           --exclude **/.local/share/Trash
           --exclude **/.cpan
           --exclude **/.cache
           --exclude **/.cache2
           --exclude **/.mozilla/firefox/*/chrome/sagetoo
           --exclude **/.mozilla/firefox/*/sessionstore
           --exclude **/.mozilla/firefox/*/Cache
           --exclude **/.adobe
```


Yours looks quite a bit different than mine.
I'm noticing some keystrokes in your's than mine doesn't have.
I will make some changes to mine and post the results.


Thank you so very much.

---

### Post by ActionParsnip on 2022-02-18
I'm surprised the system even functions after the earlier chmod command.......

---

### Post by TheFu on 2022-02-18
Life got in the way and will continue to around here for the few days or so, but I wanted to chime in ...

90 days won't take 90x the storage.  That isn't how 95% of Unix backups work.  These aren't images.  Only changed data/blocks create space.  Typically, for my systems, a 10G source area will use 13G with 90 days of daily, rdiff-backup, sets.

man pages have a method to their madness. You should use the one on your system, since that matches the version of the command there.  Man pages found on the web can be for any version, likely not the one you have. Sometimes it matters. Sometimes it doesn't.  After you get burned, you'll stop using the web for manpages.

The manpage has this summary at the top:
```
       rdiff-backup      [options]      [[[user@]host1.foo]::source_directory]    [[[user@]host2.foo]::destination_directory]
```
What that says is  there are 4 parts to a backup command, 3 are [optional].  But really, for any backup, all 4 are required.
[LIST]
[*]rdiff-backup - the program
[*]options - that's everything that isn't one of the last 2 inputs.
[*]source
[*]destination
[/LIST]
I've never seen an rdiff-backup work without a source and destination. Those 2 things MUST be the last 2 arguments of the command. Nothing is allowed after the destination.  Look at your proposed command... all those --exclude lines .... they are just dangling. They aren't magically part of the rdiff-backup command. They will cause command-not-found errors, or something like that.  Those are all part of the "options", but in the wrong place for the command.  Fix it.

Order matters for include/exclude options.
I've never used a specific file include list.  That's just too much work. My script excludes everything, then specifically includes directories I want backed up, then add in specific exclusions for areas that I don't want included.  That's in my head, but the order in the script I'd have to look up.  As I said far above (now), the list of exclusions needs to be in a single line before it gets sent to rdiff-backup.  My script does that, but for long-term maintenance, it is much easier to have every exclude on a separate line, IMHO, then my script merges them as require for a fork-exec.  You do it however you like, but I suspect this is all above your current ability, so you should just put them all on 1 line, placed inside the rdiff-backup command.

As I said before TGT isn't anything special. It is a made-up variable.  Programmers do that. You can call it almost anything you want. I don't care. I'm almost sorry that I posted my "simple" script.  There is a link above from @wyattwhiteeagle to a simple bash scripting webpage. See the section on _variables_.  Variable substitution is basic bash.  I'd be surprised if it wasn't covered on day 1, right after print/echo and what a 4-function calculator can do. Don't make it hard.  Basically, TGT is shorter than /some/really/long/path/that/will/change/from/time/to time/but/is/used/in/5/places/in/the/script/ ... so I put it into a variable and dereference it as "$TGT".  That's it.

I don't like /media/ because is it controlled by processes that I don't control and does whatever it wants. Over the decades, the location as moved where temporary mounts were located.  The standards are very clear.  Gnome and Canonical are breaking standards by using that location. Feel free to ignore me and may you never be burned by using those locations.  I'm not against automatic mounts, when I have control over where they do, when the mount happens, all the mount options, and when they are released.  /media/ breaks all of those things.

If the added things are too much, don't use them.  This is your backup script. We don't have to live with it. You do.  At recovery time, nobody here will be typing the recovery commands. You will.  Things that have have too much "magic", are bad at restore time.

---

### Post by dragonfly41 on 2022-02-19
Here follows my rather rambling notes I have taken as I study rdiff-backup..

First I am sorry for posting the earlier broken link to the GUI. But it is real as I found in the rdiff-backup mail list (see below). But I am not proposing to use it. Instead I will develop my own.

I have followed the excellent advice of @TheFu and others in this and other related threads (use advance search this forum .. rdiff-backup),

I learn more about the risks (cited by @TheFu) of mounting local backup devices on /media.

[https://unix.stackexchange.com/questions/176790/what-is-the-distinction-between-media-mnt-and-run-mount](https://unix.stackexchange.com/questions/176790/what-is-the-distinction-between-media-mnt-and-run-mount)

[https://www.linuxbase.org/betaspecs/fhs/fhs.html#mediaMountPoint](https://www.linuxbase.org/betaspecs/fhs/fhs.html#mediaMountPoint)

I have studied discussions in the [rdiff-backup mail list.]("https://www.mail-archive.com/rdiff-backup-users@nongnu.org/")

Finally I decide that I now need to join this rdiff-backup club and start writing my own GUI based on my learning. 
 But I intend to use it first as an experiment to try all the methods I read about. It is a background development task.

The experimental GUI has these goals:


[LIST]
[*]to define all configurations and options in a single file
[*]to compose and validate rdiff-backup scripts and cronjobs
[*]to develop a &#8220;hello world&#8221; tutorial or workflow for safely trying combinations of the published methods
[*]to save scripts and cronjobs in a database
[/LIST]

It is a very valid point raised by @TheFu to refer to &#8220;man rdiff-backup&#8221; for documentation since this refers to the installed version of rdiff-backup. Web sites can be out of sync in descriptions.

I use LifeRea and I have added the RSS subscription.

[https://www.mail-archive.com/rdiff-backup-users@nongnu.org/maillist.xml](https://www.mail-archive.com/rdiff-backup-users@nongnu.org/maillist.xml)


This latest message popped up ..

pip install rdiff-backup==2.1.1a0

[https://www.mail-archive.com/rdiff-backup-users@nongnu.org/msg07306.html](https://www.mail-archive.com/rdiff-backup-users@nongnu.org/msg07306.html)[INDENT]&#8220;The installation procedure hasn't changed much and is available from the readme <[https://github.com/rdiff-backup/rdiff-backup/blob/v2.1.1a0/README.adoc](https://github.com/rdiff-backup/rdiff-backup/blob/v2.1.1a0/README.adoc)> (alpha packages might or might not be offered by the maintainers, in doubt install via |pip install rdiff-backup==2.1.1a0| under Linux and use the attached binaries under Windows). You might want to use the side-by-side installation <[https://github.com/rdiff-backup/rdiff-backup/blob/v2.1.1a0/docs/migration.adoc#side-by-side-installation](https://github.com/rdiff-backup/rdiff-backup/blob/v2.1.1a0/docs/migration.adoc#side-by-side-installation)> to safeguard your productive installation.&#8221;[/INDENT]

Nevertheless I decide thar I will try two versions of rdiff-backup (current version is 2.0).

pip3 install rdiff-backup==2.1.1a0


**Migration and Side-by-Side installation**


[https://github.com/rdiff-backup/rdiff-backup/blob/v2.1.1a0/docs/migration.adoc#side-by-side-installation](https://github.com/rdiff-backup/rdiff-backup/blob/v2.1.1a0/docs/migration.adoc#side-by-side-installation)


and ..

[https://github.com/rdiff-backup/rdiff-backup/issues](https://github.com/rdiff-backup/rdiff-backup/issues)

This refers to rdiff-backup in Python

[https://github.com/rdiff-backup/rdiff-backup/issues/602](https://github.com/rdiff-backup/rdiff-backup/issues/602)


**Mail list discussions**

This discussion thread addresses: &#8220;Why are you using rdiff-backup&#8221;

[https://www.mail-archive.com/rdiff-backup-users@nongnu.org/msg07126.html](https://www.mail-archive.com/rdiff-backup-users@nongnu.org/msg07126.html)


This user explains how rdiff-backup met the requirements of auditors.

[https://www.mail-archive.com/rdiff-backup-users@nongnu.org/msg07138.html](https://www.mail-archive.com/rdiff-backup-users@nongnu.org/msg07138.html)[INDENT]"It has saved us several times. An example: auditors asked us to show the background data for a report generated eight months earlier and when we tried to do this using our current financial database (but 'as at' the original date) it came out different and we could not explain why (some backdated changes/deletions I guess). I was able to use rdiff-backup to recover the database from the time when the report was run (say 240 backup runs previously) and thus provide the required explanation to auditors."[/INDENT]

Now that is a good business case.

Now in this current discussion in post #23 @wyattwhiteeagle raises a practical point where the target device might be small in size.

I not yet read about any option or method which considers whether there is space in target to receive a backup.  This supports the argument for a dry run mode such as rsync offers.


However this &#8220;dry run&#8221; idea raised by another user  is orphaned,

[https://www.mail-archive.com/rdiff-backup-users@nongnu.org/msg07010.html](https://www.mail-archive.com/rdiff-backup-users@nongnu.org/msg07010.html)


**Encrypted Backups**

One point I have is that for the project I an developing I intend to keep backups both local and in the cloud through a zero knowledge service such as tresorit.  I have to work out how this might work. I need to research how to backup diffs through a zero knowledge service.  I consider this since I understand the need to hold several backups on geographically separate locations to guard against disaster cases. And if a backup target is in the cloud it must be encrypted using end to end encryption.


[End of ramble).

---

### Post by Quarkrad on 2022-02-19
Ref: #25 - and sorry it's taken so long to get back.  Yes, I did manually create the includelist.txt.  I got into a mess with the order and syntax of some of the *options* (re what I want to do specifically) in various posts within this forum and after a long while decided, at my stage of understanding, it was easier to create an includelsit that I could change over time as I refined exactly what I need.  I created a file called *includelist.txt* and put it in */usr/bin/* - the contents of this file is:

```
/home/dad/Desktop/*
/home/dad/Documents/*
/home/dad/Downloads/*
/home/dad/dvd/*
/home/dad/Music/*
/home/dad/Pictures/*
/home/dad/plex/*
/home/dad/Public/*
/home/dad/Templates/*
/home/dad/Videos/*
/home/dad/.aMule/*
/home/dad/.audacity-data/*
/home/dad/.cert/*
/home/dad/.config/*
/home/dad/.googleearth/*
/home/dad/.local/*
/home/dad/.thunderbird/ifmp8iai.default-release/Mail/*
/home/dad/.xine/*
```

This is almost certainly not the most efficient method/list but as said, I'm still changing.   I learn new things in every rdiff-backup post on this site - for this one I need to get my head around not using */media/ *for the backup destination and change mine!

---

### Post by TheFu on 2022-02-19
I'd ask this.  What's the difference between ~/ and that huge list of includefiles?  What happens if you forget something important under a HOME?  What about other users?

I'm a little concerned that ~/.ssh/ isn't in the include list. To me, that is, by far, the most important thing to be included - perhaps ~/.gpg/ too. Just depends on how you use the system, I suppose.  Do people here really not use ssh or gpg, daily - 50x a day?

Using /media/ isn't the end of the world, especially if you **mount** and **umount** the storage.  By using ext4, most of the badness that can happen for typical external USB storage automatic mounting is avoided.

Another thing to be aware is that my systems typically are running 18.04 still. None of the physical installs have anything newer, yet. I've avoiding using v2.x of rdiff-backup.  I actually ported v1.x to 20.04 a few years ago and have been using that rather than upgrading all the older systems to v2.x of the tool.  I'm missing out on some nice features.  For me, the most important is sparse file support.

For rdiff-backup, the python2 and python3 based versions are incompatible in the client-server model. Both use the same format on disk. The rdiff-backup team did something good with their versioning.  v2.x is python3.  v1.x are python2. That's important.  Basically, it means I need to have both versions of rdiff-backup on my servers OR I need to upgrade all of them en-masse to v2.x  The compatibility issue is with python2 vs python3 data serialization over the network. It isn't rdiff-backup's fault, but it is reality.  Broken client/server compatibility happened around 2013 too.

---

### Post by wyattwhiteeagle on 2022-02-20
Life here where I live took some major turns too, and I apologize for my delay.
While I was dealing with a family emergency after my last post, I did some thinking.
Made some changes to my laptop after I got home and rested up and I'm still working on that.

I thought I needed to chime in for a bit due to the following quoted...

> **TheFu said:**
> ..I'm almost sorry that I posted my "simple" script...

@TheFu Don't be sorry about it. If that script works for you at the time you wrote it, awesome.
It's even more awesome if it still works for you.
I believe that a lot of "beginner's" here, including myself use that same script as a learning exercise tool.
It just may need to be modified by the "beginning user" so that it works for the beginning user.
A lot of people look to you for guidance.
That's something to be proud of, honestly.

All the ranting and raving, though most time's isn't needed, usually means that the user is having a hard time and doesn't know a better way to express it to the more wise such as yourself.

Don't be down on yourself like that, your "simple" backup script actually helps a lot of people.

Until next time,
Wyatt

---

### Post by TheFu on 2022-02-20
> **wyattwhiteeagle said:**
>  
@TheFu Don't be sorry about it. If that script works for you at the time you wrote it, awesome.
It's even more awesome if it still works for you.
I believe that a lot of "beginner's" here, including myself use that same script as a learning exercise tool.
It just may need to be modified by the "beginning user" so that it works for the beginning user. 

I haven't used a script like my simple script in about a decade. I was a professional software developer for a long time, so only the most trivial scripts don't use lots of variables, decisions (if statements), functions and error checking.

My backups are pulled using backup servers (one for v1 and another for v2 of rdiff-backup). These pull backups from other machines on the network.  Most new users aren't skilled with ssh, so using that as a prerequisite is something I avoid, but ssh is central to almost everything running around here. There is actually a very special backup userid (it uses a random username) involved to allow the remote connection limited to only the backup servers on the LAN. Those backup users do not allow remote connections from any other systems. Security.

I feel is is best to start with something really simple, then build on that over time. That's how we all learn. The main script used is 50 lines alone, but really only has 5 lines that do work. The rest is setting up variables and comments or because 1 command is spread over 20 lines to be readable.  All those things will likely confuse people new to scripting, so I simplify it as far as possible to get the main ideas across in the initial post.  But on my systems, I don't really have 5 line scripts for backups. Not anymore.

I do commonly begin with 1 line in a script to accomplish the primary thing, then that gets expanded with more functionality.  Like cleaning up really old backup sets or gathering system information prior to performing any backups and ensuring that the daily system information is included in locations that are also part of the backed up data.  Think about it this way, if a partition table becomes corrupted, but everything else is fine with the machine, having an exact copy of that partition table makes the fix 5 seconds.  Without it, I'll be performing a full system restore which is between 30 and 45 minutes.  I know which I'd rather do on a Saturday morning when we have plans for the day.   5 second fix, every time.  Most of my information saving is around storage setups.  The information gathered has been improved over the decades.

By starting with a consistent solution first, small improvements can more easily happen. Over time, things that we learn can make the restore process easier and faster. After all, backups are useless if we cannot use them for a restore. The restore is the entire point. Sometimes we lose track of that fact.

---

### Post by wyattwhiteeagle on 2022-02-23
> **ActionParsnip said:**
> I'm surprised the system even functions after the earlier chmod command.......

As I said, I had to do a fresh re-install after that chmod command

---

### Post by wyattwhiteeagle on 2022-02-23
> **wyattwhiteeagle said:**
> ...Yours looks quite a bit different than mine.
I'm noticing some keystrokes in your's than mine doesn't have.
I will make some changes to mine and post the results...

How does this look?
Does it need to be modified any?

Does the 1st TGT need to be $TGT or "$TGT"?
Does anything in the --exclude --include section need modified or re-ordered?
Is the --exclude '**' line in the proper place or is it needed?

```
#!/bin/bash

# Clean up garbage inside all the HOME directories before doing the backup.
# No need for cache or trash files, for example.

# Ensure backups are by hostname, so multiple hosts can use the same backup storage
TGT="/media/wyatt/1bcaa815-53ce-4970-9ec8-21c612038f30/Backups/$(hostname)/Date=$(/bin/date +%Y-%m-%d-%b-%s)"
mkdir  -p "$TGT"

# mount the backup disk as needed; best not to leave it mounted.
/bin/mount /media/wyatt/1bcaa815-53ce-4970-9ec8-21c612038f30/Backups

# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --verbosity 5 --exclude-special-files --include  /etc  --include /root  \
           --include /usr/local --include /usr/bin --exclude / --exclude /media \
           --exclude **/.local/share/Trash --exclude **/.cache --exclude **/Cache \
           --exclude **/.gvfs --exclude **/.local/share/Trash --exclude **/.cpan \
           --exclude **/.cache --exclude **/.cache2 --exclude **/.mozilla/firefox \
           --exclude **/.adobe --exclude **/.dbus --exclude **/.dropbox --exclude **/.qt \
           --exclude **/.thumbnails --exclude **/Examples --exclude **/.ecryptfs --exclude **/lost+found \
           --include  /home  \
                                            --exclude '**'
            / "$TGT"

# Create the list of manually installed packages
# Use apt-mark showmanual and store that output somewhere that gets included in the backups.
# I put it into /media/wyatt/1bcaa815-53ce-4970-9ec8-21c612038f30/Backups/$(hostname)/Date=$(/bin/date +%Y-%m-%d-%b-%s)/apt-mark.manual=$(/bin/date +%Y-%m-%d-%b-%s)
/usr/bin/apt-mark showmanual > "$TGT"/apt-mark.manual=$(/bin/date +%Y-%m-%d-%b-%s)

######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade
######

# Remove really old backup sets - say 90 days old.
/usr/bin/rdiff-backup --force --remove-older-than 90D    "$TGT"

# umount the backup disk
umount /media/wyatt/1bcaa815-53ce-4970-9ec8-21c612038f30/Backups

```

---

### Post by ActionParsnip on 2022-02-23
> **wyattwhiteeagle said:**
> As I said, I had to do a fresh re-install after that chmod command
Must have missed that part while reading. Apologies

---

### Post by wyattwhiteeagle on 2022-02-23
> **ActionParsnip said:**
> Must have missed that part while reading. Apologies


Actually, I'm not surprised that you missed it.
It's in the course of 3 post's...


> **wyattwhiteeagle said:**
> When I change permissions to / or /root, things start not working properly.
What am I doing wrong here?
The command I used is...
```
sudo chmod -R a+rwx /
sudo chmod -R a+rwx /root
```


> **deadflowr said:**
> That just broke everything.
Some files and directories require specific permissions and rights.
The changes of making everything everything breaks that and causes programs to not run...


> **wyattwhiteeagle said:**
> ..Yeah...after I did a fresh reinstall...I didn't change any permission's.
I made a note to change the script...not the permissions...

---

### Post by TheFu on 2022-02-23
```
sudo chmod -R a+rwx /
sudo chmod -R a+rwx /root
```
are never good, for any reason.  Backups need to retain the correct permissions for every directory and file. The actual contents of files are only 50% of what is critical in a backup. When you broke your system with those commands (btw, the 1st command did everything the 2nd one would have done too), hopefully, you learned how bad it could be. Basically, the system will stop working in a few minutes and you'll never be able to login again. Perhaps that was the goal? If so, check that off as "achieved."

The file and directory owner, group, permissions created by default have specific reasons. While you don't understand those, please don't change them. Nothing good will happen and you may turn a reasonably secure system into an open system for the world at best or a non-functioning system at worst.

In short, a+rwx on any directory are for people who don't understand permissions and I cannot think of any good reason to use that setting.  I suppose if someone is in a real hurry to access data only - never configurations, settings or programs - on an external drive, maybe audio or video files, then using 777 permissions may be acceptable for 2 minutes before putting the prior permissions back.

---

### Post by wyattwhiteeagle on 2022-02-23
Ok, the current script works.

How do I test my backup's?

It appear's that ALL of the "--exclude" and "--include" specified needs to be ALL on the same line, making that command one big long single line.
That's not mentioned ANYWHERE in ANY manual I've read or been directed to.

Here on the forums, it isn't mentioned to me at all.
Those who "show" their script to me seem to have modified their own script lines in the post.
(probably in fear of someone trying to "hack into" their backups)

If the user trust's their system security's and precautionary practice's, then that fear is most likely not needed.

Anyway...thank you all, it's been quite the learning experience...and...

The Script Works!

The current script
```
#!/bin/bash

# To activate this script
# chmod +x /home/wyatt/Desktop/BackupTestScript


# To run this script
# sudo /home/wyatt/Desktop/BackupTestScript


# Clean up garbage inside all the HOME directories before doing the backup.
# No need for cache or trash files, for example.


# Ensure backups are by hostname, so multiple hosts can use the same backup storage
TGT="/media/wyatt/d98d1629-adb3-421e-a72a-381bb40b03ce/Backups/$(hostname)"
mkdir  -p "$TGT"


# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup --force --exclude-special-files --include  /etc  --include /root  --exclude **/.gvfs  --exclude **/.local/share/Trash  --exclude **/.cpan  --exclude **/.cache  --exclude **/.cache2  --exclude **/.adobe  --exclude **/.dbus  --exclude **/.dropbox  --exclude **/.qt  --exclude **/.thumbnails  --exclude **/Examples  --exclude **/.ecryptfs  --exclude **/lost+found  --include  /home  \
                                            --exclude '**'    /       "$TGT"




# Create the list of manually installed packages
# Use apt-mark showmanual and store that output somewhere that gets included in the backups.
# I put it into "$TGT"/apt-mark.manual
/usr/bin/apt-mark showmanual > "$TGT"/apt-mark.manual


######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade
######


# Remove really old backup sets - say 30 days old.
/usr/bin/rdiff-backup --force --remove-older-than 30D    "$TGT"

```

---

### Post by TheFu on 2022-02-23
```
/usr/bin/rdiff-backup --force --exclude-special-files --include  /etc  --include /root  --exclude **/.gvfs  --exclude **/.local/share/Trash  --exclude **/.cpan  --exclude **/.cache  --exclude **/.cache2  --exclude **/.adobe  --exclude **/.dbus  --exclude **/.dropbox  --exclude **/.qt  --exclude **/.thumbnails  --exclude **/Examples  --exclude **/.ecryptfs  --exclude **/lost+found  --include  /home  \
                                            --exclude '**'    /       "$TGT"
```

Can be written as:
```
/usr/bin/rdiff-backup --force --exclude-special-files --include  /etc  --include /root  [COLOR="#FF0000"]\[/COLOR]
--exclude **/.gvfs  --exclude **/.local/share/Trash  --exclude **/.cpan  [COLOR="#FF0000"]\[/COLOR]
--exclude **/.cache  --exclude **/.cache2  --exclude **/.adobe  --exclude **/.dbus [COLOR="#FF0000"]\[/COLOR]
 --exclude **/.dropbox  --exclude **/.qt  --exclude **/.thumbnails  --exclude **/Examples  [COLOR="#FF0000"]\[/COLOR]
--exclude **/.ecryptfs  --exclude **/lost+found  --include  /home  [COLOR="#FF0000"]\[/COLOR]
                                            --exclude '**'    /       "$TGT"
```

Pretty much every scripting language has a line continuation method and having a [COLOR="#FF0000"]\[/COLOR]
as the last character on the line is used probably 90% of the time.  No other characters are allowed. Not a space, tab, whatever. Not {CR}{LF}, just \{LF}

We don't know what you don't know. A beginning scripting book/class should have covered that very early. It is hard to tailor information provided perfectly for what you need to know, as you need to know it.  It is hard to ask us questions too, since some of us (me) will often go very deep, very quickly, beyond "what to type".  The what to type stuff doesn't really interest me. It is the "why" that I try to stay on.

I get that things like this are frustrating. We've all been there with something similar. OTOH, it is a lesson you'll never forget now.  BTW, I tested my basic script before posting it in that other thread.  I also said to run it from root's crontab, which was a "whooosh" for many people.  I didn't test your script and assumed that you'd figure out the typos in it.  For example, you left an extra \ in the middle of a line. That just escapes the following character, which was a {space} and didn't actually do anything bad except cause slight confusion.

There are many basic troubleshooting techniques for all programming. Bash has some too. There are plenty of websites that cover that and bash debugging. Don't expect to get every answer from these forums.

---

### Post by wyattwhiteeagle on 2022-02-23
> **TheFu said:**
> ```
/usr/bin/rdiff-backup --force --exclude-special-files --include  /etc  --include /root  --exclude **/.gvfs  --exclude **/.local/share/Trash  --exclude **/.cpan  --exclude **/.cache  --exclude **/.cache2  --exclude **/.adobe  --exclude **/.dbus  --exclude **/.dropbox  --exclude **/.qt  --exclude **/.thumbnails  --exclude **/Examples  --exclude **/.ecryptfs  --exclude **/lost+found  --include  /home  \
                                            --exclude '**'    /       "$TGT"
```


Can be written as:
```
/usr/bin/rdiff-backup --force --exclude-special-files --include  /etc  --include /root  \
--exclude **/.gvfs  --exclude **/.local/share/Trash  --exclude **/.cpan  \
--exclude **/.cache  --exclude **/.cache2  --exclude **/.adobe  --exclude **/.dbus \
 --exclude **/.dropbox  --exclude **/.qt  --exclude **/.thumbnails  --exclude **/Examples  \
--exclude **/.ecryptfs  --exclude **/lost+found  --include  /home  \
                                            --exclude '**'    /       "$TGT"
```


Pretty much every scripting language has a line continuation method and having a \
as the last character on the line is used probably 90% of the time. No other characters are allowed. Not a space, tab, whatever. Not {CR}{LF}, just \{LF}



That looks exactly like what I tried in post #34 above.
It didn't work for me.


The terminal printed
```
/home/wyatt/Desktop/MyBackupTest: line xx: --exclude: Command not found.
```
So I opened the script in gedit, looked for those line numbers, lo and behold...it was those lines where the white spaces were in front of each one of them.

The same error message happened when I tried the script in post #12.
There were no white spaces in front of the --exclude lines.


> **wyattwhiteeagle said:**
> ```
# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \
                                            --exclude '**'    /       TGT="/media/wyatt/D05C37195C36FA34/Backups/$(hostname)/Date=$(/bin/date +%Y-%m-%d-%b-%s)"
--exclude **/.gvfs
--exclude **/.local/share/Trash
--exclude **/.cpan
--exclude **/.cache
--exclude **/.cache2
--exclude **/.mozilla/firefox/*/chrome/sagetoo
--exclude **/.mozilla/firefox/*/sessionstore
--exclude **/.mozilla/firefox/*/Cache
--exclude **/.adobe
```


I believe the --exclude lines being after the --exclude '**' line was one of many issue's in that script

On those lines in post 12, there is no \ at the end of each.
I don't see how forgetting the \ at the end of the line would cause rdiff-backup to return an error message pointing to the front of the line specifying that the the --exclude command isn't found.

Unless it is the spaces in front of the first --exclude in each of those lines,
I'm gonna need to see the exact thing I did that caused it not to work for me.

---

### Post by TheFu on 2022-02-24
I can't see the post #s now. This editor doesn't show them for some reason.

> **wyattwhiteeagle said:**
> That looks exactly like what I tried in post #34 above.
It didn't work for me.
  Details matter. I tried to make the point earlier, but missed, it seems.  It is common for us to see things grouped together and assumed the computer groups them together too.

> **wyattwhiteeagle said:**
> The terminal printed
```
/home/wyatt/Desktop/MyBackupTest: line xx: --exclude: Command not found.
```
So I opened the script in gedit, looked for those line numbers, lo and behold...it was those lines where the white spaces were in front of each one of them.

The same error message happened when I tried the script in post #12.
There were no white spaces in front of the --exclude lines.

I believe the --exclude lines being after the --exclude '**' line was one of many issue's in that script


Not related. Spacing generally doesn't matter. Bash isn't python and most languages aren't indentation sensitive like python is. I can't think of any besides FORTRAN where a column matters.

> **wyattwhiteeagle said:**
> 
On those lines in post 12, there is no \ at the end of each.
_**I don't see how forgetting the \ at the end of the line would cause rdiff-backup to return an error message pointing to the front of the line specifying that the the --exclude command isn't found.**_


It appears you are seeing relations that don't exist.  If there isn't a trailing \
at the end of a line, then the next line is a new command.  Look at those lines again.  Each is a new command, not a continued part of the prior line.

```
line xx: --exclude: Command not found.
```
is bash telling you that it cannot find a program to run, named "--exclude"  That's the error.  Spacing before a trailing \
only matters if the command needs a space there when the lines are merged and the trailing \ on the line is removed. In general, spaces between options or arguments don't matter, unless the space changes a file or directory name. This doesn't mean we can add spaces in the middle of keywords or option names.

---

### Post by TheFu on 2022-02-24
The script in post #12 has a number of problems.
It isn't normal to have a variable assignment in the place where it should be a variable reference.
Also, on the line with --exclude '**'  there isn't any trailing \
at the end of that line, so that is the last line of the rdiff-backup command.  All the following --exclude lines are each new commands ... that don't exist.  

When I posted that list of excludes (ref #9), I specifically stated that you'd need to put them onto a single line and that I was using a _heredoc_ to make script maintenance easier and that in my real script, it was merged by a function.  You seemed to have missed that.  In bash, you'd need a continuation character for each exclude AND those need to be placed in the correct order inside the rdiff-backup command.  Pretty certain I wrote that too, which was missed.  My example in that same post did show --exclude-special-files (in bold) with all the other excludes following.  Perhaps that was too subtle a hint for where I'd put them?

Have you researched what a 'heredoc' is?

In #27, I tried to point out with the manpage explanation that the last 2 parts of any rdiff-backup command are the source followed by the target.  Options are not allowed to follow those.  Again, it seems I failed to get the point across. Sorry.

My posts are ***extremely dense*** with information and hard-learned knowledge. Slapping something together will seldom end with the desired outcome.

---

### Post by Quarkrad on 2022-02-24
I don't want to confuse things here, as I am very much a newbie re rdiff-backup, but this might help. Re my script in #24 - I have simplified it to something like:  [I]rdiff-backup............include these things...........exclude everything else........put the backup here
[/I]
```
sudo /usr/bin/rdiff-backup  --verbosity 5 --include-globbing-filelist '/usr/bin/includelist.txt' --exclude / / /media/dad/backup/rdiffbackuptest
            
# remove old backups
sudo /usr/bin/rdiff-backup --force --remove-older-than 90D /media/dad/backup/rdiffbackuptest
``` 

my includelist.txt now looks like this:

```
/
root/*
/etc/*
/usr/local/*
/usr/bin/*
/home/dad/Desktop/*
/home/dad/Documents/*
/home/dad/Downloads/*
/home/dad/dvd/*
/home/dad/Music/*
/home/dad/Pictures/*
/home/dad/plex/*
/home/dad/Public/*
/home/dad/Templates/*
/home/dad/Videos/*
/home/dad/.aMule/*
/home/dad/.audacity-data/*
/home/dad/.cert/*
/home/dad/.config/*
/home/dad/.googleearth/*
/home/dad/.local/*
/home/dad/.thunderbird/ifmp8iai.default-release/Mail/*
```

I've tested both scripts, and restored them - both scripts do the same thing.  As stated, this works for me and may not be what you specifically  want.  I post this because I got very confused with using a *exclude/include list* within rdiff-backup when I started - but once I got it sorted it has made my life easier. (Until I get more experienced with rdiff-backp/linux that is!).

---

### Post by wyattwhiteeagle on 2022-02-24
> **TheFu said:**
> I can't see the post #s now. This editor doesn't show them for some reason.
I remember you saying that in 2014. That's why I went and hunted down the post's so that I could quote them.


> **TheFu said:**
> Details matter. I tried to make the point earlier, but missed, it seems. It is common for us to see things grouped together and assumed the computer groups them together too.
No, it wasn't missed.
I was a MS Windows PC Programming and Repair Service Technician.
I know details matter.
DOS command line's will not work in Ubuntu, two completely different computing language's.
Sometime's my Windows experience get's in the way of doing things Ubuntu.
That get's me into a little trouble.
There are emulator's or whatever, such as WineHQ, PlayOnLinux, etc.


> **TheFu said:**
> ...Spacing generally doesn't matter. Bash isn't python and most languages aren't indentation sensitive like python is. I can't think of any besides FORTRAN where a column matters.
In Windows, if there is even one extra space anywhere in the command line whether at the beginning, within, or at the end...it's a broken command and it won't work.


Here in Ubuntu, things are just a tad bit more leniant, but not much.


That's one area where the Windows "column rule" was getting mixed in.


> **TheFu said:**
> It appears you are seeing relations that don't exist. If there isn't a trailing \
at the end of a line, then the next line is a new command. Look at those lines again. Each is a new command, not a continued part of the prior line.
In this quote...
> **wyattwhiteeagle said:**
> Your's looks more efficient than mine does.
Did you manually create the includelist.txt?




Your script...
```
sudo /usr/bin/rdiff-backup  --verbosity 5 --exclude-special-files \
           --include /root --include /etc --include /usr/local --include /usr/bin --exclude / --exclude /media \
           --exclude **/.local/share/Trash --exclude **/.cache \
           --exclude **/Cache \
            / /media/dad/backup/rdiffbackup            
```




My script...
```
# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \
                                            --exclude '**'    /       /media/wyatt/d98d1629-adb3-421e-a72a-381bb40b03ce/Backups/$(hostname)
           --exclude **/.gvfs
           --exclude **/.local/share/Trash
           --exclude **/.cpan
           --exclude **/.cache
           --exclude **/.cache2
           --exclude **/.mozilla/firefox/*/chrome/sagetoo
           --exclude **/.mozilla/firefox/*/sessionstore
           --exclude **/.mozilla/firefox/*/Cache
           --exclude **/.adobe
```




Yours looks quite a bit different than mine.
I'm noticing some keystrokes in your's than mine doesn't have.
I will make some changes to mine and post the results.




Thank you so very much.
The main thing I had noticed was the \ at the end of each line.
I didn't know exactly how it mattered, but after noticing it...I knew it mattered.


> **TheFu said:**
> ```
line xx: --exclude: Command not found.
```
is bash telling you that it cannot find a program to run, named "--exclude" That's the error.
I didn't know what was telling me there was an error. That part didn't matter to me.
I understood that to be telling me there was something wrong in the script that needed to be corrected.


> **TheFu said:**
> Spacing before a trailing \ only matters if the command needs a space there when the lines are merged and the trailing \ on the line is removed.
In general, spaces between options or arguments don't matter, unless the space changes a file or directory name. This doesn't mean we can add spaces in the middle of keywords or option names.
I know that rule applie's, but I didn't think I would break that rule by following the example's of other script's.
One need's to be very careful when following other's example script's.


> **TheFu said:**
> The script in post #12 has a number of problems.
It isn't normal to have a variable assignment in the place where it should be a variable reference.
Also, on the line with --exclude '**' there isn't any trailing \
at the end of that line, so that is the last line of the rdiff-backup command. All the following --exclude lines are each new commands ... that don't exist.


When I posted that list of excludes (ref #9), I specifically stated that you'd need to put them onto a single line and that I was using a heredoc to make script maintenance easier and that in my real script, it was merged by a function. You seemed to have missed that.
No, I didn't miss it.
I'm tired...tired of what...tired of having to spend hours up to days to do fresh OS install's and having to re-install and reconfigure things just to have the system back to the way I had it before it messed up.


I was so caught up in "getting something going" that it seemed to have clouded the need to "go read".


I apologize that I seemed to have missed it.
That wasn't my intention.


> **TheFu said:**
> In bash, you'd need a continuation character for each exclude AND those need to be placed in the correct order inside the rdiff-backup command. Pretty certain I wrote that too, which was missed. My example in that same post did show --exclude-special-files (in bold) with all the other excludes following. Perhaps that was too subtle a hint for where I'd put them?
I didn't miss those either.
Some thing's I learn by "hands-on".
I needed to "see" how thing's work for other user's.
Now that I have something working for me (though it may not be the most effective), I understand what you meant by those things.


> **TheFu said:**
> Have you researched what a 'heredoc' is?
No, I haven't.
Now that I have something going, I can read up on things.
Heredoc is one of those things.


> **TheFu said:**
> In #27, I tried to point out with the manpage explanation that the last 2 parts of any rdiff-backup command are the source followed by the target. Options are not allowed to follow those. Again, it seems I failed to get the point across. Sorry.
You got the point across to me.
I'm having a hard time understanding what options and arguments are and knowing how to notice the difference and how to recognize and use them in a script.


> **TheFu said:**
> My posts are extremely dense with information and hard-learned knowledge. Slapping something together will seldom end with the desired outcome.
Scripting, backup and restore is something "new" for me.
In Windows, there was always *.bat, *.bak, CLI command's, program's and GUI application's provided.


In Ubuntu, I get the chance to learn "new" way's of doing thing's.


I will most likely break my arms, legs, back and neck before I "throw in the towel" and go with something easier and more "simple".
I call that the "cowboy/warrior spirit in me".


> "A cowboy's work is never done."
"A warrior never quit's; never give's up."


On the "journey to learn", I knew I would "miss things", make mistakes, etc.
Is that a reason to quit or give up...ABSOLUTELY NOT!!!


It give's me more of a reason to "pick up, shake the dust off, drive forward and carry on."

---

### Post by wyattwhiteeagle on 2022-02-24
> **TheFu said:**
> ```
/usr/bin/rdiff-backup --force --exclude-special-files --include  /etc  --include /root  [COLOR=#FF0000]\[/COLOR]
--exclude **/.gvfs  --exclude **/.local/share/Trash  --exclude **/.cpan  [COLOR=#FF0000]\[/COLOR]
--exclude **/.cache  --exclude **/.cache2  --exclude **/.adobe  --exclude **/.dbus [COLOR=#FF0000]\[/COLOR]
 --exclude **/.dropbox  --exclude **/.qt  --exclude **/.thumbnails  --exclude **/Examples  [COLOR=#FF0000]\[/COLOR]
--exclude **/.ecryptfs  --exclude **/lost+found  --include  /home  [COLOR=#FF0000]\[/COLOR]
                                            --exclude '**'    /       "$TGT"
```

Pretty much every scripting language has a line continuation method and having a [COLOR=#FF0000]\[/COLOR]
as the last character on the line is used probably 90% of the time.  No other characters are allowed. Not a space, tab, whatever. Not {CR}{LF}, just \{LF}...

I need to ask...what is the {LF} at the end ofyour statement and what does it stand for?

---

### Post by TheFu on 2022-02-24
CR - carriage return
LF - Line feed

MS-Dos REQUIRES both.
Unix systems use just the LF. Having both is an error.

This is why Unix end-of-line text files aren't compatible with MS-DOS systems and vice versa.  It is the reason that **dos2unix** and **unix2dos** utilities exist.  It is also why plan FTP has an "ascii" command  and a "binary" command for transfers.

Open an MS-DOS/Windows text file in vi and you'll see ^M characters at the end of every line. I think vim might hide them unless you specifically say **vim -b {file}**  . The ^M is how a CRLF is displayed in vi/vim.

BTW, I was an MS-DOS and Windows programmer for years before I found Unix, then Linux. I remember being extremely frustrated when my Unix-team members would tell me to RTFM rather than answer questions I thought were simple.  My first attempts to install Linux failed. SLS was hard to get working.  Slackware was the easy-to-use version back then.  

For about the first 6 months on that job, I was reading everything I could on Unix commands, shells, X/Windows, programming.  Turns out that programming in C on Windows, DOS and Unix systems isn't really that different.  Instead of using a \ as a path separator on Windows, use a /.  It works.  Cross-platform programmers have known this ... since the beginning.  Any MSFT component will use either. Most 3rd party components will as well, just fine.  There are a few that will switch the / --> \ and there are a few MS-only programmers that blocked the / as an input for filenames, but I haven't seen anything like in decades.

---

### Post by wyattwhiteeagle on 2022-02-24
Does a formatted ext4 usb flashdrive/external HDD need to be mounted for the backup and/or restore to work?

With it being usb...does the mount and umount commands need to be in the script?

Where is the referenced fstab and what needs to be put into it and where in the fstab does it need to be put?

---

### Post by TheFu on 2022-02-24
/etc/fstab

"need" is a strong word. There are many different ways to mount storage on demand. If you don't mount it, how does that happen?  On my systems, it won't.  **_I consider automatic mounting that I didn't specifically setup to be a SEV-1 bug in any OS._** I don't allow that.

Do what works for you and you consider 'secure enough'.

/etc/fstab isn't anything special, but that is THE ONLY LOCATION on any system. fstab options control how it behaves and when it is mounted.

My actual backup system uses a backup server to pull data from different clients on the network, so clients don't actually have access to the storage where backups are placed. The backup server reaches out and pulls the data back. Client machines can't access the storage.

---

### Post by wyattwhiteeagle on 2022-02-24
> **TheFu said:**
> /etc/fstab

"need" is a strong word. There are many different ways to mount storage on demand. If you don't mount it, how does that happen?  On my systems, it won't.  **_I consider automatic mounting that I didn't specifically setup to be a SEV-1 bug in any OS._** I don't allow that.

Do what works for you and you consider 'secure enough'.

/etc/fstab isn't anything special, but that is THE ONLY LOCATION on any system. fstab options control how it behaves and when it is mounted.

My actual backup system uses a backup server to pull data from different clients on the network, so clients don't actually have access to the storage where backups are placed. The backup server reaches out and pulls the data back. Client machines can't access the storage.

So, what yours might need, mine may or may not need...is that what you're saying?

Also...in the script I'm using, does the following need to be modified?
```
######[ to restore pkgs ]######
#### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade
######
```

The current script
```
#!/bin/bash

# To activate this script
# chmod +x /home/wyatt/Desktop/MyBackupScript

# To run this script
# sudo /home/wyatt/Desktop/MyBackupScript

# Clean up garbage inside all the HOME directories before doing the backup.
# No need for cache or trash files, for example.

# Ensure backups are by hostname, so multiple hosts can use the same backup storage
TGT="/media/wyatt/d98d1629-adb3-421e-a72a-381bb40b03ce/Backups/$(hostname)"
mkdir  -p "$TGT"/Date=$(/bin/date +%M-%d-%y-%h-%m-%s)

# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup --force --exclude-special-files --include  /etc  --include /root  \
--exclude **/.gvfs  --exclude **/.local/share/Trash  --exclude **/.cpan  \
--exclude **/.cache  --exclude **/.cache2  --exclude **/.adobe  --exclude **/.dbus \
--exclude **/.dropbox  --exclude **/.qt  --exclude **/.thumbnails  --exclude **/Examples  \
--exclude **/.ecryptfs  --exclude **/lost+found  --include  /home  \
                                            --exclude '**'    /       "$TGT"

# Create the list of manually installed packages
# Use apt-mark showmanual and store that output somewhere that gets included in the backups.
# I put it into "$TGT"/apt-mark.manual
/usr/bin/apt-mark showmanual > "$TGT"/apt-mark.manual

######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade
######

# Remove really old backup sets - say 30 days old.
/usr/bin/rdiff-backup --force --remove-older-than 30D    "$TGT"
```

---

### Post by TheFu on 2022-02-24
> **wyattwhiteeagle said:**
> So, what yours might need, mine may or may not need...is that what you're saying?

I'm saying that the fstab is often how people choose to mount storage. It isn't the only method. If you expect to write to files to storage, it needs to be mounted, somehow.  If "magic" will mount your storage and you are happy with that, great. I don't like magic on computers. I want to control when, how, and where storage is mounted.  That's me.  Also, my backup storage isn't connected to any client, so the risks my backups have are different than the risks that yours will have, based on the scripting in this thread.

> **wyattwhiteeagle said:**
> 
Also...in the script I'm using, does the following need to be modified?
```
######[ to restore pkgs ]######
#### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade
######
```

Those are all comments. Hopefully, they are helpful to someone.

Anyway, good luck.

---

### Post by wyattwhiteeagle on 2022-02-24
> **Quarkrad said:**
> I don't want to confuse things here, as I am very much a newbie re rdiff-backup, but this might help. Re my script in #24 - I have simplified it to something like:  [I]rdiff-backup............include these things...........exclude everything else........put the backup here
[/I]
```
sudo /usr/bin/rdiff-backup  --verbosity 5 --include-globbing-filelist '/usr/bin/includelist.txt' --exclude / / /media/dad/backup/rdiffbackuptest
            
# remove old backups
sudo /usr/bin/rdiff-backup --force --remove-older-than 90D /media/dad/backup/rdiffbackuptest
``` 

my includelist.txt now looks like this:

```
/
root/*
/etc/*
/usr/local/*
/usr/bin/*
/home/dad/Desktop/*
/home/dad/Documents/*
/home/dad/Downloads/*
/home/dad/dvd/*
/home/dad/Music/*
/home/dad/Pictures/*
/home/dad/plex/*
/home/dad/Public/*
/home/dad/Templates/*
/home/dad/Videos/*
/home/dad/.aMule/*
/home/dad/.audacity-data/*
/home/dad/.cert/*
/home/dad/.config/*
/home/dad/.googleearth/*
/home/dad/.local/*
/home/dad/.thunderbird/ifmp8iai.default-release/Mail/*
```

I've tested both scripts, and restored them - both scripts do the same thing.  As stated, this works for me and may not be what you specifically  want.  I post this because I got very confused with using a *exclude/include list* within rdiff-backup when I started - but once I got it sorted it has made my life easier. (Until I get more experienced with rdiff-backp/linux that is!).
In your includelist.txt, it looks like your "root/*" is either on the wrong line or is missing a / immediately before it.

Someone said that the directory "/" and "/root" are the same thing.
That may not be true in this sense.

---

### Post by Quarkrad on 2022-02-25
If you look at the folders under **/** you will see the folders,* etc, usr, media, var, home, dev, bin,*............ all the top level system folders that sit under the top level **/** folder.  When ubuntu installs itself it automatically creates these top level folders including one called *root/*. So ... too possibly confused there is a *root/* folder under **/**.  In human speak we could confusingly say there is a root folder under root - which in a sense doesn't make sense - but when you look at the top level folder structure it does and there is a *root/ *folder there. (Language???).  There are many articles what this is used for.  Why do I back it up?  Back to a recommendation from @TheFu - there will be instances when re-building from a backup you need this folder as it could contain vital configuration files for your needs.

---

### Post by wyattwhiteeagle on 2022-02-25
> **Quarkrad said:**
> If you look at the folders under **/** you will see the folders,* etc, usr, media, var, home, dev, bin,*............ all the top level system folders that sit under the top level **/** folder.  When ubuntu installs itself it automatically creates these top level folders including one called *root/*. So ... too possibly confused there is a *root/* folder under **/**.  In human speak we could confusingly say there is a root folder under root - which in a sense doesn't make sense - but when you look at the top level folder structure it does and there is a *root/ *folder there. (Language???).  There are many articles what this is used for.  Why do I back it up?  Back to a recommendation from @TheFu - there will be instances when re-building from a backup you need this folder as it could contain vital configuration files for your needs.

When I open baobab, I see a / folder and in the list of immediate folder's I see a root folder. 
I don't see a root folder next to the / folder.
On mine, the root folder is in the / folder.
The directory path, therefore is /root.

In your list, you have root and not /root.
Maybe it is something specific with your "Mate" version.

---

### Post by TheFu on 2022-02-25
/ is the root directory to the system.
/root is the HOME directory for the root userid's account.
Confusing, perhaps. Very standard across all Unix-like OSes the last 20 yrs.  In the 1990s, root's HOME was just / which lead to a different sort of confusion and problems.

I place system information and the list of packages to be backed up in /root/backups/. I also place scripts that only the root userid should run in /root/bin/, therefore I need to include /root/ in my backups.  That may be subtle, but it is in the script.  The OP decided to handle the list of manually installed packages in a different way, which may break rdiff-backup, now that I think about it.  

Never touch the target rdiff-backup directories without using the tool.  Pulling stuff out of the backup area is fine, but copying stuff in should only be done by rdiff-backup.  This is a common limitation across all backup tools, BTW.  They expect all files to be there and indexed by their internal DBs.

---

### Post by wyattwhiteeagle on 2022-02-25
> **TheFu said:**
> ...The OP decided to handle the list of manually installed packages in a different way, which may break rdiff-backup, now that I think about it...

That concerns me.

About that particular file, I only changed the target location.

Unless rdiff-backup has a preset default location without referring to the script used for rdiff-backup for the location of that file, how will handling that file in the way I handle'd it break rdiff-backup?

Now that I think about it, you may be refering to the ext4 formatted backup usb flashdrive being mounted on /media.
Can the usb flashdrive (or someething within the system) be reconfigured to not mount the flashdrive on /media?

Can /media folder be reconfigured to "secure" it's vulnerabilities?

Or are you refering to the flashdrive write-limits?

---

### Post by TheFu on 2022-02-25
```
/usr/bin/apt-mark showmanual > "$TGT"/apt-mark.manual
```
is the problem line in the script.

**_Don't use any other too to touch files inside "$TGT", just rdiff-backup._**
My example puts those file in a location that is included in the backup source locations for a reason.

Learning by failure is best. Feel free to ignore me. Maybe the version of rdiff-backup you use doesn't care? IDK.

Don't attempt to delete intermediate backup sets either.  It would be nice to keep one backup per month after a few months of dailies, but that would break every backup AFTER the one most recent is removed.  The diffs are between the current and next prior backup set. It is necessary for efficient storage use. Only data (or file properties/permissions/owner/group) that changed between today and the most recent backup are part of the rdiff stuff.

---

### Post by wyattwhiteeagle on 2022-02-25
How do I copy the system information into /root/backups/?
Are these "root userid-only" scripts on the system by default or are they "user created" scripts?
How do I copy these scripts into /root/bin/?

> **TheFu said:**
> ...the version of rdiff-backup you use...
rdiff-backup 2.0.0-1-amd64        remote incremental backup

> **TheFu said:**
> ```
/usr/bin/apt-mark showmanual > "$TGT"/apt-mark.manual
```
is the problem line in the script.

Don't use any other too to touch files inside "$TGT", just rdiff-backup.
My example puts those file in a location that is included in the backup source locations for a reason.
> **TheFu said:**
> ...place system information and the list of packages to be backed up in /root/backups/. 
...place scripts that only the root userid should run in /root/bin/

I will change my script accordingly. I now see what you meant.

The current script
```
#!/bin/bash

# To activate this script
# chmod +x /home/wyatt/Desktop/MyBackupScript

# To run this script
# sudo /home/wyatt/Desktop/MyBackupScript

mkdir  -p /root/backups

# Create the list of manually installed packages - use apt-mark showmanual and store that output somewhere that gets included in the backups.
#I put it into /root/backups/
/usr/bin/apt-mark showmanual > /root/backups/apt-mark.manual
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

######
# Clean up garbage inside all the HOME directories before doing the backup.
# No need for cache or trash files, for example.

# Ensure backups are by hostname, so multiple hosts can use the same backup storage
TGT="/media/wyatt/544ab777-e943-4fa3-a45a-3897c72f1d3e/Backups/$(hostname)/Date=$(/bin/date +%M-%d-%y-%h-%m-%s)"
mkdir  -p "$TGT"

# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup --force --exclude-special-files --include  /etc  --include /root  \
--exclude **/.gvfs  --exclude **/.local/share/Trash  --exclude **/.cpan  \
--exclude **/.cache  --exclude **/.cache2  --exclude **/.adobe  --exclude **/.dbus \
--exclude **/.dropbox  --exclude **/.qt  --exclude **/.thumbnails  --exclude **/Examples  \
--exclude **/.ecryptfs  --exclude **/lost+found  --include  /home  \
                                            --exclude '**'    /       "$TGT"

# Remove really old backup sets - say 30 days old.
/usr/bin/rdiff-backup --force --remove-older-than 30D    "$TGT"
```

---

### Post by wyattwhiteeagle on 2022-03-11
How do I copy the system information into /root/backups/?
Are these "root userid-only" scripts on the system by default or are they "user created" scripts?
How do I copy these scripts into /root/bin/?

The current script
```
#!/bin/bash

# To activate this script
# chmod +x /home/wyatt/Desktop/MyBackupScript

# To run this script
# sudo /home/wyatt/Desktop/MyBackupScript

mkdir  -p /root/backups

# Create the list of manually installed packages - use apt-mark showmanual and store that output somewhere that gets included in the backups.
#I put it into /root/backups/
/usr/bin/apt-mark showmanual > /root/backups/apt-mark.manual
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

######
# Clean up garbage inside all the HOME directories before doing the backup.
# No need for cache or trash files, for example.

# Ensure backups are by hostname, so multiple hosts can use the same backup storage
TGT="/media/wyatt/544ab777-e943-4fa3-a45a-3897c72f1d3e/Backups/$(hostname)/Date=$(/bin/date +%M-%d-%y-%h-%m-%s)"
mkdir  -p "$TGT"

# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup --force --exclude-special-files --include  /etc  --include /root  \
--exclude **/.gvfs  --exclude **/.local/share/Trash  --exclude **/.cpan  \
--exclude **/.cache  --exclude **/.cache2  --exclude **/.adobe  --exclude **/.dbus \
--exclude **/.dropbox  --exclude **/.qt  --exclude **/.thumbnails  --exclude **/Examples  \
--exclude **/.ecryptfs  --exclude **/lost+found  --include  /home  \
                                            --exclude '**'    /       "$TGT"

# Remove really old backup sets - say 30 days old.
/usr/bin/rdiff-backup --force --remove-older-than 30D    "$TGT"
```

---

