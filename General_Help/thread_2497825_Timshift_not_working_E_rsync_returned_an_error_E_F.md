---
title: "Timshift not working: E: rsync returned an error E: Failed to create new snapshot"
date: 2024-05-19
forum: General Help
---

### Post by alexlomba87 on 2024-05-19
Ubuntu 24.04 LTS Fresh install. Server, only from terminal.


Timeshift used for the absolute first time on a clean install with nothing else installed prior, using the following command:
[FONT=courier new]sudo timeshift --create --comments "First backup" --tags B[/FONT]

Timeshift doesn't work, it throws `E: rsync returned an error E: Failed to create new snapshot`.

I have already read several posts suggesting to use a PPA version of timeshift instead. So I tried:

1. Uninstalled and purged existing timeshift and rsync with `sudo apt autoremove timeshift --purge` and `sudo apt autoremove rsync --purge`
2. Installed Timesync from the PPA version with `sudo add-apt-repository ppa:teejee2008/timeshift && sudo apt update`, then `sudo apt-get install timeshift`


Issue still there. 
Still getting `E: rsync returned an error E: Failed to create new snapshot`.

Any tips?

---

### Post by #&amp;thj^% on 2024-05-19
What version of rsync?
```
rsync --version

```

---

### Post by #&amp;thj^% on 2024-05-19
What you should try is again remove both "timeshift" and "rsync" with the same code you show in your first post#1
Then downgrade rsync:
```

sudo apt-get install rsync=3.2.3-8ubuntu3
```
Put rsync on hold:
To keep it workling:
```

sudo apt-mark hold rsync
```
Then reinstall Timeshift.

---

### Post by alexlomba87 on 2024-05-20
After having purged the system from both timeshift and rsync, I installed rysnc 3.2.3, and put in on hold, as mentioned. Then when I go and install timeshift, I get an incompatibility (see below).

Does anyone know which version of timeshift can I use with rsync 3.2.3. and where can I find it?

Also, just running [COLOR=#E8E6E3][FONT=&quot]sudo apt-get install rsync=3.2.3-8ubuntu3 [/FONT][/COLOR] would not work for me, I had to find that version and compile it from source (here: [COLOR=#CE9178][FONT=Consolas]https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/rsync/3.2.3-8ubuntu3/rsync_3.2.3.orig.tar.gz)[/FONT][/COLOR]
Is there an easier way to find it?


[FONT=courier new]$ sudo apt-get install timeshift[/FONT]
[FONT=courier new]Reading package lists... Done[/FONT]
[FONT=courier new]Building dependency tree... Done[/FONT]
[FONT=courier new]Reading state information... Done[/FONT]
[FONT=courier new]Some packages could not be installed. This may mean that you have[/FONT]
[FONT=courier new]requested an impossible situation or if you are using the unstable[/FONT]
[FONT=courier new]distribution that some required packages have not yet been created[/FONT]
[FONT=courier new]or been moved out of Incoming.[/FONT]
[FONT=courier new]The following information may help to resolve the situation:[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]The following packages have unmet dependencies:[/FONT]
[FONT=courier new] timeshift : Depends: rsync but it is not going to be installed[/FONT]
[FONT=courier new]E: Unable to correct problems, you have held broken packages.
[/FONT]

---

### Post by #&amp;thj^% on 2024-05-20
This needs to be brought to the attention of the bug-team then.
To fix your broken install please try:
```
sudo apt -f install
```
Followed by:
```
sudo apt autoremove --purge

```

I'm unable to test Timeshift here on a ZFS root, not supported. Also I'm on 24.10 Testing ATM

But i would in your case file a bug report on Timeshift.

---

### Post by #&amp;thj^% on 2024-05-20
After I re-read your first post and the command you used, You may need to use the Timeshift GUI to setup first. The Timeshift Wizzard.
First tell apt to release the hold on rsync:
```
sudo apt-mark unhold rsync
```
```
sudo timeshift-launcher
```

This is still on 24.10 but with a LVM2/ext4 format. (NO ZFS-Root this time)

Sorry I misunderstood you are on Noble(24.04) and not Jammy(22.04)

Mine worked on 24.10 and 24.04 with no outside sources needed. 24.10 will become 24.04.1 after it's release. 
```
 apt policy timeshift rsync
timeshift:
  Installed: 24.01.1-1build2
  Candidate: 24.01.1-1build2
  Version table:
 *** 24.01.1-1build2 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status
rsync:
  Installed: 3.2.7-1ubuntu1
  Candidate: 3.2.7-1ubuntu1
  Version table:
     3.3.0-1 100
        100 http://us.archive.ubuntu.com/ubuntu oracular-proposed/main amd64 Packages
 *** 3.2.7-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```
A good snapshot was indeed successful:
```
 sudo timeshift --list
Mounted '/dev/dm-1' at '/run/timeshift/35137/backup'
Device : /dev/dm-1
UUID   : ff1bc2ff-170d-4e06-9b8d-2a385faae98e
Path   : /run/timeshift/35137/backup
Mode   : RSYNC
Status : OK
1 snapshots, 170.3 GB free

Num     Name                 Tags  Description  
------------------------------------------------------------------------------
0    >  2024-05-20_10-54-27  O                  

```
And the same command you used in your first post:
```
sudo timeshift --create --comments "First backup" --tags B
[sudo] password for me: 
Mounted '/dev/dm-1' at '/run/timeshift/25722/backup'
------------------------------------------------------------------------------
Creating new snapshot...(RSYNC)
Saving to device: /dev/dm-1, mounted at path: /run/timeshift/25722/backup
Linking from snapshot: 2024-05-23_11-00-01
Syncing files with rsync...
Created control file: /run/timeshift/25722/backup/timeshift/snapshots/2024-05-23_11-07-46/info.json
RSYNC Snapshot saved successfully (18s)
Tagged snapshot '2024-05-23_11-07-46': ondemand
------------------------------------------------------------------------------

```

---

### Post by alexlomba87 on 2024-06-04
> [COLOR=#000000]You may need to use the Timeshift GUI to setup first. The Timeshift Wizzard.[/COLOR]

I really would like to avoid installing any GUI on my Ubuntu Server. Also, I can't see why a GUI would be required.

---

