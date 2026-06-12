---
title: "How do I create a back that allows me to retain my desktop and settings"
date: 2021-02-16
forum: General Help
---

### Post by Jonners59 on 2021-02-16
> **oldfred said:**
> Go back & review post #43, If then there is something you do not  understand, may be better to start new post with backup in title.
Something I have wanted to do for an age having every now and then had the need to rebuild a machine.  More at the start than now.  However it has just happened and now live in eternal fear of it happening again and I waste weeks trying to restore and recreate a whole PC from memory, or should I say not.

I am no programmer, but I think I need to back up configs and settings files such as:
fstab
smb
desktop
panels
repositories
trusted sources
usernames and passwords/online accounts
printers and scanners
shortcuts/bookmarked locations
photos for backgrounds and launchers.
any scripts

I think I may need to back up /home

there may be more

I also think that they should be duplicates of the original, updated as the original is used or changed or updated at boot, namely the config and settings files.

FOr the machine I am interested in for now:

```
$ df -h
df: /run/user/1000/doc: Operation not permitted
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           3.2G  4.0M  3.2G   1% /run
/dev/sda2        51G   26G   23G  53% /
tmpfs            16G     0   16G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           4.0M     0  4.0M   0% /sys/fs/cgroup
/dev/sdb2       192G  339M  182G   1% /media/Administration
/dev/sdb1       724G  280M  687G   1% /media/MultiMedia
/dev/sda4       834G   23G  769G   3% /home
/dev/sda1       511M   12M  500M   3% /boot/efi
tmpfs           3.2G  156K  3.2G   1% /run/user/1000



```


```
 sudo du -hx --max-depth=1 / 2> /dev/null

4.5G    /var
16K    /lost+found
144K    /tmp
4.0K    /mnt
178M    /boot
30M    /etc
12K    /srv
68K    /snap
189M    /opt
12K    /media
4.0K    /cdrom
21G    /usr
7.7M    /root
26G    /



```

---

### Post by The Cog on 2021-02-16
The vast majority of that list is your personal settings, stored inside your home folder. Backing up /home will capture that. That's what I do.
Actually, I use a separate home partition so I can reinstall or upgrade the OS without even having to restore /home.

The things that jump out at me as not being stored in /home are system settings: fstab, printers, wifi, perhaps smb. You could perhaps script making copies of those settings somewhere in /home to preserve them. Or just fix up manually after an install. Beware restoring fstab: a new install will have a new UUID and putting the old entry back will stop it from booting.

Actually, I use an ansible playbook to fix up the system settings after an install - configure ssh, wireguard vpn, firewall etc. So for me, it's:
- install system from usb
- check it works ok
- manually add my /home partition to fstab and reboot
- run a script that installs ansible then runs the playbook

P.S.
Just a bash script would do instead of ansible. I used ansible because I'm already familiar with it.

---

