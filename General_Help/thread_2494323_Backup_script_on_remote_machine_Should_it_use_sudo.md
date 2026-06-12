---
title: "Backup script on remote machine: Should it use sudo &amp; how to avoid password request ?"
date: 2024-01-12
forum: General Help
---

### Post by freeflyjohn on 2024-01-12
I have almost got my backup script working for offsite local and remote backups, using rdiff-backup and rsync.

However, I am slightly confused how to run the script on the remote machine:


[LIST=1]
[*]I am supposed to run the script on the remote machine as sudo or non-sudo ?
[*]Does the owner of the script file on the remote machine matter ?
[/LIST]

I have tried running the script on the remote machine with and without sudo, which gave the following results:

If I run the script as sudo:

[LIST]
[*]No permission errors appear
[*]However, the server password is requested for each command (i.e. rdiff-backup or rsync)
[/LIST]

If I run the script without sudo:

[LIST]
[*]The server password is NOT requested for each command (i.e. rdiff-backup or rsync)
[*]However, permission errors occur
[/LIST]

I have setup SSH keys between the server and remote machine and I can SSH into the server from the remote machine without being asked for a password using...

```
 ssh user@192.168.6.1 -p 12345 
```

I want the backup script to use the SSH keys, to avoid being asked for the server password each time the script runs each command. 
 

[LIST=1]
[*]Why does running the script on the remote machine as sudo ask for the server password, whereas running as non-sudo does not ?
[*]Am I supposed to run the script on the remote machine as sudo or non-sudo ?
[*]If I should run the script on the remote machine as sudo, then how do I avoid being asked for the server password ?
[/LIST]

I perform the initial offsite backup locally using sudo as shown in the diagram below:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293300&stc=1[/IMG]


I then perform the remote backup over Wiregaurd VPN as shown in the diagram below:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293299&stc=1[/IMG]

The backup script is shown below:

```

#!/bin/bash


# Use this script to backup internal HDD 'storage' in the server to the specified external USB HDD 
# i.e. offsite local HDD or offsite remote HDD
# For local offsite backsup use '-offsite.loc' paraemter: sudo /bin/backupscripts/./backup-storage.sh -offsite.loc
# For remote offsite backsup use '-offsite.rem' parameter: sudo /bin/backupscripts/./backup-storage.sh -offsite.rem




# backup selection
if [ -z $1 ] ; then
        echo "Parameter missing: define -offsite.loc or -offsite.rem"
        exit
elif [ "-offsite.loc" = $1 ] ; then
        echo "Performing local offsite backup..."
elif [ "-offsite.rem" = $1 ] ; then
        echo "Performing remote offsite backup..."
else 
        echo "$1 invalid: define -offsite.loc or -offsite.rem"
        exit
fi


    
# rdiff-backup
if [ "-offsite.loc" = $1 ] ; then
    cmd_rdiff="/usr/bin/rdiff-backup -v4 --print-statistics --force"
    src_rdiff=/media/storage
    dest_path=/media/storageBackupOS
elif [ "-offsite.rem" = $1 ] ; then
    cmd_rdiff="/opt/homebrew/bin/rdiff-backup -v4 --print-statistics --force"
    src_rdiff=ssh://user@192.168.6.1:12345::/media/storage
    dest_path=/Volumes/storageBackupOS
fi
    $cmd_rdiff \
    --exclude-sockets --exclude-device-files --exclude-fifo \
    --exclude ignorecase:'**.ini' \
    --exclude ignorecase:'**.DS_Store' \
    --exclude ignorecase:'**\$RECYCLE.BIN' \
    --exclude ignorecase:'**.AppleDouble' \
    --exclude ignorecase:'**.localized' \
       --include /media/storage/Media \
    --exclude '**' $src_rdiff \
    $dest_path




# rsync command configuration


rsync_excludes="--exclude '*.ini' \
    --exclude '*.DS_Store' \
    --exclude '**/\$RECYCLE.BIN' \
    --exclude '*.AppleDouble' \
    --exclude '*.localized'"


if [ "-offsite.loc" = $1 ] ; then
        cmd_rsync="/usr/bin/rsync"
        rsync_options="-a --progress -l --delete $rsync_excludes" 
elif [ "-offsite.rem" = $1 ] ; then
        cmd_rsync="/usr/bin/rsync"
    rsync_options="-a --progress -l --delete --rsh='ssh -p 12345' $rsync_excludes"        
fi




# rsync of /media/storage/svn


if [ "-offsite.loc" = $1 ] ; then
        src_rsync=/media/storage/svn/                            # end with trailing slash
        dest_path=/media/storageBackupOS/svn                     # do not end with trailing slash
        mkdir -p /media/storageBackupOS/svn                      # do not end with trailing slash
elif [ "-offsite.rem" = $1 ] ; then
        src_rsync=user@192.168.6.1:/media/storage/svn/      # end with trailing slash
        dest_path=/Volumes/storageBackupOS/svn                   # do not end with trailing slash
        mkdir -p /Volumes/storageBackupOS/svn                    # do not end with trailing slash
fi
        eval $cmd_rsync $rsync_options $src_rsync $dest_path
        


# rsync of rdiff-backup for /media/storage/Backup/Mac originally performed by the scripts 'rdiff-mac-john.sh' and 'rdiff-mac-soph.sh'


if [ "-offsite.loc" = $1 ] ; then
        src_rsync=/media/storage/Backup/Mac/                # end with trailing slash
        dest_path=/media/storageBackupOS/Backup/Mac            # do not end with trailing slash
    mkdir -p /media/storageBackupOS/Backup/Mac            # do not end with trailing slash
elif [ "-offsite.rem" = $1 ] ; then
        src_rsync=user@192.168.6.1:/media/storage/Backup/Mac/     # end with trailing slash
        dest_path=/Volumes/storageBackupOS/Backup/Mac            # do not end with trailing slash
    mkdir -p /Volumes/storageBackupOS/Backup/Mac            # do not end with trailing slash
fi
        eval $cmd_rsync $rsync_options $src_rsync $dest_path

```

