---
title: "timeshift usage questions"
date: 2023-01-02
forum: General Help
---

### Post by tc-g on 2023-01-02
I have searched far and wide for answers to questions I have about timeshift but have been unable to find clear answers to the following set of questions, Please answer if you can and are willing:

Note: I have timeshift installed on a remote system and I access the system via my laptop (both ubuntu 20.04) over ssh -X.

o If I've installed timeshift and scheduled a weekly snapshot, can I assume that it will be done without any further actions?
o If yes, when will the snapshot be performed, i.e is there anyway of know when? 
o When I want to create a snapshot on demand I can initiate Create from timeshift-gtk or run timeshift --create.  However, how can I do either of these in the background, i.e. I want log out of remote machine and check later?
o My goal is to perform a full-system backup of my server host, which runs numerous collaboration tools such as NextCloud and OnlyOffice, etc.  Can the scheduled backups be initiated and performed without someone shutting down server apps, disconnecting network shares, etc or is this kind of back only to be performed manually?

Thanks

Ubuntu 20.04
[FONT=monospace][COLOR=#000000]Timeshift v20.03

[/COLOR]
[/FONT]

---

### Post by #&amp;thj^% on 2023-01-02
> **tc-g said:**
> 
o If I've installed timeshift and scheduled a weekly snapshot, can I assume that it will be done without any further actions?
o If yes, when will the snapshot be performed, i.e is there anyway of know when? 

Assume yes, there is no way to ensure this always happen though, and I set mine up to take snapshots on any system changes.
> **tc-g said:**
> 
o When I want to create a snapshot on demand I can initiate Create from timeshift-gtk or run timeshift --create.  However, how can I do either of these in the background, i.e. I want log out of remote machine and check later?
Both work just fine for me.
> **tc-g said:**
>  However, how can I do either of these in the background, i.e. I want log out of remote machine and check later?

You check on that machine with:
```
sudo timeshift --list 
Mounted '/dev/dm-4 (sdb3)' at '/run/timeshift/1029634/backup'
Device : /dev/dm-4 (sdb3)
UUID   : 30d9ba33-1076-460a-9ae0-9031c4143e51
Path   : /run/timeshift/1029634/backup
Mode   : BTRFS
Status : OK
12 snapshots, 216.0 GB free

Num     Name                 Tags  Description             
------------------------------------------------------------------------------
0    >  2022-12-27_15-06-30  O     Automatic APT snapshot  
1    >  2022-12-27_15-08-11  O     Automatic APT snapshot  
2    >  2022-12-27_15-12-40  O     Automatic APT snapshot  
3    >  2022-12-27_15-40-46  O     Automatic APT snapshot  
4    >  2022-12-27_15-59-26  O     Automatic APT snapshot  
5    >  2022-12-28_07-06-36  O     Automatic APT snapshot  
6    >  2022-12-28_07-11-02  O     Automatic APT snapshot  
7    >  2022-12-28_07-23-12  O     Automatic APT snapshot  
8    >  2022-12-28_08-41-35  O     Automatic APT snapshot  
9    >  2022-12-28_08-48-58  O     Automatic APT snapshot  
10   >  2022-12-28_09-09-25  O     Automatic APT snapshot  
11   >  2022-12-28_15-14-02  O     Automatic APT snapshot  



```
> **tc-g said:**
> 
o My goal is to perform a full-system backup of my server host, which runs numerous collaboration tools such as NextCloud and OnlyOffice, etc.  Can the scheduled backups be initiated and performed without someone shutting down server apps, disconnecting network shares, etc or is this kind of back only to be performed manually?
In theory yes, too many things come into play here, and someone managing a set-up like yours it should be done manually just to take any guess work out.
Really, it's just so easy to do them manually as needed and forget schedule.

---

### Post by tc-g on 2023-01-02
You didn't get my question:  How can I run manual create snapshot in background (by either way to invoke)???   So I can then logout and come back later to check.

> In theory yes, too many things come into play here, and someone managing  a set-up like yours it should be done manually just to take any guess  work out.
Really, it's just so easy to do them manually as needed and forget schedule. 

I agree that a manually creating a snapshot may make more sense, but assuming it's the first full-backup I don't want wait around for unknown amount of time for it to complete.
I'm trying to figure out how I can push the process to background so I can logout and come back later to check.

However, the other question you didn't answer is:   will the backup work if no one shuts down other server tools, like docker containers, and apps running as systemd services???

thanks for your reply

---

### Post by TheFu on 2023-01-03
I know just a little about timeshift, enough to know that it works in 2 different modes, depending on whether the file system is btrfs or something else.

With btrfs, it uses a proper "snapshot" as a volume manager would.  The system can be running and used while this snapshot + rsync happens.

Without btrfs, it doesn't ensure that the underlying files aren't all closed and unused.  This can cause corrupted backups, since only rsync is used to copy the source to the target backup area.  If you make sufficient backups, then the chances that any single file will be corrupted every time is lessened.  However, if you are using any DBMS, then you'll want to use a proper volume manager snapshot before rsync runs ...
OR
perform a DBMS dump to text BEFORE running the backup to ensure the DBMS can be restored from a non-corrupt file.

Linux is fantastic at being flexible, but that means the admin needs to be aware of many details to ensure what they request doesn't cause bad mistakes.

[https://www.linux-magazine.com/index.php/layout/set/print/Issues/2019/226/Timeshift/(tagID)/53](https://www.linux-magazine.com/index.php/layout/set/print/Issues/2019/226/Timeshift/(tagID)/53) might be helpful to understand the differences between what a volume manager calls a snapshot and what timeshift calls a snapshot.  They are very different. Beware.  When using a volume manager, a snapshot is nearly instant. If freezes blocks and makes running a backup to other media on a busy system unlikely (impossible?) to get a file that is actively changing during the backup process.  For more about that,  [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)

If you won't want to create a backup and are willing to risk just having blocks frozen like LVM, BTRFS, and ZFS can do, even if the storage device fails so all the data AND the snapshots are lost, great.  Just be aware that snapshots are just frozen storage blocks, not backups.

---

### Post by tc-g on 2023-01-03
@TheFu  You give me food for thought.  Several database servers get started up and I need to get a handle on them and not only back them up but also figure out a way get them backup up regularly.
BTRFS is not an option for me as my system supports rsync.  

Can you speak to how one would run timeshift if the background when manually creating a snapshot?  Thanks

---

### Post by TheFu on 2023-01-03
> **tc-g said:**
> @TheFu  You give me food for thought.  Several database servers get started up and I need to get a handle on them and not only back them up but also figure out a way get them backup up regularly.
BTRFS is not an option for me as my system supports rsync.  

Can you speak to how one would run timeshift if the background when manually creating a snapshot?  Thanks

I don't know timeshift. It doesn't meet my requirements. Rsync isn't precluded with or without btrfs.  Follow the link I already posted for how to do backups using LVM snapshots. That's my best advice.

Also, make certain you understand btrfs capabilities, limitations and best practices BEFORE using it. There are some "gotchas", some are really nasty, if they happen - like "total data loss" nasty.

---

### Post by #&amp;thj^% on 2023-01-03
> **tc-g said:**
> You didn't get my question:  How can I run manual create snapshot in background (by either way to invoke)???   So I can then logout and come back later to check.



I agree that a manually creating a snapshot may make more sense, but assuming it's the first full-backup I don't want wait around for unknown amount of time for it to complete.
I'm trying to figure out how I can push the process to background so I can logout and come back later to check.

However, the other question you didn't answer is:   will the backup work if no one shuts down other server tools, like docker containers, and apps running as systemd services???

thanks for your reply
```
 timeshift --help

Timeshift v22.11.1 by Tony George (teejeetech@gmail.com)

Syntax:

  timeshift --check
  timeshift --create [OPTIONS]
  timeshift --restore [OPTIONS]
  timeshift --delete-[all] [OPTIONS]
  timeshift --list-{snapshots|devices} [OPTIONS]

Options:

List:
  --list[-snapshots]         List snapshots
  --list-devices             List devices

Backup:
  --check                    Create snapshot if scheduled
  --create                   Create snapshot (even if not scheduled)
  --comments <string>        Set snapshot description
  --tags {O,B,H,D,W,M}       Add tags to snapshot (default: O)

Restore:
  --restore                  Restore snapshot
  --snapshot <name>          Specify snapshot to restore
  --target[-device] <device> Specify target device
  --grub[-device] <device>   Specify device for installing GRUB2 bootloader
  --skip-grub                Skip GRUB2 reinstall

Delete:
  --delete                   Delete snapshot
  --delete-all               Delete all snapshots

Global:
  --snapshot-device <device> Specify backup device (default: config)
  --yes                      Answer YES to all confirmation prompts
  --btrfs                    Switch to BTRFS mode (default: config)
  --rsync                    Switch to RSYNC mode (default: config)
  --debug                    Show additional debug messages
  --verbose                  Show rsync output (default)
  --quiet                    Hide rsync output
  --scripted                 Run in non-interactive mode
  --help                     Show all options

Examples:

timeshift --list
timeshift --list --snapshot-device /dev/sda1
timeshift --create --comments "after update" --tags D
timeshift --restore 
timeshift --restore --snapshot '2014-10-12_16-29-08' --target /dev/sda1
timeshift --delete  --snapshot '2014-10-12_16-29-08'
timeshift --delete-all 

Notes:

  1) --create will always create a new snapshot
  2) --check will create a snapshot only if a scheduled snapshot is due
  3) Use --restore without other options to select options interactively
  4) UUID can be specified instead of device name
  5) Default values will be loaded from app config if options are not specified


```
I think the longest I've waited for timeshift on a first run was about 10-12 minutes.
TheFu has a great back-up scheme, if you can follow it.
And I also use different tools for different use case, I'm a tester so at times I need a quick before snaapshot, and that should make good sense.
Now to clear up this >>""  _will the backup work if no one shuts down other server tools""_, the quote from Tony should help.
> Since Timeshift creates snapshots when system is online, it is possible for inconsistent snapshots to be created. There is no way to avoid this. Ideally the system should be offline (not running) when snapshot is being created.

Regards,
Tony George
It all boils down to what your most comfortable with. The Forums are full of questions on this subject.
EDIT: Forgot to add no matter your method used always check that they will work.

---

### Post by TheFu on 2023-01-03
> **1fallen said:**
>  
I think the longest I've waited for timeshift on a first run was about 10-12 minutes.
TheFu has a great back-up scheme, if you can follow it.
And I also use different tools for different use case, I'm a tester so at times I need a quick before snaapshot, and that should make good sense.
Now to clear up this >>""  _will the backup work if no one shuts down other server tools""_, the quote from Tony should help.

It all boils down to what your most comfortable with. The Forums are full of questions on this subject.
EDIT: Forgot to add no matter your method used always check that they will work.

If a volume manager like btrfs, ZFS or LVM are used, then corruption is nearly impossible.  I've never seen it with LVM snapshots assuming the snapshot didn't run out of storage or some other mechanical failure didn't happen.  Taking a drive off line is unacceptable just for backups in most businesses.  This is why we use volume managers with snapshot capabilities.

So, if using timeshift AND the OS is installed onto BTRFS storage, then a proper snapshot will be used before rsync gets involved to copy the data to different storage.  In a single disk system that doesn't do any virtualization, I think that should be fine.  Multiple disks and virtual machines have caused problems for BTRFS with data loss and terrible performance, so beware.  ZFS allows the CoW aspects to be disabled for VM storage using CoW virtual disks.  Or just use LVM2 + ext4 with LVM-snapshots and whatever backup tool you like.  1 tool handles all sorts of needs.  Every snapshot/backup tool takes time to understand, so I'd rather have 1 that handles everything than need to learn 2+ different tools.  That's me.

I have to admit, my backup technique is a challenge for anyone without at least intermediate level Linux knowledge/skills.  That's the trade-off in not having lots and lots of storage tied up for backup use and having a multi-step restore process.

I've had initial backups take over an hour for some systems with lots and lots of storage.  Depending on the number of files, changed data, and total storage, the following backups can take from 10 seconds to 3 minutes to 25 minutes. Obviously, the speed of the storage on both sides (source-->target) matters as well.  I tend to post the backup times for the fastest systems. These are usually 10 sec- 120 sec total.  One system with hundreds of thousands of files and a complex DBMS usually takes longer.
```
StartTime 1672732900.00 (Tue Jan  3 03:01:40 2023)
EndTime 1672734301.25 (Tue Jan  3 03:25:01 2023)
**ElapsedTime 1401.25 (23 minutes 21.25 seconds)**
TotalDestinationSizeChange 125136086 (119 MB)
```
That's typical elapsed time for that specific system.

The day before, it tool longer:
```
StartTime 1672646498.00 (Mon Jan  2 03:01:38 2023)
EndTime 1672647953.62 (Mon Jan  2 03:25:53 2023)
**ElapsedTime 1455.62 (24 minutes 15.62 seconds)**
TotalDestinationSizeChange 110517621 (105 MB)
```
Even with less data changes.

These are all using rdiff-backup, which is the fastest backup tool I've found.  It is faster than rsync for all but the first backup.  The system is fully running during the backups, thanks to LVM snapshots.

---

### Post by #&amp;thj^% on 2023-01-05
> **TheFu said:**
> If a volume manager like btrfs, ZFS or LVM are used, then corruption is nearly impossible. 
Agreed.

> **TheFu said:**
> I've never seen it with LVM snapshots assuming the snapshot didn't run out of storage or some other mechanical failure didn't happen.  Taking a drive off line is unacceptable just for backups in most businesses.  This is why we use volume managers with snapshot capabilities.

No Argument here;)
> **TheFu said:**
> So, if using timeshift AND the OS is installed onto BTRFS storage, then a proper snapshot will be used before rsync gets involved to copy the data to different storage.  In a single disk system that doesn't do any virtualization, I think that should be fine.  Multiple disks and virtual machines have caused problems for BTRFS with data loss and terrible performance, so beware.  ZFS allows the CoW aspects to be disabled for VM storage using CoW virtual disks.  Or just use LVM2 + ext4 with LVM-snapshots and whatever backup tool you like.  1 tool handles all sorts of needs.  Every snapshot/backup tool takes time to understand, so I'd rather have 1 that handles everything than need to learn 2+ different tools.  That's me.
Again as I mentioned I use many different tools for certain case uses, I'll even use "dd" /root /etc /dev in cases. (Please don't follow me on this it is not a recommended go to)

