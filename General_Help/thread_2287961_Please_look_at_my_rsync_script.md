---
title: "Please look at my rsync script"
date: 2015-07-23
forum: General Help
---

### Post by vasa1 on 2015-07-23
To backup, I use Dropbox as well as a external USB drive. I was previously using this command:
```
rsync -lrtv --delete --protect-args --modify-window=1 --files-from=/home/vasa1/Dropbox/rsync-include.txt / /media/vasa1/TOSHIBA\ EXT/BACKUP/ &> /home/vasa1/"$(date +\%I_\%M)"rsync.log
``` where "TOSHIBA EXT" is the name of my external USB drive.

However, that command obviously won't let me access older versions of files.

Then, I came across [https://blog.interlinked.org/tutorials/rsync_time_machine.html](https://blog.interlinked.org/tutorials/rsync_time_machine.html) and decided to give it a try. To do so, I made the following script (based on what I could understand of the tutorial):
```
#!/bin/bash

date=$(date "+%Y-%m-%dT%H:%M:%S")
rsync -lrtv --delete --protect-args --modify-window=1 --link-dest=/media/vasa1/TOSHIBA\ EXT/noobak/current --files-from=/home/vasa1/Dropbox/rsync-include.txt / /media/vasa1/TOSHIBA\ EXT/noobak/back-$date &> /home/vasa1/"$(date +\%I_\%M)"rsync.log
rm -rf /media/vasa1/TOSHIBA\ EXT/noobak/current
ln -s back-$date /media/vasa1/TOSHIBA\ EXT/noobak/current
```

I think it's working but I'd welcome any feedback before I set up a cron job and junk the previous command.

The concept of "hard links" (which the new way seems to use) is also something I don't understand though the blog tries to explain it :(

Here's the output of **ls -l** for the backup folder:
```
07:27 PM .../TOSHIBA EXT/noobak $ ls -l
total 5
drwx------ 1 vasa1 vasa1  416 Jul 23 19:09 ./
drwx------ 1 vasa1 vasa1 4096 Jul 23 18:36 ../
drwx------ 1 vasa1 vasa1    0 Jul 23 18:40 back-2015-07-23T18:40:55/
drwx------ 1 vasa1 vasa1    0 Jul 23 18:48 back-2015-07-23T18:48:07/
drwx------ 1 vasa1 vasa1    0 Jul 23 18:55 back-2015-07-23T18:55:50/
drwx------ 1 vasa1 vasa1  320 Jul 23 19:09 back-2015-07-23T19:09:28/
lrwxrwxrwx 1 vasa1 vasa1   56 Jul 23 19:09 current -> back-2015-07-23T19:09:28/
07:27 PM .../TOSHIBA EXT/noobak $ 

```
The three older folders have a file size of zero whereas the latest is "320".

But if I look into each of the folders, they all seem to have the same content (other than files I've knowingly created or deleted from the source. For example, nanorc is present with the same file attributes in an older folder and in the latest folder:
```
07:31 PM .../back-2015-07-23T18:48:07/etc $ ls -l
total 12
drwx------ 1 vasa1 vasa1    0 Jul 23 16:41 ./
drwx------ 1 vasa1 vasa1    0 Jul 23 18:48 ../
drwx------ 1 vasa1 vasa1    0 Jun 11 06:07 gtk-3.0/
-rw------- 3 vasa1 vasa1 8453 Oct  1  2012 nanorc
drwx------ 1 vasa1 vasa1    0 Jun  4 06:32 xdg/
...
07:33 PM .../back-2015-07-23T19:09:28/etc $ ls -l
total 12
drwx------ 1 vasa1 vasa1    0 Jul 23 16:41 ./
drwx------ 1 vasa1 vasa1    0 Jul 23 19:09 ../
drwx------ 1 vasa1 vasa1    0 Jun 11 06:07 gtk-3.0/
-rw------- 3 vasa1 vasa1 8453 Oct  1  2012 nanorc
drwx------ 1 vasa1 vasa1    0 Jun  4 06:32 xdg/

```

So it looks like each "nanorc" is a real file.

Yet, when I look at the output of **df**, there's very little difference in free space on my USB drive (because I've only "touched" a couple of files between backups).
```
07:08 PM ~ $ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda6      219476804  14397736 193907180   7% /
none                   4         0         4   0% /sys/fs/cgroup
udev             1994280         4   1994276   1% /dev
tmpfs             401016      1232    399784   1% /run
none                5120         0      5120   0% /run/lock
none             2005068         0   2005068   0% /run/shm
none              102400         4    102396   1% /run/user
**/dev/sdb1**      488384532 110872928 377511604  23% **/media/vasa1/TOSHIBA EXT**
07:08 PM ~ $ 
```

After one run of the new sync script,

```
07:09 PM ~ $ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda6      219476804  14397752 193907164   7% /
none                   4         0         4   0% /sys/fs/cgroup
udev             1994280         4   1994276   1% /dev
tmpfs             401016      1232    399784   1% /run
none                5120         0      5120   0% /run/lock
none             2005068         0   2005068   0% /run/shm
none              102400         4    102396   1% /run/user
**/dev/sdb1**      488384532 110876996 377507536  23% **/media/vasa1/TOSHIBA EXT**
07:09 PM ~ $ 

``` The usage of /dev/sdb1 has increased by 4068 bytes (377507536 - 377511604)
And here's the corresponding rsync log:
```
sending incremental file list
created directory /media/vasa1/TOSHIBA EXT/noobak/back-2015-07-23T19:09:28
home/vasa1/
home/vasa1/.config/geany/
home/vasa1/.config/geany/geany_socket_vasa1-Inspiron-1545__0 -> /tmp/geany_socket.6b0caba5
home/vasa1/.config/gtk-2.0/
home/vasa1/.config/gtk-2.0/gtkfilechooser.ini
home/vasa1/.local/share/
home/vasa1/Desktop/
home/vasa1/Desktop/df-output

sent 196,559 bytes  received 512 bytes  18,768.67 bytes/sec
total size is 285,314,656  speedup is 1,447.78

```

So I hope things are working as intended despite my not understanding the "hard link" business.

---

### Post by vasa1 on 2015-07-23
> **vasa1 said:**
> ... So I hope things are working as intended despite my not understanding the "hard link" business.
Helpful link: [http://www.mikerubel.org/computers/rsync_snapshots/#Incremental](http://www.mikerubel.org/computers/rsync_snapshots/#Incremental)

```
09:22 PM .../TOSHIBA EXT/noobak $ ls -liR | grep 38262
38262 -rw------- 3 vasa1 vasa1 8453 Oct  1  2012 nanorc
38262 -rw------- 3 vasa1 vasa1 8453 Oct  1  2012 nanorc
38262 -rw------- 3 vasa1 vasa1 8453 Oct  1  2012 nanorc
09:23 PM .../TOSHIBA EXT/noobak $ 

```shows that the three "copies" of nanorc are actually one and the same and so won't occupy the space of three files.

---

### Post by papibe on 2015-07-24
Hi vasa1.

For the most part looks good. I usually disencourage people from scripting their own backup solutions. My main advice has always been:
> Well-know tools have been proven to work, your script has to be debug and tested in order to work fine, and it still may be on an alpha state.
In this case, I'd be recommending taking a look at 'Back in Time', or rdiff-backup.

Having said that....

I have learned **so much** scripting with rsync that I just can't spook people any more. Only show a safer alternative.

Here are some thoughts:

When you repeat a directory, a path, or filename several times, it is better to use global variables to reference them. This way if something change, you can do it in one place. For instance:
```
#!/bin/bash

BACKUP_BASE_DIR="/media/vasa1/TOSHIBA\ EXT/noobak"
FROM_FILE="/home/vasa1/Dropbox/rsync-include.tx"
LINK_FNAME="current"
LOG_FILE="/home/vasa1/$(date +\%I_\%M).rsync.log"

SOURCE="/"

time_stamp="$(date "+%Y-%m-%dT%H:%M:%S")"
DESTINATION="$BACKUP_BASE_DIR/back-$time_stamp"

rsync -lrtv --delete --protect-args --modify-window=1 \
    --link-dest="$BACKUP_BASE_DIR/$LINK_FNAME" \
    --files-from="$FROM_FILE" \
    "$SOURCE" "$DESTINATION" &> "$LOG_FILE"

rm -f "$BACKUP_BASE_DIR/$LINK_FNAME"

ln -s "$DESTINATION" "$BACKUP_BASE_DIR/$LINK_FNAME"
```
If the drive is not mounted, the script may fail, or worst, it would start creating files on your root directory. You can do a simple directory test:
```
...
# Check if path exists.
if [ ! -e "$BACKUP_BASE_DIR" ]; then
    echo "Directory does not exist. Stopping."
    exit 1
fi
```
or, you can check if the drive is mounted exactly there:
```
...
BU_MOUNT_POINT="/media/vasa1/TOSHIBA"
...
# Check if external disk is mounted.
if ! mountpoint -q "$BU_MOUNT_POINT" ; then
    echo "Backup drive is not mounted. Stopping."
    exit 2
fi
```
I've noticed that the backups are very close together in time (testing maybe?). If this is going to be the standard, you may need to consider the case that the previous backup hasn't finished yet when the script is called. This could be manage by using a pseudo lock file (not perfect, but works in simple cases).

At the begining of the script:
```
# Check if lock file exists.
if [ -f "$LOCK_FILE" ]; then
    echo "Last backup still working. Stopping."
    exit 3
fi
# Creating a lock file.
touch "$LOCK_FILE"
```
Then at the end:
```
rm -f "$LOCK_FILE"
```
That would be my main thoughts

I hope these ideas help you. Let us know how it goes.
Regards

P.S.: other common practices/ideas: only allow certain user to run the script (special backup user, or root?), and check if there's enough space to do the backup to begin with.

---

### Post by vasa1 on 2015-07-27
@papibe, thank you yet again for your patient and thorough response :)

> 
    For the most part looks good. I usually disencourage people from scripting their own backup solutions. My main advice has always been:
    Well-know tools have been proven to work, your script has to be debug and tested in order to work fine, and it still may be on an alpha state.
    In this case, I'd be recommending taking a look at 'Back in Time', or rdiff-backup.

    Having said that....

    I have learned so much scripting with rsync that I just can't spook people any more. Only show a safer alternative.


I think I've got most of what I want going well for now. I definitely will monitor the log and critical files to be sure that things are going as planned. I feel I'll learn more this way.

Also, my needs are relatively simple.

Re. your other points,

>     When you repeat a directory, a path, or filename several times, it is better to use global variables to reference them. This way if something change, you can do it in one place. ...
I will try that in the next few days ...
>     If the drive is not mounted, the script may fail, or worst, it would start creating files on your root directory. You can do a simple directory test:
    Code:

    ...
    # Check if path exists.
    if [ ! -e "$BACKUP_BASE_DIR" ]; then
        echo "Directory does not exist. Stopping."
        exit 1
    fi

That's something I didn't think of. I sometimes unmount the USB drive to copy stuff to a smaller pendrive and may forget to remount it! Otherwise, TOSHIBA EXT is always connected to my laptop (which is always in the same physical location). Plus I have "udisksctl mount -b /dev/sdb1" as part of my Openbox autostart file.

To check if the device is mounted, I used grep instead because I'm not familiar with the use of [, ], !, etc:
```
#!/bin/bash

time_stamp=$(date "+%Y%m%dT%H%M%S")
if
grep -iq toshiba /proc/mounts; then
rsync -lrtv --delete --protect-args --modify-window=1 \
--link-dest=/media/vasa1/TOSHIBA\ EXT/noobak/current \
--files-from=/home/vasa1/Dropbox/rsync-include.txt / \
/media/vasa1/TOSHIBA\ EXT/noobak/B-$time_stamp \
&> /home/vasa1/"$(date +\%I_\%M)"rsync.log
rm -rf /media/vasa1/TOSHIBA\ EXT/noobak/current
ln -s /media/vasa1/TOSHIBA\ EXT/noobak/B-$time_stamp /media/vasa1/TOSHIBA\ EXT/noobak/current
else
echo "Toshiba not mounted!"
fi

```
I checked that that works by loading the script from a terminal (after unmounting TOSHIBA EXT) **but what will happen to the "echo" part when I run the script via cron if TOSHIBA EXT isn't mounted?**
> 
    or, you can check if the drive is mounted exactly there:
...
If I run the code as I detailed above, would checking for the mount point be necessary? As things stand, I plug "TOSHIBA EXT" into the same USB port each time and the only other USB device attached to my laptop is a mouse.

>     I've noticed that the backups are very close together in time (testing maybe?). If this is going to be the standard, you may need to consider the case that the previous backup hasn't finished yet when the script is called. This could be manage by using a pseudo lock file (not perfect, but works in simple cases).
Yes, That was only for testing the script. Otherwise, I won't be running the script at less than hourly intervals.
>     P.S.: other common practices/ideas: only allow certain user to run the script (special backup user, or root?), and check if there's enough space to do the backup to begin with. 
I'm the only user of the laptop and I'm running rsync as my regular user. I am also keeping a close watch on space.

So thanks once again for your feedback!

---

