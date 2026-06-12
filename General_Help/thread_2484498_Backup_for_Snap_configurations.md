---
title: "Backup for Snap configurations?"
date: 2023-02-28
forum: General Help
---

### Post by TheFu on 2023-02-28
I hope this is something simple, but I haven't found it.
As snap packages are used for more complex needs, how can we capture the special configurations we've made using the **snap set** commands? 

For example, I bet most people connect removable media and limit the total copies of snaps to 2, instead of the default 3, and perhaps they limit how often snaps can be updated to specific days of the week only to prevent interruptions to their work.  How can we capture this data for our backup/restore needs in a flexible way.  Flexible means on a per-snap basis, since during restore, we probably won't put all the same services onto the say systems.

```
$ sudo snap get system --all
```
doesn't work.
```
$ sudo # snap get system refresh
Key             Value
refresh.retain  2
refresh.timer   sat
```
requires knowing the setting to retrieve it.  That's beyond cumbersome.  How can I get a list for all of them.

I have to be missing something. Certainly, they don't expect users to create JSON to query every possible parameter using the REST API.
Needed for 20.04 and later desktops and servers.

This is also needed to backup lxd managed lxc containers, since many will have external storage connections specific to the container or special network settings.

---

### Post by aljames2 on 2023-02-28
Does a read through this give any help.  A bit over my head, sorry I have no real knowledge in this space.  It makes sense though to want to control snap activity in order to prevent unwanted interruptions during backups or other processes.
[https://ubuntu.com/blog/how-to-manage-snap-updates](https://ubuntu.com/blog/how-to-manage-snap-updates)

---

### Post by ian-weisser on 2023-02-28
Hmmm. See if [https://snapcraft.io/docs/snapshots](https://snapcraft.io/docs/snapshots) adds any light.

Particularly this section on using snapshots for backup/restore:

> 
**Inside a snapshot**

 Snapshots are stored as a *zip* file for each snap, and each zip file contains the following:
 
[LIST]
[*] **meta.json**: describes the contents of the snapshot, alongside its configuration and checksums for the archives. 
[*] **archive.tgz**: contains system data. 
[*] **user/<username>.tgz**: contains any user data (for each system user). 
[/LIST]
 
On Ubuntu-based systems, snapshots are stored in the /var/lib/snapd/snapshots directory.




Snapshots can also be exported/imported, specifically for backup purposes.

Also, according to [https://snapcraft.io/docs/data-locations](https://snapcraft.io/docs/data-locations) , 

- System configuration data should be at  /var/snap/<snap name>/common
- User configuration data should be at  /home/<username>/snap/<snap name>/common

---

### Post by Holger_Gehrke on 2023-02-28
You might want to try
```

sudo snap get system -d

```
The '-d' option forces snap to return a JSON document and 'snap set' has an option (-t) to parse it's parameter as a JSON document (so that should take care of how to restore backed up settings, I hope)

Or you could use the REST-API as described in [https://snapcraft.io/docs/snapd-api](https://snapcraft.io/docs/snapd-api) :
```

sudo curl -sS --unix-socket /run/snapd.socket http://localhost/v2/system-info | jq

```

I'm rather certain that there's a database or some files where snap stores all these settings, but up to now I haven't looked for them ...

Holger

---

### Post by TheFu on 2023-02-28
> **ian-weisser said:**
> Hmmm. See if [https://snapcraft.io/docs/snapshots](https://snapcraft.io/docs/snapshots) adds any light.

Particularly this section on using snapshots for backup/restore:
Snapshots can also be exported/imported, specifically for backup purposes.

Also, according to [https://snapcraft.io/docs/data-locations](https://snapcraft.io/docs/data-locations) , 

- System configuration data should be at  /var/snap/<snap name>/common
- User configuration data should be at  /home/<username>/snap/<snap name>/common

Thanks.  "Snapshots" that result in tgz files are a failure to me.  I have a backup solution that understands versioned files and would like to use that. I don't want new files created with time-stamps or directories named with a timestamp having all the data included each time. To me, that's like using ZIP for system backups.  For people who don't do backups all the time, I can understand the good feeling that each new backup being 100% stand-alone would bring.  That isn't me.

The snaps I want to backup are system-level, not user-level programs.  For example, I have the nextcloud snap running with the programs and backups in /var/snap/nextcloud/common/.
Backups created by **nextcloud.export** look like this with time-stamped directories.
```
# tree -L 3 -d /var/snap/nextcloud/common/
/var/snap/nextcloud/common/
&#9500;&#9472;&#9472; backups
&#9474;** &#9500;&#9472;&#9472; 20230228-110921
&#9474;** &#9474;** &#9500;&#9472;&#9472; apps
&#9474;** &#9474;** &#9492;&#9472;&#9472; data
&#9474;** &#9492;&#9472;&#9472; 20230228-162248
&#9474;**     &#9500;&#9472;&#9472; apps
&#9474;**     &#9492;&#9472;&#9472; data
&#9492;&#9472;&#9472; nextcloud
    &#9500;&#9472;&#9472; data
    &#9474;** &#9500;&#9472;&#9472; appdata_zyxabctmyydv
    &#9474;** &#9500;&#9472;&#9472; files_external
    &#9474;** &#9500;&#9472;&#9472; ann
    &#9474;** &#9500;&#9472;&#9472; dad
    &#9474;** &#9500;&#9472;&#9472; eileen
    &#9474;** &#9500;&#9472;&#9472; mom
    &#9474;** &#9500;&#9472;&#9472; rachel
    &#9474;** &#9492;&#9472;&#9472; thefu
    &#9492;&#9472;&#9472; tmp
        &#9492;&#9472;&#9472; news

```
The exported data isn't suitable for my backup requirements due to the timestamp directories. Fortunately, getting the NC applications, NC settings, NC data and NC dumped DBMS isn't hard.  I'll probably end up scripting renaming the time-stamped directory name to a unique name to be included by my normal backup tool and let it handle the versioning.  Would be nice of the nextcloud.export tool allowed forcing the same output directory to be used.  Sigh.

Thanks for the information. It does help - for the typical stuff, but not the container environment stuff.

More stuff to research ... and need to read the next post carefully.

---

### Post by TheFu on 2023-02-28
Just to be clear, I don't care to backup programs or packages. Those are trivial to replace.

It is the customized settings and local data that matter.  

So the **lxc** command to add 3 external storage locations to a container, THAT's the information I'd like to capture for backups and have part of the restore process.  

Spent the last 2 hrs trying different commands.  Looks like
```
lxc config show nextcloud-lxd --expanded
```
is the per-instance command. 

If this seems unclear, it is partially because I remember entering about 10 **lxc config set** commands, but don't recall exactly what they were. Some were required ... and I was careful to NOT remove the non-root running aspect for any containers.
```
lxc  config show --debug
```
Has lots of stuff, but not the ALL stuff I entered, just some if it from the **lxd init** command.

**lxc config show** or ```
lxc config device list  nextcloud-lxd
```
Found it!
```
$ lxc config device show nextcloud-lxd 
```

I'm sure there's a subtle difference between "show" and "list" options that I'm not getting.  Now I just need to figure out the other 9 custom settings and how to get them back out.  I'd hate to have to manually track these things.  That's like asking someone to track manually installed deb packages.  

Part of the problem is lxd is a snap too.  So the lxc containers are managed by lxc command included in the snap and the container is running a nextcloud snap inside it.  

I didn't want nextcloud polluting my hostOS, hence the use of an lxd managed container to have each major application separate.  I'd not needed any special settings in the other lxc instances running here for the last few years, beyond using bridged networking.  Perhaps I'll go with the docker method of port forwarding specific ports in the future. The snap for nextcloud forced non-default settings.

Really want to dump all settings for all container configs 1 time. I suppose ```

Usage:
  lxc export [<remote>:]<instance> [target] [--instance-only] [--optimized-storage] [flags]
```
may be the only way. Hard to tell.  It has some caveats.  First, lxc export isn't supported in lxc v3.x, which means it doesn't work for most of my lxc containers.  I haven't researched why lxc is v3.0.3 on the system with lxd 5.11 installed.   It is in the 20.04 lxc package, v5.11.  Appears that lxc was separate in 18.04, but was merged into the lxd snap package sometime later.  
Yet another rabbit hole to follow.

The manpages for lxd and lxc have the most concise information I've found all in one place, but it is huge and somehow there aren't any manpages for either lxc or lxd on my 20.04 install.  Rabbit hole #2.

---

### Post by ian-weisser on 2023-02-28
> **TheFu said:**
> Now I just need to figure out the other 9 custom settings and how to get them back out.

My own method is to keep notes about exactly how to reinstall and reconfigure everything from bare metal.

When I was young, I thought "*Aw, I will remember it*". That turned out exactly as one might expect: I remembered nothing.

Now, if I successfully install something, I promptly tear it back out by the roots.
Then deliberately start over with my notes file handy, diligently recording each step, each test, each web page or source file or reference.
Then I tear it out again and follow my notes, step-by-step, to install it a third time.

I have used those notes to reinstall containers a couple times. But turns out I have used those notes for maintenance and repair far more often than for recovery.

Younger me would laugh at doing it three times. But then younger me would be impressed by the glowing health of my *maintained *systems, and the lack of data loss for over a decade.

---

### Post by TheFu on 2023-02-28
[https://www.cyberciti.biz/faq/how-to-backup-and-restore-lxd-containers/](https://www.cyberciti.biz/faq/how-to-backup-and-restore-lxd-containers/) does the lxd/lxc stuff, I hope.  Ah ... it doesn't work in the lxc version I need to migrate off.  Sigh.

This afternoon, my screwing around took down the LAN DNS and email gateway and a few other containers.  Bringing those backup up are priority now and lxd refuses to start ... spent 2 yrs trying to solve the issue and decided to rebuild them on a different system since the other host is on 18.04 and needs to be pushed to a different hostOS shortly.

---

### Post by TheFu on 2023-03-01
Seems /var/snap/lxd/common/lxd has good stuff in it, but also some images/ ... which I'm trying to avoid.  The lxd DBs are sqlite3 and those are in /var/snap/lxd/common/lxd/database/. The security/ and perhaps devices/ directories there could be useful as well. How?  IDK.   If the DBs become corrupt, having a backup is important.  Still looking at the other things below there that are needed to recreate a setup 100%, preferably via automation. On the old lxd/lxc version, I'm not hopeful.

Added zfs information to the backup data capture too. Doubt I have all that is needed, but when it is scripted, it can be incrementally improved.

Got my "pull" backups working for the new lxc instances created yesterday.  Still need to migrate some less important lxc containers off the 18.04 box, which is hard since the entire lxd/lxc subsystem is broke due to a corrupted DB.  
The system receiving this added workload is running short on RAM.  I have 16G more around here somewhere.  Just need to find it.
Happy to say the steps to setup a root-equiv account are 100% working every time. That's needed for the pull backups to capture everything.  

When I get this working and it isn't embarrassing code, I'll post it somewhere. Unfortunately, it isn't trivial code, so it won't help most users there.  Perhaps just the people using LVM and/or ZFS snapshots as part of their backup methodology would care for the complexity my backups have become.  I have little confidence that I could restore anything besides the data for the lxc backups at this point. Suppose that's a start.  Wish I'd be happy using ZFS snapshots + zsend to another machine as a viable versioned backup solution.  I don't think that's sufficient and the space requirements would likely explode.

---

### Post by MAFoElffen on 2023-03-02
Please do post what you come up with!!! Pretty please? I am following this with very much interest in what you find out, and what you find that works. That would definitely make life easier.

Like Ian, I 'try' to keep good notes, but after re-reading them from time to time, I have to do it again to figure out what I was thinking at the time (LOL).

---

### Post by TheFu on 2023-03-02
So, with lots of assumptions, seems that **snap save** run on the lxd host system will create a full ZIP file of lxd settings, configs, DBs, all lxc containers and data for all users.  I have ZFS setup for the storage pool used by lxd, but /var is an LVM LV.  

```
$ sudo snap save lxd
$ sudo ls -l /var/lib/snapd/snapshots/
total 1120224
-rw------- 1 root root 1147103316 Mar  2 08:31 2_lxd_5.11-ad0b61e_24483.zip

```
That lxd zip "snapshot" is for ISO/rootfs images, too.  Looks like everything under /var/snap/lxd/common/
```
# du -sh  /var/snap/lxd/* 
4.0K    /var/snap/lxd/24323
4.0K    /var/snap/lxd/24483
1.2G    /var/snap/lxd/common
0       /var/snap/lxd/current
```
The resulting zip says 0% compression. Inside 2_lxd_5.11-ad0b61e_24483.zip, are:
```
$ tree 
.
&#9500;&#9472;&#9472; archive.tgz
&#9500;&#9472;&#9472; meta.json
&#9500;&#9472;&#9472; meta.sha3_384
&#9492;&#9472;&#9472; user
    &#9500;&#9472;&#9472; thefu.tgz
    &#9492;&#9472;&#9472; root.tgz

```
The contents of the archive.tgz includes all the configs and storage for each container.  So, if you want to migrate everything from one LXD host to another, use that command to create a snapshot.  

I've read about an **lxc export** command which isn't supported on my 20.04 system.  I have lxd 5.11 and lxc 4.0.12.
[Https://www.cyberciti.biz/faq/how-to-backup-and-restore-lxd-containers/](Https://www.cyberciti.biz/faq/how-to-backup-and-restore-lxd-containers/) has a script to loop over lxc instances and back them up in series.

None of these methods are friendly towards versioned backups.  They are nearly the same as creating an disk image that can be imported.
As an example concerning the bloat involved, 
```
$ du -h *
4.0K    lxd.config.2023-03-02
4.0K    lxd.instances.list.2023-03-02
4.0K    lxd-version.2023-03-02
3.8G    nextcloud-lxd-bkp-2023-03-02.tar.xz
1.8G    pihole2-bkp-2023-03-02.tar.xz
890M    spam2-bkp-2023-03-02.tar.xz
```

For my normal backups, these are the sizes:
```
$ sudo rdiff-backup --list-increment-sizes  **spam2**
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Mar  2 00:03:16 2023         3.73 MB           3.73 MB   (current mirror)
Wed Mar  1 08:38:30 2023         1.42 KB           3.74 MB

$ sudo rdiff-backup --list-increment-sizes  **spam1**
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Tue Feb 28 00:03:28 2023         6.34 MB           6.34 MB   (current mirror)
Mon Feb 27 00:03:28 2023         1.07 KB           6.34 MB
Sun Feb 26 00:03:37 2023         1.07 KB           6.34 MB
Sat Feb 25 00:03:25 2023         1.29 KB           6.34 MB
Fri Feb 24 00:03:29 2023         2.85 KB           6.35 MB
...
Tue Jul  5 01:01:30 2022       947 bytes           6.80 MB
Mon Jul  4 01:03:47 2022       947 bytes           6.80 MB
Sun Jul  3 01:01:39 2022       997 bytes           6.80 MB

```
So with daily backups going back to Last July, the versioned backups are less than 7MB compared to 1 "snapshot" of 900MB, which will be that size every day.  I'd rather not waste 1GB/day to backup a single container when less than 10MB is sufficient for an entire year.

Perhaps I'm not being fair.  Let's look at a nextcloud backup. 
3.8G    nextcloud-lxd-bkp-2023-03-02.tar.xz   # for a single "snapshot"
vs
```
$ sudo rdiff-backup --list-increment-sizes nextcloud
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Tue Feb 28 00:05:59 2023         8.49 GB           8.49 GB   (current mirror)
Mon Feb 27 00:06:00 2023         2.74 KB           8.49 GB
Sun Feb 26 00:06:33 2023         12.0 MB           8.50 GB
Sat Feb 25 00:05:50 2023         3.06 KB           8.50 GB
Fri Feb 24 00:06:21 2023         3.34 KB           8.50 GB
Thu Feb 23 00:06:41 2023         54.3 MB           8.55 GB
...
Sat Dec  3 00:05:43 2022         63.4 MB           14.2 GB
Fri Dec  2 10:41:49 2022         55.9 MB           14.2 GB
Fri Dec  2 00:06:09 2022         6.42 MB           14.2 GB

```
So, 90 days of versioned backups take 15G of storage or 1 "snapshot" is 3.8G?  3.8 x 90 = 342GB.

Hopefully, I've made the point that images and tgz "snapshots" are nowhere near as efficient as versioned backups.

BTW, the nextcloud-lxd system was installed a few days ago. Last night was the first "normal" backup ... but the versioning seems to be working:
```
$ sudo rdiff-backup --list-increment-sizes nextcloud-lxd
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Mar  2 00:06:30 2023          785 MB            785 MB   (current mirror)
Wed Mar  1 09:23:16 2023          468 KB            785 MB
```
Time will tell.

I'm not using any LVM snapshots here.  The container storage is ZFS
```
# df -Th
Filesystem                                   Type           Size  Used Avail Use% Mounted on
lxd/containers/nextcloud-lxd                 zfs             45G  4.2G   41G  10% /
```

For nextcloud-lxd, the backup script "pulls" the backups, so it runs on a backup server system, connects to the remote nextcloud-lxd system over ssh (multiple times), does some pre-backup stuff, then finally uses rdiff-backup to pull the data to the backup server.
```

#!/bin/bash

TGT="/d/D7/backups/$REMOTE"
REMOTE="nextcloud-lxd"  # Remote system
RUSER=back1134  # Remote system "root" equiv account
DAYS="90D"      # Days of backups to retain
NC_SNAP_BAK_TOP="/var/snap/nextcloud/common/backups"

source /usr/local/sbin/pull-backup-UTILS.sh
#   To use, just call "Pre-Backup-Info() function"
    Pre-Backup-Info &> /dev/null

# ##################[ Nextcloud Backup Data+Apps ]##################
echo "INFO: Export the nextcloud snap data, db, config.php and user data"

ssh $RUSER@$REMOTE 'bash -s' <<END_NC_BACK
# Step 1: remove the last backup directory
/usr/bin/rm -rf "$NC_SNAP_BAK_TOP/current.bak"

# Step 2: Export the nextcloud snap data, db, config.php and user data
#         The redirection should retain stderr output, just not stdout
#         50K lines of junk.
/snap/bin/nextcloud.export > /dev/null

# Step 3: Move the time-stampped backup directory to "current.bak" so 
#         a real versioning backup tool can be efficient with files 
#         that didn't change. Aka - rdiff-backup
/usr/bin/mv  $NC_SNAP_BAK_TOP/20* "$NC_SNAP_BAK_TOP/current.bak"
END_NC_BACK

echo "INFO: TODO capture snap settings for NC and snap system"
sudo ssh $RUSER@$REMOTE 'bash -s' <<END_LXD_BACK
/usr/bin/snap get system -d > /root/backup/snap-system-settings.txt
/usr/bin/curl -sS --unix-socket /run/snapd.socket \
              Http://localhost/v2/system-info |\
              /usr/bin/jq > /root/backup/snap-system-info.txt
END_LXD_BACK
echo "INFO: Running  rdiff-backup $DIRS $RUSER@$REMOTE::/  $TGT"
/usr/bin/rdiff-backup  --exclude-sockets --exclude-device-files --exclude-fifos \
        --exclude '**/.cache/mozilla' \
        --exclude '**/.cache/chromium' \
        --include /root \
        --include /etc \
        --include /usr/local \
        --include $NC_SNAP_BAK_TOP/current.bak \
        --include /home \
        --exclude '**' $RUSER@$REMOTE::/  "$TGT"

# Remove older backups .... 
echo "INFO: Removing backups older than $DAYS"
/usr/bin/rdiff-backup  --remove-older-than "$DAYS"  --force "$TGT"

    Post-Backup-Cleanup

```

I left out lots of setup and helper functions that get sourced. Also, externally connected storage (lxd external mounts) isn't included.  Those helper functions fill /root/backup/ with system data as text files to make restoring to a new system easier. Some of the data captured is just handy for problem solving which don't need file restores.

The remote system doesn't have any pre-installed scripts. Those are all xferred over as part of the UTILS and the script above.  I use *heredocs* for that. Wrapping your head around which system any specific code in the script is running inside can be challenging for less experienced people.

The script will probably get tweaked a few more times.  What I'll probably end up with is either a weekly or monthly "snapshot" tgz combined with the daily versioned backups trying to achieve the best solution.  More complications.

---

### Post by ian-weisser on 2023-03-02
You seem to have identified a use case. You should tell the snapcraft team about it. Perhaps they will add a feature for versioned backups of settings.

---

### Post by #&amp;thj^% on 2023-03-02
Looks Great....very useful share.

---

### Post by TheFu on 2023-03-02
> **ian-weisser said:**
> You seem to have identified a use case. You should tell the snapcraft team about it. Perhaps they will add a feature for versioned backups of settings.

The last few years, I've been dissatisfied with my interactions with the snap/lxd teams.  We are both stubborn. Really wish lxd wasn't tied to snaps.  I understand that the next stable Debian release will have an lxd .deb package, not tied to snaps at all. [https://wiki.debian.org/LXD](https://wiki.debian.org/LXD)  Stripping out the snap dependency should make things less convoluted. At least that is my hope.

---

### Post by #&amp;thj^% on 2023-03-05
I can only add lxd on Debian is a breath of fresh air:
```
apt policy lxd
lxd:
  Installed: 5.0.2-2+b2
  Candidate: 5.0.2-2+b2
  Version table:
 *** 5.0.2-2+b2 990
        990 http://deb.debian.org/debian sid/main amd64 Packages
        990 http://ftp.us.debian.org/debian sid/main amd64 Packages
        100 /var/lib/dpkg/status


```
I'm just hinting here, but Debian Testing has been more trouble free than Ubuntu...in fact I've not had one thing break on my side in 6 months time.
@TheFu, I'm just talking, I know better to suggest anything testing in your direction.
But I've found a new home. ;)

---