> **TheFu said:**
> I have to admit, my backup technique is a challenge for anyone without at least intermediate level Linux knowledge/skills.  That's the trade-off in not having lots and lots of storage tied up for backup use and having a multi-step restore process.
I found it a challenge, a few years back and I  think that it took me over a week to fine tune it.
And I'm not sure how anyone could teach this to a average Desktop user.(Just Saying)
> **TheFu said:**
> 
I've had initial backups take over an hour for some systems with lots and lots of storage.  Depending on the number of files, changed data, and total storage, the following backups can take from 10 seconds to 3 minutes to 25 minutes. Obviously, the speed of the storage on both sides (source-->target) matters as well.  I tend to post the backup times for the fastest systems. These are usually 10 sec- 120 sec total.  One system with hundreds of thousands of files and a complex DBMS usually takes longer.

> **TheFu said:**
> 
These are all using rdiff-backup, which is the fastest backup tool I've found.  It is faster than rsync for all but the first backup.  The system is fully running during the backups, thankse to LVM snapshots.
That's what make you "TheFu".
I have no problems telling I've learned from you over the years here!
Glad to have you here!

---

### Post by TheFu on 2023-01-05
Below are 3 different rdiff-backup commands:

Here's a minimal rdiff-backup command to do local backups:
```
sudo  rdiff-backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --include /usr/local --include /etc  --include /root  --include /home \
        --exclude '**'   /       /Backups/

```

