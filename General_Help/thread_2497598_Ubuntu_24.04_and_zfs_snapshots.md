---
title: "Ubuntu 24.04 and zfs snapshots"
date: 2024-05-11
forum: General Help
---

### Post by laserburn2 on 2024-05-11
There were already things said on this subject, but I would need more recent info, applicable to the new Ubuntu. I use zfs on Ubuntu since 20.04 (no encryption) and I like how it would create snapshot whenever something is installed, I had to restore system more than once in the past. That feature is however missing in 24.04.

So, what to use now to make and manage zfs snapshots? Sadly, Timeshift doesn't work with zfs AFAIK. Does anyone use zfsnap? Could the old zfs snapshot functionality be restored again in 24.04? I'd appreciate all input. ):P

---

### Post by MAFoElffen on 2024-05-11
What you mentioned about a past "feature" was for Zsys, which came with Ubuntu 20.04 LTS using the ZFS-On-Root install. 

Zsys was short lived. It had problems filling the bpool with snapshots, becaseu the defualt snapshot count was too many, and the size of the bpool not large enough to handle that many. That could be adjusted to get around that.

I have not heard of zfsnap. I'll have to try it before I can really say anything about it.

There is a long list of ZFS snapshot msnsgers out there. They are all wrappers of the basic commands...
Sanoid
Syncoid
ZnapZend
zfs-auto-snapshot
zsys
zfs-snap-manager
zrepl
Oracle ZFSSA

I still seem to fall back to doing it manually.

---

### Post by #&amp;thj^% on 2024-05-11
just to add to MAFoElffen's list there is also ZC-Commander.
```
&#9484;&#9472; Datasets &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;&#9484;&#9472; Snapshots &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;bpool                                                               &#9474;&#9474;bpool@5-6-2024                                                       &#9474;
&#9474;bpool/BOOT                                                          &#9474;&#9474;bpool/BOOT@5-6-2024                                                  &#9474;
&#9474;bpool/BOOT/ubuntu_xj7tth                                            &#9474;&#9474;bpool/BOOT/ubuntu_xj7tth@5-6-2024                                    &#9474;
&#9474;rpool                                                               &#9474;&#9474;rpool@5-6-2024                                                       &#9474;
&#9474;rpool/ROOT                                                          &#9474;&#9474;rpool/ROOT@5-6-2024                                                  &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth                                            &#9474;&#9474;rpool/USERDATA@5-6-2024                                              &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/srv                                        &#9474;&#9474;rpool/USERDATA/home_qkvs92@5-6-2024                                  &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/usr                                        &#9474;&#9474;rpool/USERDATA/root_qkvs92@5-6-2024                                  &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/usr/local                                  &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var                                        &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/games                                  &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/lib                                    &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/lib/AccountsService                    &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/lib/NetworkManager                     &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/lib/apt                                &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/lib/dpkg                               &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/log                                    &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/mail                                   &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/snap                                   &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/spool                                  &#9474;&#9474;                                                                     &#9474;
&#9474;rpool/ROOT/ubuntu_xj7tth/var/www                                    &#9474;&#9474;                                                                     &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
 F1 Help  F2 Promote  F3 ____  F4 ____  F5 Snapshot  F6 Rename  F7 Create  F8 Destroy  F9 Get all  F10 Exit




```
[https://github.com/manoeldesouza/zc](https://github.com/manoeldesouza/zc)
And I as well like manual snapshots...:)

---

### Post by laserburn2 on 2024-05-11
Great, this seems like a nice beginning, lots of apps to check out. But I'm mostly interested in apps that people have actually tested on 24.04, because there are always these little changes in booting and whatnot, I would hate to think that I'm safe because I have a snapshot, just to end up with an unbootable system after a restore attempt. If you could perhaps restore the fs to earlier state just to confirm that the tool works fine on new Ubuntu.

