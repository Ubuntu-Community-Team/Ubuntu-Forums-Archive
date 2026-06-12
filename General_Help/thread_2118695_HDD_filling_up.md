---
title: "HDD filling up"
date: 2013-02-21
forum: General Help
---

### Post by AtariBaby on 2013-02-21
Something's going wrong. Ubuntu 12.10 says the /root is full, despite the fact that I know I only consciously have a few files there. I figure it should be 80gb free at least. Disk Usage Analyzer is spinning without results for about 20 minutes now. I right click the File System folder and look at properties and it claimed that the drive help 159TB and climbing! I can assure you this drive is maybe 250GB tops.

How can I troubleshoot this?

---

### Post by papibe on 2013-02-22
Hi AtariBaby.

Could you post the results of these commands?
```
df -h

df -i
```
Regards.

---

### Post by AtariBaby on 2013-02-22
Update: I ran bitbleach thanks to a helpful suggestion, and now things look like I expect them to. I'll just wait and see if it was a fluke or if it's going to inexplicably fill up again, I suppose.

Hi Papibe, I appear to be doing okay but here you go, if you think we should look at it:


df -h
df: `/root/.gvfs': Permission denied
Filesystem         Size  Used Avail Use% Mounted on
/dev/sda1          109G   41G   62G  40% /
udev               992M  4.0K  992M   1% /dev
tmpfs              401M  1.1M  400M   1% /run
none               5.0M     0  5.0M   0% /run/lock
none              1001M   84K 1001M   1% /run/shm
none               100M   60K  100M   1% /run/user
/dev/sdb1          112G   20G   93G  18% /media/DATA
//10.0.1.3/share   1.8T  1.3T  575G  69% /media/a300i
//10.0.1.3/a300ii  1.9T  603G  1.3T  33% /media/a300ii


df -i
df: `/root/.gvfs': Permission denied
Filesystem          Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1          7200768 539231  6661537    8% /
udev                253839    487   253352    1% /dev
tmpfs               256200    418   255782    1% /run
none                256200      3   256197    1% /run/lock
none                256200      5   256195    1% /run/shm
none                256200     26   256174    1% /run/user
/dev/sdb1         96817092    340 96816752    1% /media/DATA
//10.0.1.3/share         0      0        0     - /media/a300i
//10.0.1.3/a300ii        0      0        0     - /media/a300ii

---

### Post by AtariBaby on 2013-02-22
I appreciate the effort. feel free to disregard if you think I'm okay now I ran bitbleach

---

### Post by AtariBaby on 2013-02-22
Gah, unsolved! Had 60Gb free. Came home to find it filled up again!

---

### Post by fdrake on 2013-02-22
> **AtariBaby said:**
> Gah, unsolved! Had 60Gb free. Came home to find it filled up again!

which program says that your home is full? Can you post a terminal output of the prev commands?

---

### Post by AtariBaby on 2013-02-22
Thanks for joining in.  I see an operating system popup message with the options  something like "OK" or "Analyze", to open disk usage analyze. I closed it so I don't remember.  I'm not sure what you want in a terminal output, but papibe asked for df -h and df -i  df -h  ```
 df: `/root/.gvfs': Permission denied Filesystem         Size  Used Avail Use% Mounted on /dev/sda1          109G  103G     0 100% / udev               992M  4.0K  992M   1% /dev tmpfs              401M  1.1M  400M   1% /run none               5.0M     0  5.0M   0% /run/lock none              1001M  216K 1001M   1% /run/shm none               100M   68K  100M   1% /run/user /dev/sdb1          112G  9.9G  102G   9% /media/DATA //10.0.1.3/share   1.8T  1.3T  563G  70% /media/a300i //10.0.1.3/a300ii  1.9T  603G  1.3T  33% /media/a300ii 
```  df -i ```
 df: `/root/.gvfs': Permission denied Filesystem           Inodes  IUsed     IFree IUse% Mounted on /dev/sda1           7200768 539558   6661210    8% / udev                 253839    487    253352    1% /dev tmpfs                256200    418    255782    1% /run none                 256200      3    256197    1% /run/lock none                 256200      7    256193    1% /run/shm none                 256200     27    256173    1% /run/user /dev/sdb1         107103900    333 107103567    1% /media/DATA //10.0.1.3/share          0      0         0     - /media/a300i //10.0.1.3/a300ii         0      0         0     - /media/a300ii 
```

---

