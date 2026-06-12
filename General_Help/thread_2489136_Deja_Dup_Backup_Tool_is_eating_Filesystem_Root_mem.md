---
title: "Deja Dup Backup Tool is eating Filesystem Root memory alive. Why?"
date: 2023-07-19
forum: General Help
---

### Post by ozark_hillbilly on 2023-07-19
I do not understand a lot of things related to the Linux environment admittedly. But I cannot grasp why when
the Backups utilty Deja Dup is invoked and I backup my /Home partition to another physical hardrive partition folder
I get a warning message that Filesystem Root is dangerously low on available memory!

Why is memory being consumed on root when the backup folder is on another physical hardrrive?
How do I prevent this from happening?
Where can I look to free back up the 7 or 8 GB I had on filesystem root before running Deja Dup?

I am very leary of Deja Dup now. Lol...

update -Deja Dup did not use my other drive for some unknown reason and seems to have stuck it in root somewhere.

---

### Post by #&amp;thj^% on 2023-07-19
Just remove it then if your not going to use it.
```
sudo apt autoremove --purge deja-dup
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  deja-dup*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 1,696 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 500217 files and directories currently installed.)
Removing deja-dup (44.0-2) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1.1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.76.1-1) ...
Processing triggers for man-db (2.11.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu5) ...
(Reading database ... 499824 files and directories currently installed.)
Purging configuration files for deja-dup (44.0-2) ...

```
But I just disable it from starting:
First see where:
```
dpkg -S deja-dup-monitor
```
On XFCE4 on mine:
```
deja-dup: /usr/libexec/deja-dup/deja-dup-monitor
```
So I'll remove it via:
```
sudo rm /usr/libexec/deja-dup/deja-dup-monitor

```
And it will still work if needed.
EDIT: You set the location yourself if locally, in >>Storage location (Settings)

---

### Post by ozark_hillbilly on 2023-07-19
Yeah, I am done with Deja Dup.

Any suggestions on where to look in root for the 5 or 6 GB Deja Dup ate? I have 2 GB left and will need to
work on cleaning root up anything superfluous.
Then I will going forward just do a file copy of my /Home partition and dump it on a different drive.

---

### Post by #&amp;thj^% on 2023-07-19
> **ozark_hillbilly said:**
> Yeah, I am done with Deja Dup.

Any suggestions on where to look in root for the 5 or 6 GB Deja Dup ate? I have 2 GB left and will need to
work on cleaning root up anything superfluous.
Then I will going forward just do a file copy of my /Home partition and dump it on a different drive.

Check in Settings is where you should of set it in the first place, under "Storage location"
EDIT: I just checked and this worked for me:
```
gsettings set org.gnome.DejaDup delete-after 1
```
The 1 indicates delete all after one day.
Now you have me going down the list, you can also use:
```
duplicity remove-all-but-n-full 1 --force file:///home/username/deja-dup

```
I don't use it so mine returns:
```
duplicity remove-all-but-n-full 1 --force file:///home/username/deja-dup
gpg: WARNING: unsafe permissions on homedir '/home/me/.gnupg'
Giving up after 1 attempts. FileNotFoundError: No such file or directory

```

---

### Post by ozark_hillbilly on 2023-07-19
There is nothing there in the designated storage folder location.
Stupid question 1::::::::

Does /media/Ed/ take memory away from root when data is transferred into any device/partition listed under /media/Ed.
I know /media is listed under root but I cannot get my head around why I lose memory in root if the data is going on
a different drive/partition.
I can't even think straight right now after lsoing all that space on my filesystem root.

---

### Post by #&amp;thj^% on 2023-07-19
> **ozark_hillbilly said:**
> There is nothing there in the designated storage folder location.
Stupid question 1::::::::