Here's a minimal rdiff-backup command to "push" backups to a {remote-machine} using an account backup5492 which is configured for root-equiv privileges and has ssh-keys setup:
```
sudo  rdiff-backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --include /usr/local --include /etc --include /root --include /home \
        --exclude '**'   /  backup5492@{remote-machine}::/Backups/{remote-machine}

```

Here's a minimal rdiff-backup command to "pull" backups from a {remote-machine} using an account backup5492 which is configured for root-equiv privileges and has ssh-keys setup:
```
sudo  rdiff-backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --include /usr/local --include /etc --include /root --include /home \
        --exclude '**'   backup5492@{remote-machine}::/ \
        /Backups/{remote-machine}

```

I use the last one, because "pulled" backups are more secure.  Also, the --include locations in my version are for a read-only mounted snapshot, but to keep things clear, I've left all that out of the commands above.

I've also left out the commands that gather system information and put it into /root/backup/ for each backup client system.  Here's a directory listing just to provide some ideas of the types of information gathered daily, before the backups occur:
```
# ls /root/backup/
apt-mark.auto    crontab.root      inxi.txt       pvdisplay.txt
apt-mark.manual  crontab.www-data  lsblk.txt      pvs.txt
blkid.txt        df.txt            lshw.list      SYSTEM-NOTES
cpan.list        dpkg.list         lvdisplay.txt  vgdisplay.txt
crontab.tf       gem.list          lvs.txt        vgs.txt
crontab.munin    inxi-2021-10-24   parted.txt
```

