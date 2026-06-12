---
title: "How do I set automatic permissions on automatically mounted external USB hard drives?"
date: 2008-02-18
forum: General Help
---

### Post by nattugglan on 2008-02-18
When I plug in an external ext2 or ext3 USB hard drive, the owner is shown as 113 or root. Never giving me full access to the drive automatically.

How do I get full permission automatically?
If I put a line for the drive(s) in /etc/fstab, i.e. with the option "user", the automatic mounting breaks, and the mount point needs to be created manually.

I want to have the automatic mounting of external hard drives, but I also want to get full permission on the drives automatically. Without the need to manually edit /etc/fstab or manually **chown -R** each mount point/drive.

How do I do this?

I have searched high and low for a solution to this, but so far found nothing that works.

:. nattugglan

---

### Post by xc3RnbFO8P on 2008-02-18
mistake

---

### Post by ajgreeny on 2008-02-18
If it is formatted as fat32 or fat16 it would not normally support permissions and would be owned by whoever's session was live at the time.  Or at least I think that's the case.  If it is ext3 it will be shown as owned by root.

---

### Post by cdenley on 2008-02-18
Here is a command that will change the default permissions for automatically mounted fat partitions:
```

gconftool -s /system/storage/default_options/vfat/mount_options \
 -t list --list-type string \
[shortname=mixed,uid=,utf8,umask=027,exec,usefree,fmask=137]

```

If you want to force a uid for the owner, give the uid after "uid=" in the above command. You can also change the default permissions by setting umask and fmask.

---

### Post by nattugglan on 2008-02-18
Thank you for your replies.
Sorry. My bad. I totally blanked out and failed to mention that it is ext2 and ext3 drives I'm talking about.

I'm currently experimenting with udev rules.:

```
sudo gedit /etc/udev/rules.d/10-local.rules
```

One example.:
```
ATTRS{serial}=="************", ATTRS{product}=="OneTouch        ", NAME="maxtor_500gb", SYMLINK="usb_hdd/maxtor_500gb", GROUP="plugdev", MODE="0666"
```

Perhaps /etc/udev/udev.conf could be the solution?
I'm using Ubuntu 7.04 PPC right now, and udev.conf only contains the following.

```
# udev.conf

# The initial syslog(3) priority: "err", "info", "debug" or its
# numerical equivalent. For runtime debugging, the daemons internal
# state can be changed with: "udevcontrol log_priority=<value>".
udev_log="err"

```

:. nattugglan

---

### Post by cdenley on 2008-02-18
I did a quick test with this. If the drive is mounted at /media/disk, then you run a "chown me /media/disk", the user "me" should be the owner of the root directory in that filesystem. You can also change the owner of any file or drives in that filesystem. All changes should remain after the drive is unmounted. As far as I know, udev cannot change the permissions on mounted filesystems, only devices.

For ext3, all permissions are contained in filesystem by uid and gid, regardless of how they are mounted. If the filesystem permissions have a uid or gid that does not exist on the local system, then "ls -l" will show the uid/gid, not the name of the user/group since it does not exist. Are you moving this drive between two systems?

---

### Post by nattugglan on 2008-02-18
> **cdenley said:**
> As far as I know, udev cannot change the permissions on mounted filesystems, only devices.
Yes. I was thinking this as well. It would affect **/dev/maxtor_500gb** and **/dev/usb_hdd/maxtor_500gb**, but not the final mounted filesystem in **/media/maxtor_500gb**.

> **cdenley said:**
> For ext3, all permissions are contained in filesystem by uid and gid, regardless of how they are mounted. If the filesystem permissions have a uid or gid that does not exist on the local system, then "ls -l" will show the uid/gid, not the name of the user/group since it does not exist. Are you moving this drive between two systems?

Thank you for illuminating that.
Yes, the drive in question was previously connected to another box. And I need to be able to smoothly move the drives between several systems.

UID and GID are normally 1000 for the first user created on the system, IIRC.
113, which is shown as the owner in some cases for me, does not exist as a user on the PPC system I'm using right now, but there is a group called 113(lpadmin). I only have one user on the PPC system, and that user has the standard UID/GID 1000.

On my MythTV box the first user was also created as UID/GID 1000, but the mythtv user, which I use as the main user on that system, has UID 113 and GID 122.

:. nattugglan

---

### Post by cdenley on 2008-02-18
You can run "chmod -R 777 /media/maxtor_500gb", which will give everyone full access to everything currently on the drive. However, this will not effect files and directories created in the future.

You can keep the uid's identical on all your systems to make sure the permissions apply to the correct user.

You can give up on ext3, and use fat32 instead since it does not have security permissions. Just make sure you unmount it before disconnecting it, since it is a lot more vulnerable to corruption.

---

### Post by nattugglan on 2008-02-18
I'm looking for a solution that doesn't require manual creation of mount points, and manual change of the drive's permissions every time the drives are connected to a new computer, or swapped between different users. I've been manually changing the permissions on all drives so far, but it is a real pain in the b*tt. :|

I want to use ext2 and ext3. 

I've been thinking of changing the UID/GID of the mythtv user on my MythTV box, to eliminate this one obstacle, but that is something that potentially can wreak havoc on the file permissions and operation of that system. I need that system functioning 100%. Besides, I'm looking for a solution that will work between several computers and several different users.

FAT32 is not an option.

Perhaps a script connected to the udev rule can take care of the permissions - only requiring the user to enter the sudo password?

What controls the behaviour (and permissions used) of the auto mount in Ubuntu?
Isn't there a way to modify this behaviour? And the permissions used?

Will creating a group on each system work? Making sure that all users are a member of this group - and controlling the permissions by always using this group?

I.e. I used the group plugdev in my udev example above.

:. nattugglan

---

### Post by cdenley on 2008-02-18
Look at my first reply. I gave instructions for vfat, but I'm pretty sure you can set automount options for ext3 filesystems using this same method. I never tried it. The problem, though, is that there aren't many options for mounting ext3 filesystems. Read "man mount", scroll down to the "Mount options for ext3" section. As far as I know, there is no way to circumvent unix permissions, except of course for running something like "gksudo nautilis".

---

### Post by mudhead on 2008-05-04
Hello,

Did you already find a solution to your problem?
I'm struggling with the same problem, but with
fixed disks: I have an ext2 partition containing music,
files and want to mount it so it is not owned by root,
on /data/audio.

The only solution I found so far is to create a dir
named audio in the ext2 partition to be mounted
itself, and give that appropriate permissions.
This results in a path /data/audio/audio,
which I'm not happy with, but at least the 'second'
audio dir has the permissions/owner I want.

Best regards,
Peter.

---

### Post by cdenley on 2008-05-04
If the filesystem supports unix permissions, the permissions on the filesystem are used. You can't change the owner with a mount option. You have to change the owner on the filesystem. Use this command while it is mounted
```

sudo chown 1000 /data/audio

```

---