---

### Post by TheFu on 2024-01-12
TL;DR - if you don't use root locally and remotely, you won't get the correct owners, permissions, ACLs, and xattrs retained in the backups.  This is a fact of life in Unix systems.

We all know not to enable root for remote access, so that leaves creating a root-equivalent, randomly named, backup account that only allows connections from the backup server "pulling" the files back.

---

### Post by freeflyjohn on 2024-01-12
Thanks TheFu

So I should make a new user on the IMac (eg called backup) and give that user root privileges ?

But when I use sudo with the script it asks me for the server password. How do I avoid that?

If I use the script without sudo it does not ask me for the server password, presumably because it uses the ssh keys?

So even with a new user on the IMac, I assume it will still ask me for the server password when I run as sudo?

---

### Post by TheFu on 2024-01-12
> **freeflyjohn said:**
> So I should make a new user on the IMac (eg called backup) and give that user root privileges ?

I would specifically not name it "backup".  That account already exists and has other purposes.  I would make it root-equivalent, not just sudo. You'll need to figure out how to do that yourself.  This is one of those things that until you understand it, there's no safe way to create it.

> **freeflyjohn said:**
> But when I use sudo with the script it asks me for the server password. How do I avoid that?
This is another one of those things that until you understand it, there's no safe way to create it.  In the learning, comes the required understanding.

> **freeflyjohn said:**
> If I use the script without sudo it does not ask me for the server password, presumably because it uses the ssh keys?
You'll need to better understand which keys are used on each side of the ssh connection.

> **freeflyjohn said:**
> So even with a new user on the IMac, I assume it will still ask me for the server password when I run as sudo?
I know zero about MacOS and wouldn't pretend to have any answer.  I used a Mac for about 3 weeks around 2011 and hated it. Before I physically destroyed the box, I returned it.  I was close to throwing it against a brick wall, multiple times due to the frustration levels.

---

### Post by freeflyjohn on 2024-01-12
This is the issue I am trying to understand.

If I SSH into the server WITHOUT sudo....

```
ssh user@192.168.6.1 -p 12345 
```

... I get straight into the server without the need of a password.

If I SSH into the server WITH sudo....

```
sudo ssh user@192.168.6.1 -p 12345 
```

... it then asks me for the server password...

```
user@192.168.6.1's password:
```

As my backup script uses 1 instance of rdiff-backup and 3 instances of rsync, it means I have to enter my server password 4 times during the backup (i.e. one for each command).

I believe its asking for a password due to each command making a new SSH connection with root privalges ?

I would be happy if I could just enter the server password once when  starting the script, but dont know how or if its even possible.

I read you can include the password in the script file, but I dont want to do that for security reasons.

As I comprimise I started looking at using 1 instance of rsync by excluding everything and then including the 3 folders I want to backup. 

At least I would only have to enter the password twice (once for rdiff-backup and once for rsycn)

This is how I use rdiff-backup, I exclude everything and then explicitly include the directories I want to backup.

But I dont know how or if its even possible to do the same thing with rsycn ?

---

### Post by TheFu on 2024-01-12
Your ssh keys aren't using the correct accounts.  The value of $HOME matters on both sides of the connection.

---

### Post by freeflyjohn on 2024-01-12
Are you referring to the user and group of the ssh keys ?


[LIST]
[*]The id_rsa and id_rsa.pub key user and group on the Ubuntu server is ubuntuusername:ubuntuusername (in the /home/ubuntuusername/.ssh folder) 
[*]The id_rsa and id_rsa.pub key user and group on the iMac is macusername:staff (in the /Users/macusername/.ssh folder) 
[/LIST]

