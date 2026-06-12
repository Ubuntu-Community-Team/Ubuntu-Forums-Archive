---
title: "Mount point ?"
date: 2021-01-12
forum: General Help
---

### Post by yegnal on 2021-01-12
Greetings;

Things were fine until suddenly I noticed Gimp was unable to access a directory I had been using all along..  No changes to the system occurred that I know of....

The location in question is an installed 500gb physical hard drive, the fstab entry is:
/dev/disk/by-uuid/779A70C23D0FD88C /media/me/MISCSHARED auto nosuid,nodev,nofail,x-gvfs-hide,umask=0000

What I noticed is that the mount point is owned by root.  I tried unsuccessfully to change the ownership while it was mounted.  Then I umounted and somehow now have two identically named mount points (/media/me/MISCSHARED).  One is owned by me, one is owned by root.  

a. Immediately after re-booting or if I do sudo mount -a; /media/me has MISCSHARED as expected but it's highlighted.
b. If I then sudo umount that mount point and again perform an ls -l of /media/me, I still see MISCSHARED but in plain text.

a & b conditions above have different contents depending on which state I'm in.  

So confused.

---

### Post by The Cog on 2021-01-12
Can you post the output of "ls -l /media/me" for both conditions a and b?

---

### Post by yegnal on 2021-01-12
a.  drwxrwxrwx 1 root root 8192 Jan 12 13:22 MISCSHARED
b.  drwxr-xr-x 2 me me 4096 Jan 12 14:31 MISCSHARED

---

### Post by yegnal on 2021-01-12
[IMG]https://www.dropbox.com/s/thg1rw27hdtz0si/Screenshot%20from%202021-01-12%2013-52-28.png?dl=0[/IMG]Screenshot[IMG]https://www.dropbox.com/s/thg1rw27hdtz0si/Screenshot%20from%202021-01-12%2013-52-28.png?dl=0[/IMG]

---

### Post by yegnal on 2021-01-12
[IMG]https://www.dropbox.com/s/thg1rw27hdtz0si/Screenshot%20from%202021-01-12%2013-52-28.png?dl=0[/IMG]Trying to upload a screenshot

---

### Post by The Cog on 2021-01-12
If I understand right, then the mount point (condition b) is owned by you, but the filesystem on the drive itself (seen when mounted in state a) is owned by root. 
I don't see a problem there, because although it is owned by root, it is writeable by everybody. 
I wonder if it's been mounted readonly because of a fliesystem problem. Can you post the output of these commands while it's mounted please:
```
mount | grep MISCSHARED
touch /media/me/MISCSHARED/test_write_file
rm /media/me/MISCSHARED/test_write_file
```
I see the screenshot, but don't know what the colouring indicates.

---

### Post by yegnal on 2021-01-12
[COLOR=#000000][FONT=&quot]

[/FONT][/COLOR]

mount | grep MISCSHARED:
/dev/sde1 on /media/me/MISCSHARED type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,x-gvfs-hide)


touch /media/me/MISCSHARED/test_write_file:
This command worked, I removed the test file afterwards.

The only program with a problem is Gimp, I'm starting to think this is unique to that software.  

It's just strange how started so unexpectedly and without any changes being made to the computer...[FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][/FONT]

---

### Post by TheFu on 2021-01-12
chmod and chown don't work with NTFS or FAT-whatever file systems.  The only way to control ownership with this is via mount options.

The better answer would be to backup all your data on that drive, format using a native Linux file system like EXT4, then mount it again. At that point, chown and chmod will work as expected.

The **ls -al** lines would be more useful if you labeled which was for what situation.

If you need NTFS for some reason not stated, there are lots of mount examples in these forums for doing that.  Just search for "big_writes" and my userid here.

BTW, there is seldom any reason to post screenshots here, unless it is a GUI specific issue. This is not.

---

### Post by Impavidus on 2021-01-13
> **yegnal said:**
> 
The only program with a problem is Gimp, I'm starting to think this is unique to that software.  

It's just strange how started so unexpectedly and without any changes being made to the computer...
Could it be a snap issue? Software packages can come as deb packages and snap packages. Snap packages are restricted in the directories they can access, and /media may or may not be accessible. Maybe your gimp is a snap package. The issue could have suddenly appeared as the package was upgraded. That's one of the reasons why I avoid snaps.

---

### Post by TheFu on 2021-01-13
> **Impavidus said:**
> Could it be a snap issue? Software packages can come as deb packages and snap packages. Snap packages are restricted in the directories they can access, and /media may or may not be accessible. Maybe your gimp is a snap package. The issue could have suddenly appeared as the package was upgraded. That's one of the reasons why I avoid snaps.

Awwww, snaps.  I avoid them too. ome of my notes about snaps:
```

$ snap list
$ snap remove {name}
https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022
# Hook up snaps to access removable-media
    # snapd v2.36+.
$ snap connect chromium:removable-media
https://snapcraft.io/docs/removable-media-interface has more
  # See the available options for a snap package
$ snap connections <application-name> --all

https://snapcraft.io/docs/snap-confinement 

```
The removable-media connection is secret-squirrel code to allow 1 snap access to storage in /media ad /mnt storage. The snap package creator as to allow that connection - some do not.

---

### Post by SeijiSensei on 2021-01-13
> **Impavidus said:**
> Could it be a snap issue?
I seem to recall someone posting here about file access issues using the snap for GIMP. One reason why I avoid all snaps.

---

