---
title: "Boots to Black Screen - Xubuntu"
date: 2014-12-22
forum: General Help
---

### Post by paschalleddie1 on 2014-12-22
After attempting to update an application I ignored a warning and proceeded with the update. Now when starting, Grub loads and I get the Xubuntu flash display before the screen goes black. When I boot to the Recovery Menu and run 'dpkg' I get the following error:[INDENT]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
[/INDENT]

When I manually enter 'dpkg --configure -a', I get the following error:
[INDENT]dpkg: error: unable to access dpkg status area: read-only file system.
[/INDENT]

I am a novice Linux user and have tried various solutions to no avail. Any help would be greatly appreciated and thanks in advance. I hope I can salvage things and not have to reinstall OS.

Thanks

---

### Post by r.stiltskin on 2014-12-22
You need superuser status to install, remove or reconfigure your packages, so make it
```
sudo dpkg --configure -a
```

---

### Post by paschalleddie1 on 2014-12-22
I am in the Recovery Menu and entering 'sudo dpkg --configure -a' returns:

dpkg: error: unable to access dpkg status area: Read-only file system

---

### Post by r.stiltskin on 2014-12-23
Try deleting the dpkg file lock:
```
sudo rm /var/lib/dpkg/lock
```
and then run 'sudo dpkg --configure -a' again.

---

### Post by Bashing-om on 2014-12-23
paschalleddie1; Hello;

Welcome to the forum .

Yes, with time effort and a liveDVD, the install is always salvageable .
As to the present circumstance:
> 
I am in the Recovery Menu

By default, the file system(s) are mounted in a read only mode in recovery. at your direction, because you know what you are doing, you mount the file system as read/write with the terminal command:
```

mount -o remount rw /

```

OK, now you are at a root terminal, and have write access. Let's see what it will take to fix the system:
Now try terminal command:
```

dpkg --configure -a

```
You are root at that root terminal, so 'sudo' is not required to elevate the user privileges .

What is the result of dpkg -- configure ? Does the system repair it's self ? No, any hints to where the problem is ? If still errors, post back those errors.

Maybe we find a way to boot to the desk top and seek solutions via other means.

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-23
Re: r.stiltskin:

rm: cannot remove 'var/lib/dpkg/lock': read-only file system

---

### Post by paschalleddie1 on 2014-12-23
Re: Bashing-om

After entering 'mount -o remount rw /' @ root Recovery Menu, 'dpkg --configure -a' command returns the following:[INDENT]
dpkg: error: failed to open package info file '/var/lib/dpkg/status' for reading: No such file or directory
[/INDENT]

---

### Post by Bashing-om on 2014-12-23
paschalleddie1; Humm;

This:
> 
dpkg: error: failed to open package info file '/var/lib/dpkg/status' for reading: No such file or directory

does not bode well for the home team;

From that root prompt in the recovery mode, what returns from :
```

ls -al /var/lib/dpkg/status

```