I tried making the id_rsa and id_rsa.pub key user and group on the Ubuntu server to root:root, but it made no difference.

Or are you saying I need to put the ssh keys in a root folder, rather than a home folder ?

---

### Post by TheFu on 2024-01-13
> **freeflyjohn said:**
> Are you referring to the user and group of the ssh keys ?
No. I'm referring to the HOME directory used by the userid after the privilege is elevated.  

Also, realize that sudo doesn't just switch to root, but it can be used to change to any other userid on the system. This isn't important, if you setup backups the way I do.

You seem to have ignored the "root-equivalent" account, which I've mentioned a few times.  That's the key.

---

### Post by freeflyjohn on 2024-01-13
Thanks TheFu

```
 You seem to have ignored the "root-equivalent" account, which I've mentioned a few times. That's the key. 
```

Not ignored, just didnt understand.

So I did some further research and managed to get it working, although whether I've done it correctly might be another matter (open to constructive criticism) !

I can now run the backup script on the Mac as sudo and it does not ask for the server password i.e.

```
sudo ./backup-storage.sh -offsite.rem 
```

I did this by creating a new user on the Ubuntu server as follows:

```
sudo adduser remotebackup
sudo usermod -aG sudo remotebackup
```

I then generated a new SSH key pair on the Mac and transferred the public key to the authorized_keys file on the server for the new user:

```

su - remotebackup
mkdir ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys

```

I have only been able to test the backup script using rsync so far, because I have used a different name for the SSH keys on the Mac (instead of the default id_rsa).

Therefore I have to define the ssh key name for both the rsync and rdiff-backup commands

I managed to do this for rsync using the -i switch:

```

    rsync_options="-a --progress -l --delete --rsh='ssh -p 12345 -i /Users/macuser/.ssh/osb_rsa' $rsync_excludes"

```

But I can't find how to do the same with rdiff-backup ?

Is it possible to define a different SSH key name with rdiff-backup ?

For rdiff-backup, the source is currently defined as...

```
src_rdiff=ssh://remotebackup@192.168.6.1:12345::/media/storage
```

---

### Post by TheFu on 2024-01-13
You've also ignored my push to use the ~/.ssh/config file.  Why make things harder than they need to be?

BTW, you aren't using a root-equivalent account if there's sudo involved on the remote side.  Heck, if it works, great. Just not the way I do it.

---

### Post by SeijiSensei on 2024-01-13
I'll also mention that if you put scripts in /etc/cron.daily/ they will be run once each day with root privileges. That's my usual choice for backup scripts. You'll need to use sudo to create the file and store it in that location with executable privileges. After that it runs automatically as root.

---

### Post by freeflyjohn on 2024-01-14
```

```> **TheFu said:**
> You've also ignored my push to use the ~/.ssh/config file.  Why make things harder than they need to be?

BTW, you aren't using a root-equivalent account if there's sudo involved on the remote side.  Heck, if it works, great. Just not the way I do it.

Thanks TheFu, I've worked out how to do the ~/.ssh/config file on the remote machine (iMac).

I added the following lines to iMac ~/.ssh/ssh_config file...

```

Host 192.168.6.1
    User remotebackup
    Port 12345
    IdentityFile ~/.ssh/osb_rsa

```

So I shouldn't run sudo on the remote machine when running the script then ?  

```

[COLOR=#ff0000]sudo[/COLOR] ./backup-storage.sh -offsite.rem

```

I assume sudo is not required when running the script because the new  user 'remotebackup' already has root equivalent privalges ?  

So I assume the backup will still maintain the correct owners, permissions, ACLs, and xattrs etc. ?

Which is fortunate because for some reason when running the script as sudo its now asking me for the remote server password again, but I dont have to worry about that from the sounds of it.

---

### Post by TheFu on 2024-01-14
The client side uses the ~/.ssh/config file.  That's the side that initiates the connection whether it be rdiff-backup or rsync or ssh or scp or sftp or any of 50 other ssh-based tools.

Until you try the backup, you'll never know the other answers.  I always start with backing up /etc/ in the beginning. If that works (as verified by looking at the backup storage location) and has the correct owner, groups, xattra, acls, permissions, and versioning, then I know the other areas will work too.  /etc is small enough that the test takes just a few seconds.

If it works and you like it, who am I to say you can't/shouldn't use sudo?  Backups are about outcomes and being able to restore.  However, from reading your responses, I don't believe you have the idea of what root-equivalent means.  It is just like the root account, just not the root account.  I use a randomized name to drastically reduce remote attacks.  Many things around ssh are configured based on the account, so a root-equiv account is how to have root, but not use that name.  Calling an account 'root-equiv' doesn't make it so.

---

### Post by freeflyjohn on 2024-01-14
> **SeijiSensei said:**
> I'll also mention that if you put scripts in /etc/cron.daily/ they will be run once each day with root privileges. That's my usual choice for backup scripts. You'll need to use sudo to create the file and store it in that location with executable privileges. After that it runs automatically as root.