And since you mentioned manual snapshots, let's see how that would work exactly, since I'm not a virtuoso with the complicated zfs command. How exactly would I properly take snapshots of the existing bpool and rpool and restore them to the time of the snapshot, after let's say Nvidia driver update messes up my system, which tends to happen a lot?

---

### Post by MAFoElffen on 2024-05-11
I can let you know, both 1fallen and I are the majority of the support for ZFS in the forums, and we also are both DEV-Testers for releases in the DEV-cyles. So us testing ZFS in the DEV cycles IS something we both do.

Further, ZFS is ZFS. We found no issues with doing snapshots with "Ubuntu 24.04". There were issues that we pushed fixes for for 22.04 & 23.10, with the version of Grub, but we pushed the fix for DEV-Noble before it's release, and had the patches backported for 22.04 & 23.10.

We also got the version of the (then) current version of zfs-linus pushed for Noble to overcome some issues OpenZFS issues, and other patches pushed for other things ZFS. So that when Noble was released, it passed both what we thought should be there for us, and the other Users.

Like I said, those snapshot managers are just wrappers over the underlying zpool and zfs commands. Those commands did not change for OpenZFS 2.2.x. 

Yes. I tell people to try and review things for themselves. That is going to confirm what you feel is right for you and how you want to do things. I can't tell you what is 'best for you'. LOL. Personal tastes are diverse.

NVidia needing to be uninstalled/reinstalled is an ongoing thing. That is just a part of owning NVidia high-end graphics. 1fallen and I both have Nvidia. I thik he would agree that NVidia owners just need to learn and remember a few things to "keep them" going through updates. It's not currently as bad as it used to be years ago. There was a time when every kernel update was a trigger to manually fix it. The repetition of doing that has become second nature. For NVidia, it's not if, it's when... And rolling a snapshot back to fix that is only a band-aid. The other updates that triggered it are still going to happen eventually.

---

