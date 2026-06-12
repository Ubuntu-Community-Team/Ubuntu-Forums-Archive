---
title: "Accidentally changed external HD to root owner"
date: 2014-10-10
forum: General Help
---

### Post by AlyssaVS on 2014-10-10
Hi,

I have been using my Toshiba external drive for media storage for several months now and have never had this problem. So I figure that when I recently uninstalled PLEX from this laptop I must have done something stupid. I didn't even think the drive was plugged in but I guess it was. This is the procedure I used from one of the forums:

[COLOR=#000000]Steps:[/COLOR]
[COLOR=#000000]1)Run [/COLOR]
[COLOR=#000000]sudo apt-get purge plexmediaserver[/COLOR]

[COLOR=#000000]2) Remove bulk of plex files[/COLOR]
[COLOR=#000000]sudo rm -rf /var/lib/plexmediaserver[/COLOR]

[COLOR=#000000]3) Remove plex user (very important!)[/COLOR]
[COLOR=#000000]sudo userdel plex[/COLOR]

[COLOR=#000000]4) Remove both /etc/init/plexmediaserver.conf and /etc/default/plexmediaserver[/COLOR]
[COLOR=#000000]sudo rm /etc/init/plexmediaserver.conf[/COLOR]
[COLOR=#000000]sudo rm /etc/default/plexmediaserver[/COLOR]

This is the only thing I have done using root commands since the last time I used the drive. When I try to add or delete folders it says I am not the "owner." But when I open one of the folders in the drive I can then make changes to those files. I am unfamiliar with how these drives are set up but it says NTFS Mac and NTI on two of the folders. It is a 1 TB Toshiba external hard drive. The drive is half full so I'm really concerned about losing this data. 

If anyone could help me get ownership back I'd really appreciate it. Thanks for your time!

---

### Post by kurja on 2014-10-13
I can't see how the commands you listed would have changed ownership of some folders. Anyway, ```
ll
``` will show you ownership and permission of each file/folder. ```
sudo chown group:user <filename>
``` is the command with which you change ownership of files and folders.

---

### Post by irv on 2014-10-13
Is the problem that you can't read or write to the drive? Even if it is own by Root does not make a difference. Have you rebooted lately? If not un-mount the drive, un-plug it. restart the computer and see if it works. It sound like you didn't shut it down (un-mount) before disconnecting it.

---

### Post by AlyssaVS on 2014-10-13
> **kurja said:**
> I can't see how the commands you listed would have changed ownership of some folders. Anyway, ```
ll
``` will show you ownership and permission of each file/folder. ```
sudo chown group:user <filename>
``` is the command with which you change ownership of files and folders.

Thank you I will give this a try.

> **irv said:**
> Is the problem that you can't read or write to the drive? Even if it is own by Root does not make a difference. Have you rebooted lately? If not un-mount the drive, un-plug it. restart the computer and see if it works. It sound like you didn't shut it down (un-mount) before disconnecting it.

The problem is that I can no longer add folders to or delete them from the drive. When I right click or click edit the option is greyed out. When I go to properties of the drive I notice that the owner is "root." I am able to open folders and files that are already there and copy them.

---

### Post by yancek on 2014-10-13
If the owner is root, you need to use sudo.  For example to open a text file from a terminal:  sudo gedit /media/directory/file will open 'file' to edit.  If you go to the directory in the filemanager (nautilus?) you are not root.  You can change the owner:group also.  Where on the  filesystem are these directories/files?  Anything outside your /home/user directory will generally require sudo/root permissions.  iNot sure what your intentions are.

---

### Post by kurja on 2014-10-14
Using sudo works around the problem, which is that ownership and or permissions have changed. chown to take ownership, or if it's just a small-ish number of directories that are acting offensive, ```
sudo chmod 644 <filename>
``` to change permissions to allow owner write access, others can still read.

---