Does /media/Ed/ take memory away from root when data is transferred into any device/partition listed under /media/Ed.
I know /media is listed under root but I cannot get my head around why I lose memory in root if the data is going on
a different drive/partition.
I can't even think straight right now after lsoing all that space on my filesystem root.
One of us needs to keep our head...lol
show this please:
```
sudo -s cd /root && ls

```
EDIT: LOL My goodness it took me a beat  to find your other post: [https://ubuntuforums.org/showthread.php?t=2489119&p=14151440#post14151440](https://ubuntuforums.org/showthread.php?t=2489119&p=14151440#post14151440)
So that's where you will find your back-ups >>> /media/ed and it looks to have a bunch there.
So lets have a peek there as well, again please show:
```
cd  /media/ed && ls
```

---

### Post by ozark_hillbilly on 2023-07-19
I deleted Deja Dup. It was not friendly.
I ended up installing Bleachbit and rolled the dice on having it clean up my system.
It created 14GB of free space and now my filesystem root is only 46% full. Yay!!!

I still do not understand why my 78GB hard drive partition is having  a "1" added to the UUID mount location after being mounted. It is a mystery 
I probably will not resolve.

---

### Post by ozark_hillbilly on 2023-07-19
Here is result of the two command lines you requested:

ed@ed-G41MT-S2PT:~$ sudo -s cd /root && ls

[sudo] password for ed:
 
'Dell Notebook & Windows Desktop'   Music
 Desktop                           
'Perfect Backup Jobs'
 Diagram8.dia.autosave              
Pictures
 Documents                          
Propane_Sensor
 Downloads                        
 'Read Resistance'
 get-pip.py                        
 sketchbook
 get-pip.py.1                     
  snap
 get-pip.py.2                       
sudo
 get-pip.py.3                       
Sync
 Guns                               
Templates
 hs_err_pid11558.log               
'Tuner App final install'
'Linux-Windows Sketch Transfers'    
Videos
"Mom's Safe"                       
'Windows Desktop PC Files'

ed@ed-G41MT-S2PT:~$ cd  /media/ed && ls

04e8bdce-0446-4973-96c5-7cd2afd52d5d
  
04e8bdce-0446-4973-96c5-7cd2afd52d5d1

ed@ed-G41MT-S

I attached a screenshot as well. You notice the two identical partitions listed with one having an extra "1". ????

I added a screenshot of the DISKS showing that partition in question.

---

### Post by Tadaen_Sylvermane on 2023-07-19
I consider deja dup to be the friendliest thing there is. But from the sound of it you didn't have your backup mounting properly. Don't blame deja. For what it's worth though I run a duplicity script and just use Deja-dup as a frontend for file restoration as needed. Quite simple and convenient.

---

### Post by #&amp;thj^% on 2023-07-19
> **ozark_hillbilly said:**
> 
ed@ed-G41MT-S2PT:~$ cd  /media/ed && ls

04e8bdce-0446-4973-96c5-7cd2afd52d5d
  
04e8bdce-0446-4973-96c5-7cd2afd52d5d1


If you truly uninstalled deja-dup then those won't be needed anymore, but if you want to keep them for backup sake, and providing they are true and tested working backups, then just move them of to another storage drive.

---

### Post by ozark_hillbilly on 2023-07-19
[QUOTE=Tadaen_Sylvermane;14151464] But from the sound of it you didn't have your backup mounting properly. Don't blame deja. /QUOTE]

I have used Deja Dup before without incident. Not sure what is going with the mounting. I selected  the required folder on the partition I wanted it to be backed up to and cranked it up.
It completed the backup successfully according to the utility's message but ate up about 6GB of root in the process. Dunno. I can use a different path to storing my data.

---

### Post by ozark_hillbilly on 2023-07-19
> **1fallen said:**
> ...but if you want to keep them for backup sake, and providing they are true and tested working backups, then just move them of to another storage drive.

Now I am very confused. Those /media/Ed UUIDs listed are not backups but drive partitions unless I am losing my marbles and having another senior moment. Lol

---

### Post by Tadaen_Sylvermane on 2023-07-19
I'd suggest setting a static mount in the /etc/fstab. /media mounts aren't the most reliable, at least in my experience.
This is how my drive is set.

```
UUID=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx /.localbackups ext4 defaults,noauto,x-systemd.automount,x-systemd.idle-timeout=30 0 0
```

---