### Post by TheFu on 2021-02-16
[https://ubuntuforums.org/~#post13928432](https://ubuntuforums.org/~#post13928432) has a script. You should customize it slightly, if that is what you use.

>  I think I may need to back up /home
That is an understatement.  HOME is where each user's settings, files, configs are kept.  If nothing else, get the HOME directories for each userid (human) on the system.   
Probably want to get /etc/ as well. It is tiny.  Don't restore /etc/, but have it for reference.
If you put data somewhere else, back that up too.  
If you manually install programs, those belong in /usr/local/ .... get that too.
If you manually install snap packages, a list of those is sufficient, probably.  **snap list > ~/list-o-snaps**
If you manually install flatpak packages, a list of those is sufficient, probably.  **flatpak list > ~/list-o-flatpak**
I like to have a list of manually installed APT packages.  **apt-mark showmanual >  ~/list-o-apt-pkgs**

With those lists, we can feed the text into each installation tool after restoring to a new system. Text is tiny and compresses well. Be certain your list-o ... files get placed somewhere that gets backed up.  My backups run as root for many reasons. That means I need to include /root/ in my backup directories to get those list-o.... files.  Easy. Fine.

There are hundreds of forum threads here about backups and at least 50 about restores.  Go do some reading. Decide what method has the best trade-off for you needs.

---

### Post by Jonners59 on 2021-02-18
Gentlemen
Firstly apologies for the tardy reply.  I am drowning in repairs/projects and none seem to want to get fixed so they keep increasing I am THE Ouslumbird!

Let me take each one of these points at a time.

1.  
1.1 > **The Cog said:**
> The vast majority of that list is your personal  settings, stored inside your home folder. Backing up /home will capture  that. That's what I do.
Actually, I use a separate home partition so I can reinstall or upgrade the OS without even having to restore /home.

Now, THIS is interesting.  I think I mentioned I used to have a separate HOME, USR and ETC, but when restoring from USB because something went wrong or whatever, it never offered me the option to use them.  It seemed to either start from scratch or override them.  Are you saying that actually, I was wrong and if I had selected / for / directory and say /Home for /Home it would NOT have overridden the directory but simply used it?????  If so, then I am a ****!  Though would be nice for the install to say so.

1.2 > **The Cog said:**
>  The things that jump out at me as not being stored in /home are system  settings: fstab, printers, wifi, perhaps smb. You could perhaps script  making copies of those settings somewhere in /home to preserve them. Or  just fix up manually after an install. Beware restoring fstab: a new  install will have a new UUID and putting the old entry back will stop it  from booting.

Yes, learned to be very careful with fstab!!!  One fun one is an external drive in the housing I have.  It would shut down after a rebuild or power drop and when I rebooted it wouldn't be turned on.  Of course that meant the PC wouldn't boot up!

So I think the key directories are /Home, and bits of /etc...

1.3  > **The Cog said:**
>  
Actually, I use an ansible playbook to fix up the system settings after  an install - configure ssh, wireguard vpn, firewall etc. So for me,  it's:
- install system from usb
- check it works ok
- manually add my /home partition to fstab and reboot
- run a script that installs ansible then runs the playbook

P.S.
Just a bash script would do instead of ansible. I used ansible because I'm already familiar with it.

A script or app would be great.  I tried the Backup app in Store but it doesn't seem to work very well.  Often fails without access.  Could you, please tell me more about ansible and playbook....


2. 
2.1  > **TheFu said:**
> [https://ubuntuforums.org/~#post13928432](https://ubuntuforums.org/~#post13928432) has a script. You should customize it slightly, if that is what you use.

Just tried that and the link didn't work 404

2.2 > **TheFu said:**
> 
That is an understatement.  HOME is where each user's settings, files,  configs are kept.  If nothing else, get the HOME directories for each  userid (human) on the system.   
Probably want to get /etc/ as well. It is tiny.  Don't restore /etc/, but have it for reference.
If you put data somewhere else, back that up too.  
If you manually install programs, those belong in /usr/local/ .... get that too.

OK, but /etc surely only need a selection of config files, no?

2.3  > **TheFu said:**
> 
If you manually install snap packages, a list of those is sufficient, probably.  **snap list > ~/list-o-snaps**
If you manually install flatpak packages, a list of those is sufficient, probably.  **flatpak list > ~/list-o-flatpak**
I like to have a list of manually installed APT packages.  **apt-mark showmanual >  ~/list-o-apt-pkgs**

Being lists, that implies that a backup or extract needs to be done before work begins and that assumes it is being planned, not due to a failure?  Can a live copy be made.  I was wondering if there was a way that a copy could be placed in a backup location and it is maintained as a copy?

2.4  > **TheFu said:**
> 
With those lists, we can feed the text into each installation tool after  restoring to a new system. Text is tiny and compresses well. Be certain  your list-o ... files get placed somewhere that gets backed up.  My  backups run as root for many reasons. That means I need to include  /root/ in my backup directories to get those list-o.... files.  Easy.  Fine.

Noted.

2.5  > **TheFu said:**
> 
There are hundreds of forum threads here about backups and at least 50  about restores.  Go do some reading. Decide what method has the best  trade-off for you needs.

Yup that is part of the problem too much and too messy.

---

### Post by TheFu on 2021-02-18
> Yup that is part of the problem too much and too messy. 
Sorry that data isn't organized for your specific needs. It is there for many different considerations, many you may not have known previously.

> [https://ubuntuforums.org/~#post13928432](https://ubuntuforums.org/~#post13928432) has a script. You should customize it slightly, if that is what you use.
The link should be: [https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432)
Sorry. I recently changed to using vimwiki and it shortens links from view.

BTW, /Home/ isn't useful.  You probably want /home/.  Case matters. I added a trailing / so we know it is a directory, not a file.  
**ls -F** does this too.
When I say "HOME" (all CAPS), I mean the environment variable that gets set at login for each different userid.  
```
echo $HOME
```
will show the current value for the userid currently used. Almost every end-user GUI program cares greatly about the HOME variable.

Getting only specific files in /etc/ for something that changes every month and you'll need once every few years is a bunch of work.  I'm lazy.  Get everything and only spend the time sorting it later, if needed.  Having everything from /etc/ isn't bad and takes very little storage. Not having it is much more hassle - but completely dependent on how much system config customization you might do.  Sure, you could put a comment into each file under /etc/ that you manually modify, then search for those and only back those up.  Unless you forget, just once, to put that comment/tag into a file.  Then you won't have it.

---

### Post by Jonners59 on 2021-02-18
> **TheFu said:**
> Sorry that data isn't organized for your specific needs. It is there for many different considerations, many you may not have known previously.

If there is too much to go through then people get frustrated and confused and either walk away or ask for help in a blog.  Anyway, it is what it is.

> **TheFu said:**
> 
The link should be: [https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432)
Sorry. I recently changed to using vimwiki and it shortens links from view.

No probs.  Sort of looks fine.  I am not smart enough to understand exactly what is being said, but let me 1st understand what needs saving and how.



> **TheFu said:**
> 
BTW, /Home/ isn't useful.  You probably want /home/.  Case matters. I  added a trailing / so we know it is a directory, not a file.  
**ls -F** does this too.
When I say "HOME" (all CAPS), I mean the environment variable that gets set at login for each different userid.  
```
echo $HOME
```
will show the current value for the userid currently used. Almost every  end-user GUI program cares greatly about the HOME variable.

Noted...


> **TheFu said:**
> 
Getting only specific files in /etc/ for something that changes every  month and you'll need once every few years is a bunch of work.  I'm  lazy.  Get everything and only spend the time sorting it later, if  needed.  Having everything from /etc/ isn't bad and takes very little  storage. Not having it is much more hassle - but completely dependent on  how much system config customization you might do.  Sure, you could put  a comment into each file under /etc/ that you manually modify, then  search for those and only back those up.  Unless you forget, just once,  to put that comment/tag into a file.  Then you won't have it.

I think most of us are lazy...  I think there are actually only a handful of config files any way that makes up the look and layout etc, and repositories that one would keep.  Hence where I was coming from.  If just those are backed up that's all that is needed and restoring just copy them over to replace the newly installed, but I get your point that /etc/ is small, and /usr/local/ too.  So it looks like I should have separate /home/, /etc/ and /usr/ directories and change fstab to point at them on startup.  I should crate (if I have read you correctly) a /backup/ mounting on a 2nd directory to which I back up /home/, /etc/ and /usr/ on a daily basis.

Then if all goes wrong I rebuild my machine and restore /home/ and /usr/ back (if needed) and look for the config files for things like SAMBA, fstab (ensuring correct new entries for UUIDs), etc... ????

---

### Post by TheFu on 2021-02-18
**/usr/local/**, not /usr/.
I wouldn't keep backups on they same system or the same storage, but do what you can.

Lazy is good.  Automate what make sense, but no more.
> 
Then if all goes wrong I rebuild my machine and restore /home/ and /usr/ back (if needed) and look for the config files for things like SAMBA, fstab (ensuring correct new entries for UUIDs), etc... ???? 
Yes.  Not /usr/, just /usr/local/.

---

### Post by GhX6GZMB on 2021-02-18
**How do I create a back that allows me to retain my desktop and settings?**

Personally I use Timeshift, which will recreate your system after a total crash and reinstallation, but will _not_ restore your documents under /home. That's a different task.

My PC has two users, and using these settings, a full system restore is possible, including the desktop:

---

### Post by Jonners59 on 2021-02-19
> **TheFu said:**
> **/usr/local/**, not /usr/.
I wouldn't keep backups on they same system or the same storage, but do what you can.

Lazy is good.  Automate what make sense, but no more.

Yes.  Not /usr/, just /usr/local/.

Cheers and noted - PS  not getting any notifications of messages.  Sorry.

---

### Post by Jonners59 on 2021-02-19
> **ml9104 said:**
> **How do I create a back that allows me to retain my desktop and settings?**

Personally I use Timeshift, which will recreate your system after a total crash and reinstallation, but will _not_ restore your documents under /home. That's a different task.

My PC has two users, and using these settings, a full system restore is possible, including the desktop:

Interesting.  I used LuckyBackup and just found it again.  So, giving that a go.  It has loads of options, directory level and file type all include or exclude.  Has a schedule, a dry run too.

---

### Post by TheFu on 2021-02-19
> **Jonners59 said:**
> Interesting.  I used LuckyBackup and just found it again.  So, giving that a go.  It has loads of options, directory level and file type all include or exclude.  Has a schedule, a dry run too.

All backup tools have this stuff.  Scheduling on all Unix system is done using the crontab. You don't need a GUI.  Almost all Unix backup tools have librsync at the core. Nearly all work the same way, so it isn't all that important which tool get used.   rsnapshot, rbackup, LuckyBackup, Back-In-Time all use basically the same methods. It may not be important today, but not all provide support for sparse files, ACLs, and xattrs.  If you need that metadata included in your backups, then you really need it. If you use virtual machines, it is very possible that sparse file support is extremely important to you, regardless of whether you know it or not.

There are a few that work different, however.  

duplicity (and about 4 other tools based on it) work more like the 1970s method.  deja-dup, duplicati, and a few others use duplicity as the back end.
There are some that tried to use the git method. If you have no huge binary files, this is fine. git doesn't like binary files too much.  
There are some that use deduplication (or claim to) by creating sha1 or sha256 checksums for blocks. The math says there won't be collisions. But I'm skeptical, since using 256-bits to represent 4K of data is asking a little more than I'm willing to believe.  Some of these deduplication tools have some impressive speeds after the first run.

A few tools are designed only for 1 type of backup - say - just the OS, but not for files that change all the time.  That means we need to have 2 different backup tools, since the files that change all the time are probably OUR DATA, which is much more important to most people than the OS.  After all, reinstalling Ubuntu is only 10-15 minutes, so why bother backing up the OS at all?

---

### Post by Jonners59 on 2021-02-19
> **TheFu said:**
> All backup tools have this stuff.  Scheduling on all Unix system is done using the crontab. You don't need a GUI.  Almost all Unix backup tools have librsync at the core. Nearly all work the same way, so it isn't all that important which tool get used.   rsnapshot, rbackup, LuckyBackup, Back-In-Time all use basically the same methods. It may not be important today, but not all provide support for sparse files, ACLs, and xattrs.  If you need that metadata included in your backups, then you really need it. If you use virtual machines, it is very possible that sparse file support is extremely important to you, regardless of whether you know it or not.

There are a few that work different, however.  

duplicity (and about 4 other tools based on it) work more like the 1970s method.  deja-dup, duplicati, and a few others use duplicity as the back end.
There are some that tried to use the git method. If you have no huge binary files, this is fine. git doesn't like binary files too much.  
There are some that use deduplication (or claim to) by creating sha1 or sha256 checksums for blocks. The math says there won't be collisions. But I'm skeptical, since using 256-bits to represent 4K of data is asking a little more than I'm willing to believe.  Some of these deduplication tools have some impressive speeds after the first run.

Interesting, but another league to me. 

> **TheFu said:**
> 
A few tools are designed only for 1 type of backup - say - just the OS,  but not for files that change all the time.  That means we need to have 2  different backup tools, since the files that change all the time are  probably OUR DATA, which is much more important to most people than the  OS.  After all, reinstalling Ubuntu is only 10-15 minutes, so why bother  backing up the OS at all?

For me, the data and the setup are the most important.  Data is obviouse, but getting everything set up the way I like it can take weeks so that is why I am keen on backing up that too.  Almost true on the OS.  The last one took 3 weeks to work before I was able to start trying to set things up the way I like it.  Could not get the GRUB to install and sometimes the OS, so many, many retries...  Long story.  This is why the sudden panic, as I do NOT want to go through that again.  I have different machines and so backing up is different constantly on with an attached HD where ALL our documents and pics etc are kept.  It also runs a virtual machine running Debian and 3CX IPT switch.  That one is scary, but the 3CX itself never really changes from a config perspective.  So one copy does for all and it has a backup tool built into the switch.  The OS doesn't and does not install as per the instructions.  Took me quite a bit to figure it out over some time before it would work, so defiantly needs a backup, and then there is the host and the data...  So she's a bad'en.

Any others it is just to restore the settings and layout of the PC/Laptop and to protect the data that I normally store separately on a different HD or partition... 

So do you think Lucky Backup will do it for me?  When I look at it and set it up with my simplistic naive eyes it seems to, but I may be wrong.  I bow down to your better knowledge - hence the blog.

---

### Post by TheFu on 2021-02-19
Restoring backups: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

This assumes you begin with a fresh install.  What needs to be restored also needs to be in the backups.  I also backup some configuration settings to deal with disk failures, like corrupted partition tables.  Those wouldn't be used in a full OS restore, but if both copies of a GPT get corrupted and I don't think the data has been touched, it is handy to just force the partition layout over the existing stuff (useless without out and the data is already unusable). Sometimes that is really handy and the data takes less than 512 bytes almost always. Why not have that data as part of your backups just-in-case?

Restores that take over 45 minutes that are less than 100G of data aren't doing it very efficiently, if you ask me.

I've never used Lucky Backup. I have used **Back-In-Time**, **rsync**, **rsnapshot** and currently use **rdiff-backup**.  I've tried to use about 10 other tools and found them lacking in some way or they just didn't work.  

On paper, **duplicity** is the ideal backup tool. It lists features that map to the best practices for backups.  In practice, I couldn't get it to work.  I tried a few GUIs based on it and they were crazy slow - like over 8 hrs before I killed them and gave up.  rdiff-backup took 45 min for the same data for the first run.  Every run after that is 1-8 minutes - mostly depending on how many files are involved, not how much data actually has been changed.  rsync was taking 2+ hrs due to some very large files in my backups.  rsync doesn't handle huge files very well.

Whatever tool you choose, just be certain you understand how it fails.  Backups aren't the end-goal.  It is all about the restore.  Everyone talks about backup, backup, backup ... but backups that can't be restored are useless.

Until you've actually tested the restore, you don't actually know that it works.  When I first switched away from backing up everything, it took about 5 attempts before I'd solved all the chicken/egg problems.  That was about a decade ago.  About once a year, I've needed to restore a system using my backups.  As with most things, practice makes perfect.  The more you practice, the better you become.

Nobody can tell you exactly what to backup, since your system isn't the same as ours.  Typical desktop users really only need their HOME, /etc/ and a list of manually installed packages (for the packaging systems they use). That's the minimal with lots and lots of assumptions.  If you install snap packages, there is more needed. If you install a website or web-app, there are more.  If you modify firewalls manually, but use the firewall tools for that, there is more.  It all depends.  

So, on desktops, I tend to use ufw.  If you setup ufw using ther CLI interface, those rules are not stored in /etc/.  They are stored somewhere else.  That sucks, but I understand why.  So - if you want your firewall rules restored, then you'll either:
[LIST]
[*]need to put those rules into /etc/ somewhere, or
[*]need to backup some other location(s) to capture the CLI entries for ufw.
[/LIST]
I decided to put the rules in /etc/, but that puts the problem on me to remember that any CLI ufw command also means I need to ensure the rules get migrated.

On some of my servers, I use **ipset** to block thousands of bad subnets in the world. ipset can be used to have 1 rule with 200K subnets. It makes the kernel firewall rules fast, since it creates an optimized hash table for blazing lookups.  End-users would never use ipset.  But after about 150 ufw rules, a server admin would quickly learn that ufw is very slow both on the reboot firewall setup and in performing rule matches.  There is no automatic place for ipset configs. Everything is up to the admin to organize. I decided that /etc/ was the place for my ipset rules and my backups were already getting everything there, so it was handled already.

Some end users like to play around with GUI themes.  While those can be located in their HOME, it seems from my reading that themes also get placed under /usr/share/themes/ too.  If you do that, then you'll place files and modify files in that directory structure.  Maybe you want to include it in your backups?  But if you don't touch themes, it would be a complete waste of effort. A fresh install would put them back.

Anyway - only you can decide what needs to be in your backups.

---

### Post by Jonners59 on 2021-02-20
> **TheFu said:**
> Restoring backups: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

This assumes you begin with a fresh install.  What needs to be restored also needs to be in the backups.  I also backup some configuration settings to deal with disk failures, like corrupted partition tables.  Those wouldn't be used in a full OS restore, but if both copies of a GPT get corrupted and I don't think the data has been touched, it is handy to just force the partition layout over the existing stuff (useless without out and the data is already unusable). Sometimes that is really handy and the data takes less than 512 bytes almost always. Why not have that data as part of your backups just-in-case?

Restores that take over 45 minutes that are less than 100G of data aren't doing it very efficiently, if you ask me.

I've never used Lucky Backup. I have used **Back-In-Time**, **rsync**, **rsnapshot** and currently use **rdiff-backup**.  I've tried to use about 10 other tools and found them lacking in some way or they just didn't work.  

On paper, **duplicity** is the ideal backup tool. It lists features that map to the best practices for backups.  In practice, I couldn't get it to work.  I tried a few GUIs based on it and they were crazy slow - like over 8 hrs before I killed them and gave up.  rdiff-backup took 45 min for the same data for the first run.  Every run after that is 1-8 minutes - mostly depending on how many files are involved, not how much data actually has been changed.  rsync was taking 2+ hrs due to some very large files in my backups.  rsync doesn't handle huge files very well.

Whatever tool you choose, just be certain you understand how it fails.  Backups aren't the end-goal.  It is all about the restore.  Everyone talks about backup, backup, backup ... but backups that can't be restored are useless.

Until you've actually tested the restore, you don't actually know that it works.  When I first switched away from backing up everything, it took about 5 attempts before I'd solved all the chicken/egg problems.  That was about a decade ago.  About once a year, I've needed to restore a system using my backups.  As with most things, practice makes perfect.  The more you practice, the better you become.

Nobody can tell you exactly what to backup, since your system isn't the same as ours.  Typical desktop users really only need their HOME, /etc/ and a list of manually installed packages (for the packaging systems they use). That's the minimal with lots and lots of assumptions.  If you install snap packages, there is more needed. If you install a website or web-app, there are more.  If you modify firewalls manually, but use the firewall tools for that, there is more.  It all depends.  

So, on desktops, I tend to use ufw.  If you setup ufw using ther CLI interface, those rules are not stored in /etc/.  They are stored somewhere else.  That sucks, but I understand why.  So - if you want your firewall rules restored, then you'll either:
[LIST]
[*]need to put those rules into /etc/ somewhere, or 
[*]need to backup some other location(s) to capture the CLI entries for ufw. 
[/LIST]
I decided to put the rules in /etc/, but that puts the problem on me to remember that any CLI ufw command also means I need to ensure the rules get migrated.

On some of my servers, I use **ipset** to block thousands of bad subnets in the world. ipset can be used to have 1 rule with 200K subnets. It makes the kernel firewall rules fast, since it creates an optimized hash table for blazing lookups.  End-users would never use ipset.  But after about 150 ufw rules, a server admin would quickly learn that ufw is very slow both on the reboot firewall setup and in performing rule matches.  There is no automatic place for ipset configs. Everything is up to the admin to organize. I decided that /etc/ was the place for my ipset rules and my backups were already getting everything there, so it was handled already.

Some end users like to play around with GUI themes.  While those can be located in their HOME, it seems from my reading that themes also get placed under /usr/share/themes/ too.  If you do that, then you'll place files and modify files in that directory structure.  Maybe you want to include it in your backups?  But if you don't touch themes, it would be a complete waste of effort. A fresh install would put them back.

Anyway - only you can decide what needs to be in your backups.
Cheers, M8.  That is a lot to digest.  I will see how I get on with LuckyBackup then.  It seems to be pretty good and easy to configure for novices like me.  I'd be interested in your views of it if you do get a chance to review it.

---

### Post by dragonfly41 on 2021-02-21
From the nuggets of valuable experience from @TheFu and others in this thread I am drawing together an automation workflow to follow to restore a desktop from a current mangled (but working) desktop.

One thought I have is that instead of restoring by installing a fresh Ubuntu, and then installing an array of applications to get back to original desktop, could I save time by using Cubic to pre-install applications into a custom ISO?

Then as each application is installed the same process can be mirrored in Cubic.

The only problem is that I cannot get Cubic to run in my mangled desktop. I get a python error, 
```
[FONT=monospace][COLOR=#000000]module 'logger' has no attribute 'log_title'
```[/COLOR]

[/FONT]

---