### Post by #&amp;thj^% on 2024-05-11
+1 With MAFoElffen
> **laserburn2 said:**
> 
And since you mentioned manual snapshots, let's see how that would work exactly, since I'm not a virtuoso with the complicated zfs command. How exactly would I properly take snapshots of the existing bpool and rpool and restore them to the time of the snapshot, after let's say Nvidia driver update messes up my system, which tends to happen a lot?
here is a great place to study up on: [https://ubuntu.com/tutorials/using-zfs-snapshots-clones#1-overview](https://ubuntu.com/tutorials/using-zfs-snapshots-clones#1-overview)

Also as MAFoElffen said nVidia is just a different non native part of Linux, you will have to install the drivers again. (In most cases)

---

### Post by MAFoElffen on 2024-05-11
This is my script that automates an nVidia driver reinstall:
```

#!/bin/bash

## MAFoelffen,<mafoelffen@ubuntu.com,20180429
# Updated 2024.05.11
#
#  Purpose: reinstall nVidia Driver
#

############
# Variables
############
installed_driver=$(apt list nvidia-driver* --installed 2>/dev/null | \
    awk -F '/' '/nvidia-driver/ {print $1}')
exit_code=0

############
# Functions
############

function CheckInstalled() {
    if [ !z $installed_driver ]
    then
        exit_code=1
        echo -e "No drivers were found to remove."
        exit $exit_code
    fi
}

function RemoveOld() {
    sudo apt remove --purge -y nvidia* libnvidia*
    exit_code=$?
    if [ $exit_code -ne 0 ]
    then
        echo -e "There was a problem removing drivers. Exiting."
        exit $exit_code
    fi 
}

funcion Reinstall() {
    sudo apt install -y $installed_driver
    exit_code=$?
        if [ $exit_code -ne 0 ]
    then
        echo -e "There was a problem reinstalling the driver."
        echo -e "Check the output for the errors.... exiting"
        exit $exit_code
    fi 
}

#######
# Main
#######
CheckInstalled
RemoveOld
Reinstall
echo -e "Reinstall of nVidia driver was successful"

```

---

### Post by laserburn2 on 2024-05-11
Thank you, that's a really nice tutorial to cover to important basics. So, let's say update messed up something important on the system and I need to go back to an earlier snapshot. Like this?

zfs rollback rpool/example@snap1
zfs rollback bpool/example@snap1

Could I just run those commands in a terminal in a graphic session or would I need to go to single-user mode or something? After that, what, reboot and everything is as it was when snapshot was taken?

---

### Post by MAFoElffen on 2024-05-11
Well heck. It depends if it boots or not. LOL

Yes, except first do this to find the most recent snapshots in those pool datasets
```

UID=$(sudo zfs list | awk -F '[/, ]' ' /rpool\/ROOT\/ubuntu_/ {print $3;exit}')
sudo zfs list -t snapshot -o name -s creation -r bpool/BOOT/$UID | tail -1
sudo zfs list -t snapshot -o name -s creation -r rpool/ROOT/$UID | tail -1

```
Then roll back those datasets.

ZFS snapshot are are of datasets, not of a pool. You tell it to make a snapshot (either differential, recursive or clone) of a dataset.

If it doesn't boot, then you boot from an installer LiveUSB > Use "Try" > Open a terminal session > mount the ZFS pools and datasets to the Live Image Evironment > chroot into the installed system > Then do the above to rollback to the most current snapshots...

---

### Post by #&amp;thj^% on 2024-05-12
This bit is for zc-commander.
Don't let this confuse you, this is off an Arch Based system, but it works the same on Ubuntu/Flavors as well:
```
&#9484;&#9472; Datasets &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9484;&#9472; Snapshots &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;zpcachyos                                            &#9474;zpcachyos@tuesday-16                                 &#9474;
&#9474;zpcachyos/ROOT                                       &#9474;zpcachyos/ROOT@tuesday-16                            &#9474;
&#9474;zpcachyos/ROOT/cos                                   &#9474;zpcachyos/ROOT/cos@tuesday-16                        &#9474;
&#9474;zpcachyos/ROOT/cos/home                              &#9474;zpcachyos/ROOT/cos/home@tuesday-16                   &#9474;
&#9474;zpcachyos/ROOT/cos/root                              &#9474;zpcachyos/ROOT/cos/root@tuesday-16                   &#9474;
&#9474;zpcachyos/ROOT/cos/varcache                          &#9474;zpcachyos/ROOT/cos/varcache@tuesday-16               &#9474;
&#9474;zpcachyos/ROOT/cos/varlog                            &#9474;zpcachyos/ROOT/cos/varlog@tuesday-16                 &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
 F1 Help  F2 Promote  F3 ____  F4 ____  F5 Snapshot  F6 Rename  F7 Create  F8 Destroy  F9 Get all  F10 Exit  
 
```
 On the left is your or in this case my Pools.
 I use the arrow keys to navagate (up down && right left) Now at the bottom of the terminal youll see your options:
 ```
F1 Help  F2 Promote  F3 ____  F4 ____  F5 Snapshot  F6 Rename  F7 Create  F8 Destroy  F9 Get all  F10 Exit  
```
 "F5" takes the snapshot, and you name or date it as you wish. That will now show in the right hand side. I'm trying to keep this very short, we could write page after page here, so some learning will be needed by you.
 
 I've grown to like this little utility, a lot of features like "send" which dose not show in my current code box.
 Now if you arrow righ to a snapshot the "F5" has a Cone option and The "F9" gives you a nice look at:
 ```
&#9484;&#9472; ZFS Get All &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  &#9474;
&#9474;zpc&#9474;                                                                                                    &#9474;  &#9474;
&#9474;zpc&#9474;  NAME                  PROPERTY              VALUE                  SOURCE                         &#9474;  &#9474;
&#9474;zpc&#9474;  zpcachyos@tuesday-16  type                  snapshot               -                              &#9474;  &#9474;
&#9474;zpc&#9474;  zpcachyos@tuesday-16  creation              Tue Apr 16 15:04 2024  -                              &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  used                  0B                     -                              &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  referenced            96K                    -                              &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  compressratio         1.00x                  -                              &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  devices               on                     default                        &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  exec                  on                     default                        &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  setuid                on                     default                        &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  createtxg             69105                  -                              &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  xattr                 sa                     inherited from zpcachyos       &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  version               5                      -                              &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  utf8only              on                     -                              &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  normalization         formD                  -                              &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  casesensitivity       sensitive              -                              &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  nbmand                off                    default                        &#9474;  &#9474;
&#9474;   &#9474;  zpcachyos@tuesday-16  guid                  8613493534852254011    -                              &#9474;  &#9474;
&#9474;   &#9474;                                -------------------------------------                               &#9474;  &#9474;
&#9474;   &#9474;                                   ENTER Modify  F2 New  F10 close                                  &#9474;  &#9474;
&#9474;   &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;
&#9474;                                                     &#9474;                                                     &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```
Any who you kind of figure things out a bit more hopefully.

---

### Post by laserburn2 on 2024-05-12
I don't know, all these zfs snapshot managers seem too complicated for  my needs that could be just as easily served with few commands and  anacron. I really hope Timeshift developer warms up to zfs.

Also,  is there a more detailed guide somewhere for recovering zfs using live  Ubuntu USB drive? That might come useful, though I so far never had a  situation that Ubuntu breaks so bad that I can't reach tty, except due to some  hardware failure. Graphical environment braking, now that is more  common.

---

### Post by #&amp;thj^% on 2024-05-12
zc-commander is one of the easiest zfs-snapshot tool there is.

MAFoElffen, has written a handful of live USB recovery steps, Just search in the Forums for his name you will see plenty.

My guess here, this is going to be a long road for you, until you just dig in and read ,read , and read more.

---

### Post by MAFoElffen on 2024-05-12
The basic concepts of ZFS should be learned by it's users... I feel that is worthwhile.

ZFS is just like another Volume Manager, LVM2. In that both take just a little bit of ramp-up learning on your part. There are 4-6 commands that people need to learn for both of those to be proficient with it. Learn those and you will be fine.

Even with those, you will just be scratching the surface of what you can do with it.

But the thing is... ZFS is a system where you need to learn what it is, what it does, and how to use it. If you are not willing to learn those basics concepts, then maybe ZFS is not for you.

You could install it, not do anything more to or with it (like doing the snapshots you want to do...), and you would be fine. That is like acquiring a Lamborgini, and just driving it back and forth 2 blocks to the local grocery store.

Maybe you should install a small ZFS system in a VM and play with it. Something to learn on, and decide if it suits what you want to do, and if it is right for you(?)

---

### Post by aljames2 on 2024-05-12
+1  1fallen & MAFoElffen

I am just a young jedi on ZFS.  A little clumsy with the sabre still but getting the hang of it.  I read everything these 2 write on it, as well as Jim Salter.  I also like LVM but that’s not this..

I like & use Sanoid for snapshots & Syncoid for replicating to a backup location.  I have tested blowing up my root on ZFS and putting it back.  Practice it.

---

### Post by #&amp;thj^% on 2024-05-12
Thanks aljames2 I keep tabs on the folks who pick things up quickly, like yourself.:
Also your noted test with Sanoid/Syncoid is very helpful. :) May the Force be with you....

---

### Post by MAFoElffen on 2024-05-12
> **1fallen said:**
> :) May the Force be with you....
LMFAO!!!

My two dogs are named Pad May, and Luke Skywalker... And yes, Luke is the son of Pad May.

---

### Post by aljames2 on 2024-05-12
Hillarious!
> My two dogs are named Pad May, and Luke Skywalker... And yes, Luke is the son of Pad May.

I rewatched Rogue One this weekend, so I have the SW vibe going.
But I digress :)

---

