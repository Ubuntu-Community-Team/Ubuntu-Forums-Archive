---
title: "Windows folder shares mounted vis cifs causing system lockups when Windows reboots"
date: 2014-12-22
forum: General Help
---

### Post by mike248 on 2014-12-22
Running Kub14.04

I have all my NAS folders mounted via CIFS in my FStab using a credentials file.  I then decided to mount some Windows shares as well and ran into some major problems with applications locking up that had a file from the Windows share or was in the parent folder of the Windows mount.  

Now I have to admit, i'm not an expert in Linux and I need to figure out pest practices on how to mount local drives and network drives.  

The Windows shares are:  //Win7/1tb  and //Win7/2tb .  I created the folders 1tb and 2tb in my home directory:  /home/user/1tb and /home/user/2tb.  I mounted by ```
mount -t cifs //server/share /home/user/1tb/ -o rw,user=name
``` and then entered the password when prompted.  Everything seemed hunky dorey until for some reason Windows rebooted.  

I had 3 windows of dolphin open, each split screen, and one panel on each had a folder from the 1tb or 2tb open.  Each of these app was useless as I coulnd't do anyting with them.  I opened ne dolphin and as soon as I entered my home directory, it locked up as well.   Opening Terminal and ls or df locked up that tab.

Opening terminal, it opened into my home folder and as long as I moved down a dir, i was fine, or I could sudo su into root.  I found that I had to kill any app that was open to my home dir or open to a folder in the windows share.  once that was done I had to umount the /win7/1tb and //win7/2tb.  Once that was done I could df with do problems and things started to be normal again.  

Now the strange thing is that every night my NAS reboots and I have 5-7 mounts from that device.  Not once have I had a problem with this and it has never locked up my machine.  Once in a while it may take ~5 seconds to access the content, but I think that is the drive spinning up after hours of inuse.  

Now, what can I do to avoid this?  Does it have anyting to do with the drives being NTFS on the Windows system and should I have used the command ```
mount -t ntfs //server/share /home/user/1tb/ -o rw,user=username
```
I tried this and I get a resonse like this:
> root@Linux:/mnt/Win7# mount -t ntfs-3g //win7/500-1 /mnt/win7/500-1 -o rw,user=usernamel
ntfs-3g: Failed to access volume '//ms7/500-1': No such file or directory

ntfs-3g 2013.1.13AR.1 external FUSE 29 - Third Generation NTFS Driver
                Configuration type 7, XATTRS are on, POSIX ACLS are on

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2012 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), windows_names, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

News, support and information:  [http://tuxera.com](http://tuxera.com)



I was told that this wouldn't work as cifs was the onlything that would allow to mount files this way.  I know that my NAS formats to CIFS so maybe that is why the NAS doesn't have a problem.  


OR

Could it be the mount point in the home directory?

SO since CIFS seems to work, how should I go about making this work without it locking up the system every few hours?

---

