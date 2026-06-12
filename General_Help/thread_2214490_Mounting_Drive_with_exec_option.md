---
title: "Mounting Drive with exec option"
date: 2014-04-01
forum: General Help
---

### Post by box02-0 on 2014-04-01
Hi.

Ubuntu 12.10   gnome
I want to be able to execute python programs on an NTFS drive (SDA7). When the system is booted, SDA7 appears as an icon in the Launcher. When I want to actually mount SDA7, I can do so by clicking on the icon. This is fine.

2 questions:

1. What is telling Ubuntu to place the SDA7 icon in Launcher? I do not see any reference to this in FSTAB.

2. I have some python programs saved on SDA7. I am unable to execute them. When I request Nautilus to display the properties of the program, it does not allow me to tick "allow excuting files as programs' box. Somehow the drive must be mounting with the noexec option. How & where can I change this drive to be mounted with the exec option?


Thanks,

M...

---

### Post by SeijiSensei on 2014-04-01
When you double-click the icon, the filesystem gets mounted at that time to some temporary location.  On my Kubuntu 14.04 system that is a directory under /media/username.  You'd be much better off creating an entry in /etc/fstab and [mounting the filesystem to a fixed location at boot]("https://help.ubuntu.com/community/MountingWindowsPartitions#Manual_Configuration").

I have an NTFS partition mounted with the default Ubuntu options.  In /etc/fstab is the entry:
```
UUID=7BD7EBD65436CD44 /windows  ntfs defaults,umask=007,gid=46 0 0
```
If I type "mount" at a command prompt, I see the set of options currently in effect:
```
/dev/sda2 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```
I don't see exec or noexec in either list.

So I decided to do a test.  I wrote a simple bash script in a directory on the NTFS partition.  I had no problem running it from the command prompt.  The "umask=007,gid=46" makes everything on the NTFS partition owned by root and group "plugdev" (gid 46) with both having full read, write, and execute bits set.
```
-rwxrwx--- 1 root plugdev        53 Apr  1 19:09 test.sh
```
I was added to group plugdev automatically when my account was created.  In /etc/group, I see
```
plugdev:x:46:seiji
```
which adds user seiji to group plugdev.  Take a look in /etc/group and add yourself if your account isn't already listed there.  Add multiple accounts with commas like "seiji,nancy".

You could try editing /etc/fstab and specifying "exec" in the options list.  In that case the entry for my NTFS partition above would look like
```
UUID=7BD7EBD65436CD44 /windows  ntfs defaults,umask=007,gid=46*,exec* 0 0
```

---

### Post by mc4man on 2014-04-01
While an fstab entry would solve for you there shouldn't be any issue running exec type files on a user mounted ntfs volume.
Ex. here, ntfs volume mounted from unity launcher or nautilus - 
```
type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

```
The ntfs defaults are set in udisks source & nothing to prevent running exec type files- 
```
static const char *ntfs_defaults[] = { "uid=", "gid=", "dmask=0077", "fmask=0177", NULL };

```
This is in contrast to a Fat volume where you can't run any exec type file, defaults there are -  (red prevents running
```
static const char *vfat_defaults[] = { "uid=", "gid=", "shortname=mixed", "dmask=0077", "utf8=1", "[COLOR="#FF0000"]showexec[/COLOR]", NULL };
```

Edit; the only possible restriction in 12.10 (which I don't have),  is if it still used "cautious-launcher" but that was only on wine & java & may have been abandoned by 12.10, don't remember

---

### Post by box02-0 on 2014-04-02
I've decided that fstab should be the place to properly mount sda7 - which has a volume name of:   **DELL Dynamic Data**

I want to mount it under:     **media/mg/**

so it would look like this:    **media/mg/DELL Dynamic Data/**
        
and all the files in sda7 would fall under **DELL Dynamic Data**

I added a line in fstab:
/dev/sda7 /media/mg/"DELL Dynamic Data" auto,rw,suid,dev,exec,auto,ntfs-3g,x-gvfs-name=DELL%20Dynamic%20Data 0 0

but I end up with a directory:
  **media/mg/"DELL**
  
I tried setting the mount point as:    /media/mg/DELL%20Dynamic%20Data
and end up with a directory:
   **media/mg/DELL**
 
How do I deal with spaces in a mount point directory name?

And now that I have a directory called **"DELL**, how do I delete it?


Thanks,

M...

---

### Post by steeldriver on 2014-04-02
Try using the octal escape sequence for the spaces i.e. \040 instead of %20

You should be able to remove the empty mount point using rmdir - you will need to escape the double quote I think

```
sudo rmdir /media/mg/\"Dell
```

Not sure about some of your mount options - did you just copy those from the gvfs-mount? Some of those might not be appropriate if the device is not actually mounted by gvfs.

---

### Post by box02-0 on 2014-04-03
Thank you steeldriver.

/dev/sda7 /media/mg/DELL\040Dynamic\040Data auto,rw,suid,dev,exec,auto,ntfs-3g,x-gvfs-name=DELL%20Dynamic%20Data 0 0

works. I can now execute programs. 

When I cd   /media/mg    in terminal, I notice that "DELL Dynamic Data", and all the files within it, have a green background. How do I find out what that means?


Yes, ubuntu is addictive. I love to see Windows in my rearview mirror!


Thanks again,

M...

---

