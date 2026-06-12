---
title: "Backups Exclude Locations Evolved?"
date: 2022-03-09
forum: General Help
---

### Post by wyattwhiteeagle on 2022-03-09
Looking at the "exclude" list's from "days gone by" up to now, it seem's that over the years...the locations of what to exclude from the backups have changed.

There seems to be only two or three which have stayed constant.
All other's seem to be in different directories.

In 20.04, which directories should be excluded from the backups?

---

### Post by CharlesA on 2022-03-09
How are you doing your backups?

If I use tar, I use --one-file-system to exclude backing stuff up from other file systems.

See here for more info:
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

### Post by wyattwhiteeagle on 2022-03-10
I use a "3-tier strategy"

TimeShift
BackInTime
rdiff-backup

---

### Post by wyattwhiteeagle on 2022-03-10
Ok...
Maybe my question wasn't asked properly
And surely I'm not the first to notice this.

Some might believe I'm running an "unofficial" Ubuntu.
I'm using the one from the official link...
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

Check your own system.
You may actually be including what you have "believed" to be excluding.

I don't know...maybe my 'minimal' install has something to do with this.

On my Ubuntu 20.04, there is no gvfs or .gvfs anywhere under my /home
And ".gvfs" doesn't appear anywhere at all.


Only the following "gvfs" appears on my system.
None of them appear under /home.
Which one's do I exclude from my backups?

Same question applies for most other suggested "excludes"...such as "cpan" or ".cpan".


```
/root/.cache/gvfs
/usr/lib/gvfs
/usr/share/gvfs
/run/user/1000/gvfs
/usr/lib/x86_64-linux-gnu/gvfs
/usr/share/doc/gvfs

```

---

