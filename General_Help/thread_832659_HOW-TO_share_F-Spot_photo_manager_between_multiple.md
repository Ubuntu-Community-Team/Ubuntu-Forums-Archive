---
title: "HOW-TO share F-Spot photo manager between multiple users on a single machine or NFS!"
date: 2008-06-17
forum: General Help
---

### Post by 1066design on 2008-06-17
Hello Ubuntu users,

This is my first post to the Ubuntu forums and I hope this will help someone else with a similar problem to mine.

Before going ahead with this you should note that this is a quick and dirty solution and lacks the elegance a hard coded solution from the F-spot team would yield, but it works.

[LIST=1]
[*]Create group to share F-spot.
[*]Create file structure for shared photos.
[*]Create file structure for shared configuration.
[*]Copy files from main user into shared configuration file structure.
[*]Change owner and group for shared file structure.
[*]Backup and delete configuration files from all users to share F-Spot.
[*]Create symbolic link in each users home directory to the group configuration files with the same name.
[*]Create symbolic link in each users home directory to the group photos directory with the same name.
[*]Open F-spot and select the shared folder as your directory
[/LIST]

The down side to this solution is that F-Spot cannot be used to store just your personal photos. There is, however, a solution for this.

[LIST=1]
[*]Create your private photo configuration directory.
[*]Unpack your original 
[*]Write a shell script overwrite your F-Spot symlink back and fourth between shared and private configuration directory.
[/LIST]

Please forgive me for the abbreviated version..  I am a little short on time..  I plan to revisit this post with more complete instructions..ie. commands.

P.S.  I could uses some help with the shell script.
P.P.S.  The photos and config could reside on another machine as long as its up.

---

### Post by redcharlie on 2009-05-11
See thread [http://ubuntuforums.org/showthread.php?t=696953]("http://ubuntuforums.org/showthread.php?t=696953")

---

### Post by redcharlie on 2009-05-11
Well, thread [http://ubuntuforums.org/showthread.php?t=696953](http://ubuntuforums.org/showthread.php?t=696953) seems to be closed, so I'll add my notes here.

What I did to share f-spot with my spouse on the same machine (Jaunty):
1) create group "f-spot" and made us both members
2) figure out where to stash photos imported by f-spot, for this guide, say "/f-spot_imports"
3) figure out where to stash the common db directory, for this guide I just used my own "~/.gnome2/f-spot" directory, but it could be anywhere, as long as you replace the f-spot directory with a symlink to the new shared directory.

#backup original f-spot config dir
4) sudo mv /home/spouse/.gnome2/f-spot /home/spouse/.gnome2/f-spot_original 

#replace original f-spot config with symlink to shared config dir
5) ln -s ~/.gnome2/f-spot  /home/spouse/.gnome2/fspot

# Be sure ~/.gnome2/f-spot/photos.db exists before you do the below, if not, just start f-spot once and then shut it down again

# Change group of shared config dir and import folder to "f-spot" 
6) chgrp -R f-spot ~/.gnome2/f-spot/ /f-spot_imports

# Give f-spot group write permissions on same
7) chmod -R g+w    ~/.gnome2/f-spot/ /f-spot_imports

# Give f-spot group write permissions via file access control lists (a new concept for me and too big of a topic for this mini-how-to)
8 ) setfacl -m d:g:f-spot:rwx ~/.gnome2/f-spot /f-spot_imports

# Mono seems to be broken regarding umask and ACL, and by default creates files mode 644 regardless of the above.
See [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/201395]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/201395")
# So, to allow both me and my spouse write access to photos that the other imports or edits, I have to hack /usr/bin/f-spot to enforce group write permission

# Enforce group write permissions on imported photos
9) Add this line to the very end of /usr/bin/f-spot
"sudo chmod -R g+rw /f-spot_imports"

# so either of us can change group write perms on photos regardless of who owns the file
10) sudo visudo
(Add "%fspot ALL= NOPASSWD: /bin/chmod -R g+rw /f-spot_imports" to the very end of the sudoers file)