Thanks SeijiSensei

In my case this is not possible, because the backup script will be ran on an iMac (at my parents house) to do remote offsite backups of the server at my house.

Therefore it has to be done manually i.e. the iMac has to be turned on and the USB HDD needs to be plugged in

---

### Post by freeflyjohn on 2024-01-14
> **TheFu said:**
> The client side uses the ~/.ssh/config file.  That's the side that initiates the connection whether it be rdiff-backup or rsync or ssh or scp or sftp or any of 50 other ssh-based tools.

Until you try the backup, you'll never know the other answers.  I always start with backing up /etc/ in the beginning. If that works (as verified by looking at the backup storage location) and has the correct owner, groups, xattra, acls, permissions, and versioning, then I know the other areas will work too.  /etc is small enough that the test takes just a few seconds.

If it works and you like it, who am I to say you can't/shouldn't use sudo?  Backups are about outcomes and being able to restore.  However, from reading your responses, I don't believe you have the idea of what root-equivalent means.  It is just like the root account, just not the root account.  I use a randomized name to drastically reduce remote attacks.  Many things around ssh are configured based on the account, so a root-equiv account is how to have root, but not use that name.  Calling an account 'root-equiv' doesn't make it so.

Thanks TheFu

I realise that ~/.ssh/ssh_config  is for outgoing SSH connections and ~/.ssh/sshd_config is for incoming connections

I think I understand the idea of the root-equivalent account ?

In Ubuntu the root account is not active by default, so no user can login as root.  It is possible to setup a password the the user root but its not done by default (maybe due to security?).

So instead you use sudo to run commands that need root privalages.

The root equivlanet user I created is not the root user, but it has the same privalages as root.  

Therefore, when using the root equivalent user there is no need to use sudo

When the new user is created, the following command gives that user root privaleges..

```
sudo usermod -aG sudo newuser
```

---

### Post by TheFu on 2024-01-14
> **freeflyjohn said:**
>  
When the new user is created, the following command gives that user root privaleges..

```
sudo usermod -aG sudo newuser
```

No.  Before I posted to this thread, I thought some time whether it was a good idea to engage on this question and technique at all.  I'm thinking my initial though about it was correct.  Many people wouldn't like this technique at all.

---

### Post by freeflyjohn on 2024-01-14
> **TheFu said:**
> No.  Before I posted to this thread, I thought some time whether it was a good idea to engage on this question and technique at all.  I'm thinking my initial though about it was correct.  Many people wouldn't like this technique at all.

Can you elaborate on how it should be done then please?

I used this guide to create the user with root equivalent privileges…

