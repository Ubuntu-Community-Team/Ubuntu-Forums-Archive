---
title: "Hard disk almost full."
date: 2016-01-13
forum: General Help
---

### Post by courseinmiracles2 on 2016-01-13
HI All, I noticed there was no solution to this my problem is similar but not quite the same I am using 15.10, just upgraded. I have a 500gb HD which is saying I have used almost 90% of. but when I ran 

```
 df -h

Filesystem      Size     Used     Avail   Use%  Mounted on
udev              1.9G         0      1.9G      0%     /dev
tmpfs            376M      21M    355M      6%     /run
/dev/sda1      455G    378G      54G    88%     /
tmpfs             1.9G      88K     1.9G      1%     /dev/shm
tmpfs             5.0M     4.0K     5.0M      1%     /run/lock
tmpfs             1.9G        0       1.9G      0%     /sys/fs/cgroup
tmpfs            376M      60K     376M      1%    /run/user/1000
```


When I ran 
```
sudo du -h -d 1 | sort -h
4.0K    ./.gnome2_private
4.0K    ./.gphoto
4.0K    ./.gvfs
4.0K    ./.hplip
4.0K    ./office-images
4.0K    ./Public
4.0K    ./.ssh
4.0K    ./Templates
4.0K    ./Videos
8.0K    ./.cups
8.0K    ./media
8.0K    ./.vidalia
12K    ./.dbus
12K    ./.gnome2
12K    ./My PhotoFilmStrips
16K    ./.audacity-data
28K    ./.gnupg
36K    ./.pki
40K    ./.filezilla
56K    ./tarmak
72K    ./.lyrics
92K    ./.bluefish
120K    ./.thumbnails
148K    ./.amaya
176K    ./Happy Days
300K    ./.gconf
460K    ./.openshot
612K    ./.macromedia
840K    ./.kingsoft
1.0M    ./.gstreamer-0.10
1.2M    ./.compiz
1.7M    ./.adobe
3.7M    ./.quodlibet
19M    ./FileZilla3
21M    ./.mozilla
32M    ./.clamtk
35M    ./.gimp-2.8
37M    ./.Skype
42M    ./.dropbox
167M    ./.dropbox-dist
170M    ./.config
202M    ./.tor-browser
236M    ./Pictures
264M    ./Calibre Library
589M    ./.thunderbird
602M    ./.local
851M    ./.cache
1.7G    ./Documents
1.7G    ./WEBSITES
1.8G    ./Downloads
2.4G    ./Desktop
5.5G    ./Dropbox
12G    ./deja-dup
19G    ./Music
47G    .
```

Am I right that this is saying 47gb TOTAL? If so whats using up the space?
Any help greatly appreciated.

---

### Post by howefield on 2016-01-13
Post moved to own thread.

---

### Post by philinux on 2016-01-13
Have a read through this.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by courseinmiracles2 on 2016-01-13
Ok, I found the culprit.

/var/log/uvcdynctrl-udev.log

It's propagating from

/lib/udev/uvcdynctrl

It's a 347GB txt file. Can I delete it. How do I do that,.i.e. terminal command?

---

### Post by ian-weisser on 2016-01-13
You can easily delete it...but before doing so you should find out why udev has so many errors and fix the real problem.

```
tail -n 500 /var/log/uvcdynctrl-udev.log > /tmp/uvcdynctrl-udev.log.tail   ## Preserve the last 500 lines of the log. Please show the contents to us.
sudo rm /var/log/uvcdynctrl-udev.log                                       ## Delete the enormous file
```

---

### Post by buzzingrobot on 2016-01-13
Seems to be a bug, first reported in 2011.:eek: Something to do with webcameras, apparently.  Here it is: [https://bugs.launchpad.net/ubuntu/+source/libwebcam/+bug/811604](https://bugs.launchpad.net/ubuntu/+source/libwebcam/+bug/811604)

You might consider registering an account at launchpad.net so you can click the "Does This Bug Affect You?" link at the top of that page to add your "Me Too!".

To remove that file, open a terminal, change directory to /var/log ```
cd /var/log
``` and use ```
sudo rm -rf uvcdynctrl-udev.log
```

---

### Post by courseinmiracles2 on 2016-01-13
Here it is:
tail -n 500 /var/log/uvcdynctrl-udev.log

  
[libwebcam] Warning: The driver behind device video0 has a slightly buggy implementation
  of the V4L2_CTRL_FLAG_NEXT_CTRL flag. It does not return the next higher
  control ID if a control query fails. A workaround has been enabled.

Just this message, repeated...

FIle deleted...Thanks

---

### Post by courseinmiracles2 on 2016-01-14
Post script...
I added my problem in launchpad. Still no solution other than deleting the file. But man my machine can breathe again. Thanks for all the help!

P.P.S I also had to delete the file uvcdynctrl  found in /lib/udev/  because I noticed it had simply started to generate another error log file. After restart everything seems to be ok...touch wood ;)

---

