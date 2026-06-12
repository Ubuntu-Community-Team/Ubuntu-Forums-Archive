---
title: "ZFS sync/recv incremental backup n00b question"
date: 2024-06-04
forum: General Help
---

### Post by davie1975 on 2024-06-04
Hi, 

Please excuse me for this totally n00b question. I spent about 45 minutes trawling through Oracle docs yesterday and then I came across this: [https://ubuntuforums.org/showthread.php?t=2492948&page=13](https://ubuntuforums.org/showthread.php?t=2492948&page=13)

I have now backed up my pool using this:

```
zfs snapshot -r Pool@my_backup
```

then:

```
zfs send Pool@my_backup -R | pv | zfs receive -F Pool-Backup
```

Pool-Backup is an external drive similar to the OP of that thread.

I did as the thread suggested, verified sizes etc. and I am happy the backup is good. 

What I want to know is where I go from here to increment that backup? The Oracle docs and various sites I have looked at are confusing to me.

Do I simply snap and send again?

ie:

```
zfs snapshot -r Pool@my_backup_2
```

then:

```
zfs send Pool@my_backup_2 -R | pv | zfs receive -F Pool-Backup
```


Presumably I could then delete historic snaps from the backup pool or main pool if not needed with something like:

```
zfs list -t snapshot Pool-Backup
```

then something like:

```
[COLOR=#333333][FONT=&amp]zfs destroy [/FONT][/COLOR]Pool@my_backup
```

I'm sorry if this is obvious to those that use ZFS a lot, but if I get just one command wrong it could be.... a massive headache! I am starting out here and don't want to make a massive blunder. :(

---

### Post by davie1975 on 2024-06-10
Anyone?

---

### Post by #&amp;thj^% on 2024-06-12
Snapshots are only part of a good backup strategy.

OpenZFS snapshots are, frankly, amazing. They can be taken instantaneously, capture the entire contents of one or several datasets with atomic precision, and do not negatively impact system performance like LVM snapshots do.

However, snapshots are still not a complete backup. Taking a snapshot can protect your system from human user error, and even user malice. A snapshot still cannot entirely protect your system from human administrator error, however, and it’s no protection whatsoever from administrator-level malice.

Snapshots also do not protect a system from catastrophic hardware or environmental failures, and locally stored snapshots don’t. That’s where OpenZFS snapshot replication comes in. Using OpenZFS replication, an administrator can not only preserve the local storage system’s state but replicate It to an entirely separate machine.

Note: Snapshots are only helpful if they’ve already been taken.

There are a handful of tools or applications that will aide you Sanoid, Pyznap and zc-commander are just a couple, they have their merits and short comings.

I take hourly, daily, and monthly snapshots. I keep 36 hourlies, 30 dailies, and 3 monthlies at all times. When I have more of any of these types of snapshots than policy allows—and when the oldest snapshots are as old as you’d expect them to be, when you have that many—the system automatically destroys the stale snapshots for you. (For the Two mentioned applications Sanoid, Pyznap ) zc-comander is a hands on tool. (User driven only)
[list]
Description:
[*]Policy-driven snapshot management (sanoid), dataset sending/receiving (syncoid) and snapshot searching (findoid) tools for ZFS.[/list]


In short, it’s easy to have your system automatically manage snapshots for you, which in turn makes it near-criminally irresponsible not to! :)

The sanoid snapshot system I mentioned in the last section includes a companion app, syncoid, which makes OpenZFS replication as simple as rsync. For example, to back up the entire ZFS on root system I referenced in the last section, we can use a single command: "# syncoid –r "....easy enough right?
```
Usage:
     syncoid [options]... SOURCE TARGET
     or   syncoid [options]... SOURCE [[USER]@]HOST:TARGET
     or   syncoid [options]... [[USER]@]HOST:SOURCE TARGET
     or   syncoid [options]... [[USER]@]HOST:SOURCE [[USER]@]HOST:TARGET

     SOURCE                Source ZFS dataset. Can be either local or remote
     TARGET                Target ZFS dataset. Can be either local or remote

    Options:

      --compress=FORMAT     Compresses data during transfer. Currently accepted options are gzip, pigz-fast, pigz-slow, zstd-fast, zstd-slow, lz4, xz, lzo (default) & none
      --identifier=EXTRA    Extra identifier which is included in the snapshot name. Can be used for replicating to multiple targets.
      --recursive|r         Also transfers child datasets
      --skip-parent         Skips syncing of the parent dataset. Does nothing without '--recursive' option.
      --source-bwlimit=<limit k|m|g|t>  Bandwidth limit in bytes/kbytes/etc per second on the source transfer
      --target-bwlimit=<limit k|m|g|t>  Bandwidth limit in bytes/kbytes/etc per second on the target transfer
      --mbuffer-size=VALUE  Specify the mbuffer size (default: 16M), please refer to mbuffer(1) manual page.
      --pv-options=OPTIONS  Configure how pv displays the progress bar, default '-p -t -e -r -b'
      --no-stream           Replicates using newest snapshot instead of intermediates
      --no-sync-snap        Does not create new snapshot, only transfers existing
      --keep-sync-snap      Don't destroy created sync snapshots
      --create-bookmark     Creates a zfs bookmark for the newest snapshot on the source after replication succeeds (only works with --no-sync-snap)
      --use-hold            Adds a hold to the newest snapshot on the source and target after replication succeeds and removes the hold after the next succesful replication. The hold name incldues the identifier if set. This allows for separate holds in case of multiple targets
      --preserve-recordsize Preserves the recordsize on initial sends to the target
      --preserve-properties Preserves locally set dataset properties similiar to the zfs send -p flag but this one will also work for encrypted datasets in non raw sends
      --no-rollback         Does not rollback snapshots on target (it probably requires a readonly target)
      --delete-target-snapshots With this argument snapshots which are missing on the source will be destroyed on the target. Use this if you only want to handle snapshots on the source.
      --exclude=REGEX       Exclude specific datasets which match the given regular expression. Can be specified multiple times
      --sendoptions=OPTIONS Use advanced options for zfs send (the arguments are filtered as needed), e.g. syncoid --sendoptions="Lc e" sets zfs send -L -c -e ...
      --recvoptions=OPTIONS Use advanced options for zfs receive (the arguments are filtered as needed), e.g. syncoid --recvoptions="ux recordsize o compression=lz4" sets zfs receive -u -x recordsize -o compression=lz4 ...
      --sshconfig=FILE      Specifies an ssh_config(5) file to be used
      --sshkey=FILE         Specifies a ssh key to use to connect
      --sshport=PORT        Connects to remote on a particular port
      --sshcipher|c=CIPHER  Passes CIPHER to ssh to use a particular cipher set
      --sshoption|o=OPTION  Passes OPTION to ssh for remote usage. Can be specified multiple times
      --insecure-direct-connection=IP:PORT[,IP:PORT]  WARNING: DATA IS NOT ENCRYPTED. First address pair is for connecting to the target and the second for listening at the target

      --help                Prints this helptext
      --version             Prints the version number
      --debug               Prints out a lot of additional information during a syncoid run
      --monitor-version     Currently does nothing
      --quiet               Suppresses non-error output
      --dumpsnaps           Dumps a list of snapshots during the run
      --no-command-checks   Do not check command existence before attempting transfer. Not recommended
      --no-resume           Don't use the ZFS resume feature if available
      --no-clone-handling   Don't try to recreate clones on target
      --no-privilege-elevation  Bypass the root check, for use with ZFS permission delegation

      --force-delete        Remove target datasets recursively, if there are no matching snapshots/bookmarks (also overwrites conflicting named snapshots)

```

Again snapshots are not a complete Back-up Solution.

---

### Post by davie1975 on 2024-06-14
Hi, thanks for the reply and for such detailed information. I know snaps are not backups. I have snapped my pool and already sent it to an external drive use send/recv (the backup), what I am asking is how to "top up" the backup without doing the whole lot again. Content in the main pool has changed, so I want to send this to the backup drive too.

Syncoid looks like the tool for me, so if I am not mistaken, I can just do:

```
syncoid -r Pool Pool-Backup
```

And this should just copy the changes since the last send not the whole lot again?

If it's really that simple then you've made me a very happy person! :D

---

### Post by #&amp;thj^% on 2024-06-15
Yes it is that simple, but I will warn to check to be sure they work.

That's why I keep so many dailies. Plus I back-up all my /home, but only once per day.

Today is my manual clean up day, after pruning the unwanted snaps this is a known working list:
```
 zfs list -t snapshot
NAME                                     USED  AVAIL  REFER  MOUNTPOINT
zpcachyos@6-15-2024                        0B      -    96K  -
zpcachyos/ROOT@6-15-2024                   0B      -    96K  -
zpcachyos/ROOT/cos@6-15-2024               0B      -    96K  -
zpcachyos/ROOT/cos/home@6-5-2024        5.48G      -  6.02G  -
zpcachyos/ROOT/cos/home@6-15-2024       12.4M      -  25.6G  -
zpcachyos/ROOT/cos/root@6-5-2024        3.71G      -  7.98G  -
zpcachyos/ROOT/cos/root@6-15-2024        104K      -  9.07G  -
zpcachyos/ROOT/cos/varcache@-6-15-2024     0B      -  4.93G  -
zpcachyos/ROOT/cos/varlog@6-15-2024        0B      -   524K  -

```
```
 NAME                 PROPERTY              VALUE                  SOURCE                &#9474;  &#9474;
         zpcachyos@6-15-2024  type                  snapshot               -                     &#9474;  &#9474;
         zpcachyos@6-15-2024  creation              Sat Jun 15 13:22 2024  -                     &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  used                  0B                     -                     &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  referenced            96K                    -                     &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  compressratio         1.00x                  -                     &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  devices               on                     default               &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  exec                  on                     default               &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  setuid                on                     default               &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  createtxg             41934                  -                     &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  xattr                 sa                     inherited from zpc    &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  version               5                      -                     &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  utf8only              on                     -                     &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@6-15-2024  normalization         formD                  -                     &#9474;  &#9474;

```
A rollback:
```
&#9484;&#9472; Rollback to Snapshot &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;        &#9474;
&#9474;         &#9474;                                                                              &#9474;        &#9474;
&#9474;         &#9474;  The dataset will be rolled-back to the following snapshot:                  &#9474;        &#9474;
&#9474;         &#9474;  zpcachyos@6-15-2024                                                         &#9474;        &#9474;
&#9474;         &#9474;                                                                              &#9474;        &#9474;
&#9474;         &#9474;                     -------------------------------------                    &#9474;        &#9474;
&#9474;         &#9474;                      ENTER Confirm   Other key to cancel                     &#9474;        &#9474;
&#9474;         &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;        &#9474;
&#9474;                                                &#9474;                                                &#9474;
```
Since snapshots are important to me, I'll check the receiving "drive/streamurl" with:
```

/dozer&#55357;&#56594; 
&#9492;&#9472;> df -hT /dozer
Filesystem              Type  Size  Used Avail Use% Mounted on
zpcachyos/ROOT/cos/root zfs   410G   35G  376G   9% /

```

Have fun, and it is a slow to learn system in total. :)

---

### Post by davie1975 on 2024-06-16
Thank you :) I really appreciate the help!

I have used syncoid, and I believe it has done the desired job. I have checked sizes, and for some recently added files and they are now present on the backup pool.

One last question, if I may? I am left with a lot of snaps such as these:

```
Pool@syncoid_ubuntu_2024-06-17:02:57:52-GMT00:00

```

I take it these can be safely removed now like any other snap? I am guessing they are part of the send/recv process when data changes whilst in progress as the size of them is quite small.

---

### Post by #&amp;thj^% on 2024-06-17
It should clear out the oldest one/s automatically.

Or if you choose to manually delete/destroy as well.....That last date is pretty recent though you show.

---

### Post by davie1975 on 2024-06-20
Brilliant thanks. I'll be having a play with this and getting up to speed with it. Many thanks :)

---