[INDENT][INDENT]batten down for heavy rolls ?
[/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-23
ls -al /var/lib/dpkg/status returns:

ls: cannot access /var/lib/dpkg/status: No such file or directory
[INDENT][/INDENT]
[INDENT][/INDENT]

---

### Post by Bashing-om on 2014-12-23
paschalleddie1; Fingers crossed:


What about a backup file. Is it present ?
```

ls -al /var/lib/dpkg/status-old

```

That file (status) is mandatory, no getting around it .

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-23
Yes:
[INDENT]
-rw-r--r-- 1 root root 1952490 Dec 21 17:39 /var/lib/dpkg/status-old
[/INDENT]

---

### Post by Bashing-om on 2014-12-23
paschalleddie1; ( wiping some sweat off ) . whehh !

OK, we can get back in the saddle.
From that root prompt in the recovery console, mount the file system as before read write.
Now let's replace that file !
```

cp -p /var/lib/dpkg/status-old /var/lib/dpkg/status

```

Next we need to know what condition the condition is in:
```

apt-get update
apt-get upgrade
apt-get -f install

```
IF these 3 commands run clean, we see what it will take to boot ya to a desk top ( you do have a GUI installed, no ? ) .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-23
One more intermediate hurdle:

cp: cannot create regular file 'var/lib/dpkg/status': No space left on device

---

### Post by r.stiltskin on 2014-12-23
Well at least now you may have discovered the underlying cause of all this grief -- out of space on your disk?

You can check this by running
```
df -h
```

---

### Post by Bashing-om on 2014-12-23
paschalleddie1; 

Yepper +1 r.stiltskin.

Small steps
[INDENT][INDENT]get's to a journey's end too
[/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-23
df -h: cannot read table of mounted file systems

---

### Post by Bashing-om on 2014-12-23
paschalleddie1; Ouchh !

OK, back out of the root terminal
```

exit

```

Reboot into the liveDVD(USB) to terminal:

What have we for results:
```

sudo fdisk -lu
sudo parted -l
df -h
df -i

```
[INDENT][INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-23
xubuntu@xubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c7e0c7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       64259       32098+  de  Dell Utility
/dev/sda2   *       64260    56218175    28076958    7  HPFS/NTFS/exFAT
/dev/sda3        56219646    78139391    10959873    f  W95 Ext'd (LBA)
/dev/sda5        56219648    76570623    10175488   83  Linux
/dev/sda6        76572672    78139391      783360   82  Linux swap / Solaris
xubuntu@xubuntu:~$ sudo parted -l
Model: ATA HITACHI_DK23EB-4 (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  32.9MB  32.9MB  primary   fat16           diag
 2      32.9MB  28.8GB  28.8GB  primary   ntfs            boot
 3      28.8GB  40.0GB  11.2GB  extended                  lba
 5      28.8GB  39.2GB  10.4GB  logical   ext4
 6      39.2GB  40.0GB  802MB   logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: HL-DT-ST RW/DVD GCC-4240N (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      131kB  3842MB  3842MB  primary               boot, hidden


xubuntu@xubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            375M   46M  329M  13% /
udev            364M  4.0K  364M   1% /dev
tmpfs            75M  932K   74M   2% /run
/dev/sr0        916M  916M     0 100% /cdrom
/dev/loop0      884M  884M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           375M  8.0K  375M   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            375M   80K  375M   1% /run/shm
none            100M   24K  100M   1% /run/user
xubuntu@xubuntu:~$ df -i
Filesystem     Inodes  IUsed IFree IUse% Mounted on
/cow            95794    633 95161    1% /
udev            93121    454 92667    1% /dev
tmpfs           95794    437 95357    1% /run
/dev/sr0            0      0     0     - /cdrom
/dev/loop0     164275 164275     0  100% /rofs
none            95794      2 95792    1% /sys/fs/cgroup
tmpfs           95794      9 95785    1% /tmp
none            95794      2 95792    1% /run/lock
none            95794      5 95789    1% /run/shm
none            95794     20 95774    1% /run/user
xubuntu@xubuntu:~$

---

### Post by Bashing-om on 2014-12-23
paschalleddie1; Welp ...

We are looking at a tiny install of 10.4 Gigs. Not much breathing room there to start with.
From the liveDVD I am not able to determine the cause of "No space left on device" .

let's try and boot to the install proper - getting away from that root terminal - find the reason why.

Reboot to the grub boot menu,
With the latest ubuntu kernel selected ( asterisk on the left) press the 'e' key for edit mode ->
Boot options screen, here arrow down to the line similar to " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " arrow across to "quiet splash" and replace these terms with "text" - with out the quotes;
Key combo ctl+x to continue the boot process to the TTY1 terminal.

At this terminal log in with your user name and pass word [ When pass word is entered there is no response to the screen - normal - a security measure ];
enter your password blindly and hit enter key.

Now what returns from 
```

df -h
df -i
cd /
sudo du -sx * | sort -n
cd

```
the 'du' command will take some time to complete, patience. You may safely ignore the outputs similar " du: cannot access ‘proc/3722/task/3722/fd/4’: No such file or directory "

it's 'buntu; many paths to an end

[INDENT][INDENT][INDENT][INDENT]this is but one
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-23
**df -h**[INDENT]df: cannot read table of mounted file systems

[/INDENT]
**df -i**[INDENT]df: cannot read table of mounted file systems

[/INDENT]
**sudo du -sx * | sort -n**[INDENT]sudo: unable to open /var/lib/sudo/eddietty1: No such file or directory cd
du: cannot access 'proc/1432/task/1432/fd/3': No such file or directory
du: cannot access 'proc/1432/task/1432/fdinfo/3': No such file or directory
du: cannot access 'proc/1432/fd/3': No such file or directory
du: cannot access 'proc/1432/fdinfo/3': No such file or directory
0            initrd.img
0            initrd.img.old
0            proc
0            sys
0            vmlinuz
0            vmlinuz.old
4            cdrom
4            dev
4            mnt
4            opt
4            srv
8            Desktop
8             tmp
16           lost+found
20           media
184         root
972         run
9472       bin
12000     sbin
23460     etc
200912   boot
513944   var
1100924 lib
1554628 home
3683440 usr
[/INDENT]

---

### Post by Bashing-om on 2014-12-23
paschalleddie1; UMMPHHH ...

Think'n ...
This is a bother:
> 
df: cannot read table of mounted file systems


This is of concern:
> 
cp: cannot create regular file 'var/lib/dpkg/status': 


So, we best not rely on the package manager to get us out of this. Take care we do not dig a hole manually that will be tough to crawl out of later.

It is /boot that looks to be the fullest, however we do have the "out of space" writing to 'var' . It is a safe thing to manually remove old log files.- keep in mind we may want to look at the files and make sure we do not have a run-a-muck condition writing to the log in profussion !
Let's remove a few and see if then we can copy " var/lib/dpkg/status ? into place;
I want you to remove ALL OLD log files that end in .gz ( archieved), for example, do:
```

sudo rm /var/log/dpkg.log.4.gz
sudo rm /var/log/dmesg.6.gz
sudo rm /var/log/syslog.3.gz

```
keeping the say .1.gz and .2.gz files (for reference).

Once we have some operating head room, and the package manager stable, we can then do some general house cleaning.
[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-23
All returned: No such file or directory.

I'm ready to throw in the towel. I greatly appreciate your support and effort in this matter but it appears that recovery isn't in the cards. I should have sought advice first but I tried to follow various posting and that in hindsight was a mistake. I'm a do it yourself-er, sometimes to a fault.

Thank you very much again for your time and help!

---

### Post by Bashing-om on 2014-12-23
paschalleddie1; Hey;

The nuclear solution does work in all cases, and admittedly can be the easiest.
But but .. kinda soon to throw in the towel.

What returns from:
```

ls -al /var/log/

```

Besides, look at all the fun we are having , and have not gone to jail !

[INDENT][INDENT]the care and feeding of your 'buntu
[/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-23
Too much information to transcribe. How do I save to a file?

---

### Post by r.stiltskin on 2014-12-23
Whenever your command writes output to the screen you can use > to redirect the output to a file, so
```
ls -al /var/log/ > log_directory.txt
```
will write the output to the file "log_directory.txt".  Of course you could name that output file whatever you want.  (If a file with that name already existed it would be overwritten.)

---

### Post by Bashing-om on 2014-12-24
paschalleddie1; Hey, making progress, huh.

I do not really need to see the output, just so there is a lot of output.
For comparison, here is mine:
```

sysop@1404mini:~$ ls -al /var/log/
total 3708
drwxrwxr-x  9 root   syslog   4096 Dec 23 07:51 .
drwxr-xr-x 13 root   root     4096 Mar 13  2014 ..
-rw-r--r--  1 root   root     1145 Dec 10 12:29 alternatives.log
-rw-r--r--  1 root   root     2132 Nov 26 12:19 alternatives.log.1
-rw-r--r--  1 root   root      167 Feb 20  2014 alternatives.log.10.gz
-rw-r--r--  1 root   root      146 Jan 16  2014 alternatives.log.11.gz
-rw-r--r--  1 root   root     1513 Dec 22  2013 alternatives.log.12.gz
-rw-r--r--  1 root   root      335 Oct 28 10:25 alternatives.log.2.gz
-rw-r--r--  1 root   root      310 Sep 27 10:32 alternatives.log.3.gz
-rw-r--r--  1 root   root      168 Aug 26 09:55 alternatives.log.4.gz
-rw-r--r--  1 root   root     1725 Jul 22 12:31 alternatives.log.5.gz
-rw-r--r--  1 root   root      146 Jun 13  2014 alternatives.log.6.gz
-rw-r--r--  1 root   root      203 May 22  2014 alternatives.log.7.gz
-rw-r--r--  1 root   root      192 Apr 30  2014 alternatives.log.8.gz
-rw-r--r--  1 root   root      218 Mar 25  2014 alternatives.log.9.gz
-rw-r-----  1 root   adm         0 Apr 20  2014 apport.log
-rw-r-----  1 root   adm       555 Apr 19  2014 apport.log.1
drwxr-xr-x  2 root   root     4096 Dec  1 13:33 apt
-rw-r--r--  1 root   root        0 Jun  1  2014 aptitude
-rw-r--r--  1 root   root      210 May  7  2014 aptitude.1.gz
-rw-r-----  1 syslog adm     18960 Dec 23 21:17 auth.log
-rw-r-----  1 syslog adm     31714 Dec 21 12:49 auth.log.1
-rw-r-----  1 syslog adm      2781 Dec 14 11:46 auth.log.2.gz
-rw-r-----  1 syslog adm      3611 Dec  8 13:11 auth.log.3.gz
-rw-r-----  1 syslog adm      3074 Nov 30 15:06 auth.log.4.gz
-rw-r-----  1 root   adm        31 May 19  2013 boot
-rw-r--r--  1 root   root     4251 Dec 23 07:46 boot.log
-rw-rw----  1 root   utmp      768 Dec 21 16:26 btmp
-rw-rw----  1 root   utmp     1152 Nov 24 09:22 btmp.1
drwxr-xr-x  2 root   root     4096 Dec  1  2013 ConsoleKit
drwxr-xr-x  5 root   root     4096 Jul  6 13:43 dist-upgrade
-rw-r-----  1 root   adm     61601 Dec 23 07:46 dmesg
-rw-r-----  1 root   adm     61601 Dec 22 12:47 dmesg.0
-rw-r-----  1 root   adm     16469 Dec 21 16:26 dmesg.1.gz
-rw-r-----  1 root   adm     16322 Dec 21 16:21 dmesg.2.gz
-rw-r-----  1 root   adm     16425 Dec 21 12:49 dmesg.3.gz
-rw-r-----  1 root   adm     16356 Dec 20 11:18 dmesg.4.gz
-rw-r--r--  1 root   root    49904 Dec 22 12:49 dpkg.log
-rw-r--r--  1 root   root    87725 Dec  1 13:27 dpkg.log.1
-rw-r--r--  1 root   root     1748 Feb 26  2014 dpkg.log.10.gz
-rw-r--r--  1 root   root     2502 Jan 26  2014 dpkg.log.11.gz
-rw-r--r--  1 root   root    50875 Dec 23  2013 dpkg.log.12.gz
-rw-r--r--  1 root   root     5365 Oct 31 12:02 dpkg.log.2.gz
-rw-r--r--  1 root   root     5775 Oct  1 09:26 dpkg.log.3.gz
-rw-r--r--  1 root   root     5222 Aug 30 12:04 dpkg.log.4.gz
-rw-r--r--  1 root   root    59142 Jul 30 11:05 dpkg.log.5.gz
-rw-r--r--  1 root   root     3852 Jul  1 12:42 dpkg.log.6.gz
-rw-r--r--  1 root   root     2353 May 28  2014 dpkg.log.7.gz
-rw-r--r--  1 root   root     6348 Apr 30  2014 dpkg.log.8.gz
-rw-r--r--  1 root   root     5331 Apr  2  2014 dpkg.log.9.gz
-rw-r--r--  1 root   root    32032 May 19  2013 faillog
-rw-r--r--  1 root   root     1237 Jul  6 13:43 fontconfig.log
drwxr-xr-x  2 root   root     4096 May 19  2013 fsck
drwxr-xr-x  3 root   root     4096 May 19  2013 installer
-rw-r-----  1 syslog adm    369566 Dec 23 07:46 kern.log
-rw-r-----  1 syslog adm    641779 Dec 21 12:49 kern.log.1
-rw-r-----  1 syslog adm    153849 Dec 14 11:45 kern.log.2.gz
-rw-r-----  1 syslog adm    204889 Dec  8 13:08 kern.log.3.gz
-rw-r-----  1 syslog adm    189473 Nov 30 15:05 kern.log.4.gz
-rw-rw-r--  1 root   utmp   292292 Dec 23 07:46 lastlog
-rw-r-----  1 syslog adm         0 May 19  2013 mail.err
-rw-r-----  1 syslog adm         0 May 19  2013 mail.log
drwxr-xr-x  2 root   root     4096 May 19  2013 news
-rw-r--r--  1 root   root    56742 Dec 23 07:47 pm-powersave.log
-rw-r--r--  1 root   root    82053 Dec  1 13:29 pm-powersave.log.1
-rw-r--r--  1 root   root     1069 Nov  1 12:19 pm-powersave.log.2.gz
-rw-r--r--  1 root   root      980 Oct  1 09:25 pm-powersave.log.3.gz
-rw-r--r--  1 root   root      972 Sep  1 13:27 pm-powersave.log.4.gz
-rw-r--r--  1 root   root        0 May  1  2014 pm-suspend.log
-rw-r--r--  1 root   root     4547 Apr 16  2014 pm-suspend.log.1
-rw-r-----  1 syslog adm      1633 Dec 23 21:17 syslog
-rw-r-----  1 syslog adm     97855 Dec 23 07:51 syslog.1
-rw-r-----  1 syslog adm     54868 Dec 22 12:52 syslog.2.gz
-rw-r-----  1 syslog adm     18795 Dec 21 12:54 syslog.3.gz
-rw-r-----  1 syslog adm     18693 Dec 20 11:23 syslog.4.gz
-rw-r-----  1 syslog adm     18553 Dec 19 11:27 syslog.5.gz
-rw-r-----  1 syslog adm     18718 Dec 18 14:33 syslog.6.gz
-rw-r-----  1 syslog adm     18598 Dec 17 12:00 syslog.7.gz
-rw-r--r--  1 root   root   288972 Dec 23 07:47 udev
-rw-r-----  1 syslog adm         0 May 19  2013 ufw.log
drwxr-xr-x  2 root   root    12288 Dec 23 07:51 upstart
-rw-rw-r--  1 root   utmp   236928 Dec 23 09:02 wtmp
-rw-rw-r--  1 root   utmp   340608 Dec  1 13:29 wtmp.1
-rw-r--r--  1 root   root    51052 Dec 23 07:47 Xorg.0.log
-rw-r--r--  1 root   root    51494 Dec 22 23:02 Xorg.0.log.old
-rw-r--r--  1 root   root    50930 May 24  2013 Xorg.1.log
sysop@1404mini:~$

```

OK, any line starting with a '-' is a file and can be removed. We want to remove a bunch of these .gz files to gain some operating head room.
for instance, this one:
-rw-r--r--  1 root   root      167 Feb 20  2014 alternatives.log.10.gz
the file name is:
alternatives.log.10.gz
it's path (location) is '/var/log'.
To remove that file in terminal do:
```

sudo rm /var/log/alternatives.log.10.gz

```
Your objective is to look at the listing for your output and similarly remove your files.
In terminal is a history, once a command is executed it is in that history and one can recall a command and edit it to execute a slightly different one.
such that with the arrow key the history command " sudo rm /var/log/alternatives.log.10.gz " is pulled up, by editing '10' to '9' and hitting the enter key, file " /var/log/alternatives.log.9.gz " is also removed. Repeat this sequence as often as needed. It will not take long at all to get us some head room .

And yes, one can craft up a handy dandy bash script to do all this in one pass, this method of manually removing ONE file at a time will insure the job gets done right, at your skill level and understanding.

Once we have that operating head room we try and copy the status file back in place, repair the package manager, and repair the file system
.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-12-24
paschalleddie1; r.stiltskin;

I am done for this session.

Lord willing We pick this back up in our AM.

[INDENT][INDENT]Nighty nite
[/INDENT][/INDENT]

---

### Post by prolaiot0 on 2014-12-24
I'm ready to throw in the towel. I greatly appreciate your support and  effort in this matter but it appears that recovery isn't in the cards. I  should have sought advice first but I tried to follow various posting  and that in hindsight was a mistake. I'm a do it yourself-er, sometimes  to a fault.

Thank you very much again for your time and help!
Minded
read more pls
[ubuntuforums.org]("http://www.scoresite.org/d/ubuntuforums.org")

---

### Post by paschalleddie1 on 2014-12-24
Bad news, no .gz listed in output to delete.

---

### Post by r.stiltskin on 2014-12-24
Strange -- did you just install this Ubuntu in the last couple of days?

Anyway, I'm not accustomed to working in the Recovery terminal, and it's hard to read some of the outputs you posted, and it's inefficient for you to post complete outputs by transcribing them so let's try something else.  We can both learn in the process (hope it works).  Please reboot normally and when it's done, presumably still at a black screen, press Ctrl-Alt-F2 simultaneously and that should bring you to an ordinary, fullscreen terminal login.  Log into your normal user account.  (You'll have to enter your username first, and then your password.)

Next, I believe the standard Ubuntu Desktop installation includes a Python script called pastebinit, which lets you post the output from terminal commands directly to the Ubuntu pastebin site, where we can see it exactly, without typos, etc.  Each time you pipe a command to pastebinit, it gives you the url where the output can be viewed.  That will look like "http:// paste.ubuntu.com/ ???????.  Instead of ??????? you will see a 7 digit number which identifies the actual web page.  So, after you're logged in to the terminal, try these two commands:
df -h | pastebinit
ls -al /var/log/ | pastebinit
and post here the urls returned by pastebinit for those outputs and let's see if we can work out what's going on there.

---

### Post by paschalleddie1 on 2014-12-24
**df -h | pastebinit returns:**

df: cannot read table of mounted file systems
You are trying to send an empty document, exiting

[B]
ls -al/var/log | pastebinit returns:[/B]

ls: invalid option -- '/'
try 'ls --help' for more information.
You are trying to send an empty document, exiting

---

### Post by r.stiltskin on 2014-12-24
It's beginning to look (judging by the output from df) as if you somehow trashed that entire file system, but let's continue a bit further.

The second one happened because you didn't type a space between -al and /var/log.  Just so you understand, ls is the command which produces a listing of the contents of a directory.  -al are "options" passed to the ls command.  The 'a' tells it to list all, including hidden, files.  the 'l' tells it to give a detailed listing, including file permissions and dates.  /var/log tells it which directory we want listed.  So it's 
ls [space] -al [space] /var/log
but obviously don't type "[space]".

Please try again
ls -al /var/log | pastebinit

And also, let's see the output from 
ls  -al  /  |  pastebinit

Be sure to put spaces before and after -al and before and after |

---

### Post by r.stiltskin on 2014-12-24
By the way, you did reboot and log into the terminal as I described in post #30, yes?

Also, does the file /etc/mtab exist?  You can check by running
cat /etc/mtab

cat just writes the contents of that file (if it exists) to your screen.

---

### Post by paschalleddie1 on 2014-12-24
**Re: Reboot and log per post#30**
[LIST]
[*]Ctl-Alt-F2 after black screen did not display terminal login screen 
[*]Ctl-Alt-F2 was initiated during Xubuntu boot display to display login terminal 
[/LIST]

**df - h | pastebinit:**[INDENT]df: cannot read table of mounted file systems.
You are trying to send an empty document, exiting.
[/INDENT]
[B]
ls -al /var/log | pastebinit:[/B][INDENT][http://paste.ubuntu.com/9612387/](http://paste.ubuntu.com/9612387/)
[/INDENT]

**cat /etc/mtab:**[INDENT]No results
[/INDENT]

---

### Post by r.stiltskin on 2014-12-24
Last night I thought you said there were no .gz files in /var/log but it seems there's a bunch of them listed in the pastebin.  On the other hand they don't seem to be taking up very much space so I don't think we have to worry about them.

I don't know why you have no /etc/mtab file.  I thought that file was written every time you boot.  You can try to create it by running ```
[COLOR="#D3D3D3"]sudo grep -v rootfs /proc/mounts > /etc/mtab [/COLOR]#ignore this; see below
```
Edit: the above command was posted in error.  Correct command is in post #38

Then assuming that works, try again
```
df -h | pastebinit
```

---

### Post by Bashing-om on 2014-12-24
paschalleddie1; r.stiltskin; I am Bacckkk !

@ r.stiltskin; well done, agree completely . I too want to know what in the world is going on here - if for no other reason my own edification.

@paschalleddie1l; Believe it or not, you are doing well. I do hope you are enjoying this learning experience. Do not let frustration get the better of us.

I await the outcomes of what is mounted, and IF we can delete files from the /var/log directory. Get us some head room and get this system stable.

[INDENT][INDENT]quit never got nothing done
[/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-24
There's been some concern expressed about my lack of headroom so I'm trying to borrow a few GB from Windows, hopefully that will help. 

Regarding this learning experience, to be honest, I've never received tech support that was this extensive, not even from paid support. Most tech support would have passed the buck by now and given up, blaming the problem on hardware or some other issue. I'm in it until you run out of options.


 Please take a break until after XMAS, I think even Walmart closes at 6:00. You have provided way more support than I ever thought was possible!!!

MERRY XMAS and HAPPY HOLIDAYS!!!




**sudo grep -v rootfs /proc/mounts > /etc/mtab returns:**
-bash: /etc/mtab: Permission denied

---

### Post by r.stiltskin on 2014-12-24
Sorry, that was some kind of stupid cut 'n paste error on my part.  I meant to write
```

grep -v rootfs /proc/mounts | sudo tee /etc/mtab
```

Happy holidays to you too.

---

### Post by Bashing-om on 2014-12-24
paschalleddie1; Hey !

> **paschalleddie1 said:**
> There's been some concern expressed about my lack of headroom so I'm trying to borrow a few GB from Windows, hopefully that will help. 

Regarding this learning experience, to be honest, I've never received tech support that was this extensive, not even from paid support. Most tech support would have passed the buck by now and given up, blaming the problem on hardware or some other issue. I'm in it until you run out of options.


 Please take a break until after XMAS, I think even Walmart closes at 6:00. You have provided way more support than I ever thought was possible!!!

MERRY XMAS and HAPPY HOLIDAYS!!!




**sudo grep -v rootfs /proc/mounts > /etc/mtab returns:**
-bash: /etc/mtab: Permission denied

Welcome to our world of open source; All for 1 and One for all.

We pick this back up when you have the time.
This too is worth looking into:
> 
sudo grep -v rootfs /proc/mounts > /etc/mtab returns:
-bash: /etc/mtab: Permission denied

maybe because 'sudo' can not cross over the '>' boundary ? ( maybe that why the tool 'tee' was developed ).

simplify to a single instance:
what returns:
```

sudo grep -v rootfs /proc/mounts

```
IF that runs we will see what can be done to make up the '/etc/mtab' file.

[INDENT][INDENT]Merry Christmas,  and to all, good things -
[INDENT][INDENT][INDENT]'till we meet again
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-24
To avoid any transcription errors, how do I export the output to a flash drive?

grep -v rootfs /proc/mounts | sudo tee /etc/mtab > log_directory.txt returned:

-bash: log-directory.txt: No space left on device

---

### Post by Bashing-om on 2014-12-24
> **paschalleddie1 said:**
> To avoid any transcription errors, how do I export the output to a flash drive?

grep -v rootfs /proc/mounts | sudo tee /etc/mtab > log_directory.txt returned:

-bash: log-directory.txt: No space left on device

Try and see if the flash drive will mount, and if it does, find it's mount point in /media/<usernmae>
```

ls -al /media/paschalleddie

```
where 'paschalleddie' is the '<username> that you use on your system.

Then you could do a number like:
```

grep -v rootfs /proc/mounts | sudo tee /etc/mtab > /media/<username>/<long_UUID>/log_directory.txt 

```
-------------------------
But, testing to see, what results:
```

sudo rm /var/log/apport.log.7.gz

```
As we know that file does exist. 
Get us some operating head room by removing no-longer-needed files. Might take a look in /Downloads directory and see what can be removed. 

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by r.stiltskin on 2014-12-24
I was tempted to give you a command that would delete all the old (.2.gz and older) log files, but I'm afraid that if either of us makes a mistake you might wipe out more than we want.  But anyway, the bulk of the space is being taken up by the kern.log and syslog, especially the ones dated today.  It seems pretty apparent that that's where you ran out of space.  Seems you can free up a fair amount just by running
```
rm /var/log/kern.log.2.gz
rm /var/log/kern.log.3.gz
rm /var/log/kern.log.4.gz
```

Also I guess we ought to take a look at your syslog to see if there are any clues there.  It's really huge -- I hope it will be ok to post such a huge file to pastebin.  So try and run
```
cat /var/log/syslog | pastebinit
``` and post the url.

And after deleting those old kern.log files you should now be able to restore the mtab file by trying again
```
grep -v rootfs /proc/mounts | sudo tee /etc/mtab

And finally, with mtab restored you should be able to run
[code]df -h | pastebinit
```

---

### Post by paschalleddie1 on 2014-12-26
Update - Good News

I've added 5GB to give me a "little" more headroom. This has enabled me to fully boot up. I now recive an error notification:

"An error occured, please run Package Manager from the right-click menu or apt-get in the terminal to see what is wrong. The error message was: 'Error: BrokenCount > O'. This usually means that your installed packages have unmet dependencies.

Synaptic Package Manager Broken Filter returns the following broken packages:[INDENT]python-twisted-conch
python-twisted-runner
libc6
[/INDENT]

After running Fix Broken, it returns successfully fixed dependency problems. However, when Package Manager runs update the follow error remains:


"E: /var/cache/apt/archives/libgcc1_1%3a4.9.1-0ubuntu1_i386.deb: pre-dependency problem - not installing libgcc1:i386"

Progress has been made, close to the end.

---

### Post by Bashing-om on 2014-12-26
paschalleddie1; HoKay ;

So, What architecture do we have here ?

Show us:
```

uname -a

```

And we see what it is going to take now to clean up the package management system.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-26
**More Info:**

(synaptic:2500): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Resource temporarily unavailable
Extracting templates from packages: 54%E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Resource temporarily unavailable
Extracting templates from packages: 100%
dpkg: regarding .../libgcc1_1%3a4.9.1-0ubuntu1_i386.deb containing libgcc1:i386, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.

dpkg: error processing archive /var/cache/apt/archives/libgcc1_1%3a4.9.1-0ubuntu1_i386.deb (--unpack):
 pre-dependency problem - not installing libgcc1:i386
Errors were encountered while processing:
 /var/cache/apt/archives/libgcc1_1%3a4.9.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of python-twisted-conch:
 python-twisted-conch depends on python-twisted-core (>= 13.2.0-1ubuntu1); however:
  Package python-twisted-core is not installed.
 python-twisted-conch depends on python-crypto (>= 2.0.1+dfsg1-1.1); however:
  Package python-crypto is not installed.
 python-twisted-conch depends on python-pyasn1; however:
  Package python-pyasn1 is not installed.
 python-twisted-conch depends on python (>= 2.7); however:
  Package python is not installed.
 python-twisted-conch depends on python (<< 2.8); however:
  Package python is not installed.
 python-twisted-conch depends on python:any (>= 2.7.1-0ubuntu2); however:

dpkg: error processing package python-twisted-conch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-runner:
 python-twisted-runner depends on python-twisted-core (>= 13.2.0-1ubuntu1); however:
  Package python-twisted-core is not installed.
 python-twisted-runner depends on python (>= 2.7); however:
  Package python is not installed.
 python-twisted-runner depends on python (<< 2.8); however:
  Package python is not installed.
 python-twisted-runner depends on python:any (>= 2.7.1-0ubuntu2); however:

dpkg: error processing package python-twisted-runner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6:i386:
 libc6:i386 depends on libgcc1; however:
  Package libgcc1 is not installed.

dpkg: error processing package libc6:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.13-5); however:
  Package libc6:i386 is not configured yet.

dpkg: error processing package multiarch-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-twisted-conch
 python-twisted-runner
 libc6:i386
 multiarch-support

---

### Post by schragge on 2014-12-26
To remedy this
> **paschalleddie1 said:**
> 
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.
try
```
sudo dpkg --force-depends --configure multiarch-support
```

---

### Post by Bashing-om on 2014-12-26
@schragge;

:) thanks heaps, helps bunches.

an arrow, straight to the heart

---

### Post by paschalleddie1 on 2014-12-26
BIG BIG BIG THANKS to Bashing-om, r.stiltskin 		and schragge!!!  Package Manager and Software Updater both ran successfully and shut down. Everything looks good!

):P):P):P):P):P):P):P

---

### Post by Bashing-om on 2014-12-26
paschalleddie1; Outstanding !

Let's check and make sure:
```

sudo apt-get -f install
sudo dpkg -C
sudo fdisk -lu
df -h
df -i

```

[INDENT][INDENT]the truth of the matter
[/INDENT][/INDENT]

---

### Post by paschalleddie1 on 2014-12-26
Clean bill of health?

eddie@eddie-Latitude-C640:~$ sudo apt-grt -f install
[sudo] password for eddie: 
sudo: apt-grt: command not found
eddie@eddie-Latitude-C640:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
eddie@eddie-Latitude-C640:~$ sudo dpkg -C
eddie@eddie-Latitude-C640:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000609db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       64259       32098+  de  Dell Utility
/dev/sda2   *       64260    45206909    22571325    7  HPFS/NTFS/exFAT
/dev/sda3        45207552    78139391    16465920    f  W95 Ext'd (LBA)
/dev/sda5        45209600    76570623    15680512   83  Linux
/dev/sda6        76572672    78139391      783360   82  Linux swap / Solaris
eddie@eddie-Latitude-C640:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        15G  6.9G  7.0G  50% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            365M  8.0K  365M   1% /dev
tmpfs            75M  936K   74M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            375M  272K  374M   1% /run/shm
none            100M   28K  100M   1% /run/user
/dev/sda2        22G   19G  2.9G  87% /media/eddie/464CB2144CB1FEAD
eddie@eddie-Latitude-C640:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda5       979200 637714  341486   66% /
none             95790      2   95788    1% /sys/fs/cgroup
udev             93391    500   92891    1% /dev
tmpfs            95790    412   95378    1% /run
none             95790      3   95787    1% /run/lock
none             95790      6   95784    1% /run/shm
none             95790     21   95769    1% /run/user
/dev/sda2      3063704  43634 3020070    2% /media/eddie/464CB2144CB1FEAD
eddie@eddie-Latitude-C640:~$

---

### Post by Bashing-om on 2014-12-26
paschalleddie1; Yepper !

Looks all clean to me .

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

By golly
[INDENT][INDENT]I think you doed it
[/INDENT][/INDENT]

---

### Post by r.stiltskin on 2014-12-26
Great news eddie.

If you click on "Thread Tools" (near the right side of the window just above the first post on any page) you'll get a drop-down menu where you can click "Mark this thread as solved".

Another suggestion for future posts: when you're posting command line output, surround that part of the post with code tags so the output will be formatted exactly as is it in your terminal window and therefore easier to read on the forum.

Something like:

Comment comment blah blah blah

[IMG]http://ibin.co/1m04s96ZGXYW[/IMG]

more comments etc etc

---

### Post by prolaiot0 on 2015-02-13
thank guy 


[ubuntuforums.org]("http://www.scoresite.org/d/ubuntuforums.org")

---