### Post by fdrake on 2013-02-22
where ins your home dir? are you using a mounted forlder for your users home?

---

### Post by AtariBaby on 2013-02-22
My home folder is in one partition of an internal hard drive but pretty much obeying the standard directory structure, i.e., a username in File System/home/.

There are two mounted external windows shares in /media and the home folder the drive is on is partitioned and the other partition is called DATA. Is that answering your question?

---

### Post by AtariBaby on 2013-02-22
I want to go ahead and run bitbleach again to clear the hard drive, does anyone want me to run any terminal commands or anything before I do?

---

### Post by oldfred on 2013-02-22
cd / or cd /home
sudo du -hc --max-depth=1

 #check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB

to see where it is filling. 

But one option is that you have a run away error message that is filling the log files.
You can check /var/log for a very large log file.
       
 [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by AtariBaby on 2013-02-22
holy crap it's hard to post information here. I am retyping it just a moment.

---

### Post by AtariBaby on 2013-02-22
> **oldfred said:**
> cd / or cd /home
sudo du -hc --max-depth=1

 #check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB

to see where it is filling. 

But one option is that you have a run away error message that is filling the log files.
You can check /var/log for a very large log file.
       
 [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

80M    ./ataribaby 
26G    ./misterfantastic 26G    . 
26G    total

---

sudo du -h --max-depth=1 / | grep '[0-9]G\>' 
du: cannot access `/proc/15939/task/15939/fd/4': No such file or directory 
du: cannot access `/proc/15939/task/15939/fdinfo/4': No such file or directory 
du: cannot access `/proc/15939/fd/4': No such file or directory du: cannot access `/proc/15939/fdinfo/4': No such file or directory 19G    /home 4.0G    /usr 
du: cannot access `/run/user/misterfantastic/gvfs': Permission denied 
9.2G    /root   

---

misterfantastic@MisterFantastic:/home/misterfantastic$ sudo find / -name '*' -size +1G /proc/kcore 
find: `/proc/15892/task/15892/fd/5': No such file or directory 
find: `/proc/15892/task/15892/fdinfo/5': No such file or directory 
find: `/proc/15892/fd/5': No such file or directory 
find: `/proc/15892/fdinfo/5': No such file or directory 
/home/misterfantastic/Dropbox/.dropbox.cache/~a25f0c78.tmp 
(then it lists all the files in the external mounted drives, which are many pages long)
---
log files appear to be few and small.

---

### Post by oldfred on 2013-02-22
You should just be able to copy & paste from the terminal. Sometimes I have to copy into a text file. Then recopy as some things on Internet follow Windows and are have line ending issues.

I do not see anything, was this after you housecleaned again? If so wait for it to fill up and run again. Looking for large folder, then large file in that folder. You do not have to run all the choices if you can narrow it down first.

---

### Post by AtariBaby on 2013-02-22
Unfortunately, this was before housecleaning and unfortunately, now that I've run bleachbit again it still says 0% free space. :( I'm dead in the water here.

---

### Post by steeldriver on 2013-02-22
The find command got screwed up somehow maybe - try either

```

sudo find / \( -path '/sys/*' -o -path '/proc/*' \) -prune -o -size +1G -printf '%s %p\n' 2>/dev/null | sort -hr | head -10

```(sorry, a bit long winded) or

```
sudo du -ah / 2>/dev/null | sort -hr | head -10
```

---

### Post by AtariBaby on 2013-02-23
after the first command I just get a solid cursor.

After the second commond, I get sort:write failed /tmp(random letters):no space left on device

---

### Post by fdrake on 2013-02-23
do you have some kind of links or rsync folders in the home dir that goes to the mounted systems in /media?
if so make sure you do not have a cycle link:
ex /home/a is a link to /media/DATA
/media/DATA/b is a link to /home. That sometime my create a problem.

last question: can you post 
> sudo fdisk -l
cat /etc/mtab
cat /etc/fstab

---

### Post by matt_symes on 2013-02-23
Hi

Are your log files filling up your hard drive ?

Kind regards

---

### Post by AtariBaby on 2013-02-23
i'm sure it's probably some error on my part :confused:

```
misterfantastic@MisterFantastic:/home/misterfantastic$ sudo fdisk -l
[sudo] password for misterfantastic: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006aff6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   230252543   115125248   83  Linux
/dev/sda2       230254590   234440703     2093057    5  Extended
/dev/sda5       230254592   234440703     2093056   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f0c39cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   234436544   117218241    7  HPFS/NTFS/exFAT
misterfantastic@MisterFantastic:/home/misterfantastic$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0
/dev/sdb1 /media/DATA fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
//10.0.1.3/share /media/a300i cifs rw 0 0
//10.0.1.3/a300ii /media/a300ii cifs rw 0 0
gvfsd-fuse /run/user/misterfantastic/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=misterfantastic 0 0
misterfantastic@MisterFantastic:/home/misterfantastic$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda1 :
UUID=7e56dee0-cbec-4e20-8387-0abac85fab7d    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb1 :
UUID=7A7C25B17C256959    /media/DATA    ntfs-3g    defaults,locale=en_US.UTF-8    00
#Entry for /dev/sda5 :
UUID=dbad1a66-bc0a-460e-83d9-61291d61c56f    none    swap    sw    0    0
#entered by me following instructions on mounting shares
//10.0.1.3/share /media/a300i cifs username=nmt,password=1234,uid=1001
//10.0.1.3/a300ii /media/a300ii cifs username=nmt,password=1234,uid=1001

```

---

### Post by AtariBaby on 2013-02-23
> **fdrake said:**
> do you have some kind of links or rsync folders in the home dir that goes to the mounted systems in /media?
if so make sure you do not have a cycle link:
ex /home/a is a link to /media/DATA
/media/DATA/b is a link to /home. That sometime my create a problem.

last question: can you post

not sure...

This is a screenshot of all visible folders on home dir, and I'm currently checking all the hidden folders and will do so for the other username as well.

---

### Post by AtariBaby on 2013-02-23
One thing that's very strange. I run out of space, then I seemingly have space again, like right now I've got 20GB space of about 80, and stable.  At other times, I can watch the available free space shrinking before my eyes.

---

### Post by AtariBaby on 2013-02-23
> **matt_symes said:**
> Hi

Are your log files filling up your hard drive ?

Kind regards

Not that I can tell. In /var/logs there are maybe 5MB of log files. Not sure where else I should look.

---

### Post by matt_symes on 2013-02-23
Hi

Run the find and du commands posted. 

I would also run iotop to see what is writing to the drive.

```
sudo apt-get install iotop
sudo iotop
```Kind regards

---

### Post by Paddy Landau on 2013-02-23
> **AtariBaby said:**
> Ubuntu 12.10 says the /root is full…
Where specifically did it tell you this?

If you open System Monitor > File Systems, you can see approximate sizes of disks. Can you post a screen-shot of that?

Try this command as a start to narrow down which folder holds the big files:
```
sudo du --human-readable --one-file-system --summarize --total /* 2>/dev/null
```Once you see the results, you can narrow it down. For example, if the big files are in (say) [FONT=Lucida Console]/usr[/FONT], repeat the command but replace [FONT=Lucida Console]/*[/FONT] with [FONT=Lucida Console]/usr/*[/FONT] as follows
```
sudo du --human-readable --one-file-system --summarize --total **/usr/*** 2>/dev/null
```Repeat as needed until you find the offending folder. (Incidentally, my [FONT=Lucida Console]/usr[/FONT] folder is nearly 5Gb, to give you a guideline.)

The other thing you want to do is check your disk for errors. Issue the following command, and then reboot:
```
sudo touch /forcefsck
```

---

### Post by AtariBaby on 2013-02-23
**Hey guys,, I have a file in home called .xsession-errors.old that is 64GB...**

---

### Post by AtariBaby on 2013-02-23
> **Paddy Landau said:**
> Where specifically did it tell you this?
It's your standard operating-system pop-up message. Prompts you to say "ok" or "analyze" to open disk analyzer.

> If you open System Monitor > File Systems, you can see approximate sizes of disks. Can you post a screen-shot of that?

---

### Post by Paddy Landau on 2013-02-23
> **AtariBaby said:**
> Hey guys,, I have a file in home called .xsession-errors.old that is 64GB...
You can safely delete the file [FONT=Lucida Console].xession_errors.old[/FONT]. Reboot.

I see that others have had your problem. I'm busy investigating&#8230;

---

### Post by AtariBaby on 2013-02-23
> **Paddy Landau said:**
> 

Try this command as a start to narrow down which folder holds the big files:
```
sudo du --human-readable --one-file-system --summarize --total /* 2>/dev/null
```Once you see the results, you can narrow it down. For example, if the big files are in (say) [FONT=Lucida Console]/usr[/FONT], repeat the command but replace [FONT=Lucida Console]/*[/FONT] with [FONT=Lucida Console]/usr/*[/FONT] as follows
```
sudo du --human-readable --one-file-system --summarize --total **/usr/*** 2>/dev/null
```Repeat as needed until you find the offending folder. (Incidentally, my [FONT=Lucida Console]/usr[/FONT] folder is nearly 5Gb, to give you a guideline.)

this confirms the hidden file in Home I just mentioned above: ** .xsession-errors.old that is 64GB**
> 
The other thing you want to do is check your disk for errors. Issue the following command, and then reboot:
```
sudo touch /forcefsck
```
Thank you for these common sense steps that a n00b can understand. I will refer to them again I'm sure!

---

### Post by AtariBaby on 2013-02-23
> **Paddy Landau said:**
> You can safely delete the file [FONT=Lucida Console].xession_errors.old[/FONT]. Reboot.

I see that others have had your problem. I'm busy investigating…


Oh, that's great. Thank you and please let me know if I can do more to help test and/or try fixes.

---

### Post by matt_symes on 2013-02-23
Hi

What does the .xsession-errors log file say inside ?

Kind regards

---

### Post by Paddy Landau on 2013-02-23
OK, it seems as though it is an old bug that is resurfacing. Please issue the following command and post the results here:
```
tail --lines=30 ~/.xession_errors
```Can I confirm that you are using Ubuntu 12.10?

---

### Post by AtariBaby on 2013-02-23
> **matt_symes said:**
> Hi

What does the .xsession-errors log file say inside ?

Kind regards

matt, thank you for asking, because i do see that I should probably have a look at this file from time to time, yes? I have messes to clean up! I decided to stop using teamviewer because it's too buggy, and dropbox I think I need to reinstall. And looks like there are other problems, too.

```
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
gnome-session[1368]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "dropbox" (No such file or directory)
gnome-session[1368]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "/usr/bin/teamviewer" (No such file or directory)
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite

(vino-server:2147): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
compiz (core) - Info: Loading plugin: opengl
23/02/2013 09:15:20 AM Autoprobing TCP port in (all) network interface
23/02/2013 09:15:20 AM Listening IPv6://[::]:5900
23/02/2013 09:15:20 AM Listening IPv4://0.0.0.0:5900
23/02/2013 09:15:20 AM Autoprobing selected port 5900
23/02/2013 09:15:20 AM Advertising security type: 'TLS' (18)
23/02/2013 09:15:20 AM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
23/02/2013 09:15:20 AM Listening IPv6://[::]:5900
23/02/2013 09:15:20 AM Listening IPv4://0.0.0.0:5900
23/02/2013 09:15:20 AM Clearing securityTypes
23/02/2013 09:15:20 AM Advertising security type: 'TLS' (18)
23/02/2013 09:15:20 AM Clearing securityTypes
23/02/2013 09:15:20 AM Advertising security type: 'TLS' (18)
23/02/2013 09:15:20 AM Advertising authentication type: 'No Authentication' (1)
23/02/2013 09:15:20 AM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
23/02/2013 09:15:20 AM Listening IPv6://[::]:5900
23/02/2013 09:15:20 AM Listening IPv4://0.0.0.0:5900
23/02/2013 09:15:20 AM Clearing securityTypes
23/02/2013 09:15:20 AM Clearing authTypes
23/02/2013 09:15:20 AM Advertising security type: 'TLS' (18)
23/02/2013 09:15:20 AM Advertising authentication type: 'VNC Authentication' (2)
23/02/2013 09:15:20 AM Clearing securityTypes
23/02/2013 09:15:20 AM Clearing authTypes
23/02/2013 09:15:20 AM Advertising security type: 'TLS' (18)
23/02/2013 09:15:20 AM Advertising authentication type: 'VNC Authentication' (2)
23/02/2013 09:15:20 AM Advertising security type: 'VNC Authentication' (2)

(vino-server:2147): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(vino-server:2147): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/misterfantastic//.compiz/session/1044188747affcc8bc13616396983827500000013680039"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
23-Feb-2013 09:15:30 - INFO :: MainThread : cache set to : /home/misterfantastic/.mylar/cache
23-Feb-2013 09:15:30 - INFO :: MainThread : Checking to see if the database has all tables....
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
23-Feb-2013 09:15:36 - INFO :: MainThread : Populating Base Exception listings into Mylar....
compiz (core) - Info: Loading plugin: scale
23-Feb-2013 09:15:36 - INFO :: MainThread : Populating Custom Exception listings into Mylar....
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
23-Feb-2013 09:15:39 - INFO :: MainThread : Ensuring DB integrity - Removing all Erroneous Comics (ie. named None)
23-Feb-2013 09:15:39 - INFO :: MainThread : Retrieving latest version information from github
23-Feb-2013 09:15:40 - INFO :: MainThread : Comparing currently installed version with latest github version
compiz (core) - Info: Starting plugin: unityshell
23-Feb-2013 09:15:40 - INFO :: MainThread : Mylar is up to date
23-Feb-2013 09:15:41 - INFO :: MainThread : Starting Mylar on port: 8090
23-Feb-2013 09:15:41 - INFO :: MainThread : Checking for existance of Weekly Comic listing...
23-Feb-2013 09:15:41 - INFO :: Thread-12 : Weekly pull list present - checking if it's up-to-date..
23-Feb-2013 09:15:41 - INFO :: Thread-12 : No new pull-list available - will re-check again in 24 hours.
23-Feb-2013 09:15:41 - INFO :: Thread-12 : Checking the Weekly Releases list for comics I'm watching...
23-Feb-2013 09:15:56 - INFO :: Thread-12 : Finished checking for comics on my watchlist.
compiz (core) - Warn: Attempted to restack relative to 0x2200087 which is not a child of the root window or a window compiz owns
** Message: moving back from GtkStatusIcon to indicator
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture

** (nautilus:2155): CRITICAL **: syncdaemon_interface_get_proxy_object: assertion `SYNCDAEMON_IS_INTERFACE (interface)' failed

(update-notifier:2619): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(update-notifier:2619): GLib-GIO-CRITICAL **: g_mount_can_eject: assertion `G_IS_MOUNT (mount)' failed

(update-notifier:2619): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (firefox:3613): WARNING **: Failed to open webapp application path dir /usr/share/ubuntu/unity-webapps/userscripts: Error opening directory '/usr/share/ubuntu/unity-webapps/userscripts': No such file or directory

** (firefox:3613): WARNING **: Failed to open webapp application path dir /usr/share/gnome/unity-webapps/userscripts: Error opening directory '/usr/share/gnome/unity-webapps/userscripts': No such file or directory

** (firefox:3613): WARNING **: Failed to open webapp application path dir /usr/local/share/unity-webapps/userscripts: Error opening directory '/usr/local/share/unity-webapps/userscripts': No such file or directory
```

---

### Post by AtariBaby on 2013-02-23
> **Paddy Landau said:**
> OK, it seems as though it is an old bug that is resurfacing. Please issue the following command and post the results here:
```
tail --lines=30 ~/.xession_errors
```Can I confirm that you are using Ubuntu 12.10?
Aye, Captain!

looks like that command is slightly wrong? I don't know how to fix it...

tail: cannot open `/home/misterfantastic//.xession_errors' for reading: No such file or directory

---

### Post by matt_symes on 2013-02-23
Hi

There's not too much in that log file. Keep and eye on it when it starts getting bigger.

You may want to use logrotate to rotate the log file.

[http://www.thegeekstuff.com/2010/07/logrotate-examples/](http://www.thegeekstuff.com/2010/07/logrotate-examples/)

Kind regards

---

### Post by Paddy Landau on 2013-02-23
> **AtariBaby said:**
> looks like that command is slightly wrong? I don't know how to fix it...
:redface: Oops, my mistake. I typed an underscore instead of a hyphen. Never mind, your answer to matt_symes did the trick.

I cannot tell if it is the same problem as [Bug #870742]("https://bugs.launchpad.net/ubuntu/+source/libdbusmenu/+bug/870742"), which apparently has been fixed.

You can eliminate [FONT=Lucida Console].xsession-errors[/FONT] altogether ([thanks to Zorael]("http://ubuntuforums.org/showthread.php?p=11753618#post11753618")).

[LIST=1]
[*]Press [FONT=Lucida Console]Alt+F2[/FONT] and enter the following. You will be asked for your password.```
gksudo gedit /etc/X11/Xsession
```
[*]Locate the line, probably around line 61, that reads as follows.```
ERRFILE=$HOME/.xsession-errors
```
[*]Insert a new (empty) line after that line, and type the following. Do not type any spaces.```
ERRFILE=/dev/null
```
[*]Save the file and exit. (There will be an "Untitled Document" due to an existing bug. Just close it without saving.)
[*]Reboot.
[*]Finally, delete [FONT=Lucida Console].xsession-errors[/FONT] and [FONT=Lucida Console].xsession-errors.old[/FONT].
[/LIST]
You should be bothered by those files no more.

---

### Post by AtariBaby on 2013-02-23
I'll mark solved and unmark it if I get in trouble again. Glad to know this one may not have been my fault. :p

Guys, thanks so much for piling on the problem and helping. See attached.

---

### Post by Paddy Landau on 2013-02-23
> **AtariBaby said:**
> See attached.
LOL, that's a cool picture!

---

### Post by AtariBaby on 2013-02-24
Oh, lame, **unsolved!**

Should I just use the log rotation program recommended by matt symes? I did all the steps in Paddy's last post, but again today I have an  .old file up to 20GB already!

---

### Post by AtariBaby on 2013-02-24
> **matt_symes said:**
> Hi

There's not too much in that log file. Keep and eye on it when it starts getting bigger.

You may want to use logrotate to rotate the log file.

[http://www.thegeekstuff.com/2010/07/logrotate-examples/](http://www.thegeekstuff.com/2010/07/logrotate-examples/)

Kind regards

I worry that this is going to be a bandaid on a serious wound. The procedure describes executing the script daily. These files fill up my hard drive in about an hour!

---

### Post by Paddy Landau on 2013-02-24
> **AtariBaby said:**
> Oh, lame, **unsolved!**

Should I just use the log rotation program recommended by matt symes? I did all the steps in Paddy's last post, but again today I have an  .old file up to 20GB already!
Oh dear.

I shall boot into 12.10 (I use 12.04) and see if I can find how to solve this problem. It may take a day or so, though.

---

### Post by AtariBaby on 2013-02-24
Thanks, Bro. Please let me know if I can do anything for you related to this or something else.

---

### Post by matt_symes on 2013-02-24
Hi

If the file is filling up that quickly then logrotate is not the solution.

I'm surprised paddys solution did not work as it should be piping the errors into the bit bucket.

Just delete the old .xsession-errors file, reboot and see if it create another.

Kind regards

---

### Post by dodo3773 on 2013-02-24
> **matt_symes said:**
> Hi

If the file is filling up that quickly then logrotate is not the solution.

I'm surprised paddys solution did not work as it should be piping the errors into the bit bucket.

Just delete the old .xsession-errors file, reboot and see if it create another.

Kind regards

logrotate should still be a good solution since it uses cron and can limit the size of the log. I wouldn't be so quick to write it off. It's good advice in my opinion.

---

### Post by matt_symes on 2013-02-24
Hi

Apparently that /dev/null solution does not always work :(

You could create a cron job that deletes the log file every hour. 

It best to find out what is filling it up though.

Kind regards

---

### Post by matt_symes on 2013-02-24
Hi
> 
logrotate should still be a good solution since it uses cron and can  limit the size of the log. I wouldn't be so quick to write it off. It's  good advice in my opinion.Interesting. It's been a while since i read up on logrotate and written a logrotate config file. 

If it has some facility to delete the file if it gets too big than that would work as well as a simple cron job to delete the file.

I've just always used it to logrotate after a specified time but then i have never had a problem with huge log files.

EDIT:

From man logrotate> 

rotate count
              Log files are rotated count times before being removed or mailed to the address specified in a  mail  directive.  If
              count is 0, old versions are removed rather than rotated.


       size size
              Log  files are rotated when they grow bigger than size bytes. If size is followed by k, the size is assumed to be in
              kilobytes.  If the M is used, the size is in megabytes, and if G is used, the size is in  gigabytes.  So  size  100,
              size 100k, size 100M and size 100G are all valid.That would work. @[[COLOR=#000000]dodo3773[/COLOR]]("http://ubuntuforums.org/member.php?u=912419") Thanks :D

Kind regards

---

### Post by steeldriver on 2013-02-24
We could try to find out exactly what (presumably repeated) errors are filling up the log - sometimes just using 'tail' doesn't see enough instances to spot that

Here's a one-liner that attempts to count recurring messages - it's a mess because some messages have timestamps (which stop them counting as 'repeats'), and the timestamp format varies - this works for what's currently in *my* .xsession-errors but we may need to tweak it a bit for yours

```
sed -re '/^$d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e  's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' ~/.xsession-errors | sort |  uniq -c | sort -hr | head -10
```e.g.

```
$ sed -re '/^$/d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e 's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' ~/.xsession-errors | sort | uniq -c | sort -hr | head -10
     22  Advertising security type: 'TLS' (18)
     18  Clearing securityTypes
     11  Listening IPv6://[::]:5900
     11  Listening IPv4://0.0.0.0:5900
     10  Clearing authTypes
     10  Advertising authentication type: 'VNC Authentication' (2)
      6  Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
      5  Listening IPv6://::1:5900
      5  Listening IPv4://127.0.0.1:5900
      5 (gnome-settings-daemon:1996): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

```

---

### Post by dodo3773 on 2013-02-24
> **matt_symes said:**
> Hi


Interesting. It's been a while since i read up on logrotate. If it has some facility to delete the file if it gets too big than that would work as well as a simple cron job to delete the file.

Kind regards

I believe it does. Also, I do not think you need to setup an additional cron job as logrotate uses cron as its backend (I think (been a while for me too)). Also, maybe it would be possible to find a repeating pattern in .xsession-errors. Oh, looks like someone beat me to that idea.

---

### Post by dodo3773 on 2013-02-24
Are you running a server on this machine? Like ssh, ftp, vnc (vino process maybe (other people with the TLS issue on the internet))?

---

### Post by matt_symes on 2013-02-24
Hi

That's the best solution, to see what actually is writing so much, and then see if it's possible to lower the verbosity of the program writing to the log file.

Kind regards

---

### Post by AtariBaby on 2013-02-24
> **dodo3773 said:**
> Are you running a server on this machine? Like ssh, ftp, vnc (vino process maybe (other people with the TLS issue on the internet))?

I did recently turn on vino, looking for an alternative to teamviewer. Perhaps I should try yet something else? I wasn't happy with the lack of copy/paste functionality anyway.

---

### Post by dodo3773 on 2013-02-24
> **AtariBaby said:**
> I did recently turn on vino, looking for an alternative to teamviewer. Perhaps I should try yet something else? I wasn't happy with the lack of copy/paste functionality anyway.

Try turning off vino server / disabling the server from your services. After that delete your .xsession-errors file and the .xsession-errors.old (or whatever it was called) file and reboot your machine.

---

### Post by matt_symes on 2013-02-24
Hi

@ataribaby. Run steeldrivers command and post back the result.

Here is a log rotate file for you if you need to use it.

```
/home/<user_name>/.xsession-errors {
           rotate 0
           size 1M
           daily  
           missingok
           nocreate                                                                    
       }
```Replace <user_name> with your username.

Put it in

```
sudo nano /etc/logrotate.d/xession-errors
```Change its permissions.

```

sudo chmod 644 /etc/logrotate.d/xession-errors
```Kind regards

---

### Post by AtariBaby on 2013-02-24
> **steeldriver said:**
> We could try to find out exactly what (presumably repeated) errors are filling up the log - sometimes just using 'tail' doesn't see enough instances to spot that

Here's a one-liner that attempts to count recurring messages - it's a mess because some messages have timestamps (which stop them counting as 'repeats'), and the timestamp format varies - this works for what's currently in *my* .xsession-errors but we may need to tweak it a bit for yours

```
sed -re '/^$d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e  's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' ~/.xsession-errors | sort |  uniq -c | sort -hr | head -10
```e.g.

result; something I did wrong?:
```
sed: -e expression #1, char 4: unterminated address regex
```

---

### Post by AtariBaby on 2013-02-24
> **matt_symes said:**
> Hi

@ataribaby. Run steeldrivers command and post back the result.

Here is a log rotate file for you if you need to use it.

```
/home/<user_name>/.xsession-errors {
           rotate 0
           size 1M
           daily  
           missingok
           nocreate                                                                    
       }
```Replace <user_name> with your username.

Put it in

```
sudo nano /etc/logrotate.d/xession-errors
```Change its permissions.

```

sudo chmod 644 /etc/logrotate.d/xession-errors
```Kind regards

did all that. thanks! (changed teh filename xession-errors to xsession-errors just fyi)

---

### Post by Paddy Landau on 2013-02-24
I don't know if the previous comments have helped, but I've just been testing 12.10 and I have a great answer. It truncates .xsession-errors to zero, and makes it immutable (i.e. nothing can change it).


[LIST=1]
[*]```
mv .xsession-errors .xsession-errors.old
```
[*]```
touch .xsession-errors
```
[*]```
sudo chattr +i .xsession-errors
```
[*]Now, **reboot**. Don't skip this step.
[*]```
rm .xsession-errors.old
```
[/LIST]

This will solve your problem once and for all.

---

### Post by matt_symes on 2013-02-24
Hi

```
sed -re '/^$/d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e 's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' ~/.xsession-errors | sort | uniq -c | sort -hr | head -10
```Try that command when you need to see what is in the log files.

Paddy: Making it immutable. Interesting solution.

Kind regards

---

### Post by steeldriver on 2013-02-24
> **AtariBaby said:**
> result; something I did wrong?:
```
sed: -e expression #1, char 4: unterminated address regex
```

No, sorry something  *I* did wrong - please see the corrected version posted by matt_symes above

```
sed -re '/^$[COLOR=Red]**/**[/COLOR]d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e   's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' ~/.xsession-errors | sort |   uniq -c | sort -hr | head -10
```

---

### Post by Paddy Landau on 2013-02-24
> **matt_symes said:**
> Paddy: Making it immutable. Interesting solution.
I wish I could take the credit for this idea, but I came across it a couple of days ago. I don't remember where. It works well.

---

### Post by AtariBaby on 2013-02-24
I figure before stopping vino and before implementing Paddy's fix, I should take advantage of all this brainpower and maybe it will be helpful to identify the cause. Results of steeldriver's command:

```
misterfantastic@MisterFantastic:/$ sed -re '/^$/d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e   's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' ~/.xsession-errors | sort |   uniq -c | sort -hr | head -10
     30 (gnome-screensaver:2433): Gtk-CRITICAL **: gtk_widget_set_visible: assertion `GTK_IS_WIDGET (widget)' failed
      7 compiz (decor) - Warn: failed to bind pixmap to texture
      5 (gnome-settings-daemon:1827): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed
      5  Advertising security type: 'TLS' (18)
      4  Clearing securityTypes
      3 Traceback (most recent call last):
      3     self.__target(*self.__args, **self.__kwargs)
      3     self.run()
      3     return GCDdetails(comseries=None, resultURL=resultURL, vari_loop=0, ComicID=ComicID, TotalIssues=TotalIssues, issvariation=issvariation, resultPublished=resultPublished)
      3     resultFormat = subtxt9.findNext(text=True).rstrip()
```

I should add that right now I do not have a problem. Should I run again when the problem resurfaces?

---

### Post by matt_symes on 2013-02-24
Hi

Yes. Run it when the file gets large.

Kind regards

---

### Post by AtariBaby on 2013-02-26
> **matt_symes said:**
> Hi

```
sed -re '/^$/d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e 's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' ~/.xsession-errors | sort | uniq -c | sort -hr | head -10
```Try that command when you need to see what is in the log files.

Paddy: Making it immutable. Interesting solution.

Kind regards

Been about two hours, and just a blinking cursor so far. Do I need to keep waiting?

---

### Post by AtariBaby on 2013-02-26
After about 2 hours the hard drive filled up and on terminal:  sort: write failed: /tmp/sort0bbUht: No space left on device  Was I supposed to be looking somewhere else for the result?

---

### Post by steeldriver on 2013-02-26
Hmm OK let's try with only part of the file:

```
**tail -n 100000 ~/.xsession-errors | sed** -re '/^$/d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e 's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' | sort | uniq -c | sort -hr | head -10
```Play with the 100000 number - maybe start at 100 so it runs nice and quick and then go up until the numbers get interesting

---

### Post by AtariBaby on 2013-02-28
Wow guys now sometimes it's filling up but neither I nor any of these commands can find an xsessions-errors file

---

### Post by AtariBaby on 2013-03-01
After a reboot, the filling up begain again, and session-errors was visible, so I ran steelhead's command and got the message "authentication deferred".

---

### Post by matt_symes on 2013-03-01
Hi

Is this the message you are seeing ?

> AM Authentication deferred - ignoring client message

This may be the remote desktop bug.

Do you have remote desktop enabled ?

What's the output of 

```
ps aux | grep vino
```

If that retrun vino-server or some such then try to disable remote desktop.

KInd regards

---

### Post by AtariBaby on 2013-03-06
That fixed my problem! I'm sorry I dragged it out, but I greatly enjoyed learning all that stuff you guys had me do. Thank you.

---