YMMV. What you deem important to have will likely be different.  The most important things are the 
a) manually installed package lists (apt-mark.manual) 
b) the storage information in pvs, vgs, lvs and parted files
c) crontabs for specific users that aren't in /etc/

From these tiny text files, under 300Kb, all sorts of very important system data is available which can be used to recover from tiny issues or huge everything is gone issues.

Whenever I post and there's something in {}, that means you are expected to modify that for your system.

If you don't do anything else, do the first command at the top.  You'll have versioned backups for the most important file system areas.  Just ensure that the backup storage with ext4 file system is mounted to /Backups/ before running. This needs to be a separate storage device.  Since 2TB external USB HDDs are $45 or less, there's really little excuse NOT to do this.

---

### Post by #&amp;thj^% on 2023-01-06
Very close to mine. Thanks for adding a little more to your rdiff method.
Can I mention a need for ssh keys for remote back-ups.
A good example, Create the keys:
```

cd /backup
ssh-keygen -t rsa
```
The Info provided in this thread should get most folks going.

---

### Post by TheFu on 2023-01-06
Seems that quantum computers are cracking 2K RSA keys now.  Be careful if your keys aren't 4K or 8K.  For a while, it was believed that elliptical curve keys are safer. That isn't clear. Quantum computers are changing what is safe every month now.

