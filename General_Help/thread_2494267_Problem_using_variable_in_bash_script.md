---
title: "Problem using variable in bash script"
date: 2024-01-10
forum: General Help
---

### Post by freeflyjohn on 2024-01-10
I have the following script which sets the varibale 'cmd_rsync' for the rsync command...

```

        [COLOR=#ff0000]cmd_rsync="/usr/bin/rsync -a --progress -l --delete --rsh='ssh -p 12345'"[/COLOR]
[COLOR=#a9a9a9]        src_rsync=user@192.168.6.1:/media/storage/
        dest_path=/Volumes/storageBackupOS    [/COLOR]             

        $cmd_rsync \
        --exclude '*.ini' \
        --exclude '*.DS_Store' \
        --exclude '$RECYCLE.BIN' \
        --exclude '*.AppleDouble' \
        --exclude '*.localized' \
        user@192.168.6.1:/media/storage/ \
        /Volumes/storageBackupOS/

```

But it fails with the following error...

```

building file list ... 
rsync: link_stat "/Users/username/Downloads/12345'" failed: No such file or directory (2)
rsync: link_stat "/Users/username/Downloads/user@192.168.6.1:/media/storage/." failed: No such file or directory (2)
0 files to consider

sent 29 bytes  received 20 bytes  98.00 bytes/sec
total size is 0  speedup is 0.00

```

However, if I replace the varibale for the rsync command it works...

```

[COLOR=#a9a9a9]        cmd_rsync="/usr/bin/rsync -a --progress -l --delete --rsh='ssh -p 12345'"[/COLOR]
        src_rsync=user@192.168.6.1:/media/storage/      
        dest_path=/Volumes/storageBackupOS                 

        [COLOR=#ff0000]/usr/bin/rsync -a --progress -l --delete --rsh='ssh -p 12345' \[/COLOR]
        --exclude '*.ini' \
        --exclude '*.DS_Store' \
        --exclude '$RECYCLE.BIN' \
        --exclude '*.AppleDouble' \
        --exclude '*.localized' \
        user@192.168.6.1:/media/storage/ \
        /Volumes/storageBackupOS

```

I'm also trying to use the variables 'src_rsync' and 'dest_path', but when I use those in the script (as shown below) it just hangs...

```

[COLOR=#a9a9a9]        cmd_rsync="/usr/bin/rsync -a --progress -l --delete --rsh='ssh -p 12345'"[/COLOR]
        src_rsync=user@192.168.6.1:/media/storage/      
        dest_path=/Volumes/storageBackupOS                

        [COLOR=#ff0000]/usr/bin/rsync -a --progress -l --delete --rsh='ssh -p 12345' \[/COLOR]
        --exclude '*.ini' \
        --exclude '*.DS_Store' \
        --exclude '$RECYCLE.BIN' \
        --exclude '*.AppleDouble' \
        --exclude '*.localized' \
[COLOR=#ff0000]        $src_rsync \
        $dest_path[/COLOR]

```

---

### Post by TheFu on 2024-01-10
Keep options separate from the program.  They are kept together as a single program if put into a single variable.

---

### Post by MAFoElffen on 2024-01-10
I'm thinking if you are chaining variables together fora organization, that this should expand correctly...
```

#!/bin/bash

cmd_rsync=/usr/bin/rsync 
rsync_excludes="--exclude '*.ini' \
    --exclude '*.DS_Store' \
    --exclude '$RECYCLE.BIN' \
    --exclude '*.AppleDouble' \
    --exclude '*.localized' "
rsync_options="-a --progress -l --delete --rsh='ssh -p 12345' $rsync_excludes"
src_rsync=user@192.168.6.1:/media/storage/
dest_path=/Volumes/storageBackupOS                 

$cmd_rsync $rsync_options $src_rsync $dest_path

```

---

### Post by freeflyjohn on 2024-01-11
Thanks MAFoElffen

I tried your code but its still not working, the error is...


```

Performing remote offsite backup...
/usr/bin/rsync -a --progress -l --delete --rsh='ssh -p 12345'
Unexpected remote arg: user@192.168.6.1:/media/storage/
rsync error: syntax or usage error (code 1) at main.c(1499) [sender=3.2.3]

```

```

#!/bin/bash
# rsync of /media/storage/svn

if [ "-onsite" = $1 ] ; then
        cmd_rsync="/usr/local/bin/rsync -a --progress -l --delete"
        src_rsync=/media/storage/svn/                            
        dest_path=/media/backupstorage/svn                                            
elif [ "-offsite.loc" = $1 ] ; then
        cmd_rsync="/usr/bin/rsync -a --progress -l --delete"
        src_rsync=/media/storage/svn/                            
        dest_path=/media/storageBackupOS/svn                                         
elif [ "-offsite.rem" = $1 ] ; then
    cmd_rsync=/usr/bin/rsync
    rsync_excludes="--exclude '*.ini' \
        --exclude '*.DS_Store' \
        --exclude '$RECYCLE.BIN' \
        --exclude '*.AppleDouble' \
        --exclude '*.localized' "
    rsync_options="-a --progress -l --delete --rsh='ssh -p 12345' $rsync_excludes"
    src_rsync=user@192.168.6.1:/media/storage/
    dest_path=/media/psf/storageBackupOS
fi
    $cmd_rsync $rsync_options $src_rsync $dest_path

```

---

### Post by freeflyjohn on 2024-01-11
Fixed it by using eval in front, as shown below...

```
eval $cmd_rsync $rsync_options $src_rsync $dest_path
```

---

### Post by TheFu on 2024-01-11
There are a few failures possible with that script.  It doesn't handle every possible path.

I can assure you that if you split the command to be separate from the options, and correctly quote-escape the values as needed, it will work.

---

### Post by freeflyjohn on 2024-01-11
Thanks TheFu

The script I posted is only a snippet and slightly modified.

The actual script is shown below, so hopefully this resolves your concerns ?