I haven't thought about the ability of switching between private and shared f-spot instances, but one could simply maintain one's own .gnome2/f-spot/  directory along with a separate shared location, and use the "-b" command line switch to switch between the two. (see [http://f-spot.org/User_Guide/Share_1]("http://f-spot.org/User_Guide/Share_1")) Unfortunately, that doesn't change the import directory...I haven't found a way of changing that on the command line, but that would be the only missing piece.

---

### Post by SuperZ on 2009-05-11
very good to share pictures... worked fine with me. thanks =)

---

### Post by justpete on 2009-05-12
Resolved.

User directories apparently corrupted. Unable to find root cause but adding new users, copying, and configuring never grayed out the file management pref for photos under the media tab, etc.

Removing samba, sambasharing, shared folder, relevant groups, purging f-spot, and reinstalling had no effect. Comparing newly created users' dir and file perms step by step had no effect.  Etc.

> **redcharlie said:**
> 

# Give f-spot group write permissions via file access control lists (a new concept for me and too big of a topic for this mini-how-to)
8 ) setfacl -m d:g:f-spot:rwx ~/.gnome2/f-spot /f-spot_imports



Created a separate 'user' to hold music and picture directories.  Group membership includes two other users, one the admin, itself, and root with perms set as described.

Symlinks of ~/.gnome2/f-spot successfully created in both users' directories.  F-Spot launches in both users' desktops showing any changes made by connection of the camera via USB when running as the separate 'user'.

The camera fails as "Could not lock the device" in either users' desktops whether mounted before F-Spot launches or after or if launched without the -import option and the import button is clicked manually.  When this error occurs, a popup appears in the other user's window titled "Unable to mount Canon, Inc. Canon Digital Camera" with the text beneath as: "Error initializing camera: -53: Could not claim the USB device" but it doesn't appear in the separate 'user' window.

The setfacl command whether run from the admin user's account, sudo or not, or from the separate 'user' account, sudo or not, consistently returns "Operation not supported".  This is true after a restart as well.

No problem editing /usr/bin/f-spot although I'm not sure if I was supposed to add a return at the end, which I did.

Any idea why the operation is not supported?  Should I be running this command as root via sudo -i?

BTW, made symlinks from destination folder to each of the users' direcgtories and camera still doesn't work in either acct and the setfacl command still returns the same error message.

Any help at all would be most welcome at this point.

TIA, Pete

---

### Post by redcharlie on 2009-05-20
Try remounting the particular filesytem with acl support turned on.
"sudo mount /path/mount -o remount,acl"

My data partition is xfs, which seems to have acl support on by default.  My root partition, however is ext3, and I got the "operation not supported" error using setfacl on it until I remounted with acl support.  If that fixes it, just add acl to the line of options for the particular filesystem in your /etc/fstab and that will mean acl gets turned on automatically when you reboot.

