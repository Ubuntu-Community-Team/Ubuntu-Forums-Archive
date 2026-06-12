---
title: "Floppies mount fine, but can't seem to edit them in in Xubuntu 14.04?"
date: 2014-05-06
forum: General Help
---

### Post by RallyDarkstrike on 2014-05-06
Hi all,

Still working out the teething problems on my fresh install Xubuntu 14.04 box. I've got a Floppy drive installed on it that I need to use (long story!) which is picking up and mounting Floppy drives with no problems at all. I can view their contents and open the files just fine, however, it does not seem like I can edit anything. Right-clicking on the floppy with any File Manager has things like 'rename', 'Create New Folder', 'Create New Document", etc. grayed out, and, if I edit an existing file on the a floppy disk and try to save it, I either get an error message or the 'Save' function is grayed out as well, depending what program I am using.

Any ideas as to what is going on? Help and suggestions would be kindly appreciated! :)

[COLOR=#ff0000]EDIT - For the record, the fstab file line for the floppy drive looks like this:

**/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0**[/COLOR]

---

### Post by MrSteve on 2014-05-06
on the side of the floppy disc there should be a slide button which locks the floppy into read only or read and write mode
please check and see if this slide is set to read/write ...

---

### Post by RallyDarkstrike on 2014-05-06
Hi MrSteve - that was the first thing I checked. I've tried 4 different known-to-be-working floppy disks, having this same problem with all of them. However, the switch you mention; all of them were unlocked and set to read/write, so it's unfortunately not that simple :(

---

### Post by MrSteve on 2014-05-06
can you copy the contents of the floppy to a folder on the HDD ?

as the floppy may need to be reformatted ...

---

### Post by RallyDarkstrike on 2014-05-06
It's not one single floppy, this happens with ANY floppy I try, and I know they all work as I can use them, no problem, in my Windows machine.

---

### Post by MrSteve on 2014-05-06
sorry run out of ideas ...
but it maybe worth while copying one file to the desk top and see if that can be opened ...

---

### Post by SeijiSensei on 2014-05-06
What if you mount them as root with sudo?  Maybe whatever method Ubuntu is using to mount them doesn't grant you write permissions to the device.  If you can mount them read/write as root, but not with your user account, simply open a terminal window, mount them as root with sudo, and make sure everything on the disk has 777 permissions.  Then see if you can write to the device from your normal desktop with your own permissions.

It's been so long since I've used a floppy that I can't really recall how permissions were handled.  I was probably mounting them as root then anyway and writing to them as root as well.

What if you mount them as root with sudo?  Maybe whatever method Ubuntu is using to mount them doesn't grant you write permissions to the device.  If you can mount them read/write as root, but not with your user account, simply open a terminal window, mount them as root with sudo, and make sure everything on the disk has 777 permissions.  Then see if you can write to the device from your normal desktop with your own permissions.

It's been so long since I've used a floppy that I can't really recall how permissions were handled.  I was probably mounting them as root then anyway and writing to them as root as well.

If you mount them the way you normally do, then type the "mount" command in a terminal, what permissions does the floppy have?  What about the permissions of its mount point?

---

### Post by RallyDarkstrike on 2014-05-06
> **SeijiSensei said:**
> What if you mount them as root with sudo?  Maybe whatever method Ubuntu is using to mount them doesn't grant you write permissions to the device.  If you can mount them read/write as root, but not with your user account, simply open a terminal window, mount them as root with sudo, and make sure everything on the disk has 777 permissions.  Then see if you can write to the device from your normal desktop with your own permissions.

It's been so long since I've used a floppy that I can't really recall how permissions were handled.  I was probably mounting them as root then anyway and writing to them as root as well.

If you mount them the way you normally do, then type the "mount" command in a terminal, what permissions does the floppy have?  What about the permissions of its mount point?

According to the fstab, all users have permission to write to the disk....however, trying to mount the drive through Nemo as a normal user is what causes the issues listed in my post. If I start Nemo as Root and THEN mount the drive, I can do whatever I want with it no problem, so it does seem to be a permission issue.

What can I change to allow my normal user account to read/write to the drive?

---

### Post by steeldriver on 2014-05-06
If you are mounting the device via a GUI filemanager, are you sure it's actually using the fstab entry (rather than fuse / gvfs or whatever the Xubuntu equivalent is)? Have you looked at the *actual* mount options (using the 'mount' command)?

---

### Post by RallyDarkstrike on 2014-05-06
Ok, I opened Terminal and ran the Mount command and it gave me a list of info...not sure what am looking for to tell you though...?

[COLOR=#ff0000]EDIT - There is a listing for fuse it seems?

**gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=darkstrike)**[/COLOR]

---

### Post by RallyDarkstrike on 2014-05-07
Hi all,

Sorry for the double-post, but just thought I would post a update explaining that I have somehow fixed my issue...

I managed to figure out my issue myself! (To be honest, not sure what I did, but I did it, HAHA! :P)

I was browsing through some other forums where people were having similar issues. I noticed that one guy had the same issue as us, but had an extra command in his fstab file for the floppy - ```
umask=0
```

I added that one command to my fstab so my floppy line now looks like this:

```
/dev/fd0        /media/floppy0  auto   rw,user,noauto,exec,umask=0,utf8 0       0
```

And...voila! Mounting / unmounting, reading and writing anything to the disks in the drive seems to work fine now! Could anybody tell me what this command does so I actually know what I've done? LOL

---

### Post by baphomet2 on 2014-05-07
umask is a command to set initial permissions on newly created/mounted files/directories.  If you are familiar with chmod the formula is backwards.  So a umask of 0 (or 0000) is the equivalent of chmod 777 on newly created/mounted files/directories.  In this case the effective permissions of your newly mounted floppy is world read/writable.  I recommend reading the man page for umask as it comes in handy if you are supporting multiple users and put it in the system environment settings.

---

