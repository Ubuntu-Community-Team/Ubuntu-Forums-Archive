---
title: "cannot rename file"
date: 2023-09-25
forum: General Help
---

### Post by jgw on 2023-09-25
I am trying to rename a file.  

The file is /media/3tb   

file 3tb

```
3tb: directory
root@greg-desktop:/media# stat 3tb
  File: 3tb
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 821h/2081d	Inode: 2           Links: 7
Access: (0700/drwx------)  Uid: ( 1000/    greg)   Gid: ( 1000/    greg)
Access: 2023-09-24 15:03:46.043436639 -0700
Modify: 2023-09-24 15:03:44.399372384 -0700
Change: 2023-09-24 15:03:44.399372384 -0700
 Birth: 2023-06-01 13:15:20.000000000 -0700
root@greg-desktop:/media# 

```

opened terminal
I set myself as a super user (sudo su)
Then ran nautilus
went to 3tb and tried to rename the file and failed.

got a copy pages of the following:
```
(org.gnome.Nautilus:9738): libunity-CRITICAL **: 08:30:03.342: file unity-launcher.c: line 1638: unexpected error: Failed to execute child process “dbus-launch” (No such file or directory) (g-exec-error-quark, 8)

(org.gnome.Nautilus:9738): libunity-CRITICAL **: 08:30:03.342: unity_launcher_entry_dbus_impl_construct: assertion 'conn != NULL' failed

(org.gnome.Nautilus:9738): libunity-CRITICAL **: 08:30:03.345: unity-inspector.vala:96: Unable to connect to session bus: Failed to execute child process “dbus-launch” (No such file or directory)

(org.gnome.Nautilus:9738): dconf-WARNING **: 08:30:03.473: failed to commit changes to dconf: Failed to execute child process “dbus-launch” (No such file or directory)

(org.gnome.Nautilus:9738): dconf-WARNING **: 08:30:03.473: failed to commit changes to dconf: Failed to execute child process “dbus-launch” (No such file or directory)

** (org.gnome.Nautilus:9738): WARNING **: 08:30:03.532: Unable to get contents of the bookmarks file: Error opening file /root/.gtk-bookmarks: No such file or directory

```

Thoughts?

---

### Post by TheFu on 2023-09-25
That appears to be a mounted directory.  While it is "in-use", it cannot be renamed.  I suspect the LABEL of the partition is "3tb" and it is being mounted through gio/gvfs (not the /etc/fstab), so use a disk tool, probably **gparted**, to change the label, then reboot. There are lots of other ways, but based on prior help, I think rebooting is probably the best.  Also, if my assumptions aren't correct, it won't work either.

In general, it is a bad idea to use most GUI programs as root.

Also, I'd rather see people use 
```
sudo -i
```
or 
```
sudo -s
```
depending on your specific needs.

While technically, a directory is a file, in this 1 situation, it cannot be treated that way.  Now, if you were using the device file, which is being mounted, it would be a bad idea to rename it. the workaround for that is to modify the LABEL and you'll find a symlink under /dev/disk/by-label/ that points to the correct, true, device file using the LABEL.  LABEL needs to be unique on the system, BTW. Duplicate labels are not allowed for mounting by LABEL.

In an /etc/fstab entry, something like this could be used.
```
LABEL=3tb    /media/some-name  ext4  defaults 0 2

```
again, lots of assumptions in that line.

---

### Post by ajgreeny on 2023-09-25
I think we've been through this with you at [https://ubuntuforums.org/showthread.php?t=2490928&p=14158869#post14158869](https://ubuntuforums.org/showthread.php?t=2490928&p=14158869#post14158869) before and did not solve the "problem" for you though you did mark it as SOLVED. I think that you are confused about how partitions are mounted and often named according to the label given to that partition so please try to explain in more detail exactly what it is that you want because I am also a bit confused.

Please do not duplicate threads even under a slightly different title as I believe is the case here.

---

### Post by jgw on 2023-09-25
Thank you for the replies

My problem is that I am dealing with a program called sonarr and am trying to make something they call "root folder".  As far as I can tell it has nothing to do with a system root folder like media, for instance.  I actually setup up a link between /media/3tb/Sonarr but sonarr didn't like that either.  I was trying to change the name of the file to see if that would help but, on reflection, I am wasting my time and the time of others for a mystery that I simply cannot figure out and should probably give up.  Changing the name of /media/3tb was about all that was left to do but, I suspect, that too wouldn't do the trick.  I have changed permissions, names, locations, whatever and failed each and every step of the way.  Nothing seems to work.  

Anyway first, my apologies.  Thank you for your help but I have decided to give up on changing the name because I no longer think that will help me on my quest.

---

### Post by TheFu on 2023-09-25
I suspect many of the issues here are self-inflicted because you decided to use a mount point, not a sub-directory under the mount point.  Of the 100,000 possible locations, you happened to pick one of 2-5 that would have this specific issue.

Programs often have what they call a root folder  -FOR THAT PROGRAM-.  It never has anything to do with the OS.  I prefer to call it the program's TOPDIR myself.

```
TOPDIR/
&#9500;&#9472;&#9472; bin
&#9500;&#9472;&#9472; doc
&#9500;&#9472;&#9472; etc
&#9500;&#9472;&#9472; lib
&#9492;&#9472;&#9472; man

```
The "TOPDIR" can be picked up and moved almost anywhere.  It is also common to have an environment variable that sets the location for the TOPDIR.  These typically have "_HOME" in them,. For example, JAVA_HOME or APACHE_HOME or PROGRAM_X_HOME.  Is there a SONARR_HOME settings in their instructions?  Perhaps not.  Looks like it has a webgui for setup post-install, similar to what other media centers use.  

I've never used Sonarr (I don't BT stuff), but I have used about 5 different media centers.  Looks like the programs and settings are handled at install time or later through the webgui.  I suspect the only thing you really need to set locally is the path for your Movies and the path for your TV Shows.  Those are usually 2 different locations due to the way that scraping from the filenames is performed.  I think most media center programs use similar naming methods, so they are all interchangeable with the same media library.  However, I don't know this as fact beyond the 5 media center's I've used.

---