As for the usb camera issue, I'm not sure, as I didn't create a separate f-spot user, but from my experience only one user at a time has full access to removeable media.  For example, if I insert a cd when logged on as user A, then logout and log back in a user B, I will not be able to eject the cd as user B (I'll have to sudo eject or somesuch) as user A "owns" /media/cdrom or whereever it's mounted.  Something similar may be happening when your camera is mounted and multiple users try to access it.  Try looking at the ownership and permissions of the mount point when the camera is plugged in.

---

### Post by redcharlie on 2009-05-21
Oh, and I need to stress a BIG CAVEAT: two (or more) users SHOULD NOT USE F-SPOT at the SAME TIME.  The f-spot docs warn against this, but I want to make it clear that the above mini-howto allows two or more users to share the same f-spot repository on the same machine, but does not let them use f-spot simultaneously.

The intended usage scenario is one user is logged onto the machine at one time, or at the very least only one user is running f-spot at any given time.

The reason for this is that the db backend, sqllite, is not a client-server database engine, and so must rely on the OS for filelocking to handle concurrency.  As the sqllite developers admit, this is not very robust, but is an inherent weakness in any sort of embedded database.  As a result, if two or more separate instances of f-spot are simultaneously trying to alter the same photos.db, unhappiness could well result.

Moreover, I would not advise doing any of this over a network.  I don't know how well sqllite maintains transactional integrity, but if you access your photos.db over the network, and your network burps while you are importing, all bets are off.

---

### Post by justpete on 2009-05-25
> **redcharlie said:**
> Try remounting the particular filesytem with acl support turned on.
"sudo mount /path/mount -o remount,acl"

My data partition is xfs, which seems to have acl support on by default.  My root partition, however is ext3, and I got the "operation not supported" error using setfacl on it until I remounted with acl support.  If that fixes it, just add acl to the line of options for the particular filesystem in your /etc/fstab and that will mean acl gets turned on automatically when you reboot.

Thanks!  And sorry for the delay.  I'm reallllly starting to dislike Earthlink and/or Verizon. 'Nuff said I'm sure.

/etc/fstab as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc            /proc          proc   defaults    0      0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot  none    bind       0      0
/host/ubuntu/disks/swap.disk none swap loop,sw    0      0

So I'll append ,acl to the options text for the fs mounted at / ,reboot, and execute the setfacl command.  Oughta do the trick, thanks.

Currently I'm using a lame-azz executable:

chmod --reference=/common/f-spot/photos.db /common/Photos/20??/*/*/*.jpg

(all users' ~/gnome2/f-spot directories are a symlink from /common/f-spot)

which is made available via a menu launcher exec'ed as application:

sudo /common/fspot/fix_perms

with sudoers edited to append the following line:

%fspot-shared ALL=NOPASSWD: /common/fspot/fix_perms

The intent is to execute the 'app' before using F-Spot and after quitting if import used.  Works fine at the moment but isn't nearly as elegant as using the ACL command.  But it was at least a learning experience.

> **redcharlie said:**
> As for the usb camera issue, I'm not sure, as I didn't create a separate f-spot user, but from my experience only one user at a time has full access to removeable media.  For example, if I insert a cd when logged on as user A, then logout and log back in a user B, I will not be able to eject the cd as user B (I'll have to sudo eject or somesuch) as user A "owns" /media/cdrom or whereever it's mounted.  Something similar may be happening when your camera is mounted and multiple users try to access it.  Try looking at the ownership and permissions of the mount point when the camera is plugged in.

With a bit more experience using linux it dawned on me this was happening only when using user switching.  Duh.  Another learning experience.

I've since learned enough about the mount command and mount locations to be dangerous.  Been practicing mounting .iso files at various mount points and with various arrangements of the command line - hadn't thought to look at perms of the mount points, thanks for the tip.  I knew only the owner of the mounted volume could umount but I hadn't yet connected that with the perms of the mount point.  Duh, redux.

Tnx again, Pete

---

### Post by justpete on 2009-05-25
> **redcharlie said:**
> Oh, and I need to stress a BIG CAVEAT: two (or more) users SHOULD NOT USE F-SPOT at the SAME TIME.  The f-spot docs warn against this, but I want to make it clear that the above mini-howto allows two or more users to share the same f-spot repository on the same machine, but does not let them use f-spot simultaneously.

Learned this early on tnx to this forum, db knowledge here is pretty sparse to say the least. It's on the list to learn after Python and C which means it'll be obsolete or I'll be dead before I get that far... :D

> **redcharlie said:**
> The intended usage scenario is one user is logged onto the machine at one time, or at the very least only one user is running f-spot at any given time.

Current installation is on a single shared machine so should be ok as long as not user-switching with one already running the app - shouldn't ever happen.

> **redcharlie said:**
> The reason for this is that the db backend, sqllite, is not a client-server database engine, and so must rely on the OS for filelocking to handle concurrency.  As the sqllite developers admit, this is not very robust, but is an inherent weakness in any sort of embedded database.  As a result, if two or more separate instances of f-spot are simultaneously trying to alter the same photos.db, unhappiness could well result.

Moreover, I would not advise doing any of this over a network.  I don't know how well sqllite maintains transactional integrity, but if you access your photos.db over the network, and your network burps while you are importing, all bets are off.

Tnx for the detailed explanation, helps a lot.  I initially tried to share the photos via samba to the xp partition which was a mess and required complete rebuild.  It'll be awhile before there's a server/NAS arrangement with multiple user machines but I suspect by then F-Spot will be displaced by something more linux friendly and less windowy.

---

### Post by akaihola on 2009-10-16
> **1066design said:**
> 
[LIST]
[*]Create symbolic link in each users home directory to the group configuration files with the same name.
[*]Create symbolic link in each users home directory to the group photos directory with the same name.
[/LIST]


Why not use f-spot's -b and -p options:
```
f-spot -b /var/photos -p /var/photos
```

---

