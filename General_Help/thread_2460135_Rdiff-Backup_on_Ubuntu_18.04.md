---
title: "Rdiff-Backup on Ubuntu 18.04"
date: 2021-04-03
forum: General Help
---

### Post by Quarkrad on 2021-04-03
I have a 18.04 machine running rdiff-backup.  There are three HDs in this machine, one with **/ **and **/home** on it (sda), another used for pure data (sdb) and the third used as a backup disc (sdc).  The current rdiff-backup is in the form *rdiff-backup sda  sdc* or to be more accurate r*diff-backup /home  /sdc* - I'm simplifying this as there are --exclude options in the actual command.  This rdiff-backup command is written in a .sh script that I can run via an icon on my Desktop.    What I would like to do, but not been able to find out how to do, is to include a folder that is on on sdb to be backed up on sbc*.  Can I add this folder to my command so it looks something like:

**rdiff-backup sda, sdb       /sdc**

or if that is not possible can you run two commands in the sh script like:

[B]#!/bin/bash

rdiff-backup sda sdc

rdiff-backup sdb sdc[/B]

* can I use the same backup folder on sdc for both the folders on sda and sdb or will I have to use separate folders on sdc for those folders in sda and those in sdb?

---

### Post by TheFu on 2021-04-03
I'm confused.  Are you really using whole disk device files in your backup commands?  rdiff-backup should be used on directories, not storage device files.

In general, my rdiff-backup commands go like this, 
```
 rdiff-backup 
          --exclude-special-files \
          --include /usr/local --include /etc --include /home \
          --exclude '**'   backup5492@{remote-machine}::/ \ 
                           /Backups/{remote-machine}
```

Backups are run from a backup server via root's crontab, connect to a random account on the remote system and "pull" the specific included directories, excluding everything else.  Actually, the random account is a root-equiv with ssh-keys from the backup server installed just for that system. The account, keys used, remote name are in the ~/.ssh/config to make the commands all look the same by just changing the hostname-alias in the rdiff-backup command.  
Instead of backup5492@{remote-machine}::/ , it really says vpn-backup::/ so the correct parameters just for backups get used.
Also, I'm not showing the LVM snapshot is where the real backups come. Don't want to add too much confusion. ;) There are enough details already not clearly spelled out.

Anyways, hope this helps.  Very few examples for how to "pull" backups and get multiple locations in 1 command exist.  If this is all local, just don't make the backup5492@{remote-machine}::/ like that.  Use / instead.

---