### Post by CharlesA on 2022-03-10
What desktop environment are you using? .gvfs is specific to GNOME. See here for more info on what it is used for:
[https://gitlab.gnome.org/GNOME/gvfs](https://gitlab.gnome.org/GNOME/gvfs)

To answer your question: I use borgbackup to do my backups for data and use tar to backup the OS.

I do exclude a bunch of stuff from borg, but that's specific to my data.

---

### Post by GhX6GZMB on 2022-03-10
> **wyattwhiteeagle said:**
> I use a "3-tier strategy"

TimeShift
BackInTime
rdiff-backup

I do the same, except not the "3rd tier". Is that for a total backup?

For system backup I use Timeshift (I am admin user). This is set to include all system files _plus_ hidden files in $HOME. One exception: /usr/share/kicad/modules/***. This excludes the 3D KiCAD libraries, because no one needs them and they're damn big. But that's specific to this system.

For user backup I use Back In Time. This is set to include all user files in $HOME except the hidden files for the admin user (me).
Note that this is user-specific, each other user has his/her own setup including full $HOME backup.
I attach my settings for Timeshift and Back-In-Time (admin user only) for your reference. Works a treat, I've done plenty of bare-metal reinstalls just using these two tools.

---

### Post by wyattwhiteeagle on 2022-03-10
> **ml9104 said:**
> I do the same, except not the "3rd tier". Is that for a total backup?

For system backup I use Timeshift (I am admin user). This is set to include all system files _plus_ hidden files in $HOME. One exception: /usr/share/kicad/modules/***. This excludes the 3D KiCAD libraries, because no one needs them and they're damn big. But that's specific to this system.

For user backup I use Back In Time. This is set to include all user files in $HOME except the hidden files for the admin user (me).
Note that this is user-specific, each other user has his/her own setup including full $HOME backup.
I attach my settings for Timeshift and Back-In-Time (admin user only) for your reference. Works a treat, I've done plenty of bare-metal reinstalls just using these two tools.

Yes the rdiff-backup and what I call a 3-tier strategy is for a "total 280% backup" since nothing is 100%

> **CharlesA said:**
> What desktop environment are you using? .gvfs is specific to GNOME. See here for more info on what it is used for:
[https://gitlab.gnome.org/GNOME/gvfs](https://gitlab.gnome.org/GNOME/gvfs)

To answer your question: I use borgbackup to do my backups for data and use tar to backup the OS.

I do exclude a bunch of stuff from borg, but that's specific to my data.

I'm using the one that is installed by default with Ubuntu 20.04 LTS minimal install.
If that is gnome...then I'm using gnome

All I know is I see a lot of people suggesting to exclude "**/.gvfs" or "/home/*/.gvfs" as well as others such as .cpan or .thumbnails or something else that don't exist on my system.

The only 3 that i see people suggesting that does exist on my system is...

> /home/.cache
/home/.local/share/Trash
and the lost+found

Everything else isn't hidden and isn't under home.

They are saying "exclude .cache and gvfs" but they are also saying "include /root.
On my system I have a /root/.cache/gvfs

And since I don't have any .gvfs (hidden) at all and no gvfs (not hidden) or .gvfs (hidden) under /home...
but I do see "gvfs" (not hidden) under other directories...I thought I would ask.

---

### Post by GhX6GZMB on 2022-03-10
> **wyattwhiteeagle said:**
> Yes the rdiff-backup and what I call a 3-tier strategy is for a "total 280% backup" since nothing is 100%
They are saying "exclude .cache and gvfs" but they are also saying "include /root.
On my system I have a /root/.cache/gvfs

Why on earth include /root ?
It's used by no one. It's there for historical reasons, because user "root" needed a home directory. But Ubuntu does not have a "root" user. It has someone with "sudo" rights.

---

### Post by SeijiSensei on 2022-03-10
I use rsync each night to backup local machines and three remote servers.  I use the --files-from and --exclude-from options to control what I backup.

In the inclusions file I have this list:
```

etc/
home/
var/log
var/spool
var/lib/pgsql/backups
usr/local

``` 

and the exclusions file has

```

proc/
sys/
run/
dev/

```
which are all transient and created by the kernel at boot.

A typical rsync command looks like this:
```
rsync -avr [source]:/  [backup_directory]  --files-from=/path/to/includes --exclude-from=/path/to/excludes
```

---

### Post by wyattwhiteeagle on 2022-03-10
I think what is happening is I'm seeing tips for different versions of Ubuntu and confusing myself when I see something different on my own system.

---

### Post by GhX6GZMB on 2022-03-10
> **wyattwhiteeagle said:**
> I think what is happening is I'm seeing tips for different versions of Ubuntu and confusing myself when I see something different on my own system.
I think it would be a very good idea to present your own system and your system expectations.
SeijiSensei now presents her/his server system, which may not be your situation...

---

### Post by CharlesA on 2022-03-10
> **ml9104 said:**
> Why on earth include /root ?
It's used by no one. It's there for historical reasons, because user "root" needed a home directory. But Ubuntu does not have a "root" user. It has someone with "sudo" rights.

If you need to get a root shell with ***sudo -i***, it'll drop you into /root by default. Regardless, you should still keep it around as there may be files stored there that you need.

For example, I have my cache files for borg there even through I run it via sudo.

> **ml9104 said:**
> I think it would be a very good idea to present your own system and your system expectations.
SeijiSensei now presents her/his server system, which may not be your situation...

I would use it as a base, as everything needs to be tailored to your specific system.

---

### Post by wyattwhiteeagle on 2022-03-10
> **ml9104 said:**
> I think it would be a very good idea to present your own system and your system expectations.
SeijiSensei now presents her/his server system, which may not be your situation...

Ok...I'm not exactly sure what is being asked but I will do my best.

I'm the only one who uses my laptop...nobody else.
I use my laptop for mostly basic stuff like viewing the monthly bills and the weekly grocery prices.

I'm used to not doing backups, but I'm tired of spending almost 2 whole days re-installing everything.

I use networking with my fiance's laptop.
Her's uses Windows 7.

Everytime I use Windows 7, it completely crashes within 24 hours, so I'm not getting any real use out of Windows 7.

I need Wine-staging due to an instant messaging 3d chat client (IMVU) which contain features that work only in wine-staging.
Those feature's won't work under any other wine branch.
They wont work under PlayOnLinux either.

I use the basic raster graphics editor, kolourpaint, for editing images to use in one of those features.

My pc is getting slower and slower...even with using stacer, bleachbit, and a basic package-management cleanup bash script.
I'm also experiencing web browser (google chrome) crashes, and some issue's where it seems like the whole system is confused about what I'm wanting it to do.

Confused like such...
When I'm working on a personal file in gedit, not a file for the pc though this happens with those too, my pc will like...freeze up.
If I haven't saved what I'm doing, I lose that completely.

Not sure if this actually presents my system and expectation's, but I hope it's a start.

---

### Post by TheFu on 2022-03-11
> **wyattwhiteeagle said:**
> I use a "3-tier strategy"

TimeShift
BackInTime
rdiff-backup

This seems painful and unnecessary.  timeshift and backintime are the same unless the file systems are btrfs. They both use hardlinking for backup-set versioning.  Lots of backup tool use this underlying method over the last 40 yrs.
If you use a backup solution that needs some other backup solution, doesn't that seem like the wrong tool?

Get one solution that works for all your backup/restore needs. Use that. Everything else is just complications and confusion.

If you are just testing 3 different tools, fantastic!  That's completely different.

There are no "golden" places to exclude.  It is a system-to-system choice. 
If you have 100PB of storage, you might want to backup everything.  
If you have only 100MB of storage for backups, then you'll probably only want to backup config files and nothing else. 
If you have 20 hrs a day to complete backups AND have tonnes of backup storage, get everything.  
If your backup window is 5 minutes per system and that includes pushing the local backups to a remote location over an encrypted channel, then you can't get everything daily.

Backups are always about trade-offs. Always.  Time, storage size, restore convenience, easy of use, security needs are just a few of the trade-offs. Each admin has to choose their own levels for each of those aspects.

Let's take log files.  Many people don't backup log files because they are constantly changing and haven't been too useful when the goal is to get a system back ASAP.  But, if you are a security person, you'll probably send your system logs to a different log-server and there they will be backed up religiously.  Without system logs, it is nearly impossible to track down how an attacker broke into your system(s) and what they did. If the logs are only on the same system as where they originated, then an attacker that gains root escalation, perhaps through a recent local bug ([https://arstechnica.com/information-technology/2022/03/linux-has-been-bitten-by-its-most-high-severity-vulnerability-in-years/](https://arstechnica.com/information-technology/2022/03/linux-has-been-bitten-by-its-most-high-severity-vulnerability-in-years/)), then they can clean up or purge all the log files before leaving the system to make tracing harder.

Trade-offs.  Always.

---

### Post by GhX6GZMB on 2022-03-11
> **TheFu said:**
> This seems painful and unnecessary.  timeshift and backintime are the same unless the file systems are btrfs. They both use hardlinking for backup-set versioning..

Exactly: the basis is the same.
But for people using GUIs, there's a big difference.
The user interfaces are optimized differently. The Timeshift user interface is targeted at system backups, whereas the Back In Time is for user file backups.
Now, you've made no secret of the fact that you don't like GUI applications, but that's the way it is.

You can configure both programs both ways, but it's a major pain, where you need to keep track of different configurations for the one or the other.
Using both is easy, and keeps the use cases separate.

---

### Post by wyattwhiteeagle on 2022-03-12
> **ml9104 said:**
> I think it would be a very good idea to present your own system and your system expectations.
SeijiSensei now presents her/his server system, which may not be your situation...

What exactly is meant by "presenting my system and expectation's"?

It seem's as if everyone just know's what they need to backup.

I'll be the first to say that if one is just completely clueless or "not fully knowledgable" about doing backups,
chances are that the learning curve is gonna be very steep
And the user is gonna go through time's when he/she feels that doing backup's is just a waste of time and effort.

And the terminology lingo...sometimes it seems that if the asker isn't "politically correct" in what is being asked...sometime's it feels like there's no help but is put into more confusion and so the asker never learns anyway.

---

### Post by GhX6GZMB on 2022-03-12
> **wyattwhiteeagle said:**
> What exactly is meant by "presenting my system and expectation's"?

Exactly what you replied. It's fine, and I understand your needs now. But you also have to understand that some people are running multiuser systems, which have other demands.

Backups are closely related to the way you work, there's no "one size fits all".

Let me tell you about my laptops (I only have laptops):
They all have at least two users: my sudo account and a guest account for friends/family/visitors (plus often other user accounts). And they all have at least two partitions: / and /home.

For my own account, I run Timeshift (system) and BackInTime ($HOME) as backup programs.
Why?
Well, the situations in which I do a system backup and those where I do a $HOME backup are completely different.

I do a system backup before I make modifications to my system (new installs, updates, configuration changes etc.). No reason to backup $HOME.

On the other hand, when I've done a lot of work on my personal documents/files, I backup $HOME.

This gives me the nice option of selectively restoring the parts that have been changed.

Additionally it lets me offer individual user backups to my other users by letting them use BackInTime freely (they have no business meddling with system backups).

Now, @TheFu seems to have the opinion of "Just backup the whole thing, gung-ho!"), which is fine if you have infinite storage space and time. I have neither.

_You_ have a single-user system with probably only one partition, which is a different situation.
Just use one or the other (Timeshift or BackInTime) and do full backups, and it's fine. Both work well. Select according to which user interface you like the best.

---

### Post by SeijiSensei on 2022-03-12
On any system I would back up /etc, /home, and /var/log. /etc contains all the confgurations for your machine, /home has all your stuff, and /var/log is useful when something goes wrong.

---

### Post by wyattwhiteeagle on 2022-03-12
> **SeijiSensei said:**
> On any system I would back up /etc, /home, and /var/log. /etc contains all the confgurations for your machine, /home has all your stuff, and /var/log is useful when something goes wrong.

I was just thinking about what to include and what to exclude.

/etc...
let's say...Thunderbird.
I don't use a mail client on my machine.
I keep that stuff at yahoo or gmail.
So I purge and block Thunderbird.

Does /etc keep track of that setting?
I want to include my custom settings.
Please don't shoot me down for asking.

---

### Post by TheFu on 2022-03-12
> **ml9104 said:**
> 
Now, @TheFu seems to have the opinion of "Just backup the whole thing, gung-ho!"), which is fine if you have infinite storage space and time. I have neither.

I've not suggested that here at any point I can remember.  Actually, I'm against that, just like I'm against using multiple half-tools for the same problem.

The OP knows what I backup, since he's tried using a simple script I posted. It is far from everything.

---

### Post by TheFu on 2022-03-12
If you want to know what's in /etc/ ... go and look. Just text files in there.

---

### Post by wyattwhiteeagle on 2022-03-12
> **TheFu said:**
> If you want to know what's in /etc/ ... go and look. Just text files in there.

Oh that's real helpful.

> **TheFu said:**
> I've not suggested that here at any point I can remember.  Actually, I'm against that, just like I'm against using multiple half-tools for the same problem.

The OP knows what I backup, since he's tried using a simple script I posted. It is far from everything.

There's a thread here on the forums where you specifically state that backing up /root, /home and /etc will get most things included in the backups.
Now, your saying it is far from everything...
hmmm...peculiar

The OP (me) know's only a portion of what you backup.
There is still some which you have NOT told for fear of passing on technical information about you or your system(s).
Or so it seem's.

Just look at the list of unanswered questions at my rdiff-backup script thread...
Those question's are way too specific to quickly find answer's with an internet search.
Seem's you are refusing to answer believing that failure is the best way to learn.

---

### Post by wyattwhiteeagle on 2022-03-12
> **SeijiSensei said:**
> On any system I would back up /etc, /home, and /var/log. /etc contains all the confgurations for your machine, /home has all your stuff, and /var/log is useful when something goes wrong.

I quoted this earlier asking a question about /etc
Anyway, thank you for that info...it is really helpful.
It put's me on the right track for actually learning.

> **ml9104 said:**
> Exactly what you replied. It's fine, and I understand your needs now. But you also have to understand that some people are running multiuser systems, which have other demands.

Backups are closely related to the way you work, there's no "one size fits all".

Let me tell you about my laptops (I only have laptops):
They all have at least two users: my sudo account and a guest account for friends/family/visitors (plus often other user accounts). And they all have at least two partitions: / and /home.

For my own account, I run Timeshift (system) and BackInTime ($HOME) as backup programs.
Why?
Well, the situations in which I do a system backup and those where I do a $HOME backup are completely different.

I do a system backup before I make modifications to my system (new installs, updates, configuration changes etc.). No reason to backup $HOME.

On the other hand, when I've done a lot of work on my personal documents/files, I backup $HOME.

This gives me the nice option of selectively restoring the parts that have been changed.

Additionally it lets me offer individual user backups to my other users by letting them use BackInTime freely (they have no business meddling with system backups).

Now, @TheFu seems to have the opinion of "Just backup the whole thing, gung-ho!"), which is fine if you have infinite storage space and time. I have neither.

_You_ have a single-user system with probably only one partition, which is a different situation.
Just use one or the other (Timeshift or BackInTime) and do full backups, and it's fine. Both work well. Select according to which user interface you like the best.

This is really helpful as well, Thank you so much.

---

### Post by TheFu on 2022-03-13
> **wyattwhiteeagle said:**
> Oh that's real helpful.

There's a thread here on the forums where you specifically state that backing up /root, /home and /etc will get most things included in the backups.
Now, your saying it is far from everything...
hmmm...peculiar


Failure **is** the best way to learn.  Try it. See what happens.  In 30 minutes, you'd know the answer.

Those are the entire list of directories that I backup, for the system that list was for. There isn't anything more, but it  is extremely system-dependent.  I have over 20 different systems. Each has slightly different backup directories, based on need.  I don't have any clue about your systems. That's your job to figure out.

When I started created my backup --include lists, I knew it would take practice.  I'd do the backup, then wipe the system and attempt a restore.  Something helpful would be missing from the backup, so I'd add that to the --include list and try again.  It tool a few times to get that correct. 

During those restore attempts, I also learned which extra data would be very helpful to have and started capturing that information and placing it somewhere that would be included in the backups. Some of the information contained sensitive stuff and I didn't want to drop it into an area that any user could see or that I might accidentally allow others to access. It gets placed in to the /root/backup/ directory.  That seemed as good a place as any.  /root/ is 700 permissions, so only the root account can access it - sensitive information will be safe. Also, it is typically nearly empty, so lots of extra crap wouldn't be inside it, just information I place there.  Backups have to run as root to capture owners, groups, permissions, ACLs and xattrs anyway, so --include /root will get it.  Nobody told me where to put it. It just seemed like the best place and would work across all systems, regardless of whether they have 1 or 1000 end-users.

When I say that I don't backup "everything", it appears you misunderstand.  Everything would be making a 100% clone of the disks. I don't do that.  I don't backup anything in /lib/ or /usr/ (except /usr/local/) or /dev/ for example.  If you take the list of --includes that I've clearly provided, anything NOT in that list doesn't get backed up.

As for the other thread.  It was clear to me that I'd helped all I could and my posts there were becoming negative-wisdom, so I unsubscribed. Sorry if you felt disregarded. I was frustrated too and needed to step back.

Might I suggest that you find a LUG (real or virtual) where many questions can be asked and explained quickly? A 5 minute conversation would clarify so many things. There are many, many, virtual LUGs around the world these days. They are there to help and the interactive method can really make a huge difference.

---

### Post by wyattwhiteeagle on 2022-03-14
> **TheFu said:**
> Failure **is** the best way to learn.  Try it. See what happens.  In 30 minutes, you'd know the answer.

Failure is NOT the best way to learn...
It doesn't teach anyone anything about why the failure is happening or how to prevent it from happening again.

I know...I have failed many times at several things and the only thing it taught me is that I aint good enough.

I refuse to believe that "failure is the best way to learn."

Now, if I was to "learn" from failure where rdiff-backup is concerned,
it would be only after I made sure the script is correct and testing the backups to see if they can restore good enough.
That is intentionally failing for learning purposes.
That's not exactly "failure" as you used it.

When I modified your basic script for my system...I thought I had everything correct.
As your script sit's in the thread where I found it, it has putting the apt-mark.manual in a directory that don't exist.
Then that directory is created.

I'm not sure if you are aware of the error's that came out of just that little issue in that script.
That's not failure. 
It let me know something in the script isn't correct.
It would still work...but ONLY AFTER the very first attempt at running the script.

The line "--exclude '**'" in the script...you said "read the rdiff-backup manual".
Guess what...--exclude is in that manual...but the '**' part is not.
And there isn't a simple explanation about it on the internet that I've found.
And I haven't found a guide or manual about perl scripting anywhere.

I'm just gonna stick with my chosen little GUI's and ugly-looking bash script's for now.

Don't worry though...rdiff-backup isn't going back onto my system.
That is unless I can find some guide or how-to that put's the scripting languages in "dummy" terms.

I haven't found one yet.
You and other people here are the closest I've seen.

---

### Post by CharlesA on 2022-03-14
> **wyattwhiteeagle said:**
> 
The line "--exclude '**'" in the script...you said "read the rdiff-backup manual".
Guess what...--exclude is in that manual...but the '**' part is not.
And there isn't a simple explanation about it on the internet that I've found.
And I haven't found a guide or manual about perl scripting anywhere.

The ** is related to Globbing, but it might by specific to whatever shell that script was written is. I haven't tried using ** myself, but this is what I found when I did a search for it.

[https://stackoverflow.com/questions/28176590/what-do-double-asterisk-wildcards-mean](https://stackoverflow.com/questions/28176590/what-do-double-asterisk-wildcards-mean)

> Don't worry though...rdiff-backup isn't going back onto my system.
That is unless I can find some guide or how-to that put's the scripting languages in "dummy" terms.

I haven't found one yet.
You and other people here are the closest I've seen.

Are you having a problem with a specific part of an rdiff-backup script? If so, post the chunk and maybe we can help.

FWIW, I have a really bad script that I was running to handle my rdiff-backups from 2016. It's pretty simple, however as rdiff only runs with these arguments:

```
/usr/bin/rdiff-backup --print-statistics --terminal-verbosity 5 --exclude /home/username/Steam /home/ /mnt/daily/rdiff
```

---

### Post by wyattwhiteeagle on 2022-03-14
> **CharlesA said:**
> The ** is related to Globbing, but it might by specific to whatever shell that script was written is. I haven't tried using ** myself, but this is what I found when I did a search for it.

[https://stackoverflow.com/questions/28176590/what-do-double-asterisk-wildcards-mean](https://stackoverflow.com/questions/28176590/what-do-double-asterisk-wildcards-mean)



Are you having a problem with a specific part of an rdiff-backup script? If so, post the chunk and maybe we can help.

FWIW, I have a really bad script that I was running to handle my rdiff-backups from 2016. It's pretty simple, however as rdiff only runs with these arguments:

```
/usr/bin/rdiff-backup --print-statistics --terminal-verbosity 5 --exclude /home/username/Steam /home/ /mnt/daily/rdiff
```

The problem isn't anything to do with the script itself as far as I can tell.
The most recent questions remain unanswered.
They are too specific to find an answer quickly on the internet...

One problem within the script itself has a very simple resolution.
It's with the list of "--exclude's".
Most of those items don't exist on my system as they appear in the script.
In the script, they are hidden...like the "/.gvfs"
The script say's, "--exclude-special-files"
It also say's, "--exclude **/.gvfs"
The one's on my system aren't hidden.

My system at the time had a /root/.cache/gvfs
It didn't have any /.gvfs

Now, considering the script say's, "--include /root" then say's "--exclude **/.cache" and "--exclude **/.gvfs"

The rdiff-backup manual implies the following...
Even though the script say's to exclude /.cache and /.gvfs...they would still be included because the script gives /root precedence.

I asked about the "special-files"...that didn't get a simple understandable answer either.
One would have to be able to know how TheFu thinks to be able to understand his answer.

Note: Some specific's within the script aren't correct as my hardware has changed.

> **wyattwhiteeagle said:**
> How do I copy the system information into /root/backups/?
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

### Post by TheFu on 2022-03-14
It appears an assumption that an example script 100% applies to your system has been made.  It does not.  Change it as makes sense for YOUR system(s).
I see a question about cpan.  If you don't use cpan, then you don't need that.  Use what makes sense. That's the overriding rule.
There's a question about all the gvfs. How many of those locations are even included in your backup areas?
```
/root/.cache/gvfs
/usr/lib/gvfs
/usr/share/gvfs
/run/user/1000/gvfs
/usr/lib/x86_64-linux-gnu/gvfs
/usr/share/doc/gvfs
```
Do you backup anything there?  I would only get /root/.  I don't want to imagine how a gvfs directory was created under /root/ ... doing something that we coach people NEVER to do, is my only guess.  but it is your system, so .... do what you think is best.  BTW, isn't the an exclude for **/.cache?  Seems that would prevent anything in the /root/.cache/ directory from inclusion ... so this is a non-issue. The manpage has detailed explanations about what the include/exclude stuff does and precedence. Refer to that for clarification.

What --exclude-special-files means is spelled out in the manpage, thusly:
```
       --exclude-special-files
              Exclude all device files, fifo files, socket files, and symbolic
              links.
```
If you don't understand, then research each term. Most will have clearly written wikipedia articles. 
The rdiff-backup team has a number of examples [http://rdiff-backup.nongnu.org/examples.html](http://rdiff-backup.nongnu.org/examples.html) but these will only be for the command, not the rest of the script.

And as with all Unix scripts, there are 500+ different ways to accomplish the same goal. Everyone has a different style and different knowledge of the scripting language used, so some of the techniques used aren't what everyone else would do. That's fine, if it works. We are all different.

Figure out what works for you and use it.  It has been months since the first thread was started.

---

### Post by wyattwhiteeagle on 2022-03-14
My knowledge of 'buntu is like 0.0001% compared to my knowledge of Windows.
I am learning, and it is NOT by failure.


> **TheFu said:**
> It appears an assumption that an example script 100% applies to your system has been made. It does not. Change it as makes sense for YOUR system(s).


I didn't assume the script would fit my system 100% perfectly.
I knew I would be modifying it to suit the needs of my system.


> **TheFu said:**
> I see a question about cpan. If you don't use cpan, then you don't need that. Use what makes sense. That's the overriding rule.


What is cpan? What is it used for? Why does it exist? Why is it in one place on one system but in a different place on another system?
See, I can honestly say I don't know if I need cpan or if I even use it.


PS. Please don't try to answer those. I'm not ready to learn the answer to those yet.


> **TheFu said:**
> There's a question about all the gvfs. How many of those locations are even included in your backup areas?
```
/root/.cache/gvfs
/usr/lib/gvfs
/usr/share/gvfs
/run/user/1000/gvfs
/usr/lib/x86_64-linux-gnu/gvfs
/usr/share/doc/gvfs
```
Do you backup anything there? I would only get /root/. I don't want to imagine how a gvfs directory was created under /root/ ... doing something that we coach people NEVER to do, is my only guess. but it is your system, so .... do what you think is best.


My TimeShift, I backup everything...and I do mean everything.
That doesn't mean it's gonna stay like that because you are correct, cloning the disk 100% is a bit pointless.


About the /root/.cache/gvfs...
I didn't even know there was a gvfs in /root...much less a /.cache.
I only noticed it by watching Bleachbit do it's work.
I know I didn't tell my system to create that directory.
I don't know if one of the packages on my system has that in one of their script's.
I honestly thought that Canonical had that in their installer media.


> **TheFu said:**
> BTW, isn't the an exclude for **/.cache? Seems that would prevent anything in the /root/.cache/ directory from inclusion ... so this is a non-issue. The manpage has detailed explanations about what the include/exclude stuff does and precedence. Refer to that for clarification.


There is an exclude for **/.cache.
Remember, you said the order in the script matter's...I'll put it all on one line for better reader clarity...


```
[tool=rdiff-backup][--exclude-special-files][--include /root][--exclude **/.cache][Exclude '**']
```


Now, please understand that I'm going solely on what the rdiff-backup manpage say's.
I haven't looked in the backup's to see if /root/.cache is there or not.


Let's see what the manpage say's, shall we...


> 
For instance,


              rdiff-backup --include /usr --exclude /usr /usr /backup


       is exactly the same as


              rdiff-backup /usr /backup


       because  the  include  and  exclude  directives  match exactly the same
       files, and the --include comes first, giving it precedence.
       
According to what the manpage says, the --include /root has precedence over --exclude **/.cache.


Unless there's something about the wildcard asterisks that over-rules the precedence. It would seem that rdiff-backup wouldn't allow the over-rule.


> **TheFu said:**
> What --exclude-special-files means is spelled out in the manpage, thusly:
```
       --exclude-special-files
              Exclude all device files, fifo files, socket files, and symbolic
              links.
```
If you don't understand, then research each term. Most will have clearly written wikipedia articles.
The rdiff-backup team has a number of examples [http://rdiff-backup.nongnu.org/examples.html](http://rdiff-backup.nongnu.org/examples.html) but these will only be for the command, not the rest of the script.


Yeah, after I asked that about the --exclude-special-files...I went looking in the manpage about it.

You gotta understand...there's times it takes up to years...years...just for someone here on the forums to respond.
And that's if the asker is lucky that someone respond's.
There are questions I asked back when I was on 14.04 LTS that still have no replies.
That's at least 6-8 years ago.
Imagine it...6-8 years and still no response.

So, I posted the question then I went to go read with the hopes of finding something.


> **TheFu said:**
> And as with all Unix scripts, there are 500+ different ways to accomplish the same goal. Everyone has a different style and different knowledge of the scripting language used, so some of the techniques used aren't what everyone else would do. That's fine, if it works. We are all different.


Figure out what works for you and use it.


Thank you


> **TheFu said:**
> It has been months since the first thread was started.


Months...lol...you seem like you been on here for at least 20 to 40 years.;)

---

### Post by TheFu on 2022-03-15
If you don't like the order of the include/excludes then ... er .... CHANGE THEM!  This is your script. You set the precedence. You're smart.  Didn't I  provide a hint that --excludes, except the last --exclude '**' should all come first in that other thread.  Perhaps it was a "whooosh" hint?

Old Threads ... 
I don't look at any threads over a few days old, unless I'm subscribed for some reason and forgot to unsubscribe.  I'd love it if there were a button to unsubscribe to every thread over 30 or 60 or 90 days old, since any that are that old seem to be where spam shows up.  When I get frustrated, I unsubscribe quietly if I'm not the primary person answering.  If I am and get frustrated, I'll usually say something like "I give up" or "good luck."

I think the forum admins close threads over 6 months old when the first spammy post ends up in the thread.  I suspect the old threads were all closed. Plus 14.04 is EOL.

When looking at which posts I may respond to, I look at the title, how many replies it already has, which subforum it is located and decide if it of interest to me. I tend to avoid GUI questions, unless it is about remote GUIs.  When I don't get along with the other person in a thread or I get frustrated, sometimes those usernames get added to my ignore list.  Life it too short.  It isn't like anyone here is being paid.

I have strong opinions about certain things. That's usually after I've does significant research and found other options to be less good. I try to save other people time when I can, but it doesn't always work.  Sigh.  15 yrs ago, I tried to get the world to migrate to Linux. This was after I'd been running it on servers for over a decade. It was clear to me that 90% of the needs for all computing were handled by Linux at the enterprise level. 5% needed huge UNIX servers with hundreds of CPUs and 5% needed MS-Windows.  As you can tell, I wasn't successful, but it took years for me to finally figure out and can point people at the water hole, but they have to choose to walk over and drink.  The same applies to most software, but with software, there are usually very good reasons why someone would choose a different solution.

You might not believe this, but when I was learning Linux and Unix in the early 1990s, I got very frustrated that there weren't GUIs for everything. Don't tell anyone here that.  ;)

---

### Post by wyattwhiteeagle on 2022-03-15
> **TheFu said:**
> If you don't like the order of the include/excludes then ... er .... CHANGE THEM!  This is your script. You set the precedence. You're smart.  Didn't I  provide a hint that --excludes, except the last --exclude '**' should all come first in that other thread.  Perhaps it was a "whooosh" hint?

...

I think the forum admins close threads over 6 months old when the first spammy post ends up in the thread.  I suspect the old threads were all closed. Plus 14.04 is EOL...

Three nights ago, I was looking at the script intensively and thought...
"TheFu said that for a script to be efficient enough, all exclude's must be before any includes except the last exclude at the very end."
That's when I realized how simple of a problem it was that I was having with the script.

About 14.04...I wasn't meaning specifically you that failed to answer 6-8 years ago.
I was pointing out that while I waited for a response, it might take that long for someone to respond and by that time...I will either have found my answer or the question won't matter any more.

What system informations need to be copied into /root/backups/?
Are the "root-userid-only" scripts on the system by default or are they "user-created" scripts?

---

