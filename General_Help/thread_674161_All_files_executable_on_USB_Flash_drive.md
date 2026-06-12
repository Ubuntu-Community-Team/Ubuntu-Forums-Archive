---
title: "All files executable on USB Flash drive?"
date: 2008-01-21
forum: General Help
---

### Post by Simian Man on 2008-01-21
Hello all!

When I browse my USB Flash Drive with the terminal window, all of the files on it show up as having executable privileges.  This means whenever I call 'ls' they all are displayed in green.  I can take away the executable privilege with chmod, but it always comes back.

I never realized I relied on the colors of ls so much, but it makes it really hard to work with.  Thanks for any help!

BTW I am using Feisty Fawn.

---

### Post by elint on 2008-01-21
> **Simian Man said:**
> Hello all!

When I browse my USB Flash Drive with the terminal window, all of the files on it show up as having executable privileges.  This means whenever I call 'ls' they all are displayed in green.  I can take away the executable privilege with chmod, but it always comes back.

I never realized I relied on the colors of ls so much, but it makes it really hard to work with.  Thanks for any help!

BTW I am using Feisty Fawn.

I don't know the solution, but I have an explanation:  Your USB flash drive is FAT32, so doesn't have Linux permissions assigned to each file.  So all files will get a default permission set applied to them when the drive is mounted.  Typically, I'd edit /etc/fstab and set fmask=111 in the Options section (to mask out "executable" for files, so they're all just read/write), but I don't know where to set this option with Ubuntu's auto-mounter.  Obviously each time you re-mount the key, it's just loading the same default permission set for mounted FAT drives -- when you chmod the files, you're not actually changing any saved permissions on the drive itself.

I'll dig around and look, but hopefully somebody will find an answer for you quicker.

---

### Post by cdenley on 2008-01-21
Run gconf-editor, go to system>storage>default_options>vfat, double click "mount_options" on the right, click "add", enter the text "fmask=177", click ok.  That will change the permissions for any fat-formatted usb drives. Since fat doesn't have unix permissions, gnome just assigns it default permissions at mount time, which can be configured here. I did this on gutsy, but I'm sure feisty will work the same.

Or, you can run this command:
```

gconftool -s /system/storage/default_options/vfat/mount_options \
 -t list --list-type string \
[shortname=mixed,uid=,utf8,umask=077,exec,usefree,fmask=177]

```

---

