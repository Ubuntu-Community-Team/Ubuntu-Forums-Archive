---
title: "Why is my rdiff-backup script failing"
date: 2024-03-16
forum: General Help
---

### Post by coley9225 on 2024-03-16
Hello again everyone,
I'm working on a script for rdiff-backup. I want to save my backup to a server, but something isn't going quite right.

This is the error I get when I run the script:
```
charles:$:sudo ./rdiff_root.sh[sudo] password for charles: 
Fatal Error: Unable to create directory coley:/home/rdiff/laptop_system 
```

That directory already exists, and is owned by me. This from my server:
```
charles@coleys-server:/home/rdiff$ lltotal 28
drwxr-xr-x 4 charles charles  4096 Mar 16 15:04 ./
drwxr-xr-x 7 root    root     4096 Sep 12  2023 ../
drwxrwxr-x 2 charles charles  4096 Mar 16 13:53 laptop_system/
drwx------ 2 root    root    16384 Sep  1  2023 lost+found/
charles@coleys-server:/home/rdiff$ 
```

And finally, a snippet from my script:


```
# Define source and destination directoriesSOURCE="/"
DESTINATION="coley:/home/rdiff/laptop_system"


rdiff-backup $EXCLUDE_OPTIONS $SOURCE $DESTINATION
```

I know this is going to be something simple, but I just can't put my finger on it and it's driving my bonkers.

Any insight, as always, would be must appreciated.

---

### Post by TheFu on 2024-03-16
If you are backing up using sudo on the source, then you need to be using root on the target system, or better, a root-equivalent userid.  If not, you may get pure data, but you won't get owner, group, permissions, ACLs or xattrs in the backups. Those are absolutely critical.

Also, you probably need to restrict the types of things included in the backups.  rdiff-backup as a few --exclude-xyz options that are very useful.  Unfortunately, --exclude-special-files isn't what you need. I think there are 3 options that need to be excluded, so if a named pipe or fifo or some special device gets picked up in the source files, the backup won't puke.

If it were me, I wouldn't try to backup to a target under /home/. There are many reasons why that is a bad idea. I bet you can think of 5 yourself with very little effort.

---

### Post by coley9225 on 2024-03-17
thefu,

Thanks for the reply, sorry for the delay. I saw your post this morning, and after some research,(hence the delay), I have taken the following step.

On my server, I created a new user "joe",not the real user I used, for security. I assigned uid 0 and group 34, edit sshd_config to allow root login and tested. I do, in fact, get logged in with root prompt. So far it's going well.

Next steps:
  change mount point to /mnt/rdiff/laptop_system
  modify rdiff-backup script to use joe
  setup passwordless login for joe and disable password login for better security.
    Side not; this is all practice, the 'server' is an older dell desktop beside my desk, no access from outside lan, but intend to get off site server at some point and need the security practice.

My next question, Should I generate a new ssh key for this, will is current one suffice? If I generate a new one, can I give it a name or something to enable me to know which is which?

You also mentioned excluding some dir/files. I'm supplying the full script, showing what I have excluded, and welcome recommendations. After I get the basic script working, I follow the advice you've in the past, e.g. delete older than x days, and apt-mark shown manual, etc.
The folks here on the forums have always been very helpful, and it greatly appreciated.

This is the script as it stands at this point.
```
#! /bin/bash

# Backup script to backup root partition using rdiff-backup. Got a basic example scrit using chatgpt.


# Define source and destination directories
SOURCE="/"
DESTINATION="joe:/home/rdiff/laptop_system"


# Exclude list
EXCLUDE=(
    "/proc"
    "/sys"
    "/dev"
    "/tmp"
    "/var/tmp"
    "/var/cache/apt/archives"
    "/var/log"
    "/var/spool"
    "/run"
    "/home/"
)


# Construct exclude options
EXCLUDE_OPTIONS=""
for exclude_dir in "${EXCLUDE[@]}"; do
    EXCLUDE_OPTIONS="$EXCLUDE_OPTIONS --exclude $exclude_dir"
done


# Run rdiff-backup
rdiff-backup $EXCLUDE_OPTIONS $SOURCE $DESTINATION


# Check if backup was successful
# if [ $? -eq 0 ]; then
#     echo "System backup completed successfully."
# else
#     echo "Error: System backup failed."
# fi



```

