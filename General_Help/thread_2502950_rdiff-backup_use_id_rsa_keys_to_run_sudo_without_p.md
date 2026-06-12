---
title: "rdiff-backup: use id_rsa keys to run sudo without password (to maintain user:group) ?"
date: 2024-12-07
forum: General Help
---

### Post by freeflyjohn on 2024-12-07
I am using an rdiff-backup script to backup an internal HDD in the server to an external USB HDD.  

The  contents are mainly data files (documents, spreadheets, pdf, pictures  etc) but there is also an svn repository which has user **www-data **and group **svn**.

When using rdiff-backup without sudo, the user:group properties are lost (in this case for the svn folder backup).

To maintain the the user:group properties I have to use sudo but this means entering the password each time the script is ran.

I was wondering if its possible to use id_rsa keys so that rdiff-backup can be ran as sudo but without entering a password ?

If so how can this be implemented ?

For  example, I was wondering if one private key could be stored on the   server internal HDD and the other private key be stored on the external  USB HDD ?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294611&stc=1[/IMG]

---

### Post by TheFu on 2024-12-07
Or the easier way is to just put the backup script into root's crontab. Then you won't need sudo at all.

Of course, you could use the sudoers file to allow specific programs with specific options to be run without any password prompt.  The sudoers manpage is extensive and clearly explains how to do this.  It even has an "EXAMPLES" section, unlike most other manpages.  This is harder than using root's contrab, IMHO.

Using ssh to get around this is the long way around and hardly worth mentioning. I wouldn't do it that way until you graduate to remote backups.  I actually "pull" backups from many different client computers to my backup server with storage.  This is the only way to protect against cryptoware/malware that I know.  The trick is to ensure that none of the client machines have any access to the backup storage, if they do, then the client system with malware can destroy all the backup data.  For local, USB connected, backups, just don't leave the USB storage connected unless it is backup time. When finished, disconnect the storage to minimize the time malware has to do harm.

---

### Post by freeflyjohn on 2024-12-07
Thanks TheFu, I was hoping to get a reply from you as you’ve helped me greatly with rdiff-backup :)

I will look at the sudoers method and read the man page. 

I had a feeling about the risk with malware whilst having the usb hdd connected, so it’s good to know you confirmed this. I only intend to have the usb hdd connected only during a backup session to minimise this risk. 

I already use ssh to pull backups from my laptop (Mac) to the server over the LAN connection (again thanks to your help). 

I did try remote backups using WireGuard but couldn’t get around having to use sudo. So I have ditched that idea and will only use wired usb backups (with the exception of backing up my laptop over the LAN). 

Instead of remote backups I will keep offsite backup drives at my neighbours house and all my usb hdd are password protected.

---

### Post by TheFu on 2024-12-07
Using the crontab method would be 1000x easier.

---

### Post by freeflyjohn on 2024-12-07
crontab is a scheduled task though, isn't it ?

you set it to run a task on certain days at certain times ?

but that means manual intevntion to connect the usb hdd before the backup task is called by the crontab ?

---

### Post by TheFu on 2024-12-07
It can be run at reboot or at specific times or you could setup your script to recognize when the USB disk is connected+mounted and only then run the backups.

The USB being connected doesn't have to mean it is mounted.

---

### Post by freeflyjohn on 2024-12-07
> **TheFu said:**
> It can be run at reboot or at specific times or you could setup your script to recognize when the USB disk is connected+mounted and only then run the backups.

The USB being connected doesn't have to mean it is mounted.

Thats interesting, as I already have functionality in my backup script to recognise if the USB HDD is connected (see code below).

However, that would mean the backup would only happen when crontab calls the backup script, which would be at a certain date and time.

So to perform the backup, I would need to connect the USB HDD **BEFORE** the crontab calls the backup script ?

e.g. if I configured crontab to run the backup script daily at 5pm, I would need to connect the USB HDD **BEFORE** 5pm (or leave it connected and wait until the next day at 5pm).

I don't suppose the crontab can detect when the USB HDD is connected and then run the script ?

```

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

```

---

### Post by TheFu on 2024-12-07
> **freeflyjohn said:**
> Thats interesting, as I already have functionality in my backup script to recognise if the USB HDD is connected (see code below).

However, that would mean the backup would only happen when crontab calls the backup script, which would be at a certain date and time.

So to perform the backup, I would need to connect the USB HDD **BEFORE** the crontab calls the backup script ?

e.g. if I configured crontab to run the backup script daily at 5pm, I would need to connect the USB HDD **BEFORE** 5pm (or leave it connected and wait until the next day at 5pm).

I don't suppose the crontab can detect when the USB HDD is connected and then run the script ?


Your code to check for a specific mount is fine, but much more complex than mine.  I just place a .not-mounted file inside the directory where the file system gets mounted.  So, the check is whether that file exists or not. Simple.  When mounted, the filesystem hides that .not-mounted file.

As for waiting to mount the storage ... you can have a crontab run periodically - say every 30 minutes from 5pm - 8pm?  Have it check if the storage is mounted, if so, and if there isn't already a backup for that day, run a new backup. Not hard.

Or have it run at 10pm and when completed it shuts the computer down (or suspends it).

Crontab stuff doesn't need to be 1 time on 1 day.  There's also @REBOOT, which could be run first thing after a reboot, assuming you shutdown the computer daily or even weekly, this might be sufficient.

You don't have to disconnect the storage, just umount it or let **autofs** handle it for you.

Lots of options.

---

### Post by freeflyjohn on 2024-12-08
Thanks TheFu

What happens if the backup takes an hour but the script is called every 30 min ? 

Will it end up trying to make multiple backups ?

And how do you check if there isn't a backup for that day ?

Finally, in my script when I call rdiff-back do I use sudo ?

---

### Post by TheFu on 2024-12-08
> **freeflyjohn said:**
> Thanks TheFu

What happens if the backup takes an hour but the script is called every 30 min ? 

Then another backup process will be started.  Your script needs to ensure only 1 backup runs at a time.

> **freeflyjohn said:**
> Will it end up trying to make multiple backups ?
IDK, it might see the prior backup as corrupt and roll it back.  Best to ensure the script doesn't allow this.

> **freeflyjohn said:**
> And how do you check if there isn't a backup for that day ?
 There are thousands of different ways.  You can create a zero-length file at the start of the backup in a specific location and test for that BEFORE starting another backup.  You can look through the backup data (inside the rdiff-backup/) subdirectory and find information for each backup version, if there isn't one for "today", then keep going.  Since I use cron, once a day, I've never had this issue.  I've posted in these forums about daily backup reports. Those are just multi-part **egrep** searches on the specific files for each computer.  I get a generated "report" for each system that looks like this:
```
=== Time for Backups to nextcloud-lxd === 
StartTime 1733646214.00 (Sun Dec  8 03:23:34 2024)
EndTime 1733646228.73 (Sun Dec  8 03:23:48 2024)
ElapsedTime 14.73 (14.73 seconds)
MirrorFileSize 9531917354 (8.88 GB)
TotalDestinationSizeChange 798550 (780 KB)

```
just using **egrep**.  My backups start at 3:03am and are all finished by 3:25am.  I have some that run using a different backup server because the version of rdiff-backup is older and incompatible.  Those start at 2:02am and are all finished by 2:04am.

> **freeflyjohn said:**
> 
Finally, in my script when I call rdiff-back do I use sudo ?
Either sudo or root's crontab.  If you want permissions, owners, groups, maintained, then backups need to be run with a user that has a uid of 0. That's standard Unix stuff. No easy way around it to my knowledge,

---