[COLOR=#000000]For rsync, the command is separate from the options (as suggested by [/COLOR][COLOR=#000000]MAFoElffen)[/COLOR][COLOR=#000000].  

The separate variables are $[/COLOR]cmd_rsync, $rsync_options, $src_rsync and $dest_path

Strangely, I didn't have the same issues with rdiff-backup as the single string variable seem to work.  

Therefore I didn't have to split up the rdiff-backup command, I only had to split up the rsync command.

One issue I haven't resolved yet is the exclude file....

```
--exclude '$RECYCLE.BIN'
```

I think this is resolving to .BIN, presumably because of the $ symbol before RECYCLE ?

For some reason, I am also having to use the --force option with rdiff-backup, which I have never had to do before.  

Without the --force option, I get the following error...

```
The directory exists, but does not look like a rdiff-backup directory.  Running
rdiff-backup like this could mess up what is currently in it.  If you
want to update or overwrite it, run rdiff-backup with the --force
option.
```

I thought the issue started when I added the USB HDD to fstab, but that was a red herring.

The error even seems to happen when doing a remote offsite backup over VPN, so I now always have to use --force option, which I'm not fully comfortable with considering I never had to use it before.

Below is my actual script...

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
        echo "Performing onsite backup..."
elif [ "-offsite.loc" = $1 ] ; then
        echo "Performing local offsite backup..."
elif [ "-offsite.rem" = $1 ] ; then
        echo "Performing remote offsite backup..."
else
        echo "Parameter missing: define -onsite, -offsite.loc or -offsite.rem"
        exit
fi




# rdiff-backup
if [ "-onsite" = $1 ] ; then
        cmd_rdiff="/usr/bin/rdiff-backup -v4 --print-statistics --force"
        src_rdiff=/media/storage
        dest_path=/media/backupstorage
elif [ "-offsite.loc" = $1 ] ; then
    cmd_rdiff="/usr/bin/rdiff-backup -v4 --print-statistics --force"
    src_rdiff=/media/storage
    dest_path=/media/storageBackupOS
elif [ "-offsite.rem" = $1 ] ; then
    cmd_rdiff="/opt/homebrew/bin/rdiff-backup -v4 --print-statistics --force"
    src_rdiff=ssh://user@192.168.6.1:12345::/media/storage
    dest_path=/Volumes/storageBackupOS
fi
    $cmd_rdiff \
    --exclude-special-files \
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
    --exclude '$RECYCLE.BIN' \
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
    rsync_options="-a --progress -l --delete --rsh='ssh -p 12345' $rsync_excludes"
fi




# rsync of /media/storage/svn


if [ "-onsite" = $1 ] ; then
        src_rsync=/media/storage/svn/                            # end with trailing slash
        dest_path=/media/backupstorage/svn                       # do not end with trailing slash
        mkdir -p /media/backupstorage/svn                        # do not end with trailing slash
elif [ "-offsite.loc" = $1 ] ; then
        src_rsync=/media/storage/svn/                            # end with trailing slash
        dest_path=/media/storageBackupOS/svn                     # do not end with trailing slash
        mkdir -p /media/storageBackupOS/svn                      # do not end with trailing slash
elif [ "-offsite.rem" = $1 ] ; then
        src_rsync=user@192.168.6.1:/media/storage/svn/      # end with trailing slash
        dest_path=/Volumes/storageBackupOS/svn                   # do not end with trailing slash
        mkdir -p /Volumes/storageBackupOS/svn                    # do not end with trailing slash
fi
        eval $cmd_rsync $rsync_options $src_rsync $dest_path




# rsync of rdiff-backup for /media/storage/Backup/Mac
if [ "-onsite" = $1 ] ; then
        src_rsync=/media/storage/Backup/Mac/                            # end with trailing slash
        dest_path=/media/backupstorage/Backup/Mac                         # do not end with trailing slash
        mkdir -p /media/backupstorage/Backup/Mac                          # do not end with trailing slash
elif [ "-offsite.loc" = $1 ] ; then
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

### Post by TheFu on 2024-01-11
Try 
```
--exclude '\$RECYCLE.BIN'
```

Actually, I'd use 
```
--exclude '**/\$RECYCLE.BIN'
```
to handle all of them, everywhere, on other storage too.

A typical rdiff-backup looks like this:
```

RDIFF_B="/usr/bin/rdiff-backup"
$RDIFF_B --exclude-sockets --exclude-device-files --exclude-fifos \
        --exclude '**/.cache/mozilla' \
        --exclude '**/.cache/chromium' \
        --exclude '**/NextCloud' \
        --include /usr/local \
        --include /var/snap/lxd/common/lxd/database \
        --include /var/snap/lxd/common/lxd/security \
        --include /etc \
        --include /home \
        --include /root \
        --include /d/rom/raid/media \
        --exclude '**'       $RUSER@$REMOTE::/      "$TGT"
```

Excluding special files isn't enough.  I know my older posts show that, but we need to specifically use the three excludes I have above.
This isn't correct:
```
   cmd_rdiff="/usr/bin/rdiff-backup -v4 --print-statistics --force"
```
it needs to be split into 2 separate variables
```
cmd_rdiffb="/usr/bin/rdiff-backup"
opts_rdiffb="-v4 --print-statistics --force"
```
Hope that clarifies it.

As for rsync, 
```
#!/bin/bash 
RSYNC="/usr/bin/rsync"
RSYNC_OPTS="-ar --stats --info=progress2  --delete-during"
EXCLUDES="--exclude **/.Trash* --exclude lost+found --exclude ZCS-2012"
/bin/rm -rf /d/D[1-7]/.Trash-1000
ionice $RSYNC  $RSYNC_OPTS  $EXCLUDES  /d/D1/ /d/b-D1/
ionice $RSYNC  $RSYNC_OPTS  $EXCLUDES  /d/D2/ /d/b-D2/
....

```
I keep the options separate from the command. None of your examples shows that.

I don't backup NTFS storage, so there's no RECYCLE.BIN.  NTFS storage is untrusted. I get anything on it off, ASAP.  I've had too many data corruption problems with NTFS in my environment. To be far, I think the NTFS corruption is caused by a cheap hardware device using old, old, old, ntfs-3g code. The device has 1 button, so I don't have any direct access to the firmware. No updates have ever been available for it, without replacing the hardware.  I actually doubt that newer versions of this hardware have any newer code inside.

---

### Post by MAFoElffen on 2024-01-11
Now I see the bigger picture of the use case...

Hmmm. Good tidbits from both.

---

### Post by freeflyjohn on 2024-01-11
Thanks TheFu,

I shall try your fix for RECYCLE.BIN and add the 3 exclusions you mentioned for rdiff-backup.

Regarding rsycn, doesnt the following part of the script keep the options separate from the command (i.e. cmd_rsync and rsync_options) ?

```

if [ "-onsite" = $1 ] ; then        cmd_rsync="/usr/local/bin/rsync"
        rsync_options="-a --progress -l --delete $rsync_excludes"
elif [ "-offsite.loc" = $1 ] ; then
        cmd_rsync="/usr/bin/rsync"
        rsync_options="-a --progress -l --delete $rsync_excludes"
elif [ "-offsite.rem" = $1 ] ; then
        cmd_rsync="/usr/bin/rsync"
    rsync_options="-a --progress -l --delete --rsh='ssh -p 12345' $rsync_excludes"
fi
```

I didn't split up the rdiff-backup command and arguments as I didn't get a runtime error like I did with rsync.

I'm currently trying the offsite remote backup, but Im not sure if rdiff-backup is working.

The console just displays the following (I left it for around 30min)...

```

sudo ./backup-storage.sh -offsite.rem
Performing remote offsite backup...
user@192.168.6.1's password: 

```

Usually rdiff-backup displays more than this (as shown below).

I was unsure if it was working so I pressed CTRL-C and then the rest of the rdiff-backup was displayed...

```


^CWarning: Local version DEV does not match remote version 2.0.0.
Found interrupted initial backup. Removing...
Fatal Error: Killed with signal 2
Using rdiff-backup version DEV
	with cpython /opt/homebrew/opt/python@3.10/bin/python3.10 version 3.10.9
	on macOS-14.2.1-arm64-arm-64bit, fs encoding utf-8
Executing ssh -C ssh://user@192.168.6.1:12345 rdiff-backup --server
-----------------------------------------------------------------
Detected abilities for source (read only) file system:
  Access control lists                         On
  Extended attributes                          On
  Windows access control lists                 Off
  Case sensitivity                             On
  Escape DOS devices                           Off
  Escape trailing spaces                       Off
  Mac OS X style resource forks                Off
  Mac OS X Finder information                  Off
-----------------------------------------------------------------
Unable to import module (py)xattr.
Extended attributes not supported on filesystem at /Volumes/storageBackupOS/rdiff-backup-data/rdiff-backup.tmp.0
Unable to import module posix1e from pylibacl package.
POSIX ACLs not supported on filesystem at /Volumes/storageBackupOS/rdiff-backup-data/rdiff-backup.tmp.0
Unable to import win32security module. Windows ACLs
not supported by filesystem at /Volumes/storageBackupOS/rdiff-backup-data/rdiff-backup.tmp.0
-----------------------------------------------------------------
Detected abilities for destination (read/write) file system:
  Ownership changing                           On
  Hard linking                                 On
  fsync() directories                          On
  Directory inc permissions                    On
  High-bit permissions                         On
  Symlink permissions                          On
  Extended filenames                           On
  Windows reserved filenames                   Off
  Access control lists                         Off
  Extended attributes                          Off
  Windows access control lists                 Off
  Case sensitivity                             Off
  Escape DOS devices                           Off
  Escape trailing spaces                       Off
  Mac OS X style resource forks                On
  Mac OS X Finder information                  Off
-----------------------------------------------------------------
Backup: escape_dos_devices = 0
Backup: escape_trailing_spaces = 0
Starting mirror /media/storage to /Volumes/storageBackupOS

```


I tried splitting the rdiff-backup command and arguments but it made no difference.

I'm now doing an offsite local rdiff-backup to check the HDD is in tact and see how long it takes locally.

---

### Post by freeflyjohn on 2024-01-11
Absoultely gutted.... I'm done with backups :(

Having spent weeks implementing Wireguard VPN and trying to get rsync and rdiff-backup working remotely, my server has now broke for some reason  

It happened whilst I was running the rdiff-backup script (offsite local backup) when I lost the NoMachine connection to the Ubuntu desktop.

I could SSH into the server so I performed a reboot, but the server didnt seem to boot properly.

So I connected a monitor and keyboard to the server only to find the error "cc_final_message.py used fallback datasource"

I could still SSH into the server, but Ubuntu desktop and other apps such as Plex, Nextcloud, NoMachine etc dont work.

I ran "sudo touch /etc/cloud/cloud-init.disabled" (as in this guide...[https://askubuntu.com/questions/1333240/ubuntu-20-04-server-blocks-at-boot-cloud-init-and-login](https://askubuntu.com/questions/1333240/ubuntu-20-04-server-blocks-at-boot-cloud-init-and-login))

The "cc_final_message.py used fallback datasource" dissappeared, but the screen is still blank although I can still SSH in.

I thought I was being proactive by using Timeshift backup on the server, so I restored a snapshot but still have the same problem.

So to summarise, by trying to create a remote backup my server is now broken and the Timeshift restore doesnt fix it either.

Now I'll have to rebuild my server from scratch again which will take ages and be a right ball ache 

Pfffttt... backups :sad:

---

### Post by freeflyjohn on 2024-01-11
ggrrr

---

### Post by SeijiSensei on 2024-01-11
In my backup script, I put all the includes and excludes in separate files like this:
```
rsync -avr remote_server:/ $DESTINATION  --files-from=$EXCLDIR/includes --exclude-from=$EXCLDIR/excludes --delete-excluded
```

$DESTINATION is the local directory where the backup is written, and $EXCLDIR is a directory containing files of includes and excludes.

A typical include file contains:
```

etc/
home/
var/log
var/spool
var/lib/pgsql/backups
usr/local

```

Notice these are all relative to the server's root directory since I specify "remote_server:/" in the rsync command.

A typical exclude file contains:
```

*backup*
*.iso
*.avi
*.mkv
*.mp*
*spam/*
*cache*
*thumbnails*
proc/
sys/
run/
dev/
local/share

```

Makes the command much more manageable.

---

### Post by freeflyjohn on 2024-01-11
Thanks  SeijiSensei, I've done that before with rsync but I don't think it can be done with rdiff-backup ?

Initial investigation into my server no longer working, I'm wondering if the root drive is full.

When I SSH in I can see the following...

```
  => / is using 98.7% of 195.80GB
```

So it seems that root is almost full, which might be why the desktop does not boot etc

And after googling the issue, one of the common causes can be when running a backup script, especially if its backing up to the wrong location or creating large logs.  So this is a bit of a coincidence !

I don't understand why root is only 195GB though, the drive is a 1 TB SSD.

So Im currently trying to find why its showing that the root drive is almost full

---

### Post by freeflyjohn on 2024-01-11
I think I found the problem.... a path error in the backup script !!!!

My intention was to do an offsite local backup (-offsite.loc switch), but I noticed in the script file that the onsite backup (-onsite switch) incorrectly points to 'backupstorage'.  

I can only assume that I incorrectly set the onsite backup switch, but I can only assume this from what happened.

Because I used Timeshift to revert to a backup 5 days ago so no longer have the command in the bash history.

'backupstorage' is the onsite removalble HDD, it wasn't connected but it is defined in fstab so the directory exists as /media/backupstorage.

With the 'backupstorage' HDD not being connected, it instead filled the root drive (in /media/backupstorage) which is what caused everything to crash.

As I was able to SSH into the server, I removed /media/backupstorage which was 155GB, rebooted and everything is running again (although using the Timeshift backup from 5 days ago).

Do I risk restoring Timeshift to the latest snapshot ?

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
        echo "Performing onsite backup..."
elif [ "-offsite.loc" = $1 ] ; then
        echo "Performing local offsite backup..."
elif [ "-offsite.rem" = $1 ] ; then
        echo "Performing remote offsite backup..."
else
        echo "Parameter missing: define -onsite, -offsite.loc or -offsite.rem"
        exit
fi




# rdiff-backup
if [ "-onsite" = $1 ] ; then
        cmd_rdiff="/usr/bin/rdiff-backup -v4 --print-statistics --force"
        src_rdiff=/media/storage
        dest_path=/media/[COLOR=#ff0000]backupstorage[/COLOR]
elif [ "-offsite.loc" = $1 ] ; then
    cmd_rdiff="/usr/bin/rdiff-backup -v4 --print-statistics --force"
    src_rdiff=/media/storage
    dest_path=/media/storageBackupOS
elif [ "-offsite.rem" = $1 ] ; then
    cmd_rdiff="/opt/homebrew/bin/rdiff-backup -v4 --print-statistics --force"
    src_rdiff=ssh://user@192.168.6.1:12345::/media/storage
    dest_path=/Volumes/storageBackupOS
fi
    $cmd_rdiff \
    --exclude-special-files \
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
    --exclude '$RECYCLE.BIN' \
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
    rsync_options="-a --progress -l --delete --rsh='ssh -p 12345' $rsync_excludes"
fi




# rsync of /media/storage/svn


if [ "-onsite" = $1 ] ; then
        src_rsync=/media/storage/svn/                            # end with trailing slash
        dest_path=/media/[COLOR=#ff0000]backupstorage[/COLOR]/svn                       # do not end with trailing slash
        mkdir -p /media/[COLOR=#ff0000]backupstorage[/COLOR]/svn                        # do not end with trailing slash
elif [ "-offsite.loc" = $1 ] ; then
        src_rsync=/media/storage/svn/                            # end with trailing slash
        dest_path=/media/storageBackupOS/svn                     # do not end with trailing slash
        mkdir -p /media/storageBackupOS/svn                      # do not end with trailing slash
elif [ "-offsite.rem" = $1 ] ; then
        src_rsync=user@192.168.6.1:/media/storage/svn/      # end with trailing slash
        dest_path=/Volumes/storageBackupOS/svn                   # do not end with trailing slash
        mkdir -p /Volumes/storageBackupOS/svn                    # do not end with trailing slash
fi
        eval $cmd_rsync $rsync_options $src_rsync $dest_path




# rsync of rdiff-backup for /media/storage/Backup/Mac
if [ "-onsite" = $1 ] ; then
        src_rsync=/media/storage/Backup/Mac/                            # end with trailing slash
        dest_path=/media/[COLOR=#ff0000]backupstorage[/COLOR]/Backup/Mac                         # do not end with trailing slash
        mkdir -p /media/[COLOR=#ff0000]backupstorage[/COLOR]/Backup/Mac                          # do not end with trailing slash
elif [ "-offsite.loc" = $1 ] ; then
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



[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAywAAAK CAYAAABAV5phAAAAAXNSR0IArs4c6QAAAGhlWElmTU0AKgAAAAgABAEGAAMAAAABAAIAAAESAAMAAAABAAEAAAEoAAMAAAABAAIAAIdpAAQAAAABAAAAPgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAADLKADAAQAAAABAAACvgAAAAByGWqBAAAC5GlUWHRYTUw6Y29tLmFkb2JlLnhtcAAAAAAAPHg6eG1wbWV0YSB4bWxuczp4PSJhZG9iZTpuczptZXRhLyIgeDp4bXB0az0iWE1QIENvcmUgNi4wLjAiPgogICA8cmRmOlJERiB4bWxuczpyZGY9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkvMDIvMjItcmRmLXN5bnRheC1ucyMiPgogICAgICA8cmRmOkRlc2NyaXB0aW9uIHJkZjphYm91dD0iIgogICAgICAgICAgICB4bWxuczp0aWZmPSJodHRwOi8vbnMuYWRvYmUuY29tL3RpZmYvMS4wLyIKICAgICAgICAgICAgeG1sbnM6ZXhpZj0iaHR0cDovL25zLmFkb2JlLmNvbS9leGlmLzEuMC8iPgogICAgICAgICA8dGlmZjpDb21wcmVzc2lvbj4xPC90aWZmOkNvbXByZXNzaW9uPgogICAgICAgICA8dGlmZjpSZXNvbHV0aW9uVW5pdD4yPC90aWZmOlJlc29sdXRpb25Vbml0PgogICAgICAgICA8dGlmZjpPcmllbnRhdGlvbj4xPC90aWZmOk9yaWVudGF0aW9uPgogICAgICAgICA8dGlmZjpQaG90b21ldHJpY0ludGVycHJldGF0aW9uPjI8L3RpZmY6UGhvdG9tZXRyaWNJbnRlcnByZXRhdGlvbj4KICAgICAgICAgPGV4aWY6UGl4ZWxYRGltZW5zaW9uPjgxMjwvZXhpZjpQaXhlbFhEaW1lbnNpb24 CiAgICAgICAgIDxleGlmOkNvbG9yU3BhY2U MTwvZXhpZjpDb2xvclNwYWNlPgogICAgICAgICA8ZXhpZjpQaXhlbFlEaW1lbnNpb24 NzAyPC9leGlmOlBpeGVsWURpbWVuc2lvbj4KICAgICAgPC9yZGY6RGVzY3JpcHRpb24 CiAgIDwvcmRmOlJERj4KPC94OnhtcG1ldGE CrRFCMQAAEAASURBVHgB7N0HeBRV2wbgZ1t675U0EhIIhITeu4A0pamIfIooqGAvKBZUEDv ig0QkSKKgChSRBABAekECJDQUigJBNL77s5/ZtNDkk0oSQjPXNeS3Zkzp9yzJPPuKasA4Cce3ChAAQpQgAIUoAAFKEABCtwqAalMxvLz4tfFzyv 1Bel0avFE5MyJ/MpBShAAQpQgAIUoAAFKECBmyFQHJQU51X8uuzPsoFKcZAi75Ofyw lHLBoxIMbBShAAQpQgAIUoAAFKECBmylQHJgU51n8umyQUvF5SaAiTjI8lwOWdsU58CcFKEABClCAAhSgAAUoQIGbJFAcoMjZFT8v/lm8T34tBybyJv/UiUeueKSJxyXxyFb079vXcFJcfDx8mjQR 7hRgAIUoAAFKEABClCAAhSoewFJkqDT6ZCTm5sZGxv76YXExM2KiNatDQFLdnY2LCws6r5WLJECFKAABShAAQpQgAIUoIAQUCgUUKlUMDExgZmpKa6kpByXh4RxowAFKEABClCAAhSgAAUoUO8Ccg LVqs1PHJycmBrbR2irPdasQIUoAAFKEABClCAAhSgAAUqCMjBS3pGBhiwVIDhSwpQgAIUoAAFKEABClCg4QgwYGk414I1oQAFKEABClCAAhSgAAUqCHAOSwUQvqQABShAAQpQgAJ3qoBh/oBYoUmvL15ltm4llEol1GLCtTzxmhsFigUYsBRL8CcFKEABClCAAhS4gwUMy8mKQMXWxgZWlpaGlZrqkkNeyjYzK8swZ0ElAhcGLXWp37DL4pCwhn19WDsKUIACFKAABShQJwJaETDYWFsbAhZ5Wdm63uQy5WBJroNcF24UKBZgwFIswZ8UoAAFKNB4BJQuCL9nHCa9MBl3NeGfusZzYdmSWykgDwOTe1bqe5PrUF9D0uq77Sy/cgH Fq/chXspQAEKUKChCViEY L89di4ejZG hsZ0awKwuCnJuGh4T3RzJZ/6hrapWR9Gq5AffSsVNRoCHWoWCe rl8BI7/x67dyLJ0CFKAABWojoIZzhwl4e/pDaJm3Ek P/BQHtVWcb KN3o8/i/EDw FlkYvzkRvxw2ffYGNsboUTrDDwo7V4vatJhf2lLwt2zcSwlw6g65vv4 EIV9jbWsJUpUdexhWcP3kI21YtxNItcaiYsyEHpTeGf/B/mNDWBTamSkj6AuRmJOP8qaPY/dcqLF8XiStFbVC6tET7ZnawVIWjQ7AlVp5Jg1RaDT6jAAUoQIFGKsCApZFeWDaLAhS4kwQUMPfqiHsemYiHBgTBVqmAPqma9its0PG5z/DWMA odDnIKrCGT4fReP0zK Q8PBPbU8uHATptAQoKClfsUajUUIv8Jb34FmJdYbp8rbyakDlc/Pzg4aRCQVYqrmbrYWLtjIC2A9A0oh183hqHtzZdrSTAMIGtqzNszZTQ52UhM18Jcxt3BLb1QGCbvhgy8Du88uL3OJIlQR/3O2Z/YonejqewZguDlWquMA9RgAIUaFQC7CdvVJeTjaEABe5IAdFLce9bH Cpu4NgUVCAojiiSgqlx9343yB3qPRn8fOUIRg4 CksO6OHyuUujB3kWeEbhTOx8dW 6Nm9u3j0wbSN2SLokJC7 Q30M zrjrteXoe0khhHi0NzHsI9Qwdj4F0jMHNLKvRKB3TuEYaq 2jkqupw4rtHMeiuPujddwQmf/IXErQK2IY9glcfaQGNnEQdinufegj3jZ IwU3lz9tUcO3yOGb98Ds2btuOvzeuwU9zn0UXu0qWQ9X4YsRn67F91w5snPsIQszlDLlRgAIUoMCNCKjFr9vuVgWY6paNeU3S8at/muEhP3/FNdtwTE5zoxsDlhsV5PkUoAAF6ltAfw4bF4thVx8/h4ffXI8KHSQVaqeAZasIBIm/IPr4bdh4JAv67Chs2XEeOoUagWEtYXkT/rhAhD1mNo5wsJIDCwlXL10WIUnNNn3ORRxcMRMf/HoBelEn7753IbSS8QAKp4F48Z2H0T3QDtqks4i9lA8bZxPki96YcpvSFu0mz8Tk9rbQnV Hma/9gOM55VLwBQUoQAEK1FKgqwhU5orA5FW3LPSwyoeXiR5mSsnwkJ/3tM43HPtWpJHT3shWyZ AG8mO51KAAhSgQN0L6JG8bQG FgVr2vc0UrwC9s5OkD/x0qckI8Vwby8hOeky9GgClaMT5A6KjAr3/EYyLXNYg3av/IF/XyneJaHg3G YvSgKVU2nKU5Z/mcejh08htxRnrBw8IKnlQIHs8qnUDp7w8NUDE/LPYC5k1/A6iQdlGrxZ00uyNAlI6c3gf/oGRjY0w/qKzvxyYsfYmty/XwhXvna8xUFKECB21NA7u0Y75SDEXZ5NWqAh0aPaSKoWZlqigXJ5uJvTe039rDU3oxnUIACFLitBarvQLnuSKXIRI/Mc8dw PARHDuViEwRPGg8h DV1wbBvZZ/cRTyF8cZchWD0Cqplu7sLuxMEJ/ambfHCz txNdvjkfPJmbl58kondG d2vYIh3/fD4Dv8Xe2Kd8t/WFZ UpQAEK3ASB2gQrZYuTA5xHHK ve7uWfz7KFsvnFKAABShw wlISLl81TDPRWnvCHtDRKCAo4uTGMQlQXflipEhZcZarMPxpS/jyYmP47GHhmPES7/hoqSCY fh6Fur70OxQnjHlhAdKNBfikdCxWFecjVyD HrJ57ArCXbcCbXAS0HPoZ35n BR0JKulfEyVm4lJQu5tHYoMeTz6O3K//sGbuCPE4BClCgKgF5aFdNe1Yqy2OkfR46Wdb gyP 5q5Mk/soQAEKNCIBlVtXTHhzJl4d1w6OYnxxZtRBnNZKUDbpjr4tLKAwD0GvLl5QSVqcijyKymKD6 JQmIrhZ/YwNZwsVvmq0TgABUzsm6L7hBmYerczlFIBTm9Yj2OVjSdT28BeisHaL6fif8PH47sorWhLU3Tr6F1m4YBUbHn/VSyNzoPSrQ9efusJWJZ66rXTyJAhSoUmDBDz9gwcKFVR7ngdtXQB5K/GhlPSSKasKJSo49JoaTyXnVZuMcltpoMS0FKECB205AhcB7J2PcQB otG5I Gc/liSsxZJNozFjgD8e PIPDC3QwNJcLCt8aSOWrD13XeOLS1nUaP3k91jxPz00Vg6wt9RAqdAjfe8a/HOuuohFheDHF GvCSqYaNTiHJGjCFYu7fwcMxbHVDr/RR08Dl99NRwWly7gcqYGbv4qcU4WLp6Xl0/2KKmSlHUY3709D63mT0ZY68fwyv27MWXxGdT M76SLPmEAhSgQJ0J7Ni1q9qyunTqVO3xm3Wws gZcRPzUcptIiCxe2MR8v5dg5y/fy53yLz3fTDtOgSp744Tv5tLz3MXeci9LNvF7 2abgxYairFdBSgAAVuSwE9zu3diughI Eaux0HL4k/GlIqtn70LGZkPIv/3RUGD/NMJOz5Cwv/72tsq36JsWoEcnE5PgHJHl5iZTBnuFrpoc1NR LJaBz8ZzWW/vQPzpf vSqTTx5SLiYh1csNtuYmMNHlI/vqBcRHH8LODSuwcvNJpFd6nljUWJmOc7HpCPXxQ6BbATISo/DXmrmYsykVYhRaua3g7HJ8vLAX5j4RitBxz2DQpuew mIVGZc7ky8oQIHaCIz/3/9qk5xpayhQVVBiLJipYfY1SlbpUC4RiOTztsJr4nlp7XIGfjEkNeZr1Hw3riTGR8N71csFJcUG0DFkVE69aGqYzZ2dmwsLAozoc/KUABClCAAhSgAAXuIIG8/Hz4NmnSIFocGx8PU5Pqv72pQVS0DiohByXVBSxVHbvZVZvvkw7Pij0sRYXIAYoctMgBiqQVS8wXPS8OYCrW5XyBEhPibCrurvI1e1iqpOEBClCAAhSgAAUoQIHaCMhzWORl/cY//HBtTmPa20DAQVXJco1F9c79e7lY1VFh6FWRd2V8O 2aIWJlm1hdXmXTFT vZpZMcRL pAAFKEABClCAAhSgAAUoUD8C7GGpH3eWSgEKUIACFKAABRqdAOewNLpLWtKgqzoFPMVKk5VtZeesFA8JKzunpeI5V7S1WyaMAUtFQb6mAAUocAcK6K2bIjwgB3GR5yt8D4sCSlMLmOoykVPLPzAVGasuo2JK XV15VZ3rLK8uI8CFKBA1QLGJq7X1RyRqmvYMI7E5KrFHJb8aypTdv5K2Tkrhon4InXZfcUnn8yrXQhSu9TFpfAnBShAAQo0IgElrIK7oovDX4iu8OGZpPJHuzGdYbNhIf66WGHprVoJVF1GZdlUV251xyrLi/soQIG6E7gd57DcDgGJsaCqLq7wf1ka9LKuELCIZY3Nugy9Zs5K8ZwWeVnjnL9 vGalsJ0ir9psDFhqo8W0FKAABRqjgMIZfgGmuLDvPHJvVfvqooxbVXfmSwEKUKAeBRpKQCUHGRfF6l7y96iUbGJZ49QZ464JSOTj8vey5Gz55ZpjF0QecvBTm40BS220mJYCFKBAIxTQ2Qch2CoGJxLkP0K3Zi2WuiijEV4aNokCt50A57DcdpesxhXWih74766Y43W3rPLnlPlSyPIHxKtKjs1LNoecV202Biy10WJaClCAAo1OQAzV8g A6/lNWJsnBysKqFzboHvPcAQ5qqBLSUWOiYRLRe1WOIahS49wNHMxgyI1Ggc2/YMDyabwGDABd2csxvc70qATeUhBw/Fk6 NY8csxXJbKlyGpXRHYqx 6BtjBQsrE1T0rsfxgJhRVllt9nRrdJWGDKEABCjRQgR3i2 lXpppihF3eddXwlxTTWveuyAUxYLkubp5EAQpQoJEIKJzgH2CGxAPnIP/5kTQBaD wDdxj1mDFuixIzuHo1tfL0FhJ7Yu2d3eCz6lfsWJDASzbDME9fVrg/PKjSDyXDNMQD9gp0nBFfM28i5cL8kUQdEX FK1iGX5d0NflFDYt3Y84nRWslVnQiXI7V1VuNXVqJFeBzaAABShw2wgsED0k4qt2MNK dkGLHKwsFD0017Pdmr7/66kJz6EABShAgToXkIdqNbM5iZPxEuTYQucehBDlEezZcx5XMkTwEZeAxILC5Sd17iFoaXIUe/cmIi37Ks7tj8JZO1/4WOihjY9FvIM//MVzSekJH68sJMRehTzIrGIZ0BagwNQOjlYK6LNTcDVTb6TcqutU52AskAIUoMAdLiD/XpeHhr1z0RLyfBRjm5xmuki7QJwjn3s9G3tYrkeN51CAAhRoFAJKWIrhYO7n/8b6vMKgRGFuAfOcBGSI9fYrbgoLS5ia 6Pv463Qx3BQ/l7jJGSaSVBejUHMlQcQ5qPBf1eaIkgRjV2J8h ya8tQxm7G6gM90WPgeLTMOIb9W3dgf3XlVnOsYh35mgIUoAAF6kZgl5g4vzdbg06WBYZHU1MdnNWFIcllrRKn8lSQ08iP2s5ZqdgCBiwVRfiaAhSgwJ0ioHCEv78FEg dK1kdTMrKQpalHezVEpKKelaKOaScHORn7sWWxbtxtlxAIy93nILTMSno09QfTex9YXF6JeLlNJWUASkbVw6tw8qjdnDvNBT39svAhe2ZVZdbTZ2K68afFKAABShQ9wJyILJdzGuRH7dyM96PcytLZ94UoAAFKFBvAjq7Zgi2OyWGg4lhXEW1UCVG4UhuS3ToJnpebMxhYWUJi6K/FKqLxxEltUbHDt5wsTaHuZUjXB1MRS LvEnIP3UCp9y64a7gTJw8cUVMvhfDwSopQ7JyhYedKUyRg7TkdORpTGBRXbnVHDMUzX8oQAEKUKBRC7CHpVFfXjaOAhSgQFUC8lAtfzEcbCs25JYO/1Jo47F/7VZoenTH3WOtYCam4ueknMUhkUZRcAZ71 6GSfd GNraEia6TGQe QM/7syDVhSjzD6Go3GdEWy9E0euyL0ulZWhgNqtLbr38oGjKaDNuIAzOw4jLj8HZ6sqt5o6VdU67qcABShAgcYjoIho3drwwVp2djYsLCwaT8vYEgpQgAIUqFpArNwVMmo0Whz GitPFE64rzrxdR6pizKus2o8jQIUuFYgLz8f3p6eUKnkDxzqb9PpdEg4fx6mJib1VwmW3KAEOCSsQV0OVoYCFKBA3QjobZuhmRgOdipOVzIc7GaXXBdl3Ow6Mz8K3MkCSqUSmWLOWH1vch3kunCjQLEAe1iKJfiTAhSgAAUoQAEK3MECer0e8sPGxgZWlpZ13tMi96zIwUp6erohYGHQcge/GSs0nXNYKoDwJQUoQAEKUIACFLgTBeQAQZ4nkCYChpTU1HohkOugVCjYw1Iv g23UAYsDffasGYUoAAFKEABClCgTgVUImCQl GQf9bXxp6V pJvuOUyYGm414Y1owAFKEABClCAAnUuwIChzslZoBGB gufjVSMhylAAQpQgAIUoAAFKEABCjBg4XuAAhSgAAUoQAEKUIACFGiwAgxYGuylYcUoQAEKUIACFKAABShAAQYsfA9QgAIUoAAFKEABClCAAg1WQH01JcVQOTNTUxQ/b7C1ZcUoQAEKUIACFKAABShAgTtKQCGJTW7xjh070KZNmzuq8WwsBShAAQpQgAIUoAAFKNCwBTgkrGFfH9aOAhSgAAUoQAEKUIACd7QAA5Y7 vKz8RSgAAUoQAEKUIACFGjYAgxYGvb1Ye0oQAEKUIACFKAABShwRwswYLmjLz8bTwEKUIACFKAABShAgYYtwIClYV8f1o4CFKAABShAAQpQgAJ3tAADljv68rPxFKAABShAAQpQgAIUaNgCDFga9vVh7ShAAQpQgAIUoAAFKHBHCzBguaMvPxtPAQpQgAIUoAAFKECBhi3AgKVhXx/WjgIUoAAFKEABClCAAne0AAOWO/rys/EUoAAFKEABClCAAhRo2AIMWBr29WHtKEABClCAAhSgAAUocEcLMGCpg8svSUocOHocSQmnalSaJKmwbc8BxEZHQlGjM5jozhHIRcyahVgTnQmpQTU6D/FbFuOXA kNrF4NComVoQAFKEABClDgOgQYsFwHWm1P0YsA5OCRI0i/cqlGAYgkKXAmNg7Z6am1LYrpG7lAfvRP HTuVsRlNbSGKlBwYQ WzF6AfZkNK5RqaFKsDwUoQAEKUIACtRNQ1y5540oddfYSdmxahVF394O9Z0CFximw81AMju3fiPGjx0BpbV/heEN8KSEzZj2 X/Ardhw/j7QCDWxcfdGi90OYPLYtHBp1d42xths5jnRs/WAiPt56Ffl6QGViCVuXJmgW3hUD7xmMDl5mlV5wKfs0/vxuLpZvjUJinhlcg7th1MTHMLCpBaQLv C5CfNwXFvxVBN0m7YSb/QwBfTJ2LtkDuavO4DzOVZo0v4ePDF5FFraVnKxpGRsXvQ7rnZ8Bg FW5ULfnPOrMEHb8xF7pgfMGuQQ ExKQP/fvYMPv8nCem5ohIqU1g6uMM/tCvuGTsaXbxE SWbDmkxW/Dr6k3478gpXHIajc8/GQ2voo80pJwE7Fi5DL/9cwAxF9Oht3CBX8suGHT/fbgryEaUZ4KAERNw18bXseiPe9Hmfh/w05ASXD6hAAUoQAEKUOAGBO7ogCUrKwvycK0du3dh2D2 0ClVJZQZ2XocjdwNpV6JnNwsWN4GAYuUtg3/N 1z7He9C2OefgQ 1hJSz0UjRmkJq0ruf0sa2wieGGu7seOQdMhKS4cu5EG8Nz4CJgVZuHo Gnv XI63n/wT/afOwpTOTuVvwkVAsOvL1zHneCtMmDobrawuY9fiLzDnTR2c5j P9k598PzsUIi3UtGmw8VNn2P2Nme0CdSIfVrE/jIDM1Zko9ujU/GYw3ms/24h3nrfEl 9NwhuFa6ZPn4j/oi0Qe8POqM4ntFnnsH2VYuxaOV/OJ rROviogw/tUi/lITMoDH4QLRJnZ FlAtR2LR8OWa8moqZc6cgwlxOmIczv83AWz8mI3jA3Rjz7Fi4uXjAuThYyYzEglfewopED/QYNhbPNXWEKj0Wezesxv89vwtHX/0Iz3dxhMKsJYYO9MX6DetxbOQkhN7Rv13KXQi oAAFKEABClDgBgTu4FsKBbKys2FraYHEtHxciI2Gq3/zIkoF9h09CntTFa5q1cjLzYZl0RG9CHD2HDqCk8ePID8nAy4OdujcoR2cPHxLxu5rdQrs2LsfZ08eg74gF 4urpDycspdJp1egd0HIxF78gRystPh5mSPbp06w8bZvVy62rzQnT2Mo1nO6DfpaYwsvlts3wX9SjLR49xacWO6aD8S0wugtvVG2IAJeHqcqL98cyo wd/ 9cdYtucsLiSni9tYC7i3GoB7u2hw K9/cOh0MvItvdB2 GQ8OyoU1vINtZSD0 u/wZc/b0f0pVyRpyc6PToDr/RzhUJ7CF88NA2nR8zD7JEehk/9pcRVeGHCCvjNXIQprVKLyovFxeQ05MIcTgEdMHzSU7gnpKgHQUrBkVXz8f2a/xBzKQcKcwd4 ARj4JOv4p6mpQGmsbZrjdoUIiltvNA8NFTURGzhHdBjwF1oPes5fDr7S4QGv4k ZbupdKewb38GgkY/gmFt3UT7AuHzSAy2PrMdR8/p0D7IAT7NHAozFv9KiX9g0ZYUtJ44AwM9BHjBYaz5PQaOgz/GM8OaQw5hWpjEY/zbq7AuZgDGNyttn iKwQURWMfZd8ATzeSU8qZH4p9fY95eZwx7fQpOf/AVKhtEKLcpOCQEhv6UsLZoa3UO9806hmOJekT4KZF3VPTKLFfhwdlfYIBHxV8JuTi8aDZWnG K8Z/OxCj/4l6ZTujWtweC334GX3wxDx1avoKuNkp4dukC3yUbsOvkBISGVMyrsNb8lwIUoAAFKEABCtRG4I4etZGTkw03B3MEBLfB3kP7odYXfhSekaNHzPH96BzRBkozK8jpCjcFtu07ghOHdqJjWAgGDhwCU3sv/LbhT2RePm9IIvfY/L1rH2JPiPPDQ9G//91wdPeDXq8rc12U2LonEvEiTff24Rg86F5oTR2wbuNaKPPzyqSr3VOViyfcVVdwYPMeJBVUdq4C9s3vxqOvzMLs//sIrwx3x9nlH2LejqIJ3KLHIE7MtUnxvw/T3vsQs169H74JqzDnu/2w6vUopr47HVN6meHg9x9haVThOCd97Ep8/OVuWA58BR9/8TlmvTAGfcSNeoXOgcoqI 7gi8rzHSHyfh8zp01AZ VezH13HvYZ4rs8RC ehtcWHofjgCmYPmsW3pzUDjixFyculXRbGPI21nZjxyuvoNirdkOfcUPhn7UHG7YnlwSlhvRKF3iIbpC4/XtxwcChR3J0DJJtQtDcs2ywIVJLmdi95EcccRmK//VxMfjoLx7HiRRLtAgPNAQrcp7mLSMQokrE8RNXy5clwrmTx OgDAyGf0kcoITH8A x IuXMSrcqSQPQ90q 0cqQGbSUazbHAWdS0u0dBf//aU0bP9lPRJVl7H jYcwYvgoPPL8x1gVlVZYfl4kNm5Jgn2vMRhaEqwUZa72wF0P9od72k78ubtwsr3SPRjNrJMRHV2x/pVViPsoQAEKUIACFKCAcYGSWx/jSRtbCgVyc3PhaGqCkJYtsSx6P5LOn4ajdxAOHTsBVwvAy78ZNJHHRMAiPtkXzc/OU B41D70DW BoBZhhhs6NzdP/JhyBZGH96NrH09k5Ek4dfIwBrRtKeYKFA7QcXP3wZGYYyWAcj7RIlgZ1qUNPPwDDft7dumJJT fQnJSHOw8i3t6Sk6p0ROFx2A893QsZn3zLh7d1RQd tyFQYP6ItzDvCiAUMDSry06 xVmF9TUCrFbn8LGEwnQdQtB4ZtBAXOvFoho1QwqtIDzhX xe3kTdB7UDW3kBKJqR/5 C0ePXoQ 1Bt6sTBAmmQt0ochpKk8z6NpjepamkiU16QV2obL5YUhzCkJB57ZjL0ntWgXsAcrVsfCa/QcvHK/v6F UuoF/Kr4u/T0omfG2m7s DUZltmh9GyKAEs99iVcgA7ORU4igdITg6c8hqPTv8WUSXvQrYUeh3ZnY hrU9GhuEuuKB/p4kYxz0WLzi8NRUDR/zp9agrSYAsHuzKfG5g4wNFGQsLVVNF/4ixMijb9FSRd1sMu1FnMFimzKRRGg8OCf2dh2IBZIjiRoBcPhZkvhr7 AFrJl6vgBA5F5cE5og9GDW4JD/MMRK2cg2/f Ajm4n3UvyAe57KU8AtuWr7coiqo/ZohQFOA0/GJor62UCmd4OoE7Eu8LKxcSq3KVJlPKUABClCAAhSgQG0Eim6danNK40grr8SVn58DEytT2Fqp4RsQhoOHD6KHa5AIJg6gf9tW0KtUMDExRW5erqHRyanpUOhy4O7uXfLpt1Kph5tbEyQm7IdK9NBcScsW817y4OrqWSXUldQ0caOoxfpte4Bte0vSaXR6ZGdnwq5kT22fmMC73/P4svtYHN xGX uX47pvy5F8NjX8eYDoWIeSwEu7lyK75Zvx7FzV5GnsYYmWwdV8/wqClLCwUn0luSkIU0msBIPlQPE6DUcyRTzf8RLdfNBGB2 A3OnPo6YXndjyJCB6NJU3LhWkaOx3UpXD7gq05GWIUGXEI3Tuc7oENGkBje xtpu5LixilV6XEL25QQk6XzRfUB7uF3chcics9jx10EMbNEDriUIOpzeuB7RDr0xvpNtmQBDEoY16osSwUaeeB9KMDE1rekZJTVWR0zAZxPbQiPm6eSmnUfU5p w5N0XgLc/xxP V3E1RwmfTgPRtZVhIBz8J4/DobEfiZ7CZNzVRq4joBCBUaWbHDCJQyXHFaYwFYFQXt719xRWWg53UoACFKAABShwxwqU Wj3zjKQbxTz83Oh0cjzAcRYftHLcjopFbt27YCNMkcEMKFivwSN2qRWN1/Ft3WS CS7qq3wBlCPAT06Y8SIESWP0aPvg5tfi6pOq/F hakLmvd AM99NA fjfNA9JIvsOqMDvrYFZg56zdcCroPL703G5 88zi6uRbXuPLs1Wo1FJLe8Mm8IYVCDbVKIV7rDTey0PjhnhkLMH/6KAQkb8Ankx/FSz/FiPkv8qaAUrzDdFpdYVrDvur/UajUItgRPQFixJckhtHpxSuVKK mW1VtLz7f2PHidGV/6s/F4JToZfD09igXiEmZOzH3001wHPc2nhk5BPdPeQ9fvz8Mqr/nYOHuMnOWxFyXrdsuwLVrTwQXTz8RBSjtHERwmoqrqWWGtxWk4EqGAnZiblS5/5wKE5iZivesCASqfmeVrXXpc4WFM5r4 sLXLwDBrbtjxLPPYohrIjb9dRhacX1VCj0yMwoDUMNZZk5wtgHSRIAOJ094mOkRd/IMKhtlqIs7hbP5anh4uhbWVwRWcqxiInouuVGAAhSgAAUoQIGbIVDunuhmZHi75CH3sBSUBCzivsxWLEnrHYIT0UcQ0TwEerVGfGosQSUClvz8wh4IJzsbSCpzXLyYUPIpt16sIpaYmABXBwexypgSxWnOnYsrSVPRxNHWWvTemCI9LRn2dnawK/NQix6d4q3ws 3iV9fz0ww oqfIRUrEeTHBOv9sDGL1oRj8UD EB4kb2KZB8LS CW8BhTk8IoZg0syv8d5wO5z4bQOOyXM6lHawt5XEF2ZeQFV9ONW1SuXeBJ6qSzh27FKtb9KB8m2/thxjx4vO0F7AXwvX4Kxlewzo5lTumkrJseL7UKzg5VXaa2IuAt1Ai2wkJZV gaI YR/2J9khon3Tcj1FSvcQBNtnIerQqZJgIOfoAbEMshtCgivMA1I6wkUs25V6Obkk7bVtquEebTayRG NWgTrSvMm8HMFzkYdR/FXu0hpcYhNkYMQZzGHKwJ9uzsi e fsP5c4bylklL0l7Dlpw04Z9EOvdrLSxuLTSzTnJQMOLuVGc5WcgKfUIACFKAABShAgdoL3LFDwiAHLNp80YOiMdwMK8SnzB3CWyPGNF9Mwm9ddIMseljETV1eXr7oZZBgbiohpEVb7BCT7qGxhKW9K46ePIv8lHMI6zJI9AaISdMiTXORZmfkDrForYmYcO NvAKlWC2s9Jbd0kyBoGZh2BW5F3qlGRxcvUQaPbR56QgMDDEESqZmFoi/kAS/tKuwsC1daaq6S1xw/Bd89mcuQloHwt3OVMwvicee1WuRYBqCYU3V0GT4wVNajXVLN8Gppx9sVclIzKrt5/Xla6C/sBtrD vFp/fOMNNeRmRcJmBtU7iCmNILHTv7YunP8/F/AfnoGyA tk88i7QyHQrlcyv/SmHXBYO7L8Y7Sz/A1 YPors3cHHPVojOogrL94oRdkbabux4ccn6tHgciYyEiTYHKedPYLdYCGFrvB0GTH0KvcquECZOULq3QpjzUmxa8D2CHukNfzH/I3r9Ivyb443hLYuDGwkZ0ceQoArCSHENym2aUAwZGohNP36OLz0fQU95WeO5W5AXNhEDg0rGkxWdYi7eMz7Qrz BM9qeaFEhq3L5VnghtylKrHqn0eYi4/JZ7N wCuuvemBon1DRW2aKfncH47cFCzBnjRVGBmtxcPFSHLbrhbc7WosgRIE2D09B/8Pv4tsXX8LZEUPQKdARyrSz2Ld Bf44rEHXFyeip31hL5g USyjne6ElkFimeMK9eBLClCAAhSgAAUocD0CtbjtuZ7sG 458pAwbUFB0ZCwwnq6O1nDvXufcpWWA5bczIKimy8J3cVkejOhtkssbVyQu1csa2yLof37w9rFqyTI6SbSWIpEkccOI/vAYREUqcQQG2vY2DsVpdGjV8cI7DHX4JC4mc3eFwkzEw2a XuKVaBCRCwllsQVK5Tt3L4Zp08cQssOvcvVqfIXErQaG1il/ouVX69AUmoeFBYO8GrWBRNnPIxBYuiXwnUUXp58BV8u/wZvrs6CXmMOa3tvNHOXb0yvb9OmnsG/y1dhrvgywQK1NdwCO2LSC2J4mOF WwX/0a/hxfQ5WLzsQ/yToYOJtaP4csXWaFp2onlVRSts0HHyDDxrNhcrF8/E2gxTeAaLidwKJZTlKmys7UBuRvU2ousMlrY2UB1chjdeXgalxkJ8caQPgiPuw/SpVXxxpGlLPPLOy1DOW4a5r/ KNK0p7H3CMOS1iXigZMllHS7En4fOsYsYWlWxoWLu1Kg38HruF5i38F38lWsJnw5jMf2pQXAv1z75PLEiWMdOaLJkE3aKJYNb1GjJYLVYJtsVVluX4dUXlsjfhinaKIaHNeuGx2fdhyFFc1a8752Gt/K wvxl0/F0muglbNYLz4rhgu2KvrxHYdcBz8z EAGLlmDNyv/DxpRc6DR28AvvjkkfjsGgUPui4Wt6XNy1E7EOHTAx8I791VLxIvM1BShAAQpQgAI3KCA6DgonW zYsQNt2rS5wex4OgVurYA fhmmiC9ybP3RfDxWo5v2W1ufOs1duox10x7HD9bPY97UbrC5Jqipi9rocGbJZEz5zQHj33sVwwOLvi9HLjrvML6eOA1R/efg8wf4Tfd1cTVYBgUoQAEKUOBOELgJExjuBCa2sX4EdIjb/qtYTW2v6K06jqN7NmD 578izq0ruhSvDVw/FaufUhXO4jthhsB25/dYcji7qLeurqsies1GvIhJrROx6OkH8dDkaXj/50hkiu94OSO 4HODrhfGDWlSfsGAuq4iy6MABShAAQpQoFEJcNxGo7qcjawxUhYST4ghblticSk1B5K5I3zDBuLV5x9E8zt0ESrT4Afw/KMSTmjKfhFpHV938wAMmTYPvc5H4WDkcVy0cYSFGMaocg7HA88MLxlKVse1YnEUoAAFKEABCjRSAQ4Ja6QXls2iAAUoQAEKUIACFKBAYxDgkLDGcBXZBgpQgAIUoAAFKEABCjRSAQYsjfTCslkUoAAFKEABClCAAhRoDAIMWBrDVWQbKEABClCAAhSgAAUo0EgFGLA00gvLZlGAAhSgAAUoQAEKUKAxCDBgaQxXkW2gAAUoQAEKUIACFKBAIxVgwNJILyybRQEKUIACFKAABShAgcYgwIClMVxFtoECFKAABShAAQpQgAKNVIABSyO9sGwWBShAAQpQgAIUoAAFGoMAA5bGcBXZBgpQgAIUoAAFKEABCjRSAQYsjfTC3j7NykXMmoVYE50J6fapNGt6owJSGqLWLcSP/yZCf6N53fD5eYjfshi/HEjne/CGLZkBBShAAQpQ4OYLMGC5 aaGHHV6DRat BWR/22G4haV0RiyzY/ CZ/O3Yq4rMbQGrahxgLSVRxcswKbYtJqHyRIOUg8thsH4rJrf26lFVSg4MIeLJm9APsyGTZXSsSdFKAABShAgXoUUNdj2bd90Rcvp2PPnl24cukiJH0BrK0sEdzUB60jOkOvkGBnawsLS6t6aWfOmTX44I25yB3zA2YNcqg6aNInYSOZi/7gDO51ihSft78MTkUWhpWybMki5h9YsP46sj2srbommL55ZMhfXCZ/H5P0lIzxXpVKawdHCHf2hX3DN2NLp4mV57rpSMzYt x9WOz ChcKtydbxp9TfWPmPHy9W6AIm7V CHn/7E3lOXkWfmgmadhuOxxwejmVWRV43z0 HS1k/w8gf/wG78fMwe6VGu/cXFStmn8ed3c7F8axQS88zgGtwNoyY hoFNLQzpjR0vzEeHtJgt HX1Jvx35BQuOY3G55 MhldlH1fUsP7VX59alFfc0Nr81EXjl3ffwekR8xDuY1GbM6tIa4KAERNw18bXseiPe9Hmfh9URlPFydxNAQpQgAIUoMAtFmDAcp3AWbnAmvVr4G6tQs unaE2M8fV1HSYKnIhKRTihkeLof16G3Kvy89s9ZlnsH3VYixa R/O5yrRutr2aRH7ywzMWJGNbo9OxWMO57H u4V4631LfPXeILgVxywKe3R98gP4ZcqDd3Q4 /uHmBvTGk89P7DwpldpDW8rHf67lITMoDH4YHwE1PlZSLkQhU3Ll2PGq6mYOXcKIszLV0YfvxF/RNqg9wedURwf3dz6G2ufsePl64ucw1g bxMyO47A0/e7QIrfgiWLvsQ7Kk9890wEzMQ1r5Gn6BdI2/cNXv/qEPJNi5ErlCW/lDKw68vXMed4K0yYOhutrC5j1 IvMOdNHZzmP4/25kaOG 7l83Dmtxl468dkBA 4G2OeHQs3Fw84V3pHbrz xq9PbcqrpM31tcusJYYO9MX6DetxbOQkhPI3Y31dCZZLAQpQgAIUuEaAf5avIanZjsSrYihLfgZ6dBoAGzdfw0lNvAvPlQMUvaTGklWr0MbbGqHte Hk VRsWvcLlFJp KJQ6HHfYHG uy90egV2H4xE7MkTyMlOh5uTPbp16gwbZ/fCTGv0rx6Jf36NeXudMez1KTj9wVdIre68gqNY83sMHAd/jGeGNYdGpG1hEo/xb6/CupgBGN9MVXS2Bk4BLeFkeKWFapdIGeeCwFZhCCpOIqUYjiptvBAcEgJDf0pYW7S1Oof7Zh3DsUQ9IvzK3iXrcWH3LsTZd8ATzeSS5e0m19/fSPuMHS9pf2HtYN4GT37zLdTqov82HcKgPrUHM49H4YI Av46I UV5ac7vw4ffhqJ1i88B7O57 BwUfbX/NCdwr79GQga/QiGtXUTPSqB8HkkBluf2Y6j53Ro72/kuLg4eUdFD9tyFR6c/QUGeBj57270/aAw v6qVXnieqfvXYCXtp9CTFIBrLzC0O9/T2BcF0cc Hgs3j59D7768kH4Gt42esQufQpPrW JWfM7Cyotjs19GP3nymom6DZtJd7oId512iTsXjYPP26OxNkrOtgFdsGoSZMwOMgSCjGU7PT6b/Dlz9sRfSkXaltPdHp0Bl7p5ypslfDs0gW SzZg18kJCA0xYnXNxeIOClCAAhSgAAVulQD/Kl nrJ0Y/qVXmiD6ZAzaOXuJIVDVUzZxtcbokSMNw3h0eiXW/70FdspM2DjKAYkSW/ccwqXT 9G9U1doLB3w36HDWLdxLcaMegh6k0qGU1VabyU8hn IxSMUUGj34JNK05Tu1F88jhMplmgRHmgIVuQj5i0jEKL6G8dPXIXUzNlQ39IzavFMKkDmpWhs3BwFnUtXtHQvG6zI eTi5PE4KAOHw7 E7ubWX2deffuMHa s/SXBitwE0QNyNaUAZh6ecBIdJTXy1J7Fio8XI2voTEyI0GGJnE9Vm9IFHqKba v vbgwdAg81XokR8cg2SYEzT1FpGjsuJjYvv2X9UhUeWD9Gw9hXooWNr4dMOTRx3BvC9trrm1N6l/t 6uW5cnNziuwQcR9z2GMs4T4v5fih5mvI3/WHDzUphVM/jmEI1fHwFfGFXkfjzoH0xYPIlC8X7ZCjYBR0/FSP2fxv0cBSxcTkVsujn7/OmZsccHoJ97CZKcM7F82B19Pnwu3 c hTdJKfPzlbjg99Ao busIKSUBWS6lwyWV7sFoZr0E0dHivR/ico2PXF9uFKAABShAAQrUvUDJrWLdF317l hoo0G3rn2xe9dWnIxbgmaBTdE8pAXMbewrbZiJWgUHe/mYAtv3RUHKvoy7ht0jPhw2RXaeAtEn9mNYlzbw8A80nN zS08s fkUkpPi4OAdVGmele4Uw9GqGWRU7hR9agrSYAsHuzLBhIkDHG0kJFxNFZ9/O6O4A6XcidW8KPh3FoYNmCVuMCXRyyRBYeaLoa8/gFZmFU7SX0HSZT3sQp3F5 NltptYf62R9hk7Xn37tTi3/gssPRWIBz7pDhuBbjw/e5z79XOsxHB8ODIAJoqYMg2v5KnSE4OnPIaj07/FlEl70K2FHod2Z2Poa1PRwVJOb R4wQkcisqDc0QfjBrcEh5iCFnUyjn49o2PYP7NuxjoUv6dUqP3Q3XXR1u78uRA3bnzSDwwoJnhfdY23Bf58RPx85q9eGhyB7RUzcF/ 1MxuL89FPkxOHpSgZDxzcXQu3gDlqm9J/x8S f SBk7sXJtMtpM RhjuxUGZE2nJGHfw0ux7ehkhJumIk2yRoToGQxpKr8hmxryKflH6QRX0Y24L/GyGPjoIkIibhSgAAUoQAEKNAQB/k2 7qsgITSoCZr5j8Xp2DjRI3ECB47 gq4RoWjRulOVS7XGXkzFscM7MLRHJ5jaORtKv5KaBhRosX7bHmDb3pIaaXR6ZGdnwqFkz81 IonZFOVvWm 0BHXEBHw2sS00kg65aecRtfknLHn3BeDtz/FkRJmJ9VIecvMkEa Z3kANjNX/Ro9XpZGHuHUf4PW5F9F56gcY6Vf836j68qTkv7Hgl0z0f3sYfOVTdFXlX7xfQvblBCTpfNF9QHu4XdyFyJyz2PHXQQxs0QOuquqPu2RdxdUcJXw6DUTXVoUTiPwnj8OhsR/h713JGDCsYg9a9fUvrlVVP6Val1chJ6U7WoQ4Iu/gGVy0Go4e4V/hix37kHZXP1idOYxjuU0xJEIEL0UBS4WzoTt3Gmdzs5H0yRgM/rT4qASdVgHTq9lQ9RmE0eE7MHfq44jpdTeGDBmILk1tS4NyhSlMRRyTl5dXfDJ/UoACFKAABSjQAASK77QaQFVuzypo1AqxMpivePhj56Hj Hff3/Bt4gdTh6IJLWWalZevwD/bNiHM3wOe/i1Kghp5Vos8n2VAj26wdPIocwZgZVFhpnq5ozf2QmnnADsxy VqqjyZvqgvpSAFVzIUsHOwE59/135TWDijia9v4RwWBCC4pRvSjj LNX8dxmNi9bSS3hSFCczEhPN8cXNYOqunduUZq7/aSPuMHa 8/XLPyiy8OjcRnV99H092KDOkqNrybJGx9x/sS0vA3heHY5WhqaIXSquDfsFjGHlmGn56uXPJ0Dz5sJS5E3M/3QRHsYrYMwMcxY36EAzruwDPvTgHCzu1x8utDlR7/JVWaqjE yozI0sYmxcGhmZOcLYBEsQCERV7kIx5Vu5Res0UYm5PbcorPbP0mSTJ70XRS6iwQYde7fDNp//gv5ReCDl4EMk 3dHWWQTYhUlKTyp Js8PUzqi94vv4f7Asn2DCpg7WEOhscU9Mxag/cFN H3lSnwyeQVWP/weZt0fVPh FUG0HKuYmJa8S4tz5k8KUIACFKAABepRwNg9SD1W7XYrWg9frybQSipkphdOQC/fAiX 3X8Q5rpUdOjYUyx7XNqz4WhrDb1YBjg9LRn2dnawK/NQ13j SvnSavJK6R6CYPssRB06hYKiE3KOHsBxrRtCgktvxGuSV5VptNnIEj0pao2mfAAkbixdxFJVqZeTS8quMo8qDhirv8pI 4wdL71CpRXIOfI93v4mHu1eeQ9PdXAs16bq6 MI2 7P4dv58/DtN9/gG/nx1avo765BwPB38dmj4dcMQZKSY8X301jBy6t0vol5QCgCLUQvQpIIOIwcl8ybwM8VOBt1HMVfcyOlxSE2RQ0PT3nuR/mt vrX4P1Qy/LKly5eFZzBgcMpsAgIgqdKAeuOA9Hd6rCYB3UI/ 1JQJMunYqWYjaBHFNkZWaXBP1yXipPP/hoUnH6vB7u3t7wLnl4wcmyqLUKc3hEDMGkmV/jveF2OPHbBhwrXq1bLOmclAw4u9V KOQ1beEOClCAAhSgAAVumgB7WK6TMkHcMMbF7IenhxdMzS2RnVuAQ0ePwUKjh4OTPJG /JZ4JQsnj 1D99YhSM3JB SH Nzb2tIClmYWCGoWhl2Re8VEfjM4uHqJych6aPPSERgYYlgmuXxu1/dKStuBT6d8gmMdxVK5T0bAXBOKIUMDsenHz/Gl5yPoKS9rPHcL8sImYmDJ8l 1K0ufFo oo0eh0eYi4/JZ7N wCuuvemBon9AKN Tmos0 0K8/gTPanmhRk3ei7iS n/QM1oW8jWXPtxNBkJH6K27weMXyxPfRbFqyBldCx6GfSwrOnC4KTEVvkb2nNxxMqy9PqXCGl2HuSZGpLgc2oofOxM4NXo6iB6Riee6tEOa8FJsWfI gR3rDX8xBiV6/CP/meGN4SyeojBxXqJzR7 5g/LZgAeasscLIYC0OLl6Kw3a98HZH0eNQsTxjnsbeCqrA6su75nwxpC3 MPZF5sMsLxGH/liMFYkBGPNSO9EfJDbTVri7vweeWTkbF7N8MOx578IgS WFpv4mWL3lJ/wWPAR UhLSbDuhR/MuGD7gJ7y2fAZmqcagfwsXaHIvIy7dHXf1FXNfLu7G2sPigwU/Z5hpLyMyLhOwtoF1UWSqT4xGTLoTWgbJvVncKEABClCAAhRoKAI1uU1sKHVtUPWQh4Kl5 hxeudu5Ilx86aiB8HV2QF9BgyCytpeTDgvW10FziScEzeIetHLEgXID8MmYUjvjnBvGoZeHSOwx1yDQ9HHkL0vEmYmGjE/xlOsohVifKpD2aKMPJdHzZRWTQ3fUW/g9dwvMG/hu/gr1xI HcZi lOD4F7rOza1WILZFVZbl HVF5aIj7tNYGkrhoc164bHZ92HIUVzKEqrJ1YE69gJTZZswk6xjGyLmiwjK1YeyxfD6mzt7YpuKI3V/waPVyxPrPB14mQeMjPn4vnSqUairT544PNv8IhYvuqGPCuWZ9oSj7zzMpTzlmHu678iTWsKe58wDHltIh5oKg95MnYc8L53Gt7K wrzl03H02lKODXrhWffeRzt5C 61NbWs/TqVf5MWX15ZU9SWMOnVSjsdy3HzFczoFVZwy24MybMGo9hTYuXuRYrgd19L8JXzcahZqPQy7u4l8QG3R dgiMfLcCid3ZAZ mBtuOaoXtzH4Q99j6m287HErG897uLswFLZ/h1exRifQyoU8/g3 WrMPdiOgrUorzAjpj0wigEGEaP6XFx107EOnTARHkZMm4UoAAFKEABCjQYAYUkNrk2O3bsQJs2bRpMxViRO0BAuox10x7HD9bPY97UboaVtqprtZS5GW8/OBfW0xbhhfY1Xeq5uhyrP8byqvepk6P5Ufh20nQkjp2LN3vLE 5v0ZZ3GF9PnIao/nPw QP8pvtbpMxsKUABClCAAtclUHEY 3VlwpMocF0CYohUn3FDYLvzeyw5nF2m56fy3PJPRSPWqSfuCrv1wYpcA5ZX XW49XvzkHQ6GmdORWL9F5/jL4t78GD3WxisiFlUZ1bNxwZdL4wb0uSauT23vr0sgQIUoAAFKECB6gTYw1KdDo/VgUAOTqz ESeCRmNYczGvwkiJOrGqlkp8p01dbSyvrqTLlKM7hR ffQFLzqjh1nIAJjw3Hp1db U1z0XcpmXYZTcc97UtXeCgTI34lAIUoAAFKECBehRgwFKP CyaAhSgAAUoQAEKUIACFKhegEPCqvfhUQpQgAIUoAAFKEABClCgHgUYsNQjPoumAAUoQAEKUIACFKAABaoXYMBSvQ PUoACFKAABShAAQpQgAL1KMCApR7xWTQFKEABClCAAhSgAAUoUL0AA5bqfXiUAhSgAAUoQAEKUIACFKhHAQYs9YjPoilAAQpQgAIUoAAFKECB6gUYsFTvw6MUoAAFKEABClCAAhSgQD0KMGCpR3wWTQEKUIACFKAABShAAQpUL8CApXofHqUABShAAQpQgAIUoAAF6lGAAUs94rNoClQrIKUhat1C/PhvIvRVJZQuYcd3M/F/f56rOk1V53I/BShAAQpQgAIUuA0EbvuARZIUuJB0Gekpl8tx6/QaLFrxKyL/2wyFOFLTdOUyuc4XFcu zmx4mjEBKQeJx3bjQFw2pLJptcfw/cRRePTbSOTJ 2uarmweDeG5dBUH16zAppi08u0rWzd9KqJ37cTRi7lVpymbns8pQAEKUIACFKDAbSagrov6SpISa7fswMXTUSJw0EOlUsLa0gI 3h4Ib90GJpbW110NvQhM/vhrE/q08oWNvXNJPgqFBDtbW1hYWhn21TRdSQY38KRi2TeQ1XWdKuXE498Vy/DbPwdxMjENBWpruPo2R7u7H8Ij/QNgro/HsimTsKrpO1j2XFuUvgl0OLVwEp7eFI73Fz6JVqoUrHttLL4yfQG/TO8NcykdWz YiI 3XkWMhfZWIJW5cmaBbeFQPvGYwOXmbX1rfCOUq1GWycxTnt mDk/UPQylF17Tk13aOLxi/vvoPTI Yh3Mei9CylJZy8vODtbAVD7jVNV5rDjT8TPR rX3wYXx3RVp6Xpi2eWzoTA 3kcJobBShAAQpQgAIUoEBVAqX3qlWluCn7FcjJzUETV2uEd gJrU6PlLQsHIg8hISEFRg1/H5IJuY3paTiTJQKLYb26214We7T9 IERT9rmq7CadW vBV5VltgmYNS5mF8P/VNLD/vjM6D7sczzV2gyb6Ki2ejEJslwaRM2to/1SErLR26kAfx3vgImBRk4er5aOz5cznefvJP9J86C1M6O6F8t13xOWPw3oR2MCvIRsr5o/hr XeYujcB78yZjLZWN/mmXemDIW/MxhBjDaxpOmP5VHZcYY uT34Av0x5MJcOZ3//EHNjWuOp5wfCSwZSWsP7Zre7snpwHwUoQAEKUIACFLjNBeooYClUsjAzgZurq2GsvYcHYOPghj9 /xGJ587A1T8UB46fxZF9/yJfBDdy2pbBAWjdtjP0CqXomVFix/6DSDhzElkZadCIj877dG4L94B2InMFNv93xPAQ438wtE9nuPiHY8mqVWjjbY3Q9r2KLpPxdHJwoxdl7Tl0BCePH0F TgZcHOzQuUM7OHn4GobdSJIKW3btRmL8GWRnZYobdD1cnOzQrWNH2Lp6ifPV5crWG0kvV05u3/4jxxB97DCyM9NhqlHDwd4WPTt3gJWTwKrRloeoJbPxS7wPxn78PsYGlQ0CB9coh5okUtp4oXloKAy5h3dAjwF3ofWs5/Dp7C8RGvwm jhcG4AobbzRvHnzwnPC2qKjXwEef/4P/HnwMbTtZoJza2fgrUX7kZheALWtN8IGTMDT44S5fHMvhkbtXTRSjbXQAABAAElEQVQHS7cdQ2xiOvI1Dujy1P/hNcNl1eLY3IfRf65ccxN0m7YSb3S7gCVPTcHf7T7BvPHNCntZUMN0 is48PO3 H7tHpxJUcDBvz0GPToRo1s7FAZiUjK2f/0xlu2JxcXkNOSKFjkFdMDwSU/hnhArw/DDQkON2N8SToYXWqh2aYA4FwS2CkNQSaeSvvp2G87VI33vAry0/RRikgpg5RWGfv97AuO6eEDkWPmmTcLuZfPw4 ZInL2ig11gF4yaNAmDgyzL1K/yU7mXAhSgAAUoQAEKNDSBOg1YKjbeRCNuuRQK6HTysBkJXq72cOvdExoTM8RdSMaufdvg5uQAF7/m4qgSZ Li4W2jQXDXAdCKD64dbS2LspTQsVUgvJu1NuRjbVm8v hwyY apFNg274jiD26E13at4elvSuOxpzFbxv xH1DBsPS2VPURYFzFy/Ax8EMgd26IE8rYW/kEazftAFjRj8Evbo8q9H0GjP8u/8oTh7 Fx0jImDv4onUzHz8s20jcjLTah6w5B3C s0XYdtjEkaUC1ZKAG7NE7Ub owbitVPLMGG7cnoPczZ6I2x0swcJgod8vN1ok4K2De/G4MhJOVhKSD/2Crxd iHkB32NqNxEEiMnn0f/9h0SPcXh5SiisdRlQetmLsxLEuWoEjJqOl/o5i3eIApYuVfUh1SRdHk78MA1vrVag5/hXMMFXwtm/FuH7N15H/sefYVwzkbeUgbgjR5Di zCmPhMETe557F6 AHPfnQev755Du7IxolFtI 0uOj vwAYR9z2HMc4S4v9eih9mivrM hJPhFVWWC6Ofv86Zmxxwegn3sJkpwzsXzYHX0 fC7f5on5lRs4ZrR4TUIACFKAABShAgQYgUP7O hZXSJIkMRxMhwJ5SFhqBnbs2QcLtQ6ubk0MJbs42Iqf8kMEI05uOH76FJKSLsJVBCyFmyR6O2zg4SEHDYWbyM6wWVqYwd7evmiv3EtS8rTcE2PpcvIUOB61D33DWyCoRZihHDc3T/yYcgWRh/ejax/PktWYnOys4elZWBcTCwes X0xUpMvwMotsFyZxS qSm/i2BRHRZk9w4LRvHVbQ5nWOSKQE8FcbTZ9cjzOZangFxKESmaT1CarWqdVejZFgKUe xIuiAFQzmXmxRRlJcnBST6UYhjZlYTD2LhgDWJNQjE4VL6DFoGGX1t09itMG9TUCrFbn8LGEwnQdQspyksJC79wdGhd3GMi0hZNDzG194Sfr4fIpWiTR2FVshlLJ2X h1/WJMBvzDd4bpi3oUclLNQTObFP4pcVuzFiWjcUhsIKmDdphbbhcl3CEOaUhAPPbMbek1q0a1Wb/1I1a7dz55F4YEBhu9uG yI/fiJ XrMH48J6FNWntLFSxk6sXJuMNlM xthutgaTplOSsO/hpdh2dDLata yX6Y0Ez6jAAUoQAEKUIACDUigNndXN1ztE3HJOPHddyX5ODtYY1C//lBb24ubdAViYi/gaOQ pKemwESlQEGBDlrXmg6HKsn2hp4kp6ZDocuBu7t3SVCkVOrhJoKqxIT9UOn10JbcGZcWZW9jLe6fVcgTw9kKp/mXHqvsWdn0aXKZ2hx4efqUlFnZOUb3iYBQjtMUYghd U2H0ziDd3hePNz8ahWSX1L5/ 5r/K3/URRg3 qDBjhRo2vh0x7s3JuNtVrkwBLu5ciu Wb8exc1eRp7EW8250UDXPv/kVqSZHXUIMzuSKuT t3AuHf8lpVZ5oFeqExXticE7XrVI7pXiPuirTkZZRRZRcZZnX0W6lO1qEOCLv4Blc0PVAxdBYd 40zuZmI mTMRj8aXHBEnTiTWt6VV5NrTCIKT7CnxSgAAUoQAEKUKChC9RpwOLnbmeYdK8Qq4RZWVjAzNzCcIMt3 YlpeTi77/Xop2Yt Ir5m3oxXyEDf9srZFfTTsiapquRoVWSKQ0ZK4Q7anZTWvZ9HLPk3ymUlkx0KhQiJGXSkcPuJnqcex0rAgBwspNsNfmpomFDrIhRq JCd9qyKPx8nNyRW IPKiqeJOQK/ZBral6fkRx0go/9edicCpLCU x8lvJFI0yadStxmGWmHRvLoa/WTu6wtXOrCQo0MeuwMxZv0E58Am89GQQ7BXnsPaj97CzzPlVPq1p8FXDdDW7euVro1CpRZsliFi2Vtv1tlteaU/ulaq0SeK9BKUjer/4Hu4PLHslRK Q ICg0nNqVWsmpgAFKEABClCAAnUrUHqvWgflmplq4OLiUjKkquzNYdKVFGikXLRv0wE6UxHIiInqGjHPwegmli9WqTTIy8sz3IyVzbPcuTVM52RnA0lljosXExDkWtjLotcrkZgohgo5OEAnBxVVFlKuxBq/cJB7ZxQmYvjbBfi7eNf4vGsSmrVGr8622L7lJ2y4pwWGelVxeRWOYklpK QfOoConK6IKGYuOIt9h65A08QXHmXvda8pqMIO7QX8tXANzlq2x4vdnCq9KVZaeSAouFnhpPsKp efjUGsPhRPP9QP4dbillqygKd1TYI3E5iKaSVZmdmG91TVVa5ZOpV3IAJMV PIYfFFjSFehQGV7jyORCXDLCAQXnIBtQxKKjS13MvranfBGRw4nAKLgCB4yvUpGhIp/sMY8lZ5 sFHsxqnz vh3tu3TDBarmi oAAFKEABClCAAreNQBV3tHVffyexIlY TLH3wF40CQiGJG7gtfni034jszGUYuK2g/jEPur0Gdi5xIovClTBxkxMZnbxLdeImqYzN5UQ0qItdhwSn 9rLAsn3Z88i/yUcwjrMuhm3q W1M9S1NfXvwV2HDhiKNPCzhmn4xOhru1H9gordHzkCfQ88gG fuFFnL53EDoEOovvXcnA8bPZJeVBOLceNgwBW5fgg2kK3De4LTzUV3Fs409YmeCGQZO6wEb KL6KwEyfFo8jkZEwEcPYUs6fwO6Na7E13g4Dpj6FXpWsEFam4Eqfarz94Cmtxrqlm DU0w 2qmQkiiWYjW4qLzT1N8FqEaD9FjwEflIS0mw7oUdwhTNrmE5h1Qkjh3rj5WUz8Zn5/9DHR0y63/QDlsX6YPjkDtfMF6lQSq1f1qzdErLjD2NfZD7M8hJx6I/FWJEYgDEvid4quUSlDeysJSRFbsO 855o79kFwwf8hNeWz8As1Rj0byGWtc69jLh0d9zVtzks2MVS6 vEEyhAAQpQgAIUqF BBhOweDhaolPnvmIOy17sOxoDtZjDYmFuDmsbt2qFFAo9urVvh7//ScfaTZthplGia9swOFQIWGqaTr5L7962JcyEzC6xtHFB7l4x0d8WQ/v3h7WLV1X38NXW0dhBuW59u7THv6LMf/cfgTYvC24u7obTFLUcx6Zw6oGX/s8JzZf9jA1rv8HfV7KhU1saVh6L6BgCh6KOC03TMZgxyxLf/7AGP3 2HhmiV8MloC3GvvMoRoVbVNpLIiZ0wNLWBqqDy/DGy8ug1FiIL470QXDEfZg tYovjjTWeHFc1XQUXp58BV8u/wZvrs6CXiOuu703mrkbGcKksEH3R6fgyEcLsOidHdBZeqDtuGboXjFgqWk6EciF/G8G3jYVyxr//D5eSwXsxbLGD7wzCaObmdagJbVLYrTdCmv4tAqF/a7lmPlqBrQqa7gFd8aEWeMxrGnR5HmFK3o/OBK7Pl Lees6oc1jzRH22PuYbjsfS/78Gu8uFoGqpTP8uj2Krn0BLhJWu2vE1BSgAAUoQAEK1L AQsyfMHyUvWPHDrRp06b a8QaGAQup Zj5crvMXbw3bASQ9O4UYACFKAABShAAQpQ4E4UaDA9LHcifmmbFYg Gw9TKQ/mllbIzddjr jdcbU2ha2Te8k0hdL0fEYBClCAAhSgAAUoQIE7Q4ABSwO4zpKkwMWkZCScPoFcsSStqVoJLw9XdOoxFDqxAhU3ClCAAhSgAAUoQAEK3KkCvBtuAFdensPSs2M4ID 4UYACFKAABShAAQpQgAIlAjVZO7YkMZ9QgAIUoAAFKEABClCAAhSoSwEGLHWpzbIoQAEKUIACFKAABShAgVoJMGCpFRcTU4ACFKAABShAAQpQgAJ1KcCApS61WRYFKEABClCAAhSgAAUoUCsBBiy14mJiClCAAhSgAAUoQAEKUKAuBRiw1KU2y6IABShAAQpQgAIUoAAFaiXAgKVWXExMAQpQgAIUoAAFKEABCtSlAAOWutRmWRSgAAUoQAEKUIACFKBArQQYsNSKi4kpQAEKUIACFKAABShAgboUuK0CFklSYdueA4iNjoSiLpVqUJYkKRF5/CTOn41ucHWrQfWZhAIUoAAFKEABClCAAg1SoF4DFp1eg0UrfkXkf5trdJMvSQqciY1Ddnpqg8OUIAKWY8eRevlCg6sbK0QBClCAAhSgwP zdx7wURRvH//dXXrvpAKhJCH03qT3IiiKrw1ULNgVbKjwV5QqoKLYQEGKoGBDVIoo0ptIb6HXJBAC6fVu39m728ve5S4XMCEiv/1wmZnneeaZme8ud/Pc7M6RAAmQwI1KwKW8HUmIlt2zbj0oVkSIYi Pp4I6FODTRp1g4GzbWtd2g0EgL8/eHl7VPebji0k1dfvl3 G7wKU9Gv7 2Am4fFtljvhpnzZ6Fvy0TUrN/SIv/vZSRkJy3HnNk/YOPBc8gocoVftZqo33UInr6/BYIsp0mPjKQ1 OHH1diy9yguhNyFD6bdhWhtEVK2fou5X6/E9qMXUeARhvi2g/DoY/0R72OpLLA5qK 5jF9fG4KZOYMxYeJQJHqr6hRtwTt3vY2LD83FOwNCoJFk2/vx/o4im9PgipYjF2Jcb39oDGnYvmAGPv/1b5zL80H1VrfhiacHo6G/8CtlYu3k4Zi6Nh2FBkDr4gm/sBqo17on7rq7DxID5Fi8vOMB8o4vw QxM5F/71xM7BdkE0A7GK8q3HdUX8o9hpVfzMTitfuRUuCBagkdMHj4o hTx8vYhnRlNxZ/PBNLt55Epi4Ece0H4bHHBiDBVx5jORjZ0GORBEiABEiABEiABP5rBMoVsOTkA8uWL0OErw6db2kHFw9PpF/JhLsmH9I1BisySK2mGAN6dDUylSqI7LkLWVi3dgU6dxsAg1Y1o6wg//9mN1LGOkx//QPsqNYT9z77EGr4Srhy9jCStN4oiTcKcHzpOLyxMA0Jvfvi3ufvR3hYJEJlVHl7sHjWamS3uQPP3h0G6fQaLJj3Ed7SReGL55rBFAKWUd94EiXkHl6Et6dG4N3RPRGhK5uYS8MhGPdQU7hZzLTwjfIRk/linFwyDuO zUWHh0fh0aBzWP7Fl3hjkjc ntAP4SJoysnIhL7evZjwSEt4FOXi8rndWL7oI7yyKxWTpw9DosH5eAzZx7H/mY990WnMvXoomlH0qmjPEKkzLrS1nY/NFozDjYCI Meg NfC5i8/wPMeN/eoR8PhKtPM5i6fg3sDC7C556ewRiiw/iuxmfYfQUD3wythdCzV1wzEjpI1MSIAESIAESIAES O8SKFfAkpKeAakwC53a9oZfeE0jjeoxJihKoKE3aLB1526cPHIIebmZCA8JRIe27eAXGgH5 Y6NO3bizPEjyMnKgKuYxHZr1wKRdZtjwfffo3mMLxq06gJJTFP/PngCe//agML8PHh5uKFhQm00aSGv4pQv IgICcKR5CyE7NyIBs07QHz5XurQixWXLxbNRbdGNVG7UVujPj1Lj68Xz8Z9fbrBL6Iu1mzeipTTx5CbkyNu9jIgJiIE0bH1cSDpEC5fuggvNx2aNUxAYqNWqhUmDY6eScOuE0uQl30FQX4 aNuiGSJj48XYTMe1cIqOa1xqDPYE hN7sC8nFD0efxZ3NjCf2lbt0UNlXLBPrCAs1uG 9z5E70ib0 /ZHE9hlcXMzy1o3hcnQbxh/cj/OGZqglTkGZ9c3tuNZugqh9H2HCwuqYMiTBHOioOqHKan2jUK9BA3iqZMZs0S4s ykJwf2n4rmBiXAVwvpupzFs7Pf4Nak3hsWZKmj9YpCYmGiq37gFWoRlYdiYVfhtv1jhaeZsPAakrPwEs7aHYuDoZ3Bs8sewvdmw7PE6qa8/ir92ZCHurocwsEW4uLrrosZDSVj73HrsO6tHC7e1WHXAE13eehw9G7mLAdXBc48cxNDxv LP8z0wONI8RkeMTGr JQESIAESIAESIIH/NIFyRQEB4vYvg9YNh48kibuBiu0A0WLttt04fWgHOrZqiv79bkexexB XfULtIUFYrKuxfFTpxHu54p fXqja/feCI6oYcePhOhqgejRtTNuu 12xDdqjc17DiDl5CE7tvZFIf5u6NSlLzbsPojUU6K/13DIgdPZ5POIDvZC/7590Llrb5zLKMT2rX iobgNrm/v3oiq00hsALATV1JPWbVg0BegdZP66N2rH3xCa DnP9bgyvmTZpuK4mTVpKWgC4sSKxqX8Pfv25Bqe6eVbCVlYP2S5UjRXcTyMUNwx6DBeGjkVHy/XwSkZi WYMVon4X0y0XwiIxCiLhDqTz15Wq66H545aUuyF48ER9tvmzxLetKHxL0er3lZTCYemJIPohDl71Rv2ldY7Ai1/Ns2Az1dCk4eCjdoU9XXz8RIBWgoMDkp8zxiOsyctA7mP/hyxjcNMTSjqWPTnk5qa8NQ2S4Bqd2bMd5438bA9IOJyHNrx4So3Qw5GYjR/KCn09J4OhRqw6ipdM4cUZv6YYAb Ejs1IYqQyYJQESIAESIAESIIH/LIFyBSzBItDocEt37DmeioWLFmDH1g3Iy7xsgZJboMFhY7DSHNG16qJatWB0bt8Zl/IlpFkm9BLCgvwQKSa/MdFR8PQNsNRXZ8KC/BEZFY3Q0BA0a9QAXoGRSE1NFiFE Y 6MSFIbNwBq9atQ3GW7Xfm5fcT7O DiIgI1IqNQXxiM2i0ejRIqC/GEIn2LVtB8vBFaso5Vd8kxNWMQt34RERHR6J7p47wCqqOfQd2i6kxUJGc7I1CE9kfI57tDtd1b PhIc/g7VnL8Pf5vJLJffEh7NpfgNCEbhj83FuYMvlVDAo7gNljpmDFBSVkUTwX4 zyD/HV0bq4Z0hH MknoNz1NQho9QRe/T8/rJs HatT7a1zmdop3DQZg/r0QR/zq99jc5Ak5uqGK5eRAX8EGZ9FMffJLQjBfuI2t/QrNitnEgyF2bh4bDMWzlmJZP/WaJdYEgSYatsZj6wQtzQ6vLbKM96y6muj0P ZR9Hw9Gd45vExeO 9MXh5fi4GvPoYWnuLwK56IhK8k7Hup7U4myf4GwpwKTkN eJ2uKKikvPhiJGZChMSIAESIAESIAES E8TsJ3VORishAZx1RFf634cE7t0HTx0CH/vW4JbmjVA/SZtcelKhni uRjL120D1m23 HDVG5ArvkW2H5pYzFQZDZJOnse 3X8hU0xY3XQaMXHTo7ia d4YlWXZWQltmzbA ZSzWLNuFbr3vKdsc6daCd5iY4BCMUaDvlDMND3F8zcSPD19xDf5BQ5razV6hFWLwsVzO6E1GASn7Ari5KhJN8T0GImPOt6Pgxt/x8rli/HmD18h4f7R N89DeCdk470PC1qtO2DWxqZbsKq9fRQ7Lp/Cv7YnIbeA0PNk/cCnPp1MkbPTEa7UZNxZ6zpMpGc1R gvpzcEXf3y3ho7/P49N1lqPdmNbuddmn8IN55tIXlGRaNWJmrbnzuRRKBlsNQwuKrcNMkDOw5yVTW6BBUry eH/8w2ssP5lsOOxqB1knI7XwsuBAzGC3ItnkKqviY69WyE8eTN2553Axt92ok/9TqjmcwseffF2THx/Gh6 7R3jaN29PVFk8EdDVaDmmJGjdiknARIgARIgARIggf8OAfUM0 moXF00YmewmuJVC5t2HcSGv/5AzeqxYlrmK76oNqB3pw7wDrEOLny8Sj2d4LCd1Mv5 OOPX9BSPLdSs11r8S26G1b8udahfVkKnVgN6dmxC5b8sAhJ / yNhVzWY34Zly tUae1pZ8l21tpi7pdKbFKEkyW8s tDrxfI7aqnRekkpWF2TTiuBUuhVricY9DIld7xGv2zHw69cwYt6H L71xxhazQU6cZ6ys3LEmD1N4YBHCEL9gDNiEwWDeMxbJ77dP7t8Il6dmYJ2r07Ck61LdszSiGdbyq4fZN0RlxgMGPkYdjz9Kd5bejeCrbXGktY7HLXj4ko9w2IICBKB7hWxuYPMz/zkftFlXMoSqzdBAcYVK9mBa NhmPJ4K7jnH8I3E2dgp3csGtQ07cBlbKCM8Zj0jv86H6/My/EhZW/CzHdXI3jY53iud7DgfSsGdp NES/OwJdtW GVdp4Iaf0opi0ciowL6ch380PB6tfxxMJgJMaWeHbEyHHL1JAACZAACZAACZDAf4dAuW4JKz1cA2pGV0ex2Eo4W9waFuzvC4POHZkZaQgMCECA6uXiJj9MXL4j9dJluEr5aNW8NYJDwxASEgxXsSOZ7SF/916eI8DXBa3bdsOGnbvgUiRWRsyHHDR4iNWRy2IVRw5YKuso1muRkiye3QkONu5YVlGcyt9fD9Ro0QhhUgrOpYiJv2d1xIqFjhP7DyLH7ETKOIWTl13EbXihxiAgb 8cjP30NFq MgFPtQ62BAZG83LUt 2bVuxY9tzwJji7aBG2it3myntoI ohITAH 3cdFZsTm468fX/jYHE46iWogijvMMTWroXa9fvg VG3I2j3LEz97oQIU8x1yhqP2cZhcg3jVfuS0k7iVI6PuD1QbNFsVnjWboC6XrniNsfMkqtY4w7/ahEIzt Eud LjQa69kPrkm3d1C6ZJwESIAESIAESIIGbjkC5VljOiMnVqaQdiIqMhrunN3Lzi7Br3wF4uRoQFBIBnYcGcfGNsXn3djEx90BQtWgUFBlQXJCJunXrlRtqSKA/CuGO7X9vR/XaCWLLZDcUF8qzXNOGuvLvtrh7eOH0 VTEZqTDy9/mG307LTWsE4Ojx2sh7VTJg/vyrVo1a9QRt56tQ0DwTvgGV0N6VpGYnJcvELLTjEWUdjkL58 fR6FeEj8keRj6rBQ06iy2WBYW3hXEydKYTabo4BK8vzIf9ZrURUSAOwyZp7Htx19wxr0eBtYRp1pXFz36JmDp7NmYscwHdyYUY f8r7AnoAvGthGrZNIFrF6wDJcaDEWPsMs4fsz8nJI4D4FRMQhyd1K/1B5bcgc1COn2JB5e/ySmbS4JGm26Xrro2gC3DqiL1Qs/wEdRD6GzvK3xzDUoaDwcfeJKVh9KKmrgJfo9cvBOvPjVh/ixzRTcGXPJyXhKatvNOeNlt1KJUBvRCI1Dv8Lq2XMQ91BX1PLMwuHl87AhLwaDGorfohHXW07qCZxJScHJvRvxy9I1SI65F2OHNS214lTilTkSIAESIAESIAESuLkIlCtgkW8Fy8wz4NimrSjIz4W7qyuqhQahW 9 0PkGCmIGdGnTDNs8XbHr8AHk/rUbHm6u4pmXKGhFwKLe76gsvJHB3mjbrrsIJLbjr31JcBHPsHh5esLXL9xYTSMCjVZiq9pN63/HsUO70Kh1V6chhlynS7v2WJx8UtW0eMalST0UFWRj0859Iv0LHu5uiBYP ruJlZdrOeTJZ3REJM6eOoak5cvhIoKriLBg3Na3H7xEUGc6KoaT/f5JKHb1g8 VDfjuk2 ReqUAGq8gRMe3x/BxD6JfNfk7fg1ibn8dbxR8jM8XvYlnM7QIie C5996DC3lb/SLTuDQkQJkZ8/EyJJHkUSgUwP3fPApHqqrK7u o3hPE4ruTzyANXs/sax82B DWuqCmoPHYHT h5j15dv4Ld8bNVrfjzef6ocIeSh223JH/P89if7rXsaiz39H59H TsejbrF0Xlv2eEtXsJa4N8RDb70M7axFmDn6B2QUuyOwRmPc tpw3FNHDrqKsPvLFzFxqwfCa9VHqwcm4Y3ejRBSrv V1k2xRAIkQAIkQAIkQAL/VQIa8UyGceq3ceNGNG/e/L86To6LBEiABEiABEiABEiABEjgBiRwjc w3IAjZZdJgARIgARIgARIgARIgARuOAIMWG64U8YOkwAJkAAJkAAJkAAJkMDNQ4ABy81zrjlSEiABEiABEiABEiABErjhCDBgueFOGTtMAiRAAiRAAiRAAiRAAjcPAQYsN8 55khJgARIgARIgARIgARI4IYjwIDlhjtl7DAJkAAJkAAJkAAJkAAJ3DwEGLDcPOeaIyUBEiABEiABEiABEiCBG44AA5Yb7pSxwyRAAiRAAiRAAiRAAiRw8xBgwHLznGuOlARIgARIgARIgARIgARuOAIMWG64U8YOkwAJkAAJkAAJkAAJkMDNQ4ABy81zrjlSEiABEiABEiABEiABErjhCDBgueFOGTtMAiRAAiRAAiRAAiRAAjcPAQYsN8 5vraRSmnY8NkYTPrpFAzX5uHmrSVlYP vX2LhhpSKZSddwq4fZ2PJ9nRINxXdfCQt xLLDmf/y8ctIevAciz8fjsu/GtOUAFOr5mPJX9n/svZ3VQXNAdLAiRAAiRQTgIMWMoJ6nqYSZIG51MvIvPyxcptrvgA5gwfjIc/240CZy1JWTi5ayeS0vKdT3Suxq zdv8LeikdO5d9i9VJGc7ZXc149SnY8v33WHc8t2L9ltUHKQ8pB7bi71PXsU2b/hQe/hrvzlyLUzk2imsoSpd34MvXH8U9d92Ppyb hKP51 DEURXpMjZ99Sl OFIEX40jo6uX/7M a1B0fhsWvDcbf2X/a6Koq4fAGiRAAiRAAjclAZcLg2NNA39 QaUDyM4DFiyejzoh7ujVdzD0mgr8NK/03ld AwaDK37 bTW6NaoJv8DQq29QysTaycMxdW06CsVyiM7NG/5h1RHf9Bb0ua0/Wkd7mHxqvRESHY2YUB/orr4VxzX oV8p7xQ2fPsNflr7N5KSM2HwCkNsw/bo9393oWe8P4xXi5gM/vra/fjY/QUsebMrPI29Kca5lePx0owTaPrSO3ihYxgcR JFSNn6LeZ vRLbj15EgUcY4tsOwqOP9Ue8jwaG80sw4pFZOFhsO0w3dHj9O4zp5G5W6JGRtAY//LgaW/YexYWQu/DBtLsQ7bhhW4c3Vll/GEvefgvH7piFpjW8rn/fxUrf7/N Qnqb5zCkqY/pWjD3Iu/4MkweMxP5987FxH5BFp10ZTcWfzwTS7eeRKYuBHHtB GxxwYgwdeApB8 xebopzHzjXBsmjASc9bcgnF9SuoqA5TyTotrciF /HMXjiZnoNgtEFFxTdB58DDc0zLE0pZiL6fS5S1Yu88drUY1NV faq2cd3bt2NPfgRxnfTb/33h/R5FNg65oOXIhxt3xCHquGo15P9 O5nfXKOP/iE11FkmABEiABEigigm4XL/2Ndh96DB8xYTueEo6Mi6chU 1mOvX/E3Rkh45GZnQ17sPE4Y1g1tRDtLPHca2lYsx9smV6DVqIp5pFwKttgZuHfMebq1oJv/Ar5S5E7NGvYnvU6PQeeD9GFEnGLrMk9i 4kdMf2Ej9r4yFS90sDdBLEbKH1Px2oyjSHx2MkaUGayIAeftweJZq5Hd5g48e3cYpNNrsGDeR3hLF4UvnmsGj5BuGPleA Ra7n/TI3n1B3hvXSia13U1EyvA8aXj8MbCNCT07ot7n78f4WGRCP2vBisVfZ1cgz/D6VX4ebcfuk5uB3/z9xyG7ONY//18zPtuC87la9FE7ddwFkvHv4GF2V3w1NsjEFt8EN/N Ayjp3jgk7HdRVQhjIUfjRJy2Fl0kLL3YM6o/2HxuVC063s3nk2sBs/Cyzh1cCey8h29dUq4tGkd9nm0xOtNTOG0ulsQa5plXzuO9Tnl6LPclkvDIRj3UFO4WRrWwjdKBHkeDTGgT00sX7EcB 58HA0cDcFSjxkSIAESIAES HcQuG4fWYXFWhw8 Dd6tmiELccvYsnbglLBoG8yqLfDvU7kPHsW/3duRlZcDb0x0dWjVBTFwjlKWTMeoNGmzduRsnjxxCXm4mwkMC0aFtO/iFRpRZtyy/kqTDms1bkXL6GHJzcsS3kQbERIQgOrY DiQdwuVLF HlpkOzhglIbNTKMo6y 6L4PC58Zht9hoUEoEObNvCvFm2 IjT4fcte40ueVQ3o1g7htRte1dWi9YtGYoMGpm93m7ZGp9490WTiCLz73kdokPA/dAs4iQVPPYM/Wk7DrGHx0InbfY4t/xQffbMehy/kw8U/Cm0fHodXelRTpnOW9qWcfZjz8utYFfQYpr7RD9HqK8hw4hr95mPP/PfxQ3JdPDxtPAbXUlYx2qJD905IGPscPpzxOVo3fgUdfC1dERkRrKyZhlHv70PtpyeJ/kZC3R21pSXv2RxPfvoZXFzMlq0bw XoNow/uB/nDc1Qyy0INeKDLOZSys Yt Yymgwfhz6RpoikYJ/4Jn xDve99yF6Rzpr0YDM7bPx0vqjSEotgk90Y/R44AkMbR8JU/hjwNlfRPAzbwdSMosE xg07v0Inh3aEiFKAFR4Fmu//AQLVu/BuTwPhCfUgpu4rUcJnyydlTPOzmVxKrYumoWFv /GiUt6BNRtj8GPP47 cd6mc21Ix 5vZ2L2sm04ll4Mz9A43PbyRNwXJzsvxoGZD6LXTDmvWnEyXMLf33yGOb9sw/HLGgTVaoV Dw/HXU2CTN/ii1vjts bga/WHcDJlEwUugah/VPT8Vp3Lxwv13VnwPmtm3EqsDWeiFdGbUDKyk8wa3soBo5 Bscmf4wrcrfMh H0Wqw64Ikubz2Ono3k66kOnnvkIIaO/xV/nu BO29/DK3fmY6H78tHUJO7MLKL7epKAfYveA9LztTE0KkTcW/dkuCjXZe SjOlU7EStHndfni1Go3GJVUsds6unbL0cU77bGpG6xuFesr/f0vLpkxU /aouWAFNh95BA3qObt2bSqzSAIkQAIkQAJVROC6fWIdPnkW3shBbJ16yPOKxIY/vkXr7AzofAOMQ79wOR9bNv2GTs2bICymNrJz8 HvY5qclKWDmBKt3bYLF47tQMe2t8DVOwhbdu3Br6t wb2DhyA5G9fkVxLTt7PJ51Ez2AtxnToiN1 PdVs2IXnrn2jTsjV8WjbHkdOpWLdtKyKrVYNfeE0xjrL7UuzqbfRZI8gDdTu0R0GxhO2792L56hW4964h0Gvl70QltGlUFzHx8vfFEny9vUX6Dw XcHQbOgA/PrEAK9anoavN0orh5HeY tFWhAx5BVNbBItbWs4gJ8x2Aid6U3QGv04ah2Xa2zFuVF/rYMVOF8vrFwW7sGrNBQR1fR4DLMGK2aFLJHre3xvfPr8Uq7Zm4pbuSkNFOLd6CsZ9cAC1n5qEUb2i7U/gFXNVaglWZJl4Rif9chE8IqMQYnuHopSNrQsWYm/YALzfLcw0oRcP0q9fshwpukgsHzMEsy4Xw69ma9z68KO4vb75tjVVW3K2oMgPzf5vBO4NlXD6j68wd/xoFE78CE8YZ7QaBCb2xcOv3IkQHwlpu5bgky/fwazaczCqg/hWXMrBjs9GY/IfXiLQGYUnarjg0v6VWHTIfsBSNvN87JszGuPWhOGuJ97A0yFZ2LFoBj55cybCPx Bll4FOLxgNMZ8p8ctQ0bggThfFKVnwCdceZtwQe3Bb KlHqHiStfAO0y XgtwaO7reONHDToPewWP1JRw4rd5mDNGjHHq xgaL2wEs8NbtiAlcihefqYBfPVZ0EYHQjq5sFzXHZCPIwdPQVt3EGopXRE9iBz0DubfIdZIirdhmg1zQ242ciQv PlYKsCjVh1ES5tx4owemjYtMWySeNnUsxTFNbn89xQEdHkKd6iCFYveQUa6sBHrDnqj1eAmMN AWWLp7Npxpg9y0mdLSxL0er248cx0aDRasapquri1EQmI912Aw4fFhg31zNe0pR4zJEACJEACJPDvJFDyaV6J/ZNXK/Yf2INGdWrD4OqG2tER2OgViqSkPUhs3lFMy4Gc/HwxBTIgOiICvsHBEP8sR1m63AINDh/agYHtmyOyVl1jnc7tO2PBN0eRlnoKOTp5leDq/SqNB/v7IEL0SQ5gUjOb4eju1WKVoj4KdTqEVauBQ0cOIDXlHPxFwJLjpC8B0YlGtyEBvoiKijKO280rCMt mo8raefFBDDeqPf28kBgYKDShQpJtVF1UNvbgL/OnBcTGT8rn4bMK8iQfNGsUWPUqyNPs pY6Y0F/QWsf/8LzExug1ffeQD1vW1n96WrlMuvqGZIO4OzuVrExtVW3cZS4s lZhxquxXh2Gl5t60wo6J4/xy8ti0HkQ98eFXBSolXOVeMs8s/xFdH6 KeaR3hZzMkKXkVFq8tRruXBqC28j l BB27S9AaLNuGNy/ISI9s7D/uxn4bMwUeH76NvqE2TgRE vQdnfint5iJUu02KJpTRSeHo5vxArG0MadRBAvJv6xLdAu1tSzuDo OLn2Kaw6dAb6DvXEbXGbsHS1uPXsgVl4/rYIYS2Ohj44tmob9puqWP0ti7mUtQnf/ZKG5s9Mxf0dTMFVnWdS8deDX2HdvqfRMnELvv3xFGre yleuDPG vkm8zM97oFRiK0ZaeqHaFnK3oIly84gVtQZMTBGjBZo3CAKeSefxJJvt KO1zuIMcqHFl6xTdG6iYmDLCneXY7rTjYUKzipFw0IaBBqfX2I1Vlb2rK5fOiqJyLBeynW/bQWPZ/ugmj3QlxKThOhTzGKiuzc/2WqZvlrSDuNszla1HRwTVoMrTISUjetwyGfNvg/46qOlVIM2Mm1E hEX rasvFvLhZumoxBfSZblLrqd2P6Z8MQJ1 A2hBUCwH Srko3gfCnK9IWrwwQwIkQAIkQAJVR0CZhlVqD1Iv5yAj7QTqdrzDOEl30ekRF9cQ w5vRMMm7VCsc0H1aoEIiayLb39Zgfg6tVC/fgMEBFcz2pelu3QlAygqxvJ124B12y3jcNUbkCu Za1eJ Ga/FocWTISvL19UCjaMugLxYzIE1qNBE9PHxQUFBitnPXFtJZkcWjMBPr5iimUDgX5eeaJnbX epRcEvvhrqYbMXPUY0gSt7vcemsftK/jr5qwGnBx buYmh GwdOfRpsgR9NE694691ti73wKWWIr57Sh9dEibCfWfCsCjrjReKBpoMPJq3VNpVSAU79OxuiZyWg3ajLujLX9r6AXQcFyHA7qimFtS1ZOpJx0pOdpUaNtH9zSyHTPT62nh2LX/VPwx Y09B4YWnY/tBGoXy8YBTuP47y E rqipC86St8sXg9DpxNR4GrL1xz9dAlimtMHPpzJ3C6KBTtE8v3bXhZzPVnj FEfi5Sp92L/u8qHMS38cUauKfnouhMktgtSzyv0ShCde4VO/upXtQ5bq6j3MEG8TxQowYhmL8tCWf1HRDv4HIpq69WrUkFyC Q4ObuXjZbVSWNzy149MXbMfH9aXj4tneM9dy9PVFk8EfDAEtPVTVsspJkfO RVyfKfUjJ2LguCb6t70ND5a5GVWVn106vTv/w2jK35dL4QbzzaAtLcKdxD0J1ZXcNjTvcxXcSynuWqnvMkgAJkAAJkMC/loDtLK0SOqoRgUmS HZRiy8X/2DlX6Mx4ML54wiKiYOLzoBBvbvj1PkU7N6zB998/yM6tWyIBBHQlKUzPocq/PTuJL7JDYm08u/j5Vlm3bL8WjkyF3Q60 RFEpMZ4yEmYhqtTjwnYyo664vZjVWiNT7DoxGTI5MT8yM9VjYVUTCcFZNR8Y1xVEykmIyKTUh2ssbhs3G612rsZP332HaU9/ix8fnICJd8fBNO/SwL9 R9Q5/TuWfrAALSY gAZiRy2nh1O/Jg/a4ChEeRqwJ kYCns1NbdZ4r345BGcKHRBVHS4 J7e9DS8Nqw9nnntITR//394/41RyH59Ip5qXfo2thIv6py8sjIRr85MQbtXJ FJe/X0R7F23XlUu UFJCiPTQgXGvHsi05cb9lZOeKMeZom0B4hCBWLVmeuiJ3NEOp0si9J8hhMqwOGk99i/MSl0PZ5Ai89GYdAzVn8MmUCNindNV4Q4towmC8yRe4oLYO5Tr5QtcHo uIE3F1XmcHKjjTwDPKF5pRyFTpw7uCUl7NnpZ2W0Ver b7GDR7uGhSKLwbK35YGIa0fxbSFQ8UGH nId/NDwerX8cTCYCTGqsdeuluyRBsShQgPA/YfO4kiNLZM/u1bm6SG8 J2sCN aDOkYalrWLZwdu1IFXBtye1ovcNROy7O/g5lIviTv19xc5dv5 NBAiRAAiRAAjcGgav4 vDaBiQ/bH/i2H7c0iwRd9xxh U16I7B8AmtjoOHD0JrnvFrxIpFzahqGNinF2o3bIu/9 2Dq7gXWz4c6YL9fWHQuSMzIw2BAQEIUL1c3MzT7Wvwey2jLU9fyvQr qnTuRq//XQwNyyzukNl8Xn89uUynPBuhd52d9oSNTWeiGx2Kx4f/wkmDArAoaUrcMCyta8GbrF98erkkWhxZTHenrwc5yw6h62aFGX6Ndf1aIoenUKQvmYRfjllWlmweC1OxuqFK3BO3GbTvY2fKUBQlG7R6PbSVIzpKWHluNfw2d/l 72TvL1zMPbT02j5ygQR5AQbb2NSXCqp4cxf2JEagGat6ljfNuNZHbHVgBP7D4onskyHlHEKJy 7IDJKfrbDyVF0HH/vuQyv2nGIEvPmwhNJOGlogP5DeqBpXE3UrCPk8lZ65kMXUxe13S9g59 nxUpcOQ8HzHVRsajhegXHzhkQERODGMsrGiHeWrEwUgs1XS9i755ky/MPJS26QZ7j5mTnmkNGk8bUP7mO6scx9eewd38aPGrXRbSz2MBBX0vaFTkRZIWJLdiuXEwTwcNVHmJFwb9aBILzN2Hu90kI7toPrcsTbLs3QZd2Abj0x9dYfrY8rYqNATaswzH/tujYwEEw4Ozacaa/yqHbNTekITUNCA13HljbrU8hCZAACZAACVQBgUpfYTl2JhkasRVovfg 0JofsFfGGVsrHod2rEL7fLH9bpEOF5NPIDgoBEV6jfHHE73ELSDyLmLpmXkOdd4eGsTFN8ZmsbuYQeuBILHbVkGRAcUFmahbtx4uZeU7rFuWX6WPV5M664szX1qNHkHiNrj9x44jIOykeJxZBz8xvmDLDmLOPJj0hozT2Lt7N9yK83D53CFsFRsQrD0dgN6jnkIX XYuy5a9ZvvzW/HLHgNqxobCo/gidp8SKzC fqV 9M4lvCteGH0OL738GSYvjsOUe vY/SZZ6aWhnH4hvgtu sBzGHDgLcx6cSSOid MaVNXbGuccQLbl/ AlYc90OnlR9FB3s/W9it2TRBaPfE2RmS8gKkTJyHy3bcxIPIE5jz HH6tNxaLRra0DjikC1i9YBkuNRiKHmGXcfzYZVN3xbf4gVExCDLGuOKXyg8fwBldHO6sY/NfRFcXPfomYOns2ZixzAd3JhRj5/yvsCegC8a2EasUyuAtqYTc03vw1 5CeBSkYNfP8/FtSm3c 1JL4zfg phYREk/4tevViOkcyz8dWlIMe5fa 6WT1sMHlgDL33zFsZjCPo2DINb/n6xW5gtCJN9Wcw1/u3FKubXeG3xOEzU3Yte9cPgmn8RpzIj0LN7IrxkfZ v8epXb Ed6V50F7eu6XJSkR/eUTxjE406tdzw45qvsTThVsRKqcgQk/NOiW1x54AYvLxoPN73fADdaoiH7lfPxaKTNTDo6dZl3uZYVl8t IwZT/F/vAYMyw/heHFn1Lc5Jda2SklCTuoJnElJwcm9G/HL0jVIjrkXY4c5 m0UpZ451Xij9YNPoPOeSfh05Is4eltftKoTAk9DFlLEFzDJEYPwSFfzM0VyFbGN8vp1xxHY7hHUdxCvwNm1o/O5ymvLps/lKBpSDiMpMwQN44LtXKvlcEATEiABEiABEqgCAuX66L/WfkmSFoePHkaNsGC4 viX tY2rmZN/L3dDSePi1WWkDjs2H1A/I7IFbHKAPFgqNiauHMPcSeZFtl5hQ518uy7S5tm2Obpil1ikpn71254uLkivlaU2FWoXpl1y/Rrfz7oBEXZfVF27XHkRL5FrkOrlvjjz0z8svp3eLhqcUuLxlcRsOjg7e8H3c5FGPPyImhdvcQPR9ZAQrP/w5ujVD8cadOB4ivHsWHx9 KB kwUufgivG4bPP7CYNSWvx23CW484u/BS0N24pm57 Pb1u/jPsvT6DZORbFMvzbmGv8WePzd6ai3eBFn0Opi7MgsEjGDUadMRTU 5Bn8QAx6sXYmOFLiNewdHnR HzKUvQYHJjFBaK29gCA0pPyopPiI0SCpCdPRMjSx55Es8k1cA9H3yKh4y3Sulx/vQ56IPbI7LUVk9axNwudsUq BifL3oTz2ZoERLfBc /9Rha2n5zr/FFjUYNELh5Mca/miWe1RJsE9rhkYnDMLCO6T4zXZ3BePnpS/ho8af43485YlMKT/gGxiA Qgl 3JEwdAIm M3G3GWf4q2vsqB380VoVEO0r 5VanxlM/dC40cn4U3/z7FAbAn89vxcwDsUsR0eNu6 5iVCqEaPTMRYv1mY98uHGDs3Hzr/6ujwWFO0rRWCjg8/g71TZmPeWxuh945Ei6Hx6JhYA/UeGIex7mJb428m4bUrQKDY1vgesZ3wXfFWN3bZnPGruT7EjmBt2qL6gtXYJLbjrV u7XiLsfvLFzFxq9gGulZ9tHpgEt7o3QghV/GOpwnpiJemi1vIFn2DFctn4s9LYnXJ1Qch1RPQamCh8f1McWc4vQHrTwah7eOJZexW5 za0ZT/2ipFszwCA5I3b8LJoNYYXlfpeXnq0YYESIAESIAEqpaAJvXOmsap RHxS/fNmzev2t6wdRKoAAJS9u8Ye99M L4 Dy 0KnvSXAHN0cX1ICBdxK vP4a5viPFD4x2KLWj2/XoguM2DDg /0k881sTTJ79L/5BxoI9 GT469jfawY uIe/dO/4fFJDAiRAAiTwbyNQcrP8v61n7A8JXCOBQrGqdzKkM3o2ZrByjQj/fdU0oeK3hG6F/6Y5WLAnt9SdgVXaYf0JrN9wRmxf3QEJ/9qFiyIc//5zrNB3wdBbqzteraxSkGycBEiABEiABOwT Nd vNrvLqUk4JyAe5Mn8cVnYmtgXt3OYd1AFu4J92DkwxIOuTq7ufL6Dkp/Yj02nBXbQT8Xb/281PXthpPWxP H0Ka457lBpW9ddFKTahIgARIgARKoagK8JayqzwDbJwESIAESIAESIAESIAEScEiAt4Q5REMFCZAACZAACZAACZAACZBAVRNgwFLVZ4DtkwAJkAAJkAAJkAAJkAAJOCTAgMUhGipIgARIgARIgARIgARIgASqmgADlqo A2yfBEiABEiABEiABEiABEjAIQEGLA7RUEECJEACJEACJEACJEACJFDVBBiwVPUZYPskQAIkQAIkQAIkQAIkQAIOCTBgcYiGChIgARIgARIgARIgARIggaomwIClqs8A2ycBEiABEiABEiABEiABEnBIgAGLQzRUkAAJkAAJkAAJkAAJkAAJVDUBBixVfQbYPgmQAAmQAAmQAAmQAAmQgEMCDFgcoqGCBEiABEiABEiABEiABEigqgkwYKnqM8D2SYAESIAESIAESIAESIAEHBJgwOIQDRUkQAIkQAIkQAIkQAIkQAJVTYABS1WfAbZPAiRAAiRAAiRAAiRAAiTgkAADFodoqCABEiABEiABEiABEiABEqhqAgxYqvoMsH0SIAESIAESIAESIAESIAGHBBiwOERDBQmQAAmQAAmQAAmQAAmQQFUTcLnuHZAu4/C6jdh1IhORPe9Gh0jGTNf9HLBBEiABEiABEiABEiABErhBCFz/aKH4MJa /yGHoVDlwx3CCY2E0SIAESIAESIAESIAESIIGqIOA8YJEyseat29GrZ0/0GT4Px/TW3TScWogn /ZEz1734v2/CqyVLJEACZAACZAACZAACZAACZDAPyDgPGDR KFll5bw1QD60 ux/oQ6YjHg1Pr1OFkMaMNuQdfG7v gK6xKAiRAAiRAAiRAAiRAAiRAAtYEyvUMi0 LbmgbuBYr089i/bqjuL9OPIwV9cexbt1JFEOH6I5dkOgqnBvSsfv72Zj38xYkXSyEZ3gibrn9QTzUL8EY9Fg3bypJWasw5u6p2CbFY9hn03F3jAG7P3oAryxNg2 f8Vg0ogVcRFu/vjsTvx48heS0DOTqPRAa1xa92gXj LrfseP4FcC/Bpr3fwzP3NMEASLAMh76S9j57eeY 8tWHL2kh09kIjoMfhTDetSCp9FGjwtb5 Pjuauw6 QV6D38EFq9Ex4b zja CtOzL6YkAAJkAAJkAAJkAAJkAAJXFcCzldY5O54NkWPjtWghR7n1v2JJLGiIh/FR9di7Rmx4qKrgS7d4uAi5WL3zFfw2qxV2JucC627Btln/8bPH76C1xcdRZGp2rX9NVzAvk07kXQuHQUufvB1zUfq/t8wd9bX2HA0G66eOuRfOor1c8fjkw1ZkIyt5GHPF6MwevbvOJiuQ1CoJ/LO/I2l017Du2vTjTZS mp8OGERNh27ApewGqge6oasS0Vw82awcm0nirVIgARIgARIgARIgARIoOIIlC9ggRsSe3RFjE4soKRswJr9haIHRTi0Zh3O6zVwS iBbrE6SGm/Y Evp1GkCUXnUV/iuXYOZT4nYy5OHwd4uxJacCOq6JwK3jFuCb a jS6AIKjRuaPHcPCxe/AWeaeYBjXjmZteOJBFawdSfZadR7JqIhz76CvO XIjPn20BL1zGpl824JKIagxp55BcKEHj3gQPTpmBjz4TvuY8iSblWnuqgPHQBQmQAAmQAAmQAAmQAAmQgEMC2rAlJyC/nB0udXqid4IbNGKlY8Mfu5FfsAer16XCoPFCs75dESFih Jjh3BEnvz7t0SvDmHitjE3RHfrggauGkg5R3BIXo2poEPjE4d61UUEJRmQl5svHqIJQt26YWIVSEJOZpYxYCk dhBJoj9S4QHMfrQ/evbsjfve345cSYL YjIuGBeHWqF1lLiXLX8HPhz2AEa8swDrzxaA6ysVdKLohgRIgARIgARIgARIgAT AYHyryOIlY1u/VpgwYFNSN wEr/Ha7HxkgGawFvQ/5ZA0wT/Gmf5Go0WWrmuoQhFRaabuZyPyQWuLnIlCQaDKRBycTUPx2CAvGGy1pxq3Guh4 1tEKVaT9L41UeoiHfg0gAPT5uG6ku wQ8rt LA6nk4sGEz7p/6PobEyQ/l8CABEiABEiABEiABEiABEqgqAqopvLMuaBDQvj86BYs1jOxNmPnZRmRKOsT07I9mnqa6LrUSUNdNrKZkbMfK9RfEw/hFOPv7GuwVQYjGqw7iokWEIIITnRwoiFu3Ll7MMz1r4hGAQC8RfBiScfBgujHYcNab8uhdatRGTZ3oT1EGikI74a4HHsSDDz6I 27vg359WiBUjneKs3BFUwe9HnkDn86fgaEJLpDyT2DzX crrB/l6SttSIAESIAESIAESIAESIAEShMo/wqLXFc8fH9b/1pYNfco8vJE7OHZDAP7i4ftzX41IV1xd58fsHfpWfw56UFs/dAVRTl5InBxR53b7kQbH2FoiEL1KBdoDmZj/TvDMd1jNp5vnYj2bYKxckUadnz4MP7vKx8Ysi6Zghmz72tJNBE9cHe3n/DWqhRsmvE4Bs/2h7cmD1k5Hug biFeaOmK4iNfY QLy5AXFoEQryJcOClWazTeCA8P4G1h1wKddUiABEiABEiABEiABEigAglcxQqL3KoONfrcgVbGHbQ0CO44CN3C5GUK8yEmfikEjQAAQABJREFU k2Hv4O3H yCemEeKM43wCuiIXoNn4gJQ JF2CIObRT6P/c0ejeIhI/OG34B8m1XXmg5/E083acRIn3FMyjpV1DoGojIOk3QOiFUPJdyjYfGH22em4q3H qBhlH 0BVkIqvIDSG14hDmWmgMiPQGX0RV90VR2ikcPXERUmg9dHlwNJ7q7M A5RqxsxoJkAAJkAAJkAAJkAAJVBQBjSQO2dnGjRvRvHnzivJLPyRAAiRAAiRAAiRAAiRAAiTwjwlc8 LFP26ZDkiABEiABEiABEiABEiABEjACQEGLE4AUU0CJEACJEACJEACJEACJFB1BBiwVB17tkwCJEACJEACJEACJEACJOCEAAMWJ4CoJgESIAESIAESIAESIAESqDoCDFiqjj1bJgESIAESIAESIAESIAEScEKAAYsTQFSTAAmQAAmQAAmQAAmQAAlUHQEGLFXHni2TAAmQAAmQAAmQAAmQAAk4IcCAxQkgqkmABEiABEiABEiABEiABKqOAAOWqmPPlkmABEiABEiABEiABEiABJwQYMDiBBDVJEACJEACJEACJEACJEACVUeAAUvVsWfLJEACJEACJEACJEACJEACTggwYHECiGoSIAESIAESIAESIAESIIGqI8CAperYs2USIAESIAESIAESIAESIAEnBBiwOAFENQmQAAmQAAmQAAmQAAmQQNURcKmMpiVJQnJyMi5duoTCwsLKaII SYAESIAESIAESIAESIAEbjACbm5uCAkJQXh4ODQaTbl6XykBS0pKCs5vWAFpxRwg6zLkrhi7I/4o3VKn6jw0krHjVjLVUBS5SmTJyjpTbYvIKmOrU8pKCkljqS/LFLlVKgq2Ot2ouWjfvr1VW//lwsaNG2 q8f6XzyXHRgIkQAIkQAIk8O8gcLPMr TFjKNHj0KOFyIiIsoFv1IClrS0NBhWfAmNCFZcXV0RGBYOTx8faLSmO9AcBR2O5PJIytKVa6QqIyUAUYksWUc6RS4ZDMjLycblC6ko4uqRhRszJEACJEACJEACJEACJOCMgLzCUrt2bezZs6fcAUulPMMiR06arHToXFwREVsbXn5 /5pgRYZYVvDjSKfI5aDLy9cPETVrGcenyJ2dHOpJgARIgARIgARIgARIgAQAd3f3q3pspFJWWJQTEVwtHFqdDnnZYkUi5Tz0xUWWYEGe6CuTfY2D28AUvexPnbcq2ypkpXKYl0WU1REbsbGo6Eql4vYw ZDlap0chAVFRMLD2wfy C6cO2O04x8SIAESIAESIAESIAESIIGKJ1ApKyxKNz3EbWDykW4nWFFslKdGlLjDNpXtFJmSNz6fIwvVCllpe5htZHu1qb28IitJlTClpK6sk4OuS2I88iEHLTxIgARIgARIgARIgARIgAQqj0ClBSzy5F5rfmbFICb5ylESEJglQmArU8qyhVVeLqgESrGs1NyKsZ56IwKVG4tLRWZMzQUrmdmZocg0Hq1Oa6lraYcZEiABEiABEiABEiABEiCBCiNQaQGLbQ Vib8sV/LKrWBWMlVFi51cx1yQE WlMnWYVWzN1Y1 LHlVLbsym1vVZHPFTlWVWRIgARIgARIgARIgARIggUoicN0CFrn/6sm 7a1gtuNTbI2puaDIFFu57Oyl2Mqppb7IKHklVdupbZV qmW2tiyTAAmQAAmQAAmQAAmQAAlUDoFKC1jUgYDdvBAqcoeprDDbKTYyBrO4XERsbS1lkVGv2ih S6VyBXGYkzLzRiX/kAAJkAAJkAAJkAAJkAAJVBiBSgtYrGb4orvWE377D7TLo1LsbIMJRafo1WVZ5ugl28mHojeVHLej FdSU93S/VX8WDpsETBDAiRAAiRAAiRAAiRAAiRQUQQqL2Ax99B64l8itCdXZLapXEuRKXl12ezVbiLbqW3t5RWZbaq0pThQ9Ba53RYpJAESIAESIAESIAESIAESqCgClR6wyB21muibH2QvJTePyGgr/ljVUenUcsWHLLP3MlczJopeqaPojP7EH2MqhEpays5BvxU/TEmABEiABEiABEiABEiABCqeQKUFLPLE3 HkXzUOtY1RLARqmZJXUtlGzisvYx0HfxQb27qyeSmZWmBPb25DbSbn1WWzCRMSIAESIAESIAESIAESIIEKIlBpAYu9/tnbxli2Uyb9ynMrSl2LXBGobBWRMWgQf S6Vi/FwJwqvuSikldSxVRpXy23yqtWWZQ6TEmABEiABEiABEiABEiABCqPwHUJWKwm/aqx2JMrMnupIpNdKMGJJfpQ TVmhbHFxqyT6ys nKVyFcWmrLys40ECJEACJEACJEACJEACJFA5BCotYFFP9uWu2/6eiaJXUjk6UPKOUqMf2U4xMPo11ZNFti/ZXj7sBS5GuVFrqmcpm30rTSg zaZW47DUUZRMSYAESIAESIAESIAESIAEKpRApQUspXopZv5KEKDolLJtACLrLTrFWJYpQrNeVVRZlWRlvdrGtr5sqeiV1CgzF9Qyi62tUFbwIAESIAESIAESIAESIAESqBQC1yVgsV1dUY9Emf8rqaxT8kpqlJkLcmIlN5cVuTqV68mHIjPmVZWVrJIqtupUzsuHtU3J77KYtPxLAiRAAiRAAiRAAiRAAiRQGQQqLWBRT/Dl2b66LOctZZXOIrMZqbIyotbLeXXZpoqxaGuj2Cv bOtY9LLCXLDrQzEsMbN1xTIJkAAJkAAJkAAJkAAJkEAFEKi0gMVe31TzfKNaXVbypVKzQC1X8kob8gqO7UvRyalsr9SxpOaMpWyuoJSVemaxMVHr1HLmSYAESIAESIAESIAESIAEKodApQcstpN8q7IoqMtK3pKaM5ayioE6QFGJLVl7els/ykqLrVx2YpQpCqVs8W7db5WYWRIgARIgARIgARIgARIggQokUOkBi9xXed6vmvvbLStjUuzKDiasnyFR/KtTxZ cysGLclj8mwW27chixUbJl1U2u2FCAiRAAiRAAiRAAiRAAiRQCQQqLWBRT/KVflvJREFdtpdXZEoq 7ENPtQ6pR2Tna3/MoIWVUW1P2NeJVBlLTXsySxKZkiABEiABEiABEiABEiABP4RgUoLWORe2ZvM28rUZUvekinxodzipfhVmRgByGXlZRSY/6hltj4sdmZn5sQoVudlgW3ZkcxYmX9IgARIgARIgARIgARIgAQqhIBLhXhx4sR2sl9WWdEpqa1rtVy5nassG8m8sCLXK1ljKamhyJVU1qjzjsolHpgjARIgARIgARIgARIgARKoLAKVusKi7rQcBFgOUZDLapklb9bJtopMuQ2spCx0SsHsVC4qL7PImMh2imlJagpdSsrmyiWJqa5SVgyVslHLPyRAAiRAAiRAAiRAAiRAApVNoNICFiXIUA9Anver5v5GlbqsDkIUueLHUpYz5oKSVXRKW6XkQqD4Vmxt/cp1FRtjXnFmThWfNmLRFXvrNrZWLJMACZAACZAACZAACZAACVwLgUoLWJSgolSn5ODBRqguW dtVkJUSlXW6E0uKy 1e7WdEpAoMnWwocjkuuq8pWwrVBpxJFf0TEmABEiABEiABEiABEiABK6ZQOUFLKou2ZvT28qUYEKuptYpeUUvly0yc14py3XlQ7FR5ErZqDMLFZ1iL6fyobRjKpW0pZSNNuoC8yRAAiRAAiRAAiRAAiRAApVG4LoELHLv1QGCMhpbmbpsb/XDWq94KUnVekWqlil5JZVt7LVjr25ZMkXHlARIgARIgARIgARIgARIoGIJXLeARe62vHqhDhaMMlkuZ8yH3bxaKOzURTmvvGQXSt7WRtZZDrPSkY3iw2IvMkaZuoJayTwJkAAJkAAJkAAJkAAJkEClEKi0gKWsuX0pnRCoZVarHmaFolenSt4RGVmv2JRKFYHRpuTBeaNYpZN92xRlkeUoS2cxYoYESIAESIAESIAESIAESOCaCFRawKL0Rp7Q25vU25Or7ezlFZmSym3IeUcvWS8fir1tqtbZ5pWyUkcuK4fSnlJmSgIkQAIkQAIkQAIkQAIkUDkEKj1gUbptb Iv62zl9lZX1HaKfXmCBrWNup6lT4rQ2I SVRZ1e4qtkqqqKCKmJEACJEACJEACJEACJEAClUTguvzSvbHvYqYvT/ZLTfjtyNU29vKlZGqBAkrEH0oIIqvlvJLKJmXlZb2kNjDb25PLMh4kQAIkQAIkQAIkQAIkQAKVQ C6rbCouy/HAvYO29UVxU5J5TpWebmgFqidCrl6i2K1mZKXU2sbJcRRO3LchLUVSyRAAiRAAiRAAiRAAiRAAhVNoNICFmMwUEZvHemVYEKpqpSV1CI3C TE0Uu2VQckxrL8Rxyl/JnEVn8Vv1ZCVcGZXmXKLAmQAAmQAAmQAAmQAAmQwDUQqLSARd0X2 DAohMKezpnQYait1fX4ltkFL2tvSJXbBW9UpZTo42todnAgVhdnXkSIAESIAESIAESIAESIIEKIHBdAhZ59i9P8h1N9E0669uxbO2VukpwoZRlBoqtOlXYKHZl1VNsTb4kJ/00N6iuxDwJkAAJkAAJkAAJkAAJkEClELg AYuq60oAoRJZsvZ0apmSV6dK3uLEnJHlis42lU0UmdncmNiTKfqydIoNUxIgARIgARIgARIgARIggYolcN0DFrn78uTfUQAgr4TY6ixllc4iU/mTZcpLZI2HYmdMzQVFprZRVmAUmZLKtrb2io4pCZAACZAACZAACZAACZBA5RKokoDFOCQRBZQVDNgGCeqAQq1T59Wo1HKrvLogKtgULS5kuVHnyMBiyQwJkAAJkAAJkAAJkAAJkEBlEai0gOVq5vnydsb27G1ljsqy3PYlA3Nkr8C01St11NsrK7aOUns HNlSTgIkQAIkQAIkQAIkQAIkcHUErssPR5Z3Um/PTpap5UreNrUdtqxX/1ikUpbtlLrWj/mb5LYyW7/q vZ0ikxKW4oXHvwK2bXC4SGEuqi ePHeK5j8sS/entAPvue/xvMzTHl/pUNK5QpKpYw9 HWHF3p0rQO3CvJJNyRAAiRAAiRAAiRAAiRwPQlUfsBinozLidN5uTCwa2eWK2AUP0oqy9W3jEnmqEPWq4MWo50sUxSyQByKH1u5SVvy12KnVHIS3WhFkDLq/QdRS1nHkgyY9jbgKhwZStxWWk7K2IvlfwSjEwOWSmNMxyRAAiRAAiRAAiRAApVLoPIDFpv y5N ZeJvo7Iq2rNRy5S8OlBRHCgyOXCR7ZS4Qp232Kr0isw2VdpS/Njqy1s2nF MF8yrKr7qSoZ0bJs9DQsPGOCJfHi2fxwv3REPt7MrMOXdlcjw8oZGXw09Rj6O6J ew9yocXi7d5CQHcGcZ ag2rjx6JW70tp2xFD4rVyHs0mueHfCbtTq Tjua6bHdjvtuJ YhyfeOY76UQacS06B1PYedM3ZhE3HziLFpRteGXsnaruqO8w8CZAACZAACZAACZAACVwfAtc9YFGGJQcBSiCgyGxTezbqOkpgItdTP3eiPBEj621XW5Q2FD9lBSHlsVH82UsN537FpOf/FreEaVGt 0i80tyeFZC/bRY u9AL703rCD/pPL59aRp aT8Znbavxtkmz LdobGWW7oMfboid ofSO55J0L2LsfW6D6YFiQhfa0d214dEX0qGCNf6w0f0XT lsl22pmCQUInFUSgx8vDUc wFe/c/wVSp3yEt2KLsX7C0/jlwG14tnGVXSr2oVFKAiRAAiRAAiRAAiRwUxComlmoEgkIxI4euLfQF7Yqc6NYXVYHKkodRWYJXIRCHZjI9cu6/cvkXxJ1zC0ZKyjey5/a3hJmOLfJTmUDLh4/icwzuZgxcYNRnye5IiFDg5Duw9Bj9hy8/nwWXKI7YejjA1Evojt6 4zGymM9UefXA6jf73F4i4DIy45tvFVrjtoRZMQDLrro2qghP iiD0JwSHXERstLKhoEBeqQm6OmZ WUBRIgARIgARIgARIgARKoVAJVE7DYGZIcE5jDAztak06tV6 uyBXUOvX02naVRbZV6 Wycig HOkVu4pNtQiuUQOB5zvj2RfawEfuhFgWkkTHpeJ4DHjuLQxEIfZ89BgWbOiO8b0D0KFvTYxc DEOXmyD4Q1Mj9NLnqVt326og1avh14ekKaMdk7IehVDW7gVO2B6IwESIAESIAESIAESIIFyE7iuAYtk8MaMDB8Uueihk7Rwdc3AQ1758JO7a44W5MSctRqEZHDHuiID2rsXQf7u36D3xYRsPZ73z4Gv0P1ZKHQeJp0kdOOyDUadj9mb7NNRIKK0Z9RbGbphVWYANuhdoHe7hDe8CsRaRsUfXm0fxSOHpuONV5bB21OcEm0d3P7yfQhf x7eXZMOd8ErR98Kg//Py9i4Z/N aDJjBA4M hKxOllkQOrq0rZa/6ZorZ OsWO2o37/5zHMbjtD0Ljih0SPJEACJFAuAsYdFR/6BgVx4XDJyoJb6 F4fVgLBChvzGV4sd0J0XCuZPdFv0zrXRLVun yM6OUuQEfjvkaR8UHRoFYfa5x2wt44dZacC jn1SRAAmQwLUQsLfj7Msv9UZERU1Gi05j5fT38OMpDbxd9cjXNccTE4ei/nWNDspHRiOJQzbduHEjmjd38JBF XxZrHbs2AGPd4YiIr6BMfq4cHifKWwQAcvH2Vrc4Z FKMkNS0Uw4OKTigFi0i1/qS9/Ptm ZIEskwOUiTl6vOiXC29ZIA69CEFMwYsf3hbBy0siePEWcnlAxeIlz WV27rkUcpy9UsuqMuWvEWuRYZBA5fiAEwqysFoc8Ai24XJYxOZZDG2/JfnoX379kJ6nY6iQ5j5/NeoPeENdPsnn7zX2F35Wrmu473GfrIaCZDAv5 A/IH80uuX8eQnYkfFYvHe9sQUuLw6E8PqGL NcTwAgwH6s4vw3MxgTBpnek4PYifGIr3YidFFC8Ppr/CsA51jp XQGIrF54sLRBOQMlbjf49uRs/5Y9CBEUs54NGEBEigLAK28yur90d7QYp4H5S0WuM8uSy/jnT5697GQ392xKwxnYx3 OhzslHo5QNP8zzbUb2Kkl9N7FF1MZSmCDEC8r5iTyzN9UKywC0WRRDnnY7bXcUJ0PthXJYraruIDyVtARLE/lmpxRK zHJHjEcG uu8MFFUGOGfh9P5nkgWutmZsu4KbtV5i9UXWZcjHjbXYWtWIFbKH2LiwZVgj8sY6lEMTbEIcoT/umL1okByQZo2Gw975xsfTi85ERL8tBIKSgRVntMf wnvfLQCmZ1G4qEqCFaqHAA7QAIk8N8l4BaLutHp2HxmK7748mecFKvHVy4Z0Pjh1/BwiwBIYkfDx8cfQmJ8MIoDE9HYYL0T4j0Ry007MY7viKM2uyRadOJ3sPwNKfhzxlR8d1oH98IiVOs/As/3ioFO3jFxwhE0qh MvMzTSAm C68/2QaB6g9vrQhWzGfAkJ8HXWw8qnMXxf/uNcmRkcC/jIDB6n2wOe5/sBFOf1l6p1lPBzvQeqrGo3FzE1/87MZfR qhZa0weHuLYEXojW2MO4jExGrQ557HxaCBePGJ9gjJ24YvJv5Y6r1ZY7iErbPfw9eHJXi7a Av7uh5oY8v/rKzM626fVVXnGaV912nhldroH5/t1dXktxxSDxfEeGSj 7uecbfJpH0Pngv2xsXxQpMqLFSETr4ZiJW5CW9Dn8I wd9TSsskghA5EMjPtASPfIQUazHw345kG aMgid0n5 gR9 kLLxun8 vEWbX17xxxZxe1dbYSdB PfJRKT4 Pk1IwA7DfnoYC ClRtycCjtOFBXuFhXewBefXdAhfulQxIgARKoagJS5i7sOBaBmuKWsMEd28FVLLIYkpdg5KSVON/s/xAhd1Cqhb7PP4I4ESQYTqdj6emSnRAN58wj0Piiqc0uiRadMMnd AXm5Q/C9Knt4Ju3A 89/Rl b/02esrutXXR95mhiNWcwVfPzsCGy61xa5D1O72Uvg4fT1qMLUcuIeb sQi1Vps7wYQESIAE/jmBUjvONhQ Ve D8g6wr5faaXYK p 0twPtFNwZXjLRdW81HP9LnoevP3gRH5wpQHSX4Xj5qa5iXiwOQ030fnY4ElxzsHHSCCzc0wrPNmqGoWNblXpvDtos2krtiffe6Qjlu3RHO9Oq278aOpUWsKg7oX4vl/ReWCRWQnQiXKjmeQWdtK7YnOMDEZSJsEGHdEMhskVlOWDR6ooRrnYk8s6eB1e3JVe9LJ4/CXQtMt9GVoTaOhckm3 1USf8hxj9G ArHGfL93qV47BtoxxVaEICJEACJOCAgOH8Kkx7aQ9cilwQc/cI3BZyAis WoK/M8SzjtoLuHglARni/VkOWHRRNWHcxNCBL diAy6dTUZIvQTTJide8WL3xRScvSA GEQQpAuPRLjxfmI/BPjmIStP/mCwftfXBHXEU KD YnMrXj3qQ/xc9vpuCuyZBLgvA 0IAESIIHyESi14 wJ9fugox1g9Q52oBXvZ qJtTYADW5/FuNuFzFQThLmv/IKZm9qi9HV1W14IibGDT fy4WhbgpWfGH73myA4dRZhDSoDz/LW6Wjftm0Xz4ERqvrErDILcljML7t63Jxj594hsUsyy4IxmbtFbzkVQytwQfvZsihjOmwjNtc1opbuuSFFWXbYrPYWJY/KpStitX1AnV6XCl0QZ6o6Sm2Cz6hL0ZN2dgctCg ypsq4yivPe1IgARIgATKJqCN7IkXpohnWIxzfgmXfx6FlUFPYfqz1aFJ/R4vvJxq U0t cPE8h6vUEaNOGQ50WQdHhSNuShNxb28A7/wgOp4QjPkw0ftnGh71iURGKXF2Nz09q3Xzg4yby1 2T1F6HKCMBErjpCFjeBx3vAJuXZn8HWjUrffo5XPQUX9KIh1Y0XtUQGSjmyeZJuP7EASTl9UIz8RhGUpK4k l2T2SsmW3nvVmLkJrRuLRmPzIHKCssjvulbv9q8tf1bVb kLF80Jh76e2Sh9BcfyzKKRbrKyKw0MiPy5c tOI5lkYIELuMuaOu52XcIb4BU3zJuqZC9/4VD8SZdbIHWe/pnoGBhYGYdsUXbiKiCRT6NuUOWFywJTsAm4tdxbd7LvhYX4DOPhlooDRcuptWkhtt9xvDyWUY/ 4vOG/QorjQGy2GjcKjbYIrZWc0K1AskAAJkICFgAZ jToicsbnmD6jGlykVORojTcoWCyUjDbMeifEB2MUjVihL0Pn3X4YhuyYhlEv/gD3gkKE3jkC3eRtycoRsBQfWYz/ffYX8rXiAf98DaIGPIUH5GCHBwmQAAlUAQH7O80OQVMHO8M2VT1Eoj//J6bP3IxcF3HnU6FYQakxDCPaCQNxe63GNx1/Th6DJZcvIq/OMIxu5AY/sbps773Zs80jeHTfu/jfiyvg5 2CAFEe0dveDriiX6r2rwZXpe0S5il2CQs37xJ20bxLmDzPN77ME35T2bSPl91dwoSByUaVGmXmOnb8KaszpXcFE syQinrrV5lykrWcmzrhpp3CUsRY8tzsEuY1e4ON8DuN4aMc0jWRCDKTwv9ucUY epFPDr7KTSwCWttd7G4mguOtiRAAiRAAiRAAiRAAqUJ/FvmV/JD9099GYl3x3Y3PoRfuqcVI/n37BImRxsOjjJUDmqULVb8yakckFTUUaY/pdHyNHYD7H6j9Y8y3qonD0cjbnPQiR bvJohlgcDbUiABEiABEiABEiABEjgagjYfHd NVX/uW3J sU/9yV7KDO4uIYm5P4pv NyDdWtqtwou98YO118DiumL4PXPRNQr0qvECuELJAACZAACZAACZAACVQyAW3sUHwytpIbuUr3nI5eJbCrNb/Rdr B4QLWTXsLv8W9iHG9wvn8ytWecNqTAAmQAAmQAAmQAAlUKAEGLBWKs7SzG2r3G/EjQ1umv4ElgU9g/JBE81bQpcdECQmQAAmQAAmQAAmQAAlcLwKVG7BIxfjpUC5WZUZCL36scaxXgeUXguUByrdbybdxJRcEYFGB2J5S5KuJX6q/z13eMazkkAzemJwegAKvVLzhbdKl5YXixWwtBgWl4jatD8Zd8kWhSzE8hJccTR7u98tEvOoBDH2xP8ZkF Ml/xz4GV27Y0G6D oEXEIrlV1Jq6b qcv/PP/v3v2maPssTPj1AsLqz8UbI eK3yRoggcnPIDGlXuV/HOs9EACJPDvICC 9Ng6axLm7i0Su3u5InHIK3hM3mnwauU2o8k7vgIzP/0JSfnucBO7c/0/e cBHlXR9fH/7qb3TgollAQivTdBAVGUpigWxN6w966fDUV9sWEFfdFXsSuoKFhABUF6Cb13CIFAes/ufjN3dzZ3N5uwgWyI5n fZ3dmzpw5M/O7m905mXKtwam46I5bMdB3Nu6/7kuUpiYi0FyIwsC uPWxq9AptPJL3enwExzFD I5AwevnYpb24uHrsjLvAMf3joFwXcNxpK730TJDR/h7XHNxC JBZmz7sdVbxXimg/fwxWWn054iqLbkyGvbYGFj1RT51Ov49IknjBmuxF8JwESOCUC5i347JGXMXvbIVQMmoTP7 nqNObWbFuO4u93J HjzUCQtQSB/W7Fo M62p5JZa9cfo/dd9mUar8LxwWd Hv3lPpRTWEvD0VNGNg6FF22ZuA/LqcVy43x8ifFagnCNyUWjA7PRhvhbnycG4Y1fsfRo/L3Rmu60VQOU3kQDiEPzcQtWFZqQLLOqzGYCnFTpMwzYGN E8wqKcTDgfKpLad21biBv8ZM0b Y0Zg81bl U/PheOzl4c5CmXJdL jbFle /A6udGhejimT7Ima8kyJGHTvKxjkKGeP6O0bwjF80hRXDfj2fhg//FZFTAEJkAAJeESgPP0TvLNrICZPGYGYvHl4 t4PsbLLA i6uXbyXgGV1VnzFmPKM7 g6ROTcVdKkPa7UZKxDrvsvxGVs9ilWPPGDZjx5wi8NDJK06u0Yo8ZYzBwSCLunrcBN7TvCj8hrtg6H4vCBmNSnAHLm7eFaeUf2Hu5eNI9MvDnknKkqB ayG64fuJw3SmKX2BTj6qnKDraYz8ZcuZZUzGmmjpfTKCzUuUeUUACJHByBIzNMeyhNzF6/cu4cZ17E5a9c/G/DV3x6FtXIdmyGVMnfIB55/4HF8Y6fxeZavouFKYd33PisSIn/N5135RaS51bWOviJypgQISfwWm2RJbQj/MrKvxx2FSKZPHjYzCU4gyTL7ZWuHgroozBUII Jj/xTBTxzMeKIKw3FqGL0WZJHjksL1tgQJF4KGSwyKtqxabn m4xh2FiTjS Es9cmZEfgzcKA5CvU9K3VydmlARIgARIwEHAiqJDGTC2aoMo8ctiCGuDNn7rsWZ3RS3lzv9oKlr M1a3uxQX250VWV1AQiecEe/y82UtQ2GhESGh/jV89xsQfuY5aL16HtaUSEvl2DhvCeKGDESMbHNANwxuug7zt5vFk5t/x4rIQehtn63RTlEUR77Ly6NTFO0nQx4 aq2xTs0g30iABEjgVAkYghAVG1xlzK03a4huhVaBhSgoF2Pm0nwUmKIRFeTyXSoK1PRdqLcHj753nUqcdKJqK0/a1IkLyoG/6 C/zGqEj8Hi IEJFA9kKXZV0kxbkepfjp1iScDOUn/EBZSK ZjKy2IOxvvZsXjueBP8t6IYQ/zEsoHKbA9i5egfkoPxoTloaw7BWuH06C93bdfnM04CJEACjZuAAcEtk2HYsAr7yoQrkLEaa/blIr/QWku5/svXgpxjOQiJjdGeLA x5OHLpx7EvbfegCd/yBCLtsQ/sA79ilcefAD33XYzXttzJkb1DKrxNhhCemPoGRswb0UhrCVr8duqFhjaP9L2G2TwR8fBrbD59/XitQaJg3ogyPU/X45TFC q8RRFx8mQSSbUWGeNrWUmCZAACdQdAUNIGs5qvRbP3ngrJtz0Kg6dezn6Bruxf4Lvwtp 77qpodaienVY3LXOTzgrFcJpUc6FdFYCXX8g7AV9fYrRWuxF aSsAn18VQmbE2QUS8JujDiKJyIz8GygH6YXBIj/ndnybHMtVrEm2QD9/ 7Mola1qsxoqkCMVo8FodU6TVUdLnd9oowESIAEGiMBn7TxeHDwAbz36KN49uMMRLaIRmS4 KdULeWV7IwIjw5HwbFj0FYVm9rhsmdewgNnB F4vvyGV0sTJuPVd2fgnRE78Oq0NRD Ug1XILqd0wXbxcxK5srfsL7tUPQOq/zR8TtjMNK2TsVba1ticBd/Zzu6UxQfreYURdsP X2454lvgcvvxUXN5c9szXU6V8IUCZAACXiHQPmqD/HGrnPx ofvYupHk9B5wcv4bJf n0SV9db0XWhbElab791Kuycb8/IeFluzKl0L1UwDCi0G IvNk74 pYgv9sdesfmnDfyxxVwmnqxetYRW0lCG/v5lKEAhUg1W7FPmdKEsGSjsFlmM2g c6qDRWI5EcyB2iPvSU/x yKVoe40VOKfyd0pnRUXFbI9op1G2U4hKhGMF4WDJdc lFcLREg9W5EUCJEACJGAnYAhB2kUP46WLxHfswe/x5IuBGNBS/FuotnId0OBe56HzJ1/hu51dcFlr27y6xezuN8KIoNBAFGZna/ skt/T1V3 nYai1ztT8erXueg4/j7IfzA6LPqk4tzz05BXdgE6iCXNO5QRD09RrFzbrQraQnd1OmswRQIkQALeIFCKvGNlCIgOhcFsFl/H4QjRBsehiPAvwJ4C6bC4Gc9W913o1ETPv3edip1EQo3nT6JozUW0L3 rBQt2FWGecEhyrT5421yKwSG56CQWc32eG4C kdnoKPaiXOwfic/zYsRshwGxgdnoWo0TIW0milPErhP5wo3QGqB ZOSSsA9y/IVl4QxZzbgwtFj8T0v3IyRODrsk2B/T82LxhyhfKnR6B cgQei49y2leT98lxuCZHGSWG x0X9Bvlg2EHwU55iM HtHPnYnhON8qaa/PDmlwRMdYfNUT8a5/9pPUdAq3rZ0Tmw2HXT3E7iopZsPpajLmrsOc1YFYejgNppDprpkzf4Dz1z3PLLGz8CUS/hcFsWFIQmQgBsCFRvx6f/9F6tKzCgzNsPw5EqvyVqa1cZ9oQdibueTIPU6c gDvEwSuhYgq Aq1xwXWx2q AbUZjAwLFWuqCshiMv7u/5oDoTMBy8Bf85750BMjfFlNzjHjoDgztm4cJv/XAq130i4tlKSOan3cX7pNRS6Z8165TPkXRN62GOlUtDEmABEjgJAlYxEO/J7 KuZt24ljBITxwsBvGPjkB/QOX4JWbl L8Lx5Bn 5X4OoFk/HQXXPEKWEFsLS AQ 3r84VcP9dKFvnyffuSfai2mIGq7hk7uLFi9G9e/dqFWuTsWrVKgS8fDUS2naQngWObN0gg8qXSFSmbQu2xCosnawyLoWVuva4FGj2KjfW20WaXDkxMlQaspe2dGUoBa4yLe2Qy2fd23UcMls6TvZNyDJE30oe hj9 /fX6oa1CMezrPDXTmm4EJ 4O1bOAx15Ms7Ld34jTsZ5HuOcTsbpINZNz8aDj2fjtnevRSv7CQ2ft5ridDKO01Ge7n0UW3vt75Z9n KuadF4ceIwhDhySpD zv/hy33HUNjjebxmd1jkZ8XRX4cuIyRAAiRAAiRAAiRAAidLoLGNr2rje3gwlD1Z7KdWTjkK7qyoU8FkntSTl9LXp205Ik8JlcAeqjIu4lNLenBKAzzQqduTcSq7VLzxv7j7vk xo8yKvJVv4NaHZ2F/eT7W/LIQB7b9iFdfeAkzVuZqPM17ZuHL3HNxeQc5b8WLBEiABEiABEiABEiABOqfQHXzQPXfEuk9iFGx8i2qGyDb1bT2ydkTOQeil8kMZUPNruhlWkGXN6mvylRGXJTqNenmZJxn/4ulR44j5PyJeLpf5XScf9FB7DUPwpN3Vz0ZxzFlJ2H6pODix25G3/bX4P7 j HF/xxD1P58XDpxNJr5GpF03kA03RuN x6zz7BYsjDv4/Xocu0ziPhrVr32npWRAAmQAAmQAAmQAAmQgCLQYBwW5TDU5KjIRqt8OWsil5GpS5VXaRXqZ1ekTnV6Uv9E cqm90P7yTh75Mk4KTDZT8Y588u78YLTyThySZgZmT88igfFyTgf3NvNaf J 82fPmh wRi0 OwJ7BwzHWfJhw 4uQpXz8BvMZdjYnMTjrjJp4gESIAESIAESIAESIAE6oOA 9Gqt2vWeQ1yFkSXrFqzyHTN16dt5XWei7DgKtPrywq0tKtQV7PM0s/OVGmATtfzqDylIf8Ex21WWtNOxtkkT8bRnm6mZXhyMk6lhWpi1jwsf28G8sfehbS/38H3 7TDQsVGVBOM4vQI2 E7ZhzaegB5Wz7GEw88hJfn7MGO71/C 0vz6wZFNU2jmARIgARIgARIgARIgARcCZy2GRblLzi7Gs7Nc6cjZaqMfpbFycGwm3GdXdFbtzkleknVuCc6VUp5ckqDqZqTHHTPAqjzk3HEvpmeNzyFIQdfxUdlV D5y/ojqFsuHnnlE7R76TqkxXVFb/MbeObJFWg/4h5cf VkTLtS9s6CfZ/eiVf9H8ZNfcSReFU6TAEJkAAJkAAJkAAJkAAJeI9AvZ8SJrsiB73Op4LZ3A29zKGn09XLVFyG8nJaHqY8HSFXUb3zocXFWxWZ1HfIq54QJutRZao9JUwq/cuvxnaKxb/8drJ7JEACJEACJEACDYBAYxtfNaxTwuQIX1xqoG9LVfPucBZc8u1yJbWbdDgjUq45GlJPZUqZvYAKNT3Hmz1TBDJf09ErVmY7Yg49KTmBrqMQIyRAAiRAAiRAAiRAAiRAAidNoF72sHg6tnen5 QkiG4qHdfQlYBrvkpLPRnXp1VZdzKVpw891dOXYZwESIAESIAESIAESIAESKD2BLzmsNRmUG/bJF 18a42qktLuetLWqtOX9Xkmq/KuNsPo8q4hu5suOowTQIkQAIkQAIkQAIkQAIkcHIEvOawnLA5YqQvB/vVDfhd5e6Wesk6XPVUvXq5U1yfOEF5TdVFX9lnSAIkQAIkQAIkQAIkQAIk4H0Cp8VhkT5AdX6A2vSu77pDV0RUXIVST8ZdX6q80tNCe0LJ9Dp6h0jJZSh1XfX1 YyTAAmQAAmQAAmQAAmQAAl4j0C9Oyw1Df7d5ellKq4PVdwVkZSrPNdQ6iqZvpw7mcqvKU/pMCQBEiABEiABEiABEiABEqhbAvXjsIjRvhzwVzfot U5P HDVV VVTMhKi1xKF19qDApvZrKKV2breofZKnsV9sRvSHGSYAESIAESIAESIAESIAETplAvTgsymmo0lqR4S5PORdKX k4QntEpZWea6jylT1H2kVR5evFmq4qoM8Q8WrELlpMkgAJkAAJkAAJkAAJkAAJnCoBrzksclBf08C unzXMiqtQtVh5WQoO 5Cqav0HOXskSr2lIIuVDZ1IqfoifKdlJkgARIgARIgARIgARIgARKoNQGvOSw1tcTVWVC6 uOEpaOh9FQo9ZziMqEXKEN2Rb2zoldTca24SmimnJelKXM6FSViSAIkQAIkQAIkQAIkQAIkUA8EfOqhDlsVYtRvtfsDTm6BG7l0EJSOu7irrFqnxd45qS8vFZ4orunple1l3cmlLV4kQAIkQAIkQAIkQAIkQALeIVBvMywu439Hb1zlrrMsSlHp6UMVVzquocxXOq6h1HWegVEuks2K0relKt rk1dqMEYCJEACJEACJEACJEACJFBXBLzusMgBvrtBvju5Xs9dXMlUKCHIeHUvmS8vpe8a6vNc4yqtysi0ulR9Ks2QBEiABEiABEiABEiABEjAOwS85rC4G irLlTJEwK9zN0si8rXhyqu7LqGMl/pVAmVQNOpnF3RxLo8adMlKUWOq6Y8hxIjJEACJEACJEACJEACJEACJ0XAaw6Lu9boN9KrfDng1w/63cb1Qjf6ehsqri ij2v12gV6uWtcn5ZlZFq/hEyzwzcSIAESIAESIAESIAESIAGvEqg3h8XVAZC9cpXp006zLHYEzvlVuejzVa5epuIqlDru6nFXtiaZymNIAiRAAiRAAiRAAiRAAiRQtwTqxWHROwiq a4y/eyFPk/FVb5MO2T2uErrbbvTk/l6O3p9R9zFmEtSU3MnU UZkgAJkAAJkAAJkAAJkAAJ1B0B7zks1Y3qhdw1S592jtv2liiZcjZk95VMoZBp9VIyGer1VHklq252ReUrO1raVeiUqRIMSYAESIAESIAESIAESIAE6pKA1xwWvTOgGizH/K7jfn1aORRSX8mVHUdaRuwJFVV5spy8qsiFQNlWuq52tXIq025DytSlbKq0CpUdlWZIAiRAAiRAAiRAAiRAAiRQdwS85rC4NlHnC2gehasD4MgXERWvDF1mWoRx5YCoeqSueimZDKVepR1bjnIynOT2hJJpZWV5FbEVddiyJxmQAAmQAAmQAAmQAAmQAAl4kUC9POleDvorDw62OQHVpZWuCl37rpfrnRZXe 7KucpkWtqTlwpd456kpQ4vEiABEiABEiABEiABEiCBuifg1RkWvROgmu4q06cdcUek0pGQsyL6mRGdimZaptVL1SVDvczVhkPPbsweaGJ9XNlx6Nsjrjqu UyTAAmQAAmQAAmQAAmQAAmcGgGvOSzuBvNOMpHQp93FlUyFsqvKabHFnW3oUcgyNZVT5fWh27jOiC4qVbXLnUzlMSQBEiABEiABEiABEiABEjg1Al5zWPTNkoN6/cDeXVrpKz213MuRVgqaLf0CMJttZVOFOvUqTo7Mc9i1R1Ran6firnn6tNThRQIkQAIkQAIkQAIkQAIk4B0CXndYXAf3TmmR0KdV3BHaI460joFa3qWfcdFla06K0lFyVzs1O0WilCrgHNXM6bKUeYYkQAIkQAIkQAIkQAIkQAJ1TMDrDou va6DfH1axauEdoFeruLKtnJM9KHKk6HUV2UcoT3iSNsLqLQqZxdrgT5PLz8d8Y0bN2LLli2no2rWSQIkQAIkQAIkQAIkQAL1RsBrDovT4F4k9GkZd6R1eQ6ZS/ddZ0JktpMNF32VdNVR9pU9padCR74U2BNubSjFSjVlot7CWbNmYebMmbWu7/bbb8fixYtrXY4FSIAESIAESIAESIAESOB0EPCaw6LvjH7Zlm6sr6motAqlUMVVqMnsCRk4ye1pJdeHspy8lEyL6wqrqAqVrj6UcXk56zjvobFp1N97bm4u/vjjD/z /Iy8urVcXr16/Ho48 iltvvRVLly6tVVkqkwAJkAAJkAAJkAAJkEB9E6gXh0XrlBjx6wf9UqbS hkPh8xOQqU1fV1CRnVJu7Zz4KpT23pc7WtpV6FzlfWSmj9/PsrLy1FWVqY5LidTqVxS9tBDD2mOy4YNG07GBMuQAAmQAAmQAAmQAAmQgNcJeO3Bka7jejnLIp kIi VJ cpZFybrxARq4joZSpPhVpZmRCXQStUacsmdf ud1Skht2E 9CeqddRcVtZe8X2qvR5dlGdByUlJcjJyUFBQQHMZjNeUXRx0///wz2rVrh8DAQAQEBCAiIgJ fn6O/BNFpOMil4kNGTJEc15iY2NPVIT5JEACJEACJEACJEACJFBvBLzmsOh7IAf1aph/orjKdxdKmw47UkGlldAmsr2LfLuKQ6pPq3h1oSyk8mqKO4x7KfLRRx9h vTp1VqXDsdNN93klH/jjTfi6quvdpLVlLAKj27evHlYtGgRrrnmGlxxxRUwGutv8q2mtjGPBEiABEiABEiABEigcROo11GpVU6h2C93zsCJZkJkUX05lZblqrzs9ahAX07FVejQsQv0cqe4rv2qjLfDa6 9Fg8CB8fE7sW5pMJk23Ns6Kvv1yJmfq1Km48847sW/fPn0W4yRAAiRAAiRAAiRAAiRwWgh4zWGRA32nwb6ue9XJNRWR6S7fVSbTepnOvCOqdPR6Kq5CqazF9QIls1vSZ7nG9Wm7ep0HI0eOxOuvv46YmJhqbUdGRmLy5MmQuqd6GdR6u1M1xPIkQAIkQAIkQAIkQAIkcIoEvOaw6NulH9SfcJZFFhQFnMrYjUmZXm5X1WQqTx/ai2mBkqsyKk zJ960UAhVWEVPN7ui11F2vB126tRJc0iqq eNN95A9 7dq8v2SB4cHIy77roLU6ZMQfPmzT0qQyUSIAESIAESIAESIAES8CaBE68zOsXa9YN7GdcWhYmI2mAvzSt5daFeR8VlWLnATKbcX9Km/tKnVby6UJbT8uwKSs8h1xuuh/jmzZurrWX79u1ITk6uNr mDLlfZejQobj55pvBTfc1kWIeCZAACZAACZAACZBAfRPwnsOiH92LXsmkcjBcTwyTcpXvCEVErkxSaQlGxuVVaceW9uRdlVW6Kq32zTjSdgWVlsmaniPjaJQy7MVwyZIlDutyBkSeGHbw4EFNJvOk01Hbq1u3brjtttuQmppa26LUJwESIAESIAESIAESIAGvE/Caw I84Hd2MjSHQyioWRapW63TIvLUaixXR0Wla6Kkb4fUc6Rl/faCNYb2TKXjZMNuz5N22Ks66UCe5CUf ihnQ8aMGaPNhkhjb731FmbPno309PRa2e7QoYN2Iljv3r1rVY7KJEACJEACJEACJEACJFCfBLzmsLjrhBz0q8G9mmXRy/RllFwL7QklU3oyXZvLoS8iKq5CVztKXuPsimshL6b379 vbbp/4YUX0L59e0dNDzzwAM4991y89tprOHz4MOLj4x157iKdO3eGPHnsVPe7uLNNGQmQAAmQAAmQAAmQAAnUNYF6c1ikA1DprNhnVMTUicFgcw1UvgplR1Vc0xBvaomYgqDsqbS7UCury1BLwKRIn6fiKtTy7VM7TjKdrfqMylPA3n//fbfPR5Eb8j/44AMUFxefsElvvvnmCXWoQAIkQAIkQAIkQAIkQAINhYDXTgmTg3yLxaL10 jj6 ivGvyrUHoNKu4aykJKpsVlQidQyZpCWU67hJKnzopWhfZWWZ09qZky tr6YzFb9M2xV SdIDQ01K2zomqTz2AJCQlRSYYkQAIkQAIkQAIkQAIk8K8g4DWHRdIpKSzQIEUnJMIkBvlq0K9CmamWXCmZa2jT0cxobzJfczy0SKXcbcyuI/VlVF3u4kpWGVbO31TKoPUjOj5RM6X6p wyJAESIAESIAESIAESIAESqFsCXl0Sln0kEwFBIQgIDkFia9spVJVugHNHqpNLrZrynK14nlJOiLsS1eXp5XJ25fjRTHfFKSMBEiABEiABEiABEiABEqgjAl6bYZGD /KyMhzatQNFeXmO5WH6QbD9XJpU5NeXobnsZrslddnpLLZW6yPxl7dqJC9E/JPa2beiRAAiRAAiRAAiRAAiRAAp4T8OoMi2xGRUU5jh7cb5slEVMlarZEH rjsG/Cd5Lp qPkOpEjKvNqciBc81RahfL8ZBWXoT4uK9HS4k2fJ W8SIAESIAESIAESIAESIAEvEPAIJ7voY3DFy9eXGdH3a5atco7raVVEiABEiABEiABEiABEiCBfwUBTx z4bUZljZt2vwrQLITJEACJEACJEACJEACJEACdUtgx44dHhv02h4Wj1tARRIgARIgARIgARIgARIgARKohgAdlmrAUEwCJEACJEACJEACJEACJHD6CXhtSZhr1yoqKpCVlYWioiLHiWGuOky7J2A0GhEUFITo6Gj42h9a6V6TUhIgARIgARIgARIgARL4dxGoF4dFOisHDx5EQkICUlNT4efn1yApLl26FH369GlwbSsTxydLZ /QoUNISkqCj0 93LYGx4ENIgESIAESIAESIAESaHwE6mXkKwfb0llJTLQ9Ib7xYT61HksHT7GTLOPj40/NIEuTAAmQAAmQAAmQAAmQwD EQL3sYZHLwGJjY/8hSBpuM2NiYrQldQ23hWwZCZAACZAACZAACZAACdQtgXpxWOTT4bn34tRvnJxpkSx5kQAJkAAJkAAJkAAJkEBjIVAvDktjgcl kgAJkAAJkAAJkAAJkAAJ1C0BOix1y5PWSIAESIAESIAESIAESIAE6pAAHZY6hElTJEACJEACJEACJEACJEACdUuADkvd8qQ1EiABEiABEiABEiABEiCBOiRAh6UOYbqays/Px8qVKx3id955B8eOHXOkGSEBEiABEiABEiABEiABEqiZAB2WmvmcUm5mZiYeffRRzJ8/H19//bX2Ki8vPyWbLEwCJEACJEACJEACJEACjYlAvTw4sjEBlX2VRw8bjUbIY4jNZjMmTpzoQDB16lT07t0bK1aswOOPP67pOTIZIQESIAESIAESIAESIAEScCJAh8UJR90kXn31Vaxfvx4FBQWwWq3ak mTk5M12Z9//gn5uvHGG ms1A1uWiEBEiABEiABEiABEvgXE CSMC/c3JtvvhkRERE4fvw42rdvj//973 YNGkSPvjgA4SEhGg1Dh482As10yQJkAAJkAAJkAAJkAAJ/LsI0GHxwv0MCwtDixYtNMvSMZFLw QVHx Prl27avHnn38ec bM0eJ8IwESIAESIAESIAESIAEScE AS8Lcczkl6SuvvIKff/5Zs7Fjxw6HrYqKCuzevVtL /r6Qm7K50UCJEACJEACJEACJEACJFA9ATos1bOpdc6BAwfQtGlTtG3bFnLPyrRp0zTHxWQyabLff/8dUicpKQnSqZEb83mRAAmQAAmQAAmQAAmQAAlUT Af4bAMGjSo h7ocv744w9dqv6jciP9008/jdjYWKSnp0O2 5dffsGPP/6ovVSL5N4WObuSkJCgRAxJgARIgARIgARIgARIgATcEPhHOCyn2xFxw81J9Ndff6G4uBjR0dHavhT5sMjzzjsPS5cuxRVXXIGAgABt4/2QIUMgN TLZ7IcOnSIDosTRSZIgARIgARIgARIgARIoCqBf4TDUrXZDUcin7Py2WefITs7Gx999JHmnKxZswbTp0/HVVddhQsvvBBySdjff/ tPX8lJiYGt956a8PpAFtCAiRAAiRAAiRAAiRAAg2YADdRnOLNkc7IM888o 1ZkTMp8kpLS8PGjRsxb948beZFyl588UUMGDBARnmRAAmQAAmQAAmQAAmQAAl4SIAOi4egalJ74403sHr1aixZsgR5eXna7Io8zvjdd991PHdFPpdFHW9cky3mkQAJkAAJkAAJkAAJkAAJVBLgkrBKFicdGz58uLb0S578JR2WZs2aISsrC Xl5ZDHF/MiARIgARIgARIgARIgARI4OQJ0WE6Om1Opfv36aemOHTtqT7YfPXo0tmzZQmfFiRITJEACJEACJEACJEACJFB7AnRYas s2hKPP/64I0/uY FFAiRAAiRAAiRAAiRAAiRwagS4h XU LE0CZAACZAACZAACZAACZCAFwnQYfEiXJomARIgARIgARIgARIgARI4NQJ0WE6NH0uTAAmQAAmQAAmQAAmQAAl4kQAdFi/CpWkSIAESIAESIAESIAESIIFTI0CH5dT4sTQJkAAJkAAJkAAJkAAJkIAXCdSLw2I0GrVnknixH43CdFlZGSRLXiRAAiRAAiRAAiRAAiTQWAjUy g3MDAQR48ebSxMvdZPyVCy5EUCJEACJEACJEACJEACjYVAvTyHJTw8HBkZGbBarYiNjYWfn19j4Vsn/ZQzK9JZOXz4sMavTozSCAmQAAmQAAmQAAmQAAn8Awh4xWGRy5YsFotj VJAQACio6Nx/PhxHDx4UMtrqGyWLl3a4JomeUqGUVFRWtjgGsgGkQAJkAAJkAAJkAAJkICHBPR gidFvOKwyMF1UVERQkJCtDbIAXdwcDB8fX1hNpu1mQ1y7UwAAEAASURBVBZPGkcdGwGDwQCTyaTx4x4WfipIgARIgARIgARIgAT yQSknyD9BU8vrzgscXFx2kxKUFCQY5ZFDrr9/f09bRf1SIAESIAESIAESIAESIAE/mUE5OzKsWPH0LRpU4975pVN93L5V0REBPbt24eCgoIGvQTMY1JUJAESIAESIAESIAESIAESOCkC0lGRfsH /fs1P0FudfD08soMi6y8efPm2pKwzMxMHDlyhE6Lp3eEeiRAAiRAAiRAAiRAAiTwLyMgtzXI027lzEptnBWJwWsOizQuG1PbBslyvEiABEiABEiABEiABEiABEhAEvDKkjCiJQESIAESIAESIAESIAESIIG6IECHpS4o0gYJkAAJkAAJkAAJkAAJkIBXCNBh8QpWGiUBEiABEiABEiABEiABEqgLAnRY6oIibZAACZAACZAACZAACZAACXiFAB0Wr2ClURIgARIgARIgARIgARIggbogQIelLijSxmkkUIJtsz/C7K0FsJ7GVjS4qq252DjnI3y26DAsp71xpdj3xyf4enUe79FpvxdsAAmQAAmQAAn88wjQYWkA98xs8cXH38xC tL5MDSA9vyTmlC29Qu8Om0B9hb k1pdD221Hsea2d9g3rbc2jsJ1mIc3rQMq/cW1b6s264ZUH5oOWa8Nh0rC hWukVEIQmQAAmQAAmQQLUEvPoclmprbYQZGUfzsHz5Ehw7kgGrpRyhIcFo16YFunTrB4vBiojwcAQFh5wWMsW7ZuOlJ6ehZNz/MGl4VPVOkyULK2a8hQ/mrMbB4hA073Uhbr1jLDqGV3WzShe9gEuf34whz0/FXd2CXPplxt4v78Md/zPh g9fwUVNRHlrPha9fjem/JmJvJIKwOSP4KgEtOpwJi4cfyn6N/V3sSGS1izM//gHHO9zN67qGuLU7rrvkxlHFryCh176ExHXf4DXLknU6rMW7cQv/52GrxZsxOHSADRpNwBjb7kJ57cJcmqParz1 E949Ko3sLpcSURXm1 ON6ZejzaZX PeG9/HZtF958sPAx7/Fk epRiYkbvtD8z6bh6Wrt BIzGXYsorl6JpXf37wbwVXz/3LHZe/D66tnC9d84t8yzlh9YX34hzf30CH/94Ebpf3oLnqXsGjlokQAIkQAIkQAKCAB2WevgYFJYAs fORkKoCWef2Q8 AYE4npMHf0MJrAaDGLxVYNTQwVpL6vP/z5aCXfhr5if4 NulOFhiRJcaWVRgz9cTMfGbIgy44RHcFHUQc//7EZ56MRjvvDAc8U4 ixW5WcdRbj4iBvPfYWSncWip 6RZj/ Jj77eglJrU2TniAVLTUyi5grkHclEQeo4vHR9N/iUFSL70EbMorTHw0B89PuxPdAp0baNn3K35MD8Pgl/pB Uze6ZPoz8r38MQ7a1Hmr uocLKWvP0E3trcCTc 8ho6hRzFkk/exFv/Z0bMB/ehl5uxvrW4CMXGNhg78T4MjrbZMvhFIkkgMMYMwX2vdUCRYw2XGRnzpuC1hbHonuJr73wpdn0/EU99loV2wy7AuHvGIz4uEbF15aw4I667VEBHjDo/GXN/notNl0xAB93noe4qoSUSIAESIAESIIF/IwEOG rhrh4 LpbllOXjrL7DEBafrNXYvJmtYumgWKw mDFzJro3C0WHXoOw/WAO5s35GkZrpftiMFhw2QhRPiEZZosBy9akY8/2LSguykN8TCQG9O2HsNgEm1GP3i04/Mu7eH9FLEY/cSd2vvQOcmoqV74Bs3/YhugRk3H36DMgh8/t/fbh mdmYs62Ybi rXQ61GVB9vHjQEwSYg98j8 XjMCjA8LsMw7l2Drrc6wMaYrE4jxk51X2UZY2hjVFu7Q0aHMJnXugR8gBXDZpEzYdtqBbS/2o3IJDy5Zgb2Rv3NpWDea90yfzwTl4 dV0dLn/XgRMexbrVDfNO7ByVT5SL70Oo3vEi/6loMV127Dg7r w4YAZvVL1TGyFrIX5KDDEolX7NmgdrAzZQ78otGgb5RBaD/ Ij//IRpdbJuL8RFvfSzeIWbCvTLjytTcxLPFEf74W5K2Yjgf/2oFtmeUIadoZQ6 5FVf3j8bqyePxzM4L8c7bVyJZM23Bnk9vx 1zO2LSB/1EGyqwadq1OG abI5uhqciE8s fx fzU/H7mNmRKT0x9gJEzAiNRgGsZRs59z38PaXf2HrkRL4hCeh7w0T8fDQJoKNEUn9 yN5xs9Ysv1GdEg7UdsdGBghARIgARIgARJo5AT0I8BGjsJ73Y8Qy78sRj9s3b4NMFdZ71Ol4uZNQnHpJZdg7NixGHPxZQiMjEN8VAjCoqVDYsSC5enYt2UVBvbqihHDL0KFfxTm/PoTjGWlVWxVLzAicczL OTNhzC2a4zmgFSvK5yqjM3Ykh2M9l1THLqBHbshzXQYm7ccd9nrYEVedj6MLS/CLecHY8kXP2Kv2WZdzq58MScXva 8Ct3CS5CTI6af3F3WchRkbsCc RthjuuIjgmuH9USbN 8F8aUdmjlGPt6oU8Vu/HN5E9QOOph3Ngt3LmlxjgkiqmlvatW4JB2Wy3I2roNWWFpOENOmbi5rHm5yPcxovR4FvLLnJ01J3VrAZbN Azr40bhmiFxNmdPbKT/6 u5OGw6irlPXoWLx4zFdfdNxsyN1e9TKS0PQ7fL7sXTzz2IS1OO4ofnn8AH6Wa0794JfvvXYv1xexuE7c0bD8C/fSekaDx90Hrs83hv2jRMm/Y2JvT0E80rwYYPn8DEucXoccNTeOXlB3FByGq8 /Q0rCwSn5E932Ly28sQfP7DmPzmFEy6fxyGpFYuMTQmtEPb0Cxs3er6eXHqORMkQAIkQAIkQAIk4ETAMdRzkjJRpwSiw3wx4MxzsGzJAmzfOwNtU9rgjLT2CAyLdFuPn48JUZEyz4C/Vm6Etegozh19ofhHtz KSg3YKpyV0f27I7FVilb 7P5nY8aXO5CVuRdRzVLd2nQrFMvRdAuc3KoooSUnG7kIR1SEznEQMwLRYVbsP54jTqKKReUQvQx5 cXwCY1Gt4svRodfPsWs1RfhXjHo3T1nFlZFXYBXBjbF318BO3JyRdkQ4YbZrvJFkzB62CSxP8UqZp6sMAQkY9QTV6BTgGqJPbQcQ ZRCyI6xIr// uuOu1TJA7MmoJvMQYvX9IafgbhcOovYxJG3HkTNjw9FXdOWI4B7S1Yu6wIox57BL1dZ0/s5crKDAgL3owPbr0Sb1hC0aLXKNx0 5XoGVtJT6paM34V 2Iq0O/BUWit/kortmDtxlLEdhuCsSM6IjEwHxu/fQtTn/wPAt97DufHud5NI2L7XYIrhrXV7k2Prsko23cLvpy9Alfd0RsdTW9h6aocjDgvEoaybdiw3YC0689AAPZprfWPTELLZNteHa1N X/j25 y0P3OyRg/IFz77LS5MxMrr/0UCzfcga7 Oci1hqJbp85IayNvWBvNjuPNGIMmMcDKw0dhRhzXozrAMEICJEACJEACJFATATUUqkmHeadMwIoOqc3RttV47NyzV8xIbMHqDV/jzG4d0L5L32qPnd2TkYNN6xZj1Fl94R8Rq7XimBjgo7wCcxcuBxaucLTM12xBUVEBKhcUObLqKGIVsyiuA JqTIvZgfx8ICgmGKbYbhg76As818jEuLxaw5h9HlmlFI8StFuhjUF Q5H0fs0 1GvH5LD/hazSjJPYiN87/AjOfuB56Zgtu66TbWW0tRUmoVPpy/p61y09ia 2TN h3Tvy7Aec MRrL8S7HPElUasqLo6H5kmpMxcFgvxGcsQXrxbiz bQ3Ob3 WbWtOpbIWC p3D7QVV YCHNrwB2a8NQ3PPuuLKa9fgZYOn8WMnb/Oxdaowbi r80xkIWthcdxvNiIFn3Px5mdbBt6Wt1xNdaO/w9 X5KFYaNja2ZhTED7tGiUrtmFjJAxOKvrO3hz8UrknjsUIbvWYVNJG4zsJpwXu8Pi0nSYD zE7pIiZL4yDiNeVblWMWlogP/xIpiGDMelXRdj2iM3Y9ugCzBy5Pno3ya80pE1 MNf DGlpbWZCVT1MCQBEiABEiABEmisBOiw1OOd9/UxiJPBksWrFf5euxmLVv6O5OYt4R9l39Cia0up E/8nwvnoXOrRCS1au9wauQCHrmfZdhZAxAck6grAYQEuexKd8o9tYQxIgoRYpfLcblJXg1By7NxLN AiKgIxwyJVou1EAViiVBgUIAY/Aagy0Uj0Pz2WfhwagSW gzG02dHC/lxBAWIAX9BodNyMkNQLJonJ9v2sKA12nWMR 7mezD7t3W4SZyo5phNMfghQGyALxOD3xoWVtXY6Zr7FI78FX9iZe5 rHhgDGbaOgZLhRmW6Tfhkl2P4/PbrJj26jxEi1PD7h4m zQSo8 ZjnsfeAsf9e2Fh/vVcD9MIUjsPBJ3Xb8Zy59bjGUHL0PL5vZ5JrE3ZsHCQ2hy5v1op7bniPoNPj4wiXtfkC ZBYr6xBUQg9gwYL84xMF5lktrcJU3q1XePzGzZghD70E98d6rf2Jp9iCkrVmDrBYD0SNWWLWpVCkrZ71gjMbgB17A5SkO70qzFxgVCoNvOC6cOB291szDD99 i1fu AbfXfsCJl2earufwsmUvoqfv MuVq2DEhIgARIgARIgARJwIUCHxQVI/SQtSG7aHOkrTGKGIduNw2LEolWrEWjOQe8 l4tjjytnNqLDQ2ERR/7m5WahaZszTnqwXtt GhPS0C6yEGvW7kB5zzRtH0vxhtXiCN54DG1XuU9Bs2spQkGhVfw3XTosYozbdBgu7PEVXvr1MNrecC86aTvqAxEo/tteJDwbx6FY7hpVUYRCMZPi4 vr7BSJgXOcOBor52gW5AnBJ/NBrrlP0Qhvei mdhAnual2Wfbg26dewrYzn8WjF6XBlDVTPP8lBJ2bVs6CBLbugJSgb3EwUz4k0e5UqPJuQqvuYAWVbdm/EqsyI9CtVxvnfgU2R8smwJyNm8WemgFiIZ2Ydcndiz3ZPkhMinXmo4zpw/JdWL0uG0GtU8WpZAYE9jkfA0Oewq/z1yJ3 X4079/XdjSyxQ/Spyi03xvlmpiSWqKF73fYedCChMHJzm1T9RgCkdhtJCZ0OwcDxMluD37/szgVLBVd5Q0Sx2JnZgGx8frlg6ogQxIgARIgARIgARJwT BkxnnuLVFaLYH9YvC6d9sqJCU2hX9gMIpKyrF2wyYE VoQFZNQpdzhY4XYvmklBnZJQ05xGSBfYvgbGhyE4IAgpLbtjCXpK8RG/gBENWmK0nILKkrzkJKSph2TXMXgSQisuYvx6p2vYFMfcWzvbd0Q6NsBI0elYN5nU/B20nU4Wx5rPO0PlHa BedXOQ2rGMViL32A3WGBIRxnjrsem0Lz0W9Ykn1g7SPyTbCI2YJi4RGo/7lbcvdh44YN8K0oQf7R3Vj180zMPZ6IUUM6uAyQAwWHFrDM3YJdFWejvSefZPN2fDjhbsxJewaf39dTOEE198koTvNqqt LYi5GmJgl84uIR9No4YyEdELn2E8xb/qHSL1uMFqJPSVb536MRcXNMKZjDAyu9VkO4a vFqKwWYo44tqAwgNr8dNnC1CWcg36JqldPFbkb92E/aZUXNLGpVOmFAy9oB2 nz4db80OwSXtKrDmk0 xLmIQnukjZjiq3Gcxg7VvHVamlyGg9DDW/vgJvjncGuMe7ClcKXH5d8IF5yXi7m9fQ0ZhC4y r5nt3piaok0rP3z3xxf4vt1ItLRmIje8L846oz/GDPsCj301EZNM43Be zj4lhzF3rwEnHuO2PuSsQw/rRPOeMtYBFQcRfreAiA0DKKr2mU5vBXb8mLQMVXORvEiARIgARIgARIgAc8IuIyIPCtErdoRkEvB8oot2Pn3MpSKPQD YragSWwUhgwbDlNopNhcrrdnwK79B8Rg1yJmWTYC8qVdVowc3AcJbTpjUJ9uWB7oi7ViYFu0Mh0Bfr5if4xwBITDUmWbhd50LePyn/ VTfNB8tgn8UTJm3j/o fwW0kwWvQej6dvH44E19GnpcTmsASqBx0Kh6TNcNxxr74BYrGYcGismQUQq8fEdn4fcSxzE4Qs ByP3j9DrDrzQ3C4WB7WdgBunnSZeJaL6/IqcSJYn75oPmMe/hbH5Lb35JhccfKY3PQeHhlhHzDXok/6pqu4f0dc9 xDML7/OaY9MQu5Ff6IbNEZIx 7BVe0EfMSFS71CS45e5bjO3Gsc0ZeOXzFsb9te96A5667CC3UNIa4g4f2HYQ5uj8S5b51p8uIZhc9jqdK38EHnz Nu3KNiGk7CPc8ezN6hrjcBIPY0N pAyKXfIXnH81HhSkU8e364cZJ12N0G7XOTJwEdsFF6DrzNaxtOxaDmtmdJrFcbOANd2L9f6bj42cXwxyciB5Xt8XAM1qg800v4unwDzBDHIn93CfizgXHouWAGyDOlIBPzi4s mompmXkodxH1JfSBxPuH4vWWt8syFjyN/ZE9cYttmPInHrGBAmQAAmQAAmQAAlUR8AglqRoY9LFixeje/fu1elRTgINj4D1KOY8fjP F3of3n9kAMJcxuyuDbYWzMczV05D6OMf4/5elc6Uq15dpeu7vpNqd9lGTJ3wNA6Pn4b/Gyw33HvpKl2Hd295HBvPewtTruCT7r1EmWZJgARIgARI4F9JQK1D Vd2jp36lxMQS7aGXD0S4X9/iBnrinSzQe77XbZjK/bEnI1zO3vfWZEtqO/63PfanbQUmTu3YteOdMwVz0v5LehCXDnQi86K2GW0a YH Nk8CFePbH7ivTbumkwZCZAACZAACZBAoyXAGZZGe v/LR0vxpbvPsOW1Esx gx3 zic 2kWp3yZxHNu6uuq7/o86pc4heyze 7HjF0 iO84DDfeez36NfEmkxLsnfc5lkSMwWU9Kg8o8KitVCIBEiABEiABEmj0BOiwNPqPAAGQAAmQAAmQAAmQAAmQQMMlwCVhDffesGUkQAIkQAIkQAIkQAIk0OgJ0GFp9B8BAiABEiABEiABEiABEiCBhkuADkvDvTdsGQmQAAmQAAmQAAmQAAk0egJ0WBr9R4AASIAESIAESIAESIAESKDhEqDD0nDvDVtGAiRAAiRAAiRAAiRAAo2eAB2WRv8RIAASIAESIAESIAESIAESaLgE6LA03HvDlpEACZAACZAACZAACZBAoydAh6XRfwQIgARIgARIgARIgARIgAQaLgE6LA333rBlJEACJEACJEACJEACJNDoCdBhafQfAQnAivxNc/HZzBU4YnUDxHoMa7 bjq9XHBeadXmdoN6aqvKkTZ7o1FQH80iABEiABEiABEiABE47ATosp/0WAGaLLz7 ZhbSl86H4XS0x5qNvz99D7O2lyPUXQPMh7F05kws3FVUtw7LieqtiYUnbfJEp6Y6mEcCJEACJEACJEACJHDaCfic9hY08AZYrUb89MdiZOzcCKvVAh8fI8JCgtE0KRGdOnRAUHj0KffAYLAiIjwcQcEhp2zrZAxYs5diwQZ/9HqkKwJPxsBJljld9crmFu ajZeenIaScf/DpOFRp8dRPEluLEYCJEACJEACJEACjYkAHZYT3m0DikuK0aJJGDr3GogKswXZuQXYvHUbNn/7LS4YfBbik9ue0syD0VCBUUMHay2p2yVXJ ycULDi2N8LsSGgJx7vUq/uymmp11KwC3/N/AQff7sUB0uM6OIJIuqQAAmQAAmQAAmQAAmcNgJ0WDxEHxjgi4T4eFiEflISkNauHX6cvwC/LVyAK MSYQgKFUu7DFi2Jh17tm9BcVEe4mMiMaBvP4TFJmLOguUwZ23GRWPGo8JgW4m3ctNebFoxB9decQs mv0jujcLRYdegzTnxyJmdlau24htm9ahtCgfocEBGDZoIMKaNK hngQPe6NTs2ZhycKNCOr1BDorf6XsABZ89C5mzFuHg8UBiG/XCn4FVvjqiqEiE8s fx fzU/H7mNmRKT0x9gJEzAi1QfLX7kKz wYhbffHo WWleFU/TjI7jmw0g8OuMR9Jf1uNZrLcbOue/h7S//wtYjJfAJT0LfGybi4aFNbLMfnrTphDoWHP7lXby/Ihajn7gTO196Bzn6PjFOAiRAAiRAAiRAAiTQ4AhwD8tJ3hKT0YK PXojr8yAvbs3CytGLFiejn1bVmFgr64YMfwiVPhHYc6vP8FYVoLmzZojM6cA5YX59hqNOHhoP1rEx8Hq4 fSCgMWr9qAjasXoUf7FFxwwXB07dkXgWGRJ6in1MXOiZPWI4uxcHMweg3sggCpbi3EqqlP4KW52Thj3COY OwDuKJzMMrK9XM/Jdjw4ROYOLcYPW54Cq 8/CAuCFmNd5 ehpVF/ujQoxP896dj/TFVpggb1myDqX13dNAqEdW41GvZ8y0mv70Mwec/jMlvTsGk 8dhSKp9qZYnbfJER9yjxDEv45M3H8LYrjHODtiJUVGDBEiABEiABEiABEjgNBDgDMspQI8OC4HRLwjZOTloUmrAVuGsjO7fHYmtUjSrZ/c/GzO 3IGszL1omdgWfxkDceDgLjRr2xVlFUYcPrQbXXqeAbPLRvfiMiM2bFyJc7q2R2qnbk7LzYpOUE9Us9Ra9MiKTLEcbEtIH1zWyV8rZ837G9/Py0K7a97HPRcm2GY3OoZg56/LsdFu2Zr/N779KQvd75yM8QPCNZ02d2Zi5bWfYuGGO9CjS290NL2J5atzMfK8CBhK1mP5OjPSru2KMK2vVeu15OUg1xqKbp06I62N9GraOPrhUZs8aLdm0GDgfhUHWUZIgARIgARIgARIoOEToMNyivfIancnsnJygfIKzF24HFi4wmHVV x5KSoqQKS/AU0SW2P3nt1okdoFezOOwMdcgBYtUrVlZo4CIpKVnQtDRRESEpo5OStS59gJ6onSGzpR3JqBxQu3IbT3leho81dgPrgb 8pj0f MuGoH9uYDO7G7pAiZr4zDiFdVJVaYKwzwP14EhPXCwC5GvLVkJfLOPQcB65dgVVkHXN032mbTTb0 ZwzHpV0XY9ojN2PboAswcuT56N8mHCZh3qM2edBu1VKGJEACJEACJEACJEAC/xwCdFhO4V5l5eXDWlaMyIgIzbEwGCwYdtYABMckOlkNCQqEzEtpnYKVizZioNjEv33XTrROiIMpMKSKw6IWUjkZsSdkXk31uCtTncxySCwH2x6GPld1hN1fkcaFuqjFUkMrrCLPGI3BD7yAy1OkS6EuAwKjQoUJA3qd3R3GNxZieW5/RPy1DKWdrkffSNtUktt6fVviwonT0WvNPPwgDjN45Y5v8N21L2DS5akwedImT3RUMxmSAAmQAAmQAAmQAAn8YwhwD8tJ3iqzWMe1ZMVShPlZ0aJlGqLDQ2Ex SMvN0tzYCKEE6NePn42dyC1RVOUm8Kwbfs2HNi3BWmpaWI5mMt6MNEezZYxABkZ 6vMcnhSj2ddsuDQooXYGd4XAztU7qExNUtBa/8jWLN6HyqqMWRKaokWvjnYedCChGbN0MzxaoqYYPmRMiCsz1D0DUjH/N/mYf4yM3qe2w8RWlfd16tVZQhEYreRmPD8u3hhTAS2fP8zNolGeNQmD9pdTXcoJgESIAESIAESIAESaMAEOMPi4c0pKinDoUOHUCFmHuSxxpu2bUNRdoZ2rLFRnBAWLAbpqW07Y0n6CliEsxHVpClKyy2oKM1DSkoarMIx8fe1oFXrDli8chXCAyxIap7i1ikIDjCgbbsuWLR6Ocrhh0hxCllxWQWiQ/0QHp14wno86pLlAP5auAuR/W5E 0p/BYaQvhg7ugUe/PJZPI rcEHHOPiVbBSnhVXOuBjC 2PMsC/w2FcTMck0Due1j4NvyVHszUvAueecgSDpmAR2E7NNEXj442kwhQ/FM71CbM5XNfVaDi3DT ssSG4Zi4CKo0jfWwCEhmkPsvSoTR602yMuVCIBEiABEiABEiABEmhQBOiwnPB2WBEYEIC9O/Ow98cf4WMyIjQ0GC3kgyMH99MeHGkbylswqE83LA/0xdqtm1C0Mh0Bfr5o2yoJRuGwmLV6rOiU1g7bNq9En9QUmH2cDgrWtcSCs3t3xQpxlPLqzRtQvGINggP9cFaf7sJhifegHp2paqKWfYvw154o9J1whstpWf5od/ULeCFsOv43 z08 2k zH6hiE3qiP7Ng wzPkHofNOLeDr8A8wQxwQ/94nYtxIci5YDbsCZ5wBBWp1 aH/BeWg5ewYqzh2OzvY1Z9XVW5GzC4u molpGXko9wlFfEofTLh/LFprK848aZMnOtXAoJgESIAESIAESIAESKDBEjBYxSVbt3jxYnTv3r3BNpQNq0sCFuz65Dbc VsXvDR9AjrUm9t6uuqtS3a0RQIkQAIkQAIkQAIkUJ8EuIelPmk3lLrMu/HXov2I7TcA7erNWRGdP131NhTubAcJkAAJkAAJkAAJkECtCdBhqTWyf34B8 6/sOhALPoNbIv69VdOT73//DvGHpAACZAACZAACZBA4yXAJWGN996z5yRAAiRAAiRAAiRAAiTQ4AlwhqXB3yI2kARIgARIgARIgARIgAQaLwE6LI333rPnJEACJEACJEACJEACJNDgCdBhafC3iA0kARIgARIgARIgARIggcZLgA5L47337DkJkAAJkAAJkAAJkAAJNHgCdFga/C1iA0mABEiABEiABEiABEig8RKgw9J47z17TgIkQAIkQAIkQAIkQAINngAdlgZ/i9hAEiABEiABEiABEiABEmi8BOiwNN57z56TAAmQAAmQAAmQAAmQQIMnQIelwd8iNpAESIAESIAESIAESIAEGi8BOiyN996z5yRAAiRAAiRAAiRAAiTQ4An84xwWq9WAQ5lHkZd91Amu2eKLj7 ZhfSl82EQOZ7qORlh4t9PwFqMw5uWYfXeIlj//b1lD0mABEiABEiABEjgH0/Axxs9sFqN OmPxcjYuVE4DhaYTEaEBgehRbNEdO3SHX7BoSddrUU4Jj/ Ng9DOiUjLDLWYcdgsCIiPBxBwSGazFM9h4E6iFitJnz541zkZexxa83HVIYbxl0La6CtjW6V6ktozcei1 /GlD8zkVdSAZj8ERyVgFYdzsSF4y9F/6b wuvLxpzHxuMd//vx9dODEWhvm7V4LxZ98yV WLAa2zLyYAmKQ8uO/TH8sktxbttwzWEUhVGwbS4 nD4LizcfRG65L8KaJKP94Ktwx/geiJJepbo8aYvSPdXQvBVfP/csdl78Prq2CDpVayxPAiRAAiRAAiRAAiTgZQJecVgghqzFJcVo3iQUXXufjQqzBdm5hVidvhb793 DsWMuh9VPDX/rpodGQwVGDR2sGavpP ee6p1MqwwGCwb364mK0g6iuAGrNu1A8dHtOHvgeagwGCCdKvjXbb9Ppp22MhXIO5KJgtRxeOn6bvApK0T2oY2Y99VXmPhoDp6fdie6BVS1bs1bg/cfeRozM5Nw9ujxuLdNNEx5e7Di5 /wxv2Lsf7hybh/QAyQuxBvPD4Fq5qci3F3XYcWoVbkHNiKbcZghOidFa0KD9rSULBVRUIJCZAACZAACZAACZCAFwl4yWGxtTgowA/xTZrAIpKJiUBYVDx /OEzHD6wC01adcDqzbuxfuUilAnnRup2bNcaXXr0g8VgFDMzRixetQb7d21HYX4ufE3AkH49kNC6p7BmwPyl67WX/E/ qCH9ENeqK2bMnInuzULRodcgO7IT60nnxiLqWr52PbZvXo y4nzERUWgXeiElM1pYNyZmTP5Ysw F9u1BUWACj6FFcTAQG9OmD8CZN7XXJwIq46EgRypcBm/YeQcVxIxITElBhlKvvDPjxz2WwHNuCi8aMF06MTbZo9RYc3PIXxl92I35dsQqH9 5EYUE TMLBiY LQZ ePRCpq8dsMWDZmnTs2b4FxUV5iI JxIC /RAWmyDqqN1lDGuKdmlpEPMpQOce6BFyAJdN2oRNhy3oluxqqwTrPnkdszJScMMrz2NsK62UUOqLAeechXbP3I033/oAvTs/jL6712FDYSyGTrgLl3Swf8x69cdQV5O6dI1taSlYWY5h9ZdT8eFPy7Er24CoVr0w/IZbcGmXKHFP7JcnOqjApmnX4rxpsowfBjz LZ48S/VFGWJIAiRAAiRAAiRAAiTQEAh41WFx7aCfr68YsxtgNoslSGJw37RJJOIHnw1fvwDsPZSFJSsXisF3FOJaniFyjdi1dx ahfmi3ZnDUCG8nujwYLtJK/p0SkGztl00O6HBSm7PdgSe6BmwcOV67NnwN/r36oXgyCbYsG03vv/5F1w2cgSCY5NEWww4kHEILaICkDKgP0orrFiRvh5z5/2McZdeBYuvp4NdK5o3bYZlO1egvCgfhuBwzTHLOHwIzeOboNzog/0HD6JFhKjnzH4oLbciffNWfDfnJ1w2ahSCoqVDYsSC5WtxZOcqDOx7JnyDo7B07TrM fUnjBsr2uLnaVsckGwRazkKjmzFr/M3whx3JjomOFyASsXStfj1jyOIGnwPRjmcFXu2TyLOHT8M39zzPX5dlof 7ZOQYBIOxvzlyGzbD03Erff4ctuWUmz53 N46jsDzr7 YdyYbMXu3z7Gh08 gbLJr Pqtn7CvCc6shU aD32aTw4NFbQNCA4TpblRQIkQAIkQAIkQAIk0BAJeNVhsVqtYjmYGeVySVhOPhYvX4kgHzOaxDfXWMRFhYtQvoQzEhOPzTt3IDMzA02Ew2K7xIxFVJiYnZFOg 0S5rQrOCgAkZFyJsN2WZSCEtjDE kVlxqweeNKnNO1PVLbd9bqiY9PwmfZx5C bhXOHJKkzRBJczERoUhKsrXFLygKs3/4BDlZhxCW0NKl1uqTLZMSscgYhINilqlp266CjxHHsg6gT6/2lfVEynqaam1p1iwZn4qZo3WiLf0GjUCBaO/WLaswun93JLZK0So6u//ZmPHlDmRl7kVUs9TqK3eTU75oEkYPmyT8R6uYaRKuWUAyRj1xBTrJ5WAuTC1Z 3GgyIiWqa3FvETVyyc5Fa39yrFz32FYh47AvXftwaT3nsMNS9qg95BzMXz4OeiaGChcBPdXTW2xFizF17P3o W493Dv6GbajErnDkko3nMbvv5mGS5 fACCPNBRrq1/ZBJaJidW2xb3LaSUBEiABEiABEiABEigvgl41WHZsjcLW/77X0efYqNCMXzoefAJjRRjYQO27TmEDekrkZeTDT TAeXlZlQ0EWvH6vHKysmDwVyMhIRmjvG50WhBvHCqDu9fBZPFIpZuVW1QZFioWFhkQqlYzlabKzjAgCaJrbFzz240T 2Cw8eyYazIFw6Ke6fHx2RBQqJoy6F0GEVbjuUUAOUVmLtwObBwhaNqX EUFhUVIMoh8Szi0 1GvH5LD/hazSjJPYiN87/AjOfuB56Zgtu6VrXh4sNUVXBI/NBs6H14e B4bF48H7/M/QpPz/oU7cY/gf 7ooObfSxi3qOGttwcuA27SmLRr1OC5qxo1ZiS0KlDDD5Zvg0HzAPQev Jddo62scICZAACZAACZAACZDAP4GAVx2WlgkR2qZ7gzglLCQoCAGBQZpTIAe9mdkl P33n9BT7FtJ7tdbzC744ec/F3jETKwq8 jyVM8jYy5KRs24QfTH8yG8NCE35qempGL5go04q6RQLIU7iMTIMPiFhKPMpQ6VNGh7XWwpWZu0MeysAQiOcXbuQoJqvzPdEBSL5snJtj0saI12HeORu/kezP5tHW7qmqaaoIXG6CQkBVqwbttOlJ3X1V6mUqViz3bsLvNBUtN4h1Nh8I/DGYOvEK LMPqLx3Dvx29iZu93cHVrsSnJ5aqpLdeNqjLh41LalvTobnj4 XFbAYUkQAIkQAIkQAIkQAL1SsDNRoW6qz/A3xdxcXGIjo4Rh2PZnBVlPVPMLPhaS9Cre29Ex8YhJiYavgEeDLjFRnSTyRelpaU1L fxUC8mIgxWUyAyMvY77FksRhw vB9NoqJg1jbLq1bXTdi2uVhm5heJHWLT/D6xkT81uSXMOqdEX4tFbPjPzDyIWLH8zSLaEh0eCos4gjgvNwuRERGI0L18Tnb/ir7CiiIUllrhI/YbVflwBHTF0LNicPyPz/HTXhf3qiID8z77GQdD uCcPmEOlpWmA9CiRyfEWQ/joNjQ79Gla4tvsxS09j K9esOO5bOwXwQ6zdmIaB1CpoK/8fkgY7cZO8v1rMVFhRV2vGoMVQiARIgARIgARIgARI4HQS8OsNSU4diIuWMgj9WrF6B5q3bwWrwQ0VZiSji5ixdnSGjwYyo6CbYuHMXIuL2iG3WJoSJZVaRcck6LbE13UO9QH8r0tr3wOK1f0PsYLdtutG2XZB9C5/3CvDGp9fcQsS9vOWL5uJQrFccLJZ12sm6cRS X2HoJ/ CYEhkRg4469KD6 Dx16D9PaIpeUybJL0lcIByYAUeL0sNJysWytNA8pKWmCY 2mDyy5 7Bxwwb4VpQg/ hurPp5JuYeTxQnr3UQW9Pl/dBfgeh6zd0YtelZvP/Afdh54Qj0SRHHGufuxoq5s/DL1gCc9dBNGBAulvdt/hqv/1KCtC4pSIjwhyVvH5Z/9xP2 6dhdBv3H7ua2uIbYsQlo5rhoc fx uB12BIC7Hpft7/8PmeFhhzR29oe1NC p5Yx9QUbVr54bs/vsD37UaipTUTueF9cdYZoW6cLH3fGScBEiABEiABEiABEjgdBNyPHOuhJYnRwejb7xyxh2UFVm7YBh xhyUoMBChYfE11i6XQw3o1RO//5mHn bNR4CvEWf26IwoF4fFUz250Ghgj44IECSWiKONy0tWiI3 4Rh13nkIjbNtfK xQSeVaUWXtHbCUViO1rERCAyPgf0sAc2a0egnji3eiKKCHDGjEoIRgwchwn7EsjjbF4P6dMPyQF s3boJRSvTEeDni7atkmAUDoveTs1N8xHHIDdByILP8ej9M8T0hB Cw8XysLYDcPOkyzCyk5jtEjNgrpchvAcmvPoG0r76HD/M/xCTP8uHJSAaLToMxO3/uQLnnxEhZmasKPUNQ0jOInz77jfIzBGzYeKQgqZtOWiddieBNXp8qDtoiGpF0zEc/4i2ONv3wRj WIw6PFscZXPDsBl7ZVJ6P5n1jHEIaBN9yJ9f Zjo fXQxzcCJ6XN0WA mwuN5qpkmABEiABEiABEigQRAwiJO8tGX/ixcvRvfu3RtEoxpDIyrMJnzyzRcY1r0dEtp01Lpssfo4PUvGo/0YjQEW 0gCJEACJEACJEACJNBoCZy2GZbGSdyAo8eOiaVHBqzesBUxfmVoKo5w9nxWpHFSY69JgARIgARIgARIgAQaLwE6LPV47y0WE35d DdKjmegWXwMzjtnOMymqqdl1WOTWBUJkAAJkAAJkAAJkAAJNGgCXBLWoG8PG0cCJEACJEACJEACJEACjZtAlZNrGzcO9p4ESIAESIAESIAESIAESKAhEaDD0pDuBttCAiRAAiRAAiRAAiRAAiTgRIAOixMOJkiABEiABEiABEiABEiABBoSATosDelusC0kQAIkQAIkQAIkQAIkQAJOBOiwOOFgggRIgARIgARIgARIgARIoCERoMPSkO4G20ICJEACJEACJEACJEACJOBEgA6LEw4mSIAESIAESIAESIAESIAEGhIBOiwN6W6wLSRAAiRAAiRAAiRAAiRAAk4E6LA44WCCBEiABEiABEiABEiABEigIRGgw9KQ7sY/sS3WLCya iRe/GEvLP/E9rPNJEACJEACJEACJEACDZoAHZY6uD1WqwGHMo8iL/toHVirNOEtu5U11EHMmo89a9dgW1YJrHVgjiZIgARIgARIgARIgARIQE gUTgsZeVWLFmVjs / gbv//e/ Oij6Zj74/c4sn nnsVJxy0WX/z42zwc3b/jpG24K gtu1pdln34/PYLMPa1lahwqtyMHR/dhAvGv4N1zhlOWkyQAAmQAAmQAAmQAAmQQH0Q8KmPSk5nHcVlwKyffkJ57mF0SEtDTFx3lJmtyDhyBBUVIpMXCZAACZAACZAACZAACZBAgyXwL3dYDFi8ag3Kcg5i7IhRCI5NcNyIlDatHHGL1Yjla9djb1KCvOR1xUBPr17omYxGRtmZPVasIfS5bh8L5dKCosgFHs1oiLicCAPn0Q3qSp3Y4B85eu114QpUYN6Yf41h1hthiwbE069mzfguKiPMTHRGJA334IE205WbtNWnVC pZd2JC AsX5uQgO9MeAXl3QLLWTo091FhF7VP56dzI X74HGVm5KEEgYlr3xpgJt PCtBAYXCqyFm7Ahw89jl jbsbkp4ajqcmD8pZjWP3lVHz403LsyjYgqlUvDL/hFlzaJQRrXr8aT24 H2cw1am0Rl5Svx2vincWj8R3h5ZIyo34rcX/4P49/1wwMzboXxY8/b6tJ0JkmABEiABEiABEiABBoggX 1w1Je4YMd2zegR vmCJEOgtsbYMDCleuxZ8Pf6N rF4Ijm2DDtt34/udfcNnIEcLJSRLlDDiQcQgtogKQMqA/SiusWJG HnPn/Yxxl14Fs9FPWLaiT6cUNGvbRYuHBgeL0IgFy9fiyM5VGNj3TPgGR2Hp2nWY8 tPGDf2KlT4Bp U3SPZJVj69284q3sXxDVrjYKiEoSH Lrt3SkLxR6VvevXIzv5Wjxydyp8Sw5i2VfTMe2599H0v/ei5/ 3d/exVhfmAcefc194FeRNLu8gL4IDRMpFRcSXWmdnl9KZ2qaui8m6LE3TZdmWduvaZVnn0ro1G91f3ZKVOE07qjZdTavbate1s26oKKio4ERLrbSgAg55vffudwHhqvDIkjaPpZ8TDTf3Oef3HD/n/nG//s7vMPj4hr6DW Obn70x7mz7tbjxj66JKf0/Xb1v8vihOJmz8Zf/q1Vlz m38YvzWjL7b82z/G6j/5VBz43Kq49vz5MeieJ PJ3X0xa3QrerZujCd2H4wdj2 OA02wDI6DsXnjpoi5H4z5Q1 Ou7PnOvT4c/UVAQIECBAgQIDAz4fAaR0su/fsjZ4De2P8WV0niZWIvftb8fhjD8Q7Fs Pc YvOny/CRMmx5deeiHWb3gwLrly8rFPvxo3akRMntwfMBGDho2JO79 S zc8aMYPn7u4Vd7 LAhMXr06GOv/CvNsZ984sFYuXxJTJo55/D3L19 edy65qnY8eNnY9SUXzr8vf/vcffs29UkVG9MmTgxRowdG80/P NbK4ZOOy 6F8 N9lgUi8b9ONb97j1x/ ZDsXTB0dU9P4nvrfqH PvnL4pP/OUNMX/4wHMvJ39898z/itvu3BpnX/ F L2VU5vEi1i0YHLsfeYjcdvt/92cyVkc82J1bHh8X1xz8ZB4sQmSbUObMzsbN8RTh5bF/NaW2PDonph 1fkxptV/0c3Jdy0977T cf8Z/ww4PAECBAgQIECgRuC0/g2u72imtAb 7vw65x07d0erZ29MnDj16L2b8yJtvTFhwrTYtvXBaO/tjUMnePzokSOai9XbY/vdF/LuVEtxd27mrewnQo7vru2ojv3n/sLp09vfHKK/8bo4595/gXp3LcaV2jm7erzYnbv3F3zG3e2jZ//oIYNfbkUXb86D dr9q6JkVX2 7Y9fKr56x6Y/tdfx2f2zc rvv8R OiMScAG7B64ON7tm6Kp/edFRefN/FwrBy W/vkOG/BuLhl7aZ47sxr4oLZX4g71m2Kg8tmxiMPPxPz3vv GHL7d2L9D3vj3M4Nsf4nk2Lp0knN438wYMuRLwfuesPQNwgQIECAAAECBN7yAqd1sIwcPizaOgbHjhd2xLTmpXj11 ufxqvSdriC q gOHLUE0VR/6TV6o13XrYiho b9Jq1Zww78fuTTuW4He29ce073xHP/mhbcxZoQ6z56tfisqULY975F5/6f2OrIzqbd5Ed2LsveppndvwHoS/2Nd Ljs442ZvMWu0dTar1RdNyR2 tOHP pTH7B/fEP//trdH9mRtiwRknj5bXPz59XVpd0X3hjPjiv6yNzXv2xP2PT47uD10RQzd8Kb69bltc2bE2tpx1QXxkev8FLm 8vX7XG /hOwQIECBAgAABAm9lgdP6Y40723ti2ox58chTz8T nTtO DqMGzUy tqHxvPPb23eTHTk1tvbFtu2bY2uMWOa61NOgajVF 3tnbF///5jx g/0tgzR0RvDYvWtHjB41KkYN Ldj0ICLP47ufcMfJzlu//1azWzG5K5Y StXx6yFy2Ldo49GZ09/epzirTU2pk89Iw48vi4e2zvgMQe3xAMPvxCd02bEpBM3wIA7v/plKwadfU184qbfj 6dX4k/v mueO4UPxK5feqcmDV4ezyyYduxt95Fz3PxyGM7YsisOc1F 20xZfklMWP7ffHvX/1erB 1ON42cVwsWXp2PP39u Ob/7kpzlq ImYdL65Xn5Q/CRAgQIAAAQIETgOB0/rXvP6zGyuWLok7nn 2uU7i683bjBbG6HFdcaj55K7tL7wYXSPbY9rshXHu/O649 HvR3NV/JGL7jdviQMv/TAWLX/X8V ikxe7rdUTY5q3ZD32P0/HqPFNHDXnH0YOacXYrmlxztxFcV/zaV69bUNiTPOJYvsPNm8x27875sw5NznikdHJjtsaOja2P78lxo4ZFwd7Wof/wsphgwdH74lO85x0y A4f XKmPUft8ZNn2zF 3 1OyZ1vBgb//Wf4o6tE JdH14eI/sLLj398dqDd0x4e/zBp56Lj3387 Kmr5wTf3X97Oai PzWOmNZvPfdU PjX/6LWDX0hrhyenPR/bduji8/Mz2u/eiFR95uN3lFXDb7lli9ZntMue5vYkZ7K9qWLY8Zzd nc1vvlHjfb88ecIYo32dKgAABAgQIECDw8yVwWgdL/0sxcnh7XPee98SDDz10 KOA9 5ZHx3N/7Uf25xZ6Vowrzkj0heXdi MIY3Efc1HGx/cd3/zscZnxruvvjpGjJ9ySr vHw6jC5bGt7 zO77xrXtiSGdbXNK9KMY1gXLFRW LtUM74 EnN8YrD6yPIYM6Y 7MydHWBMubnQ852XE7xo6IB9dvjD27djZndiK6 j8q fKr4tCpnA0a8PPZOfv6uPEzw2P1zXfGmlV3xct9w2L8rO744Kc/FNctHvaas0UDHpZ OWTuB Jjv/FQ/M7Nq L2C1fFr5 d3r0ZDo5zb7gx/mxw87HGaz4bf7wzYnTzscYf PSH431zj ZO26S44pfPi1s2vRQrLp3Z5GBzm3hJXDpndWzuvSqumnnKp4Le7MmYEyBAgAABAgQIvMUEWn3Nrf853XvvvbFkyZK32NPzdAgQIECAAAECBAgQ EUWOIULNH6Refy3EyBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECDMl67WAAAIX0lEQVRAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUCgqVS324CBAgQIECAAAECBFIBwZLyGBIgQIAAAQIECBAgUCkgWCr17SZAgAABAgQIECBAIBUQLCmPIQECBAgQIECAAAEClQKCpVLfbgIECBAgQIAAAQIEUgHBkvIYEiBAgAABAgQIECBQKSBYKvXtJkCAAAECBAgQIEAgFRAsKY8hAQIECBAgQIAAAQKVAoKlUt9uAgQIECBAgAABAgRSAcGS8hgSIECAAAECBAgQIFApIFgq9e0mQIAAAQIECBAgQCAVECwpjyEBAgQIECBAgAABApUC/wfKvHz/RoW0lQAAAABJRU5ErkJggg==[/IMG]

---

### Post by freeflyjohn on 2024-01-11
PS.  This is the SSD the root drive is on...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293296&stc=1[/IMG]

---

### Post by TheFu on 2024-01-11
My servers don't have a desktop.  That's a huge liability for performance AND security in a server.
I pull backups from VPS nightly following my normal pull-backup rdiff-backup methods, which have been posted here. 

Different servers take different times, but for a minimal VPS with just some haproxy and wireguard, it is a few seconds. I only backup the stuff required to put the system back, nothing else. My remote system doesn't actually hold any data.  Putting everything back would take about 5 minutes, so hardly hours and hours.  For each container/VM that I run, the restore times are different, but most would be 15-30 minutes to restore because they don't actually hold that much data.   Again, I've posted my restore and backup methods using rdiff-backup in these forums for a few years. They've been tested a number of times.

The hardest part about pull-backups is getting the ssh configuration setup to be sufficiently secure, allowing only my backup server to pull and using a root-equivalent account.  If you don't know how to do that, it isn't my place to explain it, since there are many subtle aspects which would compromise system security if not addressed correctly.  Backups need to run with root-level privilege on both sides of the connection.  No need for any GUI or remote desktop or wireguard for rdiff-backup or rsync backups to work.  Why have multiple encryption layers in a tunnel?

I'll never understand why people use multiple backup tools.  Makes no sense to me.  Use the one that handled everything. rdiff-backup is that for me.  

20 yrs ago, I used rsync + hardlinking for backups and it worked well enough to provide versioned backups without eating too much storage.  Eventually, the backup times took longer and longer until they didn't complete within the allowed nightly backup window.  I needed to new solution.  That's when I found rdiff-backup.  The first backup is the same as an rsync, but every version after that is faster.

BTW, here's the storage use on my VPS:
```
$ df ..... lots-of-options
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext4   24G  9.8G   13G  45% /

```

And here's the backup summaries:
```
# rdiff-backup --list-increment-sizes .
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Jan 11 00:08:23 2024         37.1 MB           37.1 MB   (current mirror)
Wed Jan 10 00:09:37 2024         1.47 KB           37.1 MB
Tue Jan  9 00:08:22 2024         1.39 KB           37.1 MB
Mon Jan  8 00:11:45 2024         1.40 KB           37.1 MB
...
Wed Jun 28 00:11:33 2023         1.19 KB           37.5 MB
Tue Jun 27 15:01:25 2023         1.64 KB           37.5 MB
Tue Jun 27 00:10:36 2023         6.58 KB           37.5 MB
Mon Jun 26 18:55:54 2023         1.36 KB           37.5 MB
Mon Jun 26 18:49:39 2023         1.54 KB           37.5 MB
```

I setup this VPS last June. Because it is a high risk system, directly on the internet, I keep more backup versions.  Everything I need to recreate it in about 5 minutes takes just 37.5 MB. Seems like a bargain to me.  I think 366 days of versioned backups will be retained for that system. Yep, just checked the backup script for it.

For my nextcloud setup, running inside an LXC container, a little more storage is used:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Thu Jan 11 00:07:27 2024         1.40 GB           1.40 GB   (current mirror)
Wed Jan 10 00:08:44 2024          966 KB           1.41 GB
Tue Jan  9 00:07:28 2024         1005 KB           1.41 GB
...
Mon Oct 16 00:06:27 2023          764 KB           1.90 GB
Sun Oct 15 00:06:27 2023          177 KB           1.90 GB
Sat Oct 14 00:06:19 2023          763 KB           1.90 GB

```

That is just the stuff needed to recreate the container and nextcloud DB and some data that it holds.  Because LXD is managing it, I could use their crappy "tar" file export method to get 100% of everything, but that breaks versioned backups, so it is bloated and useless to me. 1 backup copy as a tgz file being huge isn't an option to me and I certainly don't want to transfer it around when less than 1MB of stuff actually changed.

I should point out that backups start here at 00:03 am daily.  Last night, the nextcloud backup started and ended ...
```
=== Time for Backups to nextcloud-lxd === 
StartTime 1704949647.00 (Thu Jan 11 00:07:27 2024)
EndTime 1704949658.93 (Thu Jan 11 00:07:38 2024)
ElapsedTime 11.93 (11.93 seconds)
TotalDestinationSizeChange 909124 (888 KB)

```
12 seconds for rdiff-backup to work according to the rdiff-backup generated logs. There are a few seconds before and after for other scripts to run so current system information  is included in the backup data.  I mostly use nextcloud as an RSS feed reader, so there isn't much data managed my it.  Don't get me wrong, it has TB and TB of files, but they are read-only to nextcloud. I don't trust php webapps with data.

Step 1: Don't use a GUI on a remote server.

---