I have the checks commented out because I don't know if that will work with the backup going to server. That's a headache for another day.

Thanks again.

---

### Post by TheFu on 2024-03-18
[https://lpi.jdpfu.com/2023-Backups/2023-Backup-How-To.html](https://lpi.jdpfu.com/2023-Backups/2023-Backup-How-To.html) is how I recommend doing things for _local_ backups.    Sorry, I didn't do a presentation about push or pull backups. It was for an audience that 90% wasn't doing any backups at all, so I didn't want to confuse them with ssh complexities when 50% of them had never heard of ssh. Crazy, right?

_Push_ backups just get a target with the server address and ssh setup.

_Pull_ backups are a little more complex, since the source is remote and people have trouble understanding that ssh setup requires lots of root-equiv accounts on every client. Also, clients should never have direct access to the backup server storage.

I work the rdiff-back exactly to opposite.  I don't exclude specific directories.  I exclude everything, but include the specific stuff I want.  Seems backwards, I know.  I fought and fought with getting my scrips to be generic before a post on the rdiff-backup listsrv made that clear.  exclude everything, but include the specific directory structures you want. Order in the arguments matters.  Anyway, look at my backup how-to for the correct order.  The **TL;DR** section has the important parts and the correct order for exclude/include stuff.

I do not backup OS programs, since my restore process begins with a fresh OS install.    There's little reason to backup /bin or /usr/bin or /lib or /usr/lib - why bother?  A fresh OS install from an ISO will put back the core things.
You need to specifically exclude FIFOs, named pipes, sockets, and device files.  I used to use --exclude-special-files, but then some things were included and broke a backup on a server, so I actually read the manpage details to learn that special-files didn't include everything that *absolutely must* be excluded.

If a backup fails, it will tell you, loudly. No need to check.  When you automate it via cron, just email the stderr output. If you don't get any email, then it finished without errors. If you do get an email, something bad happened and the error will be in the email.

Lastly, "joe" is a poor name for a root-equiv account.  Think long, random, hard to guess, usernames.  "backup21349323432O"  You know what it is for and nobody will guess it.  I use different backup root-equiv accounts for all my clients.

For ssh keys, you can have as many as you like.  I hope you are using the ~/.ssh/config file (documented in the *ssh_config* manpage) to specify the config from which ever account initiates the ssh connection.  If sudo is used on 22.04, that would be /root/.ssh/config.  The target account, even if root equiv, will be used for the public-key side ... so that would be /home/joe/.ssh/authorized_hosts.  Just need to be clear which userid is initiating and which is receiving the ssh connection.  

Scripts need to specify the full path to any programs used.  "rdiff-backup" ----> /usr/bin/rdiff-backup.  Doing this prevents so many problems. Never trust the $PATH in scripts.

Don't forget to remove old backups - 60, 90, 180, 366 days old.  You need to put that into your script so you don't forget it.

That's probably enough to chew on for now.

---

### Post by coley9225 on 2024-03-18
thefu,
Thanks for the input. I bookmarked the site you gave and will most definitely be reading, at least twice. "joe" is not the actual name I used, so for now I'll leave what I have. Again, this is on my home network, no incoming access. I am still getting the error that it is unable to create the target directory, even though it exists already. I'll read and digest the info you provided and chew on it a little, then modify from there.

I do have a couple of rdiff-backup scripts you've given on here, and refer to them often while working on these scripts. I'm mainly working on rdiff-backup to get a better versioned backup scheme set up. I currently use timeshift, daily, for system backups, and back-in-time for my /home/<user> and my data partition. Works well, I've had the misfortune of needing it once or twice, but want something with a smaller 'footprint'.

Again, I appreciate all the help, from you and others over the brief time I've used linux based systems, you guys are great.

---

### Post by TheFu on 2024-03-18
A few times I've heard of people behind a firewall which should have prevented any outside access, only to find that someone still got in.  I expect that from people who like to play around with things, but a few times, some professionals had the issue too.  I looked at their firewalls, and could see in the logs where outsiders were getting onto the LAN, even with all ports closed.  In the end, we swapped out their firewall for a fully maintained one that wouldn't likely need to be replaced in 10-20 yrs and wasn't using Linux.

When it comes to security, 1 = none.  2 is the bare minimum for long term use and 3 is a comfortable set of prevention.  I don't mean we need 3 firewalls, but we need 3 different protective methods to ensure outside connections aren't getting where they shouldn't.  It is easy to make a tiny mistake and be 100% certain things are safe, only to discover a problem with our first line of defense.

Crackers are crafty. If they want to get in, they will find a way. They can be patient.  They aren't out to get you or me individually. They are out to get everyone they can.  We want to be in the hardest 10% to crack, right?  That usually means we aren't a target, since they can't get in after a full year of trying.  We need to be 100% correct every time. They just need us to be wrong, once.

I'm not a fan of any tool that suggests you need another too to properly do the same task.  That's timeshift.  A proper rdiff-backup setup completely negates the need to use timeshift at all.  If you want snapshots, use LVM-snapshots. That will greatly improve your backups too, though it will make them a little more complex. How much is an assurance that no backup will have corrupted files worth even while the system keeps running at full speed?

---

### Post by coley9225 on 2024-03-19
thefu,
Points taken. I haven't gotten to much into the firewall issue yet, but will bring it back to the front burner. I read the presentation you linked, a couple of times. There is some interesting things in there, thanks. 1 thing I noticed was under problems. You said to use rdiff-backup for a local backup solution, and the rsync that to the remote location. I have an rsync script that uses rsync to back up a few files/dir to my 'practice server', and it works well. I am going to look at possibly rewriting the rdiff script make make a local backup, and the rsync the to my server. Again, this is practice for me. There is little sense in paying for an offsite backup location if I can't get the backup to it. For a remote backup, unfortunately, I will have to push, rather that pull, my backups. Long story short, my son controls the router, and his girlfriend controls him, so I can't forward a port to my computer, for now.

I'll work on modifying my backup strategy, and get back here in a day or two. I know you, and others on here, have life outside of here, which make me appreciate the help even more. Thanks.

On a side note. I joined the forums in late 2018, and since then, I have looked at the xman thing in the corner. I really was curious, but never acted on it, until yesterday. I ran xman. Wow, never new that was there, and it will be very helpful. Funny, sometimes there is help right in front of you and you never even notice..lol. Any way, have a wonder day, and I'll be back on soon with an update.

---

### Post by TheFu on 2024-03-19
> **coley9225 said:**
> thefu,
Points taken. I haven't gotten to much into the firewall issue yet, but will bring it back to the front burner. I read the presentation you linked, a couple of times. There is some interesting things in there, thanks. 1 thing I noticed was under problems. You said to use rdiff-backup for a local backup solution, and the rsync that to the remote location. I have an rsync script that uses rsync to back up a few files/dir to my 'practice server', and it works well. I am going to look at possibly rewriting the rdiff script make make a local backup, and the rsync the to my server. Again, this is practice for me. There is little sense in paying for an offsite backup location if I can't get the backup to it. For a remote backup, unfortunately, I will have to push, rather that pull, my backups. Long story short, my son controls the router, and his girlfriend controls him, so I can't forward a port to my computer, for now.

Remote is over 500 miles away, not just a different system in the same building. Don't know if that was clear.  rsync can push or pull and uses ssh credentials.  A family member and I setup VMs for each other to swap rsync backup areas.  We backup the entire rdiff-backup taget data storage area, but because that needs to run as root, we setup our VMs for each other that way.  That's pretty advanced and I assume anyone doing it wouldn't need help.

> **coley9225 said:**
> 
On a side note. I joined the forums in late 2018, and since then, I have looked at the xman thing in the corner. I really was curious, but never acted on it, until yesterday. I ran xman. Wow, never new that was there, and it will be very helpful. Funny, sometimes there is help right in front of you and you never even notice..lol. Any way, have a wonder day, and I'll be back on soon with an update.
xman is just a GUI for normal manpages. It has been available since the very early days of X/Windows in the 1980s.  I haven't used xman in a long time.  Forum policy doesn't let me answer questions with RTFM.  It is really sad that every new user to Linux isn't forced to learn about their local manpages as part of the first Intro-to-Linux start screen post-install.  When the manpage has the correct answer to a question, I'll often copy/paste the relevant paragraphs from the manpage to highlight the answer.

---

### Post by coley9225 on 2024-03-20
[COLOR=#000000]> Remote is over 500 miles away, not just a different system in the same building. Don't know if that was clear. rsync can push or pull and uses ssh credentials

I understand the remote backup being at a totally different area. However, as i mentioned, I can't justify(or afford) paying for such an offsite location if I can't transfer files to my 'practice server' over the local network. Purchase of remote storage space is the end goal, but Iif I can't ssh in or transfer file a few feet, I certainly won't be able to send a backup to Cali. (I'm in Florida). And I also understand the push/pull idea, and I've seen you mention pull is better, for many reasons. The problem with that, is I would need to setup port forwarding on my router. Easy enough to do, except my son is in charge of the router, aand his girlfriend thinks he and I are both blooming idiots, and won't allow that. So until I can set that up, no incoming request to my computer is available, so for now it's push as my option. I may have been a little confusing in explanation in the previous post, sorry.

That said, I've made great progress. I rewrote the script, and after working out a couple of bugs, I'm able to use rdiff-backup to  backup basic system files. I need to go back over you rdiff how-to again and continue to expand the script. You mention saving copies of all crontabs, lshw, and some others. Not sure I understand the need for some of it, but I'm still learning. I also have, within the same script, a simple rsync command to sync the backup to my 'practice server'. Again, had a few wrinkles to iron out, but it is working fine.

Now, beside expanding the script I have, which is ONLY for the / partition, I can begin a script to backup my data partition, and another for my /home partition. I just need to go through and decide what to back and what to exclude.

This all began with an issue of 'cant make dir' error. Now you've shown me an easier way to do this and I've gone in a whole new direction. Oh well, sometimes my way aint the best way.

This is what I have so far.
[/COLOR]```
#!/bin/bash


#script using rdiff-backup to backup to external(local) hard drive


mkdir -p /mnt/backups/laptop_root
TGT=/mnt/backups/laptop_root #set target for backup
DAYS=120D
/usr/bin/mount /mnt/backups #make sure directory is mounted


# get list of manually installed packages
/usr/bin/apt-mark showmanual > /root/apt-mark.lst
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade


# Do backup
/usr/bin/rdiff-backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --exclude '**/.cache'  --exclude "$TGT" \
        --include /usr/local   --include /etc  \
        --include /root \
        --exclude '**'   /       "$TGT"
        
#remove older backups
/usr/bin/rdiff-backup --remove-older-than "$DAYS" --force "$TGT"


/usr/bin/rsync -e "ssh -i /home/charles/.ssh/id_rsa" -avh --delete --log-file=/home/charles/My_stuff/projects/backup/rysnc-log.txt /mnt/backups/laptop_root/ mrb:/mnt/backups/laptop_root


# unmount backup partition
/usr/bin/umount /mnt/backups



```[COLOR=#000000]

One problem I still have, it doen't unmount the backup partition, stating target is busy. This a 320GB hdd in an enclosure, a single partion mounted at /mnt/backups, and for now, 1 sub-directory, laptop_root. It is mount from the script(marked noauto in fstab) and only used for the script. Any way I make it unmount without finding whats holding it open and kill the PID. This time it was /bin/bash. I feel when the script completes, it shouldn't be busy for more than a minute or so and should umount without issue. I could use the -l flag and do a lazy umount, but would prefer the proper way, if there is one.
Thanks[/COLOR]

---

### Post by TheFu on 2024-03-20
> **coley9225 said:**
> [COLOR=#000000]...aand his girlfriend thinks he and I are both blooming idiots, and won't allow that. So until I can set that up, no incoming request to my computer is available, so for now it's push as my option. I may have been a little confusing in explanation in the previous post, sorry.
Well, all men are idiots, sometimes. She does have a point.

> **coley9225 said:**
> 
That said, I've made great progress. I rewrote the script, and after working out a couple of bugs, I'm able to use rdiff-backup to  backup basic system files. I need to go back over you rdiff how-to again and continue to expand the script. You mention saving copies of all crontabs, lshw, and some others. Not sure I understand the need for some of it, but I'm still learning. I also have, within the same script, a simple rsync command to sync the backup to my 'practice server'. Again, had a few wrinkles to iron out, but it is working fine.

rdiff isn't the same as rdiff-backup. They work differently.

Backups aren't just there to restore a full OS. They are there to help fix partial failures.  To that end, I create current hardware and especially disk layouts daily, just before my backups run. That way, if a partition table becomes corrupted, I have a copy and can slap back the exact same partition table, if that is needed.  Crontabs are stored in multiple places on the system. No all of them are in /etc/, so I want to ensure I have captured the crontabs I've created.  If you don't have any automation running from crontabs outside /etc/, then you don't need it.  I do.  I learned that some installed software would use the non-/etc crontables too.  I didn't alway have backups and with my email server (it is much more than that), there are 30+ contab jobs setup by the communications server to run periodically to maintain the system, create performance reports, and do other clean up tasks.  After a restore, I didn't have any of those jobs - so the restore wasn't great and in a few days, the system ran out of storage because none of the clean up happened.

There's a reason for everything I do.

> **coley9225 said:**
> 
Now, beside expanding the script I have, which is ONLY for the / partition, I can begin a script to backup my data partition, and another for my /home partition. I just need to go through and decide what to back and what to exclude.

Forget partitions. For backups, those don't matter, unless you are using LVM snapshots.  It is important that you use a single rdiff-backup command to backup everything in the system. This is called ensuring data homogeneity. Basically, if we backup different parts at different times, it is possible for the first part to have data that isn't compatible with the other part.  It is easily avoided, assuming you know about it and understand it.  I worked as a multi-threaded software developer and saw some really odd outcomes from data that wasn't consistent. This needs to be avoided in our backups too.

> **coley9225 said:**
> 
This all began with an issue of 'cant make dir' error. Now you've shown me an easier way to do this and I've gone in a whole new direction. Oh well, sometimes my way aint the best way.

The way I started doing backups sucked.  It was a huge hassle and I had to run them manually, because I didn't trust the little rsync script I'd created.  In reality, what happened was I manually ran the backup every week for about 4 months, then slowly ran it less and less and less.  Eventually, it was over 6 months between backup runs and that was just to create 1 copy, no versioning.  Then my system got hacked.  Thru some huge luck, I happened to have created a new mirror the prior week. Talk about luck!  With that mirror, I compared all the differences between the live system and my mirror and saw exactly where files had been downloaded and which userid had been hacked.  It was an automated attack. I was about 3 months behind on patching my server - it was a different time back then. Updates were per-project, not distro-wide.  A new distro was put out every 6 months - this was before Ubuntu existed.

> **coley9225 said:**
> 
This is what I have so far.
[/COLOR]```
#!/bin/bash


#script using rdiff-backup to backup to external(local) hard drive


mkdir -p /mnt/backups/laptop_root
TGT=/mnt/backups/laptop_root #set target for backup
DAYS=120D
/usr/bin/mount /mnt/backups #make sure directory is mounted


# get list of manually installed packages
/usr/bin/apt-mark showmanual > /root/apt-mark.lst
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade


# Do backup
/usr/bin/rdiff-backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --exclude '**/.cache'  --exclude "$TGT" \
        --include /usr/local   --include /etc  \
        --include /root \
        --exclude '**'   /       "$TGT"
        
#remove older backups
/usr/bin/rdiff-backup --remove-older-than "$DAYS" --force "$TGT"


/usr/bin/rsync -e "ssh -i /home/charles/.ssh/id_rsa" -avh --delete --log-file=/home/charles/My_stuff/projects/backup/rysnc-log.txt /mnt/backups/laptop_root/ mrb:/mnt/backups/laptop_root


# unmount backup partition
/usr/bin/umount /mnt/backups



```[COLOR=#000000]


You need to validate that the backup storage mount actually worked.  If you don't, it will be bad when it fails .... and **it will fail.**  There are threads in these forums for a few different options about that.

Your rsync command is entirely too complex. There's never a need to use _-e ssh_. ssh is the default.  To use a different key, setup your ~/.ssh/config file.  BTW, rsa isn't the best choice and hasn't been for some time. You really should switch to a different method.  Also, rsync behaves different based on if the source and target are local or one is remote.  I'd use variables for the source and target to make the script more flexible.  I'd want to see  /mnt/backups/laptop_root just once in the script. Everywhere else should be using the variable.  This prevents bonehead mistakes.

> **coley9225 said:**
> 
One problem I still have, it doen't unmount the backup partition, stating target is busy. This a 320GB hdd in an enclosure, a single partion mounted at /mnt/backups, and for now, 1 sub-directory, laptop_root. It is mount from the script(marked noauto in fstab) and only used for the script. Any way I make it unmount without finding whats holding it open and kill the PID. This time it was /bin/bash. I feel when the script completes, it shouldn't be busy for more than a minute or so and should umount without issue. I could use the -l flag and do a lazy umount, but would prefer the proper way, if there is one.
Thanks[/COLOR]

You cannot have a shell pwd be anywhere in the mount point or have any program with an open file down there.  
Scripts need to run from any PWD, always.

---

### Post by coley9225 on 2024-03-21
thefu,
Wow, lots to cover.
> [COLOR=#000000]Well, all men are idiots, sometimes. She does have a point.[/COLOR]
 
True. I have trashed my system more than once, usually because of something stupid. I've had to start from scratch a couple of times. That's why I now have backups, and wanting to initiate a better backup strategy.

> [COLOR=#000000]rdiff isn't the same as rdiff-backup. They work differently.[/COLOR]
]
I understand that. I sometimes will use rdiff only( in my posts) to save a few keystrokes...I'm kinda lazy like that.

> [COLOR=#000000]Backups aren't just there to restore a full OS. They are there to help fix partial failures. To that end, I create current hardware and especially disk layouts daily, just before my backups run. That way, if a partition table becomes corrupted, I have a copy and can slap back the exact same partition table, if that is needed. Crontabs are stored in multiple places on the system. No all of them are in /etc/, so I want to ensure I have captured the crontabs I've created. If you don't have any automation running from crontabs outside /etc/, then you don't need it. I do. I learned that some installed software would use the non-/etc crontables too. I didn't alway have backups and with my email server (it is much more than that), there are 30+ contab jobs setup by the communications server to run periodically to maintain the system, create performance reports, and do other clean up tasks. After a restore, I didn't have any of those jobs - so the restore wasn't great and in a few days, the system ran out of storage because none of the clean up happened.[/COLOR]
Thanks for explaining that. I now understand, a little better, the reasoning behind the action. Explaining clearly like that informs my of the why, not just saying 'because it's a good idea'.

> [COLOR=#000000]It is important that you use a single rdiff-backup command to backup everything in the system. [/COLOR]
Valid point. I start working toward that goal. Even if I run every backup daily, there could, possibly, be a conflict. I never considered that.

I'll start researching ways to validate the backups. Right now, I simply go into the backup and see if everything seems to be in place, but that's a lot of unnecessary typing (back to lazy thing).
I ended up using ssh -e, because the script continued to ask for a password. I read about sshpass, but the idea of my password being in plain text doesn't appeal to me. Nor does using a password file. I'm using this method untill I find a way for it not to ask for password. As for using variables, I used them on the rdiff-back portion, and just went braindead on the rsync, and used actual path rather than the variable. I correct that right away.

And on the unmount issue, according to PID ( I got from lsof), the activity was from /bin/bash, so apparently I had a shell still in that directory. As far as running from any directory, as soon as I get the bugs worked out, the script will be move to somewhere in my $PATH. I'm not sure of best location though. Should it go in ~/.local/bin, or somewhere else?

Well, that should do it for, Thanks again.

---

### Post by TheFu on 2024-03-21
> **coley9225 said:**
>  I'll start researching ways to validate the backups. Right now, I simply go into the backup and see if everything seems to be in place, but that's a lot of unnecessary typing (back to lazy thing).

As I wrote already, if the backup fails, it will complain, loudly.  Validation is built-in.  I create a daily report about backups run here that can be gathered from data in the target backup location logs.

> **coley9225 said:**
> 
I ended up using ssh -e, because the script continued to ask for a password. I read about sshpass, but the idea of my password being in plain text doesn't appeal to me. Nor does using a password file. I'm using this method untill I find a way for it not to ask for password. As for using variables, I used them on the rdiff-back portion, and just went braindead on the rsync, and used actual path rather than the variable. I correct that right away.

Use ssh-keys and use the ssh_config file in the user's HOME that initiates the backups.  The actual HOME location depends on a few things. No password prompt or need to put usernames, ports, ssh ID files into the command at all.  The ~/.ssh/config file is great a documenting different logins to different systems, for different purposes.  Backups would be 1 specialized reason, but there are hundreds of others.

> **coley9225 said:**
> 
And on the unmount issue, according to PID ( I got from lsof), the activity was from /bin/bash, so apparently I had a shell still in that directory. As far as running from any directory, as soon as I get the bugs worked out, the script will be move to somewhere in my $PATH. I'm not sure of best location though. Should it go in ~/.local/bin, or somewhere else?

**_Never trust the PATH!!!  Not in any script!_**  When you are done, the crontab should spell out the exact, full, location, of the script to be run too.

---

### Post by coley9225 on 2024-03-25
Sorry for the delayed response, been busy.
I've overcome the issue with asking for my password. I simply copied the ssh keys to /root/.ssh, and that solved that problem. Using sudo make the script being run as root, so root ned the key for verification.

I've decided on a new overall strategy. I have been doing a lot of 'spring cleaning' in my system. I deleted some old, unused files and apps, and I'm trying to reorganize all my stuff so it makes a little more sense. My new plan is to keep working on my script, and fine tune it. When lubuntu 24.04.1 is released, I'm planning to wipe out my partitions(all 3, format, not delete and make new), and do a fresh install of 24.04.1. That gives me an opportunity to change my backup mount points to the / partion, and generally fix a lot of mistakes I have made in the past.

As I refine my script, I'll continue to make test runs to be sure it is working, and I will find the best way to do a test restore, to verify the backups and and get more familiar with the restore procedure. using a VM is not really an option, my computer becomes unstable, and eventually freezes, because of low resources. I do have a vast amount of unallocated space on my ssd, so I think I'll do a new install, and backup to that to test.

If I'm successful, I' have a fully functional backup scheme with rdiff-backup, and a fresh install of the newest LTS release of lubuntu, a win-win. I will still be using timeshift and back-in-time for a while, as I have restored from them and know they work, plus there is no such thing as too many backups.

If I encounter any additional problems, I'll start a new thread to address those issues. I won't make this as solved, because the original issue was about a 'can't make directory' error, which kinda got lost along the way.

One last thing for now. You mentioned rsa keys were not the best option, so what should I use instead. If I going to clean up some and fix some mistakes, I may as well fix that too.

I really appreciate the help you've given me thus far.

---

### Post by TheFu on 2024-03-27
> **coley9225 said:**
>  If I encounter any additional problems, I'll start a new thread to address those issues. I won't make this as solved, because the original issue was about a 'can't make directory' error, which kinda got lost along the way.

That was just solved by using a root-equiv account and sudo on the source and target sides of the backup.  This is SOLVED and wasn't going to be solved any other way, while creating useful backups.  You could have solved it without that method, but it wouldn't have been "useful" as a backup, since the owner, group, ACLs, permissions and xattrs wouldn't be retained.

---