[https://mhagemann.medium.com/how-to-create-a-user-with-root-privileges-on-ubuntu-93de0bec648c](https://mhagemann.medium.com/how-to-create-a-user-with-root-privileges-on-ubuntu-93de0bec648c)

I saw other guides talking about sudoers, but I don’t have that folder…

[https://www.thegeekdiary.com/how-to-create-an-almost-root-equivalent-users-but-not-root-identical-user-in-linux/amp/](https://www.thegeekdiary.com/how-to-create-an-almost-root-equivalent-users-but-not-root-identical-user-in-linux/amp/)

---

### Post by aljames2 on 2024-01-14
I am also hesitant because it's not clear what your backup strategy is, and there can be many many possibilities. Plus, I have zero knowledge regarding the iMac side of things.

If your issue is regarding permissions and the request for password on the ubuntu server side, then the info already provided is exactly what you need.

Elevated priviledges does not infer "sudo" priviledges outright.  For example, do you want your backup user to be able to delete files on the remote end during a session.  How about, should the remote user be able to move directories around on your server once the backup session begins.  Probably not.  Full sudo priviledges means the power to destroy any and everything on the system, probablly not what you imagine a backup session user being capable of.

I learned, also from TheFu some years back, this concept.  When I do this now, I have a separate user, as suggested, with a random username, that has the power to only use /usr/bin/rsync, or /usr/bin/rdiff-backup on the server... and even with this power, I've restricted it to read-only mode.  Now, my backup session user has no power to destroy, but elevated enough permissions to access & run this specific command on the remote end.

There is also a way to create this special use-case user where it is not assigned to any usergroup, basically a stripped down user.

---

### Post by MAFoElffen on 2024-01-14
I didn't comment before this, because I feel TheFu explains backups and does backup strategies better, especially with rdiff-backup.

There's many reasons why backups or other maintenance jobs are run with either another "special" user or service account. One being in the case if a job is interrupted. In that case it is hard for anyone else to continue the job, because of file permissions and ownership used during that process and the transition of.

The one question I have is on this as an idea... (Hint)
```

ssh -t user@server "sudo <scriptname>"

```

---

### Post by freeflyjohn on 2024-01-14
Thanks aljames2

To summarise, I have four 4TB HDDs in my Ubuntu server which I use for storage of files.  

Most of these files are not really system files, they are typically documents, spreadsheets, pictures, pdfs, software etc

In case one of those drives fails, I have four 4TB USB HDDs which are for onsite backups.

However, I would also like an offsite backup too in case the house burns down or the drives are stolen etc (like a 3-2-1 backup system).

The 4 HDDs in the server are:

1. Storage [ext4]:  This contains a backup of all the files I've collected over the years on Windows and Mac machines.  I also perform an rdiff-backup of my current Mac Book Pro to the server on this drive (not system files though).  There might be some files that are system files, for example there is an SVN server repo on the drive.  So to be on the safe side and protect for the future, I planned to keep the permissions etc the same when doing the remote backup.
2. General [ext4]:  This just has a backup of my Nextcloud files (not the Nextcloud system files).
3. Plex 1 [ext4]: Media (rsync backup only)
3. Plex 2 [ext4]: Media (rsync backup only)

One solutiuon would be to buy a NAS for my parents house (who live 100 miles away), but this is a very espensive solution.

So my intention was to use my parents machine (in this case an iMac), connect a USB HDD to that machine and perform a remote backup over VPN.

I did try to setup an SSH connection between my parents machine and my server but was not successful, so I setup a Wireguard VPN instead.

I want to use a single backup script for each drive in the server, then use switches to select whether that backup is onsite, offsite local (which I use to do the initial backup) or offset remote. I'm starting with the 'Storage' drive, as this uses both rdiff-backup and rsync.

I don't want the remote machine (i.e. the iMac at my parents house) to delete or change anything on the HDDs in my server, I just want to backup the server HDDs to a remote USB HDD.

At the same time I want to keep my server and data secure when performing the remote backup, as it will be over the internet.

I came accross this guide and thought it would do what I needed, but it confused me even more because it appears the server is making a backup of the the client, but I need the client (iMac) to make a backup of the server HDDs

[https://www.mad-hacking.net/documentation/linux/reliability/backup/using-rdiff-backup-remote.xml](https://www.mad-hacking.net/documentation/linux/reliability/backup/using-rdiff-backup-remote.xml)

To backup the Ubuntu system files I use Timeshift and the data is stored on the 'Storage' HDD in the server. I don't make another backup of the Timeshift data to the oniste or offsite HDD, but I may do in future.

So configuring everything which allows the backup script to maintain permisions etc seems the best way to protect for now and the future.

---

### Post by TheFu on 2024-01-15
Seems like your backup coding method is like NASA's moon shot method.  Everything, with all the complexities has to work the first time or nothing really works.  At least with your method, nobody dies.

Step 1.  Get something easy working.  I'm a little shocked that you couldn't get ssh working, but wireguard does?  ssh is 100x easier than wireguard.
Step 2. Get a tiny rsync command working in the way you want between the systems.  If you want "pull" backups, then get a tiny "pull" script working.  Like I wrote above, using the /etc/ directory for this to ensure everything is mirrored is a good idea. /etc/ on any Unix system will be relatively small, but have files owned by different accounts with different permissions.  Many will be read-only or zero-access for all accounts except root.  You need to learn to solve that issue. I've tip-toed around it for "pull" backups.  If you can't get it working, using "push" backups is a logical step while you gain more knowledge, experience and skill.
Step 3.  Add complexity to the script a little at a time. Then when it breaks, you can see what changes caused the break.  I assume you will have some versioning of the backup script - that can be daily local-only versioned backups or using a VCS like git.  It is up to you.  If you don't do this, break something and can't figure out how to get it working again, that's your own fault.  We've all been there.

Timeshift?  I don't see the point, unless you are using BTRFS which would really take advantage of the BTRFS snapshot capabilities and rsync to mirror the snapshot to alternative media. To each their own.

I do the 1-2-3 backup method for really important things, but not for stupid media files. I've posted my backup methods here and a few scripts over the last decade. My current "pull" backup script isn't posted anywhere because it is so specialized for my needs as to be confusing for others.  Additionally, I push code to the remote system for pre-backup and post-backup tasks. This is not intuitively obvious how to do and I don't want to teach how to do things like that. People at the right level of skill/knowledge will either know how or figure it out in an hour.  The same goes for setting up a root-equivalent account.  There are huge security implications in doing it and some subtle steps are needed which I'm not 100% certain I can remember to convey, so it is best for anyone doing it to have the right level of skill/knowledge to either already know how or figure it out in an hour.

They always say our reach needs to exceed our grasp. There are many things Linux related that are beyond my understanding.  OTOH, I've known how to setup a root account since around 6 months into my learning.  That all happened with sudo was very new, but not yet universal.  In many wants, sudo has removed basic Unix skills because people run their systems without ever switching to a different, non-root, userid.  In the old days, changing to different users was extremely common.  
```
su - pete
su pete

```or 
```
su -
su
```
Simple, but subtle differences in those commands.
Similar to using 
```
sudo -i
sudo -s
```
or
```
sudo -i -u pete
sudo -s -u pete
```
in the results.

Also, don't forget that ssh can be setup to only allow specific commands to be run over a remote connection. This is important too.

---

### Post by freeflyjohn on 2024-01-15
Thanks TheFu,

In fact, everything is working correctly with the exception of permissions etc due this root-eqiuvlent user on the server side.  

So I am 90% there, if I can just get these permissions issues sorted out then it will be complete.  

This is the part thats giving me the biggest headache and the main thing I need help with.

In addition to this, I have just tried using ssh on the iMac and this time it worked, so I don't need to use wireguard after all (I'm not sure why I couldn't get it working the first time)

As you suggested, I created a config file in ~/.ssh/config... 
```

Host mywebsite.com
    User username
    Port 12345
    IdentityFile ~/.ssh/osb_rsa

```

This makes the backup script much easier as I don't have to define ports and key files etc. in the script.

Both rsync and rdiff-backup are working BUT I am having issues with permissions.

For example, the result of the rdiff-backup show these errors...

```

********************* Performing rdiff-backup *********************
WARNING: this command line interface is deprecated and will disappear, start using the new one as described with '--new --help'.
WARNING: Server will be called with deprecated command line interface to guarantee compatibility. It might lead to a deprecation warning from newer rdiff-backup versions. Use '--api-version 201' (or higher) to avoid it.
NOTE: Remote version 2.0.0 doesn't know about API versions but should be compatible with 200
WARNING: Previous backup seems to have failed, regressing destination now
NOTE: Regressing to date/time Sat Jan 13 09:21:44 2024
Using rdiff-backup version 2.0.0
    with cpython /usr/bin/python3 version 3.8.10
    on Linux-5.4.0-169-generic-x86_64-with-glibc2.29, fs encoding utf-8
Unable to import win32security module. Windows ACLs
not supported by filesystem at /media/storage
Traceback (most recent call last):
  File "/usr/local/lib/python3.12/site-packages/rdiff_backup/rpath.py", line 909, in delete
    self.conn.os.unlink(self.path)
[COLOR=#ff0000]PermissionError: [Errno 1] Operation not permitted: b'/Volumes/storageBackupOS/Backup/Mac/macusername/Documents/Finance/CreditCard/Credit201207.pdf'[/COLOR]

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/local/bin/rdiff-backup", line 8, in <module>
    sys.exit(main())
             ^^^^^^
  File "/usr/local/lib/python3.12/site-packages/rdiffbackup/run.py", line 35, in main
    sys.exit(main_run(sys.argv[1:]))
             ^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/rdiffbackup/run.py", line 108, in main_run
    ret_val |= conn_act.run()
               ^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/rdiffbackup/actions/backup.py", line 139, in run
    ret_code |= self._operate_regress()
                ^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/rdiffbackup/actions/__init__.py", line 550, in _operate_regress
    self.repo.base_dir.conn.regress.Regress(self.repo.base_dir)
  File "/usr/local/lib/python3.12/site-packages/rdiff_backup/regress.py", line 292, in Regress
    ITR(rf.index, rf)
  File "/usr/local/lib/python3.12/site-packages/rdiff_backup/rorpiter.py", line 146, in __call__
    last_branch.fast_process_file(*args)
  File "/usr/local/lib/python3.12/site-packages/rdiff_backup/regress.py", line 120, in fast_process_file
    rf.mirror_rp.delete()
  File "/usr/local/lib/python3.12/site-packages/rdiff_backup/rpath.py", line 914, in delete
    self.chmod(0o700)
  File "/usr/local/lib/python3.12/site-packages/rdiff_backup/rpath.py", line 719, in chmod
    self.conn.os.chmod(self.path,
[COLOR=#ff0000]PermissionError: [Errno 1] Operation not permitted: b'/Volumes/storageBackupOS/Backup/Mac/macusername/Documents/Finance/CreditCard/Credit201207.pdf'[/COLOR]

```

When I look at the file 'Credit201207.pdf' on the server the attributes are...

```

-r--------  1 username  group 148538 Aug 20  2012 Credit201207.pdf

```

Now, I could change the attributes for that file but it highlights the fact that the permissions arent being kept during the backup.

In fact, the user and group for ALL the files on the USB HDD backup have now been changed to the username and group of the iMac.

There are similar issues with rsycn...

```

********************* Performing rsync backup of svn *********************
receiving file list ... 
1465 files to consider
                    
sent 100 bytes  received 19126 bytes  12817.33 bytes/sec
total size is 59888986  speedup is 3115.00
********************* Performing rsync backup of Mac *********************
receiving file list ... 
210666 files to consider
macusername/        
macusername/Desktop/
macusername/Desktop/Microsoft Edge.lnk
        1878 100%    1.79MB/s    0:00:00 (xfer#1, to-check=210662/210666)
macusername/Desktop/Thumbs.db
       44032 100%    4.20MB/s    0:00:00 (xfer#2, to-check=210661/210666)
macusername/Desktop/Ubuntu Linux
         800 100%   32.55kB/s    0:00:00 (xfer#3, to-check=210660/210666)
macusername/Desktop/Windows 10
         800 100%   28.94kB/s    0:00:00 (xfer#4, to-check=210659/210666)
macusername/Documents/
macusername/Documents/CV_Sep14.pdf
      116770 100%  523.09kB/s    0:00:00 (xfer#5, to-check=210657/210666)
macusername/Documents/Contract.pdf
[COLOR=#ff0000]rsync: failed to modify permissions on "/Volumes/storageBackupOS/Backup/Mac/macusername/Documents/ProTrack/Logbook": Operation not permitted (1)[/COLOR]
     2399508 100%    1.27MB/s    0:00:01 (xfer#6, to-check=210656/210666)
macusername/Documents/BPA Magazines/
macusername/Documents/BPA Magazines/2006-06-01.pdf
    76300235 100%    3.06MB/s    0:00:23 (xfer#7, to-check=210646/210666)
macusername/Documents/BPA Magazines/2008-10-01.pdf
   151322624  66%    2.62MB/s    0:00:28

``` 

These issues don't occur when I perform local backups, they only occur when performing the remote backup and its all due to not running the backup script with root privalages as you've already mentioned previously.

If I can just fix these permission issues then everything will work correctly.

Then I would also like to setup ssh to only allow specific commands to be run over a remote connection, which I will look at once I get these permission issues sorted.

The only other potential issue is that the version rdiff-backup on the iMac is 2.2.6 whereas the version on the server is 2.0.0, so I get a warning saying that the versions do not match.

To install rdiff-backup on the iMac I have to use something called homebrew and it just installed the latest version.

Once I sort out the permission issues, I might have to look at trying to get the rdiff-backup versions to match, which from previous experience is not straight forward.

I don't understnad why the rdiff-backup version can't be the same (preferably the latest version) for all operating systems.  Even on Ubuntu the latest version seems to only be 2.0.0.

The backup script is below for reference...

```

#!/bin/bash

# Use this script to backup internal HDD 'storage' in the server to the specified external USB HDD
# i.e. onsite HDD, offsite local HDD or offsite remote HDD
# For onsite backsup use '-onsite' paraemter: sudo /bin/backupscripts/./backup-storage.sh -onsite
# For local offsite backsup use '-offsite.loc' paraemter: sudo /bin/backupscripts/./backup-storage.sh -offsite.loc
# For remote offsite backsup use '-offsite.rem' parameter: sudo /bin/backupscripts/./backup-storage.sh -offsite.rem

# backup selection
if [ -z $1 ] ; then
        echo "Parameter missing: define -onsite, -offsite.loc or -offsite.rem"
        exit
elif [ "-onsite" = $1 ] ; then
    # check external USB HDD is connected
        if ! mount | grep -q /media/backupstorage; then
          echo "Onsite HDD not mounted"
          exit
        else
      echo "+++++++++++++++++++++ Performing onsite backup +++++++++++++++++++++"
    fi
elif [ "-offsite.loc" = $1 ] ; then
    # check external USB HDD is connected
        if ! mount | grep -q /media/storageBackupOS; then
          echo "Offsite HDD not mounted locally"
          exit
        else
          echo "+++++++++++++++++++++ Performing local offsite backup +++++++++++++++++++++"
        fi
elif [ "-offsite.rem" = $1 ] ; then
    # check external USB HDD is connected
        if ! mount | grep -q /Volumes/storageBackupOS; then
          echo "Offsite HDD not mounted remotely"
          exit
        else
          echo "+++++++++++++++++++++ Performing remote offsite backup +++++++++++++++++++++"
        fi
else
        echo "$1 invalid: define -onsite, -offsite.loc or -offsite.rem"
        exit
fi


# rdiff-backup
echo "********************* Performing rdiff-backup *********************"
if [ "-onsite" = $1 ] ; then
        cmd_rdiff="/usr/bin/rdiff-backup -v4 --print-statistics --force"
        src_rdiff=/media/storage
        dest_path=/media/backupstorage
elif [ "-offsite.loc" = $1 ] ; then
    cmd_rdiff="/usr/bin/rdiff-backup -v4 --print-statistics --force"
    src_rdiff=/media/storage
    dest_path=/media/storageBackupOS
elif [ "-offsite.rem" = $1 ] ; then
#    cmd_rdiff="/opt/homebrew/bin/rdiff-backup -v4 --print-statistics --force"
    cmd_rdiff="/usr/local/bin/rdiff-backup -v4 --print-statistics --force"
    src_rdiff=ssh://mywebsite.com::/media/storage
    dest_path=/Volumes/storageBackupOS
fi

    $cmd_rdiff \
    --exclude-sockets --exclude-device-files --exclude-fifo \
    --exclude ignorecase:'**.ini' \
    --exclude ignorecase:'**.DS_Store' \
    --exclude ignorecase:'**\$RECYCLE.BIN' \
    --exclude ignorecase:'**.AppleDouble' \
    --exclude ignorecase:'**.localized' \
       --include /media/storage/Media \
    --exclude '**' $src_rdiff \
    $dest_path

# rsync command configuration
rsync_excludes="--exclude '*.ini' \
    --exclude '*.DS_Store' \
    --exclude '**/\$RECYCLE.BIN' \
    --exclude '*.AppleDouble' \
    --exclude '*.localized'"

if [ "-onsite" = $1 ] ; then
        cmd_rsync="/usr/local/bin/rsync"
        rsync_options="-a --progress -l --delete $rsync_excludes"
elif [ "-offsite.loc" = $1 ] ; then
        cmd_rsync="/usr/bin/rsync"
        rsync_options="-a --progress -l --delete $rsync_excludes"
elif [ "-offsite.rem" = $1 ] ; then
        cmd_rsync="/usr/bin/rsync"
    rsync_options="-a --progress -l --delete $rsync_excludes"
fi

# rsync of /media/storage/svn
echo "********************* Performing rsync backup of svn *********************"
if [ "-onsite" = $1 ] ; then
        src_rsync=/media/storage/svn/                            # end with trailing slash
        dest_path=/media/backupstorage/svn                       # do not end with trailing slash
        mkdir -p /media/backupstorage/svn                        # do not end with trailing slash
elif [ "-offsite.loc" = $1 ] ; then
        src_rsync=/media/storage/svn/                            # end with trailing slash
        dest_path=/media/storageBackupOS/svn                     # do not end with trailing slash
        mkdir -p /media/storageBackupOS/svn                      # do not end with trailing slash
elif [ "-offsite.rem" = $1 ] ; then
        src_rsync=mywebsite.com:/media/storage/svn/           # end with trailing slash
        dest_path=/Volumes/storageBackupOS/svn                   # do not end with trailing slash
        mkdir -p /Volumes/storageBackupOS/svn                    # do not end with trailing slash
fi
        eval $cmd_rsync $rsync_options $src_rsync $dest_path



# rsync of rdiff-backup for /media/storage/Backup/Mac
echo "********************* Performing rsync backup of Mac *********************"
if [ "-onsite" = $1 ] ; then
        src_rsync=/media/storage/Backup/Mac/                            # end with trailing slash
        dest_path=/media/backupstorage/Backup/Mac                         # do not end with trailing slash
        mkdir -p /media/backupstorage/Backup/Mac                          # do not end with trailing slash
elif [ "-offsite.loc" = $1 ] ; then
        src_rsync=/media/storage/Backup/Mac/                # end with trailing slash
        dest_path=/media/storageBackupOS/Backup/Mac            # do not end with trailing slash
    mkdir -p /media/storageBackupOS/Backup/Mac            # do not end with trailing slash
elif [ "-offsite.rem" = $1 ] ; then
        src_rsync=mywebsite.com:/media/storage/Backup/Mac/          # end with trailing slash
        dest_path=/Volumes/storageBackupOS/Backup/Mac            # do not end with trailing slash
    mkdir -p /Volumes/storageBackupOS/Backup/Mac            # do not end with trailing slash
fi
        eval $cmd_rsync $rsync_options $src_rsync $dest_path



# rsync of rdiff-backup for /media/storage/Backup/MacM1 
echo "********************* Performing rsync backup of MacM1 *********************"
if [ "-onsite" = $1 ] ; then
        src_rsync=/media/storage/Backup/MacM1/                          # end with trailing slash
        dest_path=/media/backupstorage/Backup/MacM1                     # do not end with trailing slash
        mkdir -p /media/backupstorage/Backup/MacM1                      # do not end with trailing slash
elif [ "-offsite.loc" = $1 ] ; then
        src_rsync=/media/storage/Backup/MacM1/                # end with trailing slash
        dest_path=/media/storageBackupOS/Backup/MacM1            # do not end with trailing slash
    mkdir -p /media/storageBackupOS/Backup/MacM1                # do not end with trailing slash
elif [ "-offsite.rem" = $1 ] ; then
        src_rsync=mywebsite.com:/media/storage/Backup/MacM1/        # end with trailing slash
        dest_path=/Volumes/storageBackupOS/Backup/MacM1            # do not end with trailing slash
    mkdir -p /Volumes/storageBackupOS/Backup/MacM1              # do not end with trailing slash
fi
        eval $cmd_rsync $rsync_options $src_rsync $dest_path

```

---