[https://www.schneier.com/blog/archives/2023/01/breaking-rsa-with-a-quantum-computer.html](https://www.schneier.com/blog/archives/2023/01/breaking-rsa-with-a-quantum-computer.html)
[https://www.schneier.com/blog/archives/2022/02/breaking-245-bit-elliptic-curve-encryption-with-a-quantum-computer.html](https://www.schneier.com/blog/archives/2022/02/breaking-245-bit-elliptic-curve-encryption-with-a-quantum-computer.html), so perhaps elliptic curve keys have some time.

I've been using ed25519 keys for about 5 yrs.  It was a bit of a hassle and a few older systems didn't like it much.  Still, ssh-keys are 10000x safer than passwords, provided the private key is kept private. ;)

---

### Post by #&amp;thj^% on 2023-01-06
> **TheFu said:**
>  Still, ssh-keys are 10000x safer than passwords, provided the private key is kept private. ;)
+1
Thanks I left quantum computers are cracking 2K RSA keys now out it seems to generate paranoia in the forums, but since it is now mentioned, with a strong warning for very strong 4K or 8K passwd.
Humm I guess I'm going to have to study up on  ed25519 keys. Good Tip Thanks.:)

---

### Post by TheFu on 2023-01-06
> **1fallen said:**
> +1
Thanks I left quantum computers are cracking 2K RSA keys now out it seems to generate paranoia in the forums, but since it is now mentioned, with a strong warning for very strong 4K or 8K passwd.
Humm I guess I'm going to have to study up on  ed25519 keys. Good Tip Thanks.:)

2K RSA key cracking is based on the theory from China.  However, an existing IBM quantum computer is large enough to solve it.   In theory.
As for ed25519, they were moved up in the ssh-priority for types of PKI to be used a few years ago.  Basically, it comes down to 
```
   $ ssh-keygen -t ed25519
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote

```
That's it.  May be worth removing older, shorter, RSA keys.  No need to explicitly specify ~/.ssh/id_ed25519 again, ever.  Just the ssh-copy-id command, as far as I know. Heck, it may not even be required there is no RSA keys exist in the client-side ~/.ssh/ directory.  IDK.  I have different keys for different risk levels on different systems.  Then just specify the exact key in the ~/.ssh/config file for each remote system that doesn't use the defaults.  Most home users wouldn't need that, since they'd only be accessing their home system when away or traveling.

---

### Post by #&amp;thj^% on 2023-01-06
> **TheFu said:**
> Most home users wouldn't need that, since they'd only be accessing their home system when away or traveling.

But we are not just a Home user, but still agreed most won't need it.
TheFu thanks, I'm always appreciative on your tips, and for this suggestion>>"ssh-keygen -t ed25519"

---

### Post by TheFu on 2023-01-07
[https://www.theregister.com/2023/01/07/chinese_researchers_claimed_quantum_encryption/](https://www.theregister.com/2023/01/07/chinese_researchers_claimed_quantum_encryption/)
says: 
> "All told, this is one of the most actively misleading quantum computing papers I’ve seen in 25 years, and I’ve seen … many," he wrote. ®

Another quote from UT Austin:
> Late that day, on January 4, Scott Aaronson, chair of computer science at The University of Texas at Austin, and director of its Quantum Information Center, offered a rebuttal with a succinct three word review of the paper: "No. Just No."

Hook 'Em! 
[img]https://tyrannyoftradition.files.wordpress.com/2012/04/deathtongue2.jpg[/img][img]https://tyrannyoftradition.files.wordpress.com/2012/04/deathtongue3.jpg[/img]
That's Opus Croakus on rhythm tuba showing the secret devil worship sign ... along with Steve Dallas.

It appears that the predicted scalability of the method proposed doesn't really scale in that way, if I'm reading this all correct.

---