### Post by Quarkrad on 2021-04-03
Apologies - I'm not using whole disk commands.  My current rdiff command looks much like yours although I'm backing up to an internal disk rather than to a remote machine.  The additional folder I want to add to my backup is called *photos* - on my machine it is at  */media/dad/store1/photos/* - there are many many sub folders in 'photos'.  Taking your rdiff-backup command above, how would you add the photos folder (media/dad/store1/photos) to it?  I was trying to ask .... can you add a reference to photos to the existing rdiff-backup command or do you have a second, separate rdiff command for the photos folder in the bash script?

---

### Post by TheFu on 2021-04-03
Are you using rdiff or rdiff-backup?  Those are two VERY different tools.
Does my last paragraph above not answer the all local question?
Maybe posting the actual command would get a better answer?

---

### Post by Quarkrad on 2021-04-03
Sorry again - I'm always talking about rdiff-backup.  Unfortunately I have not got access to my 18.04 pc at the moment.  For a specific example, if my script is:

[B]#!/bin/bash

#backup dad home folder to backup disc
sudo /usr/bin/rdiff-backup /home/dad  /media/dad/backup[/B]

how would I add the additional photos folder (which is specifically at /media/dad/store1/photos) to the above script?

---

### Post by TheFu on 2021-04-03
> **Quarkrad said:**
> Sorry again - I'm always talking about rdiff-backup.  Unfortunately I have not got access to my 18.04 pc at the moment.  For a specific example, if my script is:

[B]#!/bin/bash

#backup dad home folder to backup disc
sudo /usr/bin/rdiff-backup /home/dad  /media/dad/backup[/B]

how would I add the additional photos folder (which is specifically at /media/dad/store1/photos) to the above script?

```
 sudo /usr/bin/rdiff-backup 
          --exclude-special-files \
          --include /home/dad  --include /media/dad/store1/photos \
          --exclude '**'   /        /media/dad/backup

```

Realy hope that /media/dad/backup is a different physical drive.

---

### Post by Quarkrad on 2021-04-03
Thank you very much for your time.  Yes, /home is on sda, /media/dad/store1/photos on sdb and /media/dad/backup on sdc - all physically difference HDs.

---

### Post by TheFu on 2021-04-03
> **Quarkrad said:**
> Thank you very much for your time.  Yes, /home is on sda, /media/dad/store1/photos on sdb and /media/dad/backup on sdc - all physically difference HDs.

But you are trying to backup /media/dad/store1/photos to the same drive!!!!!
Backups need to be on different physical devices.

---

### Post by Quarkrad on 2021-04-05
Afraid I'm still struggling with this. I have three physical hard disks:

dev/sda    mounted as /media/dad/backup               [COLOR="#0000CD"]note: I have a folder on this HD called backup[/COLOR]
dev/sdb    mounted as / (sdb2) and /home (sdb3)
dev/sdc    mounted as /media/dad/photos                [COLOR="#0000CD"]note. there is only 1 folder on this HD - called photos
[/COLOR]
I would like to backup key /home folders on sdb3 to my backup folder on  sda  and the photos folder on sdc to my backup folder on sda

I have been playing with my backup.sh script but getting in all sort of trouble.  I have potentially two commands that I don't know if they can be combined or if the two commands could be run sequentially in a single bash script (backup.sh).

sudo /usr/bin/rdiff-backup --terminal-verbosity 8 --include /home/dad/.thunderbird/8jnp9mo2.default/Mail --exclude "**/.*" /home/dad    /media/dad/backuphd/backup

sudo /usr/bin/rdiff-backup --terminal-verbosity 8 /media/dad/photos/  /media/dad/backuphd/photos

I do not want to backup the hidden folders in /home but I do want to backup the Local Folders in thunderbird mail. (The few key folders in .thunderbird and .mozilla needed to rebuild ff and tb are hard-linked to a folder in Documents).

Each of the above rdiff-backup commands work OK on their own but I'm having issues combining them or running them sequentially in a single backup.sh script.  At one point I had the target destination, /media/dad/backup/backup, the same in both commands but running them sequentially resulted in the second over writing the first - which I now realise, in hindsight, is obvious.

---

### Post by TheFu on 2021-04-05
Follow the example in post #6.  Only change the **--include** directories.  Do one command for backups.  Different drives don't matter if they are sources.  If you want more exact control, you can create a file with specific directories to be included and use that option to rdiff-backup.

The --exclude in #9 above is messed up. That won't work.  BTW, I find it much easier to read commands in code-tags. I think you want this:
```
sudo /usr/bin/rdiff-backup --terminal-verbosity 8 --include /home/dad/.thunderbird/8jnp9mo2.default/Mail \
         --exclude '**'    /      /media/dad/backuphd/backup
```
for the first command.  That will only get the Mail directories.
If you want the entire HOME, but not settings (WHY?????!!!!!!!), the settings are more important to me than almost anything! Those make the system "my system" - anyways ... 
```
sudo /usr/bin/rdiff-backup --terminal-verbosity 8 \
  --exclude-special-files \
  --exclude /home/dad/.[a-Z0-9]* \
  --include /home/dad  \
  --include /home/dad/.thunderbird/8jnp9mo2.default/Mail \
  --exclude '**'    /      /media/dad/backuphd/backup
```

I think that would work. Might need to move the .file exclude around a bit OR the .thunderbird include higher. IDK.
Always - ALWAYS - use --exclude-special-files .... ALWAYS.  Named pipes and other non-standard files can show up anywhere.

---

