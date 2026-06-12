---
title: "How to limit LiveCD persistency to home/data only and have an immutable system?"
date: 2020-10-20
forum: General Help
---

### Post by jsun-7 on 2020-10-20
I managed to create a ubuntu 20.04 liveCD on usb drive.  When I booted it up with PC, it automatically creates a 3rd partition, "writable", and turns on persistency.  That is great!

However, for security reasons I like to restrict persistency to user data only (e.g., wifi credential, app files).  I don't want to allow any changes to system programs (at least not persistently).  Nor do I want any downloaded executables.  

I suppose this is similar to previous "home-rw" partition, right?  How do I do that now?  What are ways to achieve my overall purpose of having an immutable system?

---

### Post by sudodus on 2020-10-20
Try by changing the label 'writable' to 'home-rw' for the ext4 partition.

---

### Post by C.S.Cameron on 2020-10-20
"casper-rw" was changed to "writable" in 20.04.
"home-rw" is still "home-rw" 
The only thing in the home-rw partition is the users home directory.
The user is "ubuntu" until changed in settings/users.*
A **mkusb** persistent drive is ideal for your needs. The OS partition is read only ISO9660, there is an easy to mount persistence partition, an optional NTFS data partition and the USB has an option for backing up and restoring.

Edit
*My error, It looks like a New User is not persistent without a casper-rw or writable partition, and mkusb backup option does not work for home-rw. 

@sudodus: Any chance of adding home-rw to backup options?

---

### Post by sudodus on 2020-10-20
[SIZE=3]General description[/SIZE]

It works for with the standard user to have only [FONT=Courier New]**home-rw**[/FONT] (and not [FONT=Courier New]**writable**[/FONT] alias [FONT=Courier New]**casper-rw**[/FONT]).
```

$ sudo parted -s "/dev/sdc" print
Model: OCZ-AGIL ITY3 (scsi)
Disk /dev/sdc: 60,0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 2      1000kB  2000kB  1000kB               primary  bios_grub
 3      2000kB  258MB   256MB   fat32        primary  boot, esp
 4      258MB   2064MB  1806MB               primary
 5      2064MB  60,0GB  58,0GB  ext2         primary
 1      60,0GB  60,0GB  1464kB               primary  msftdata

$ lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE "/dev/sdc"
MODEL            NAME   FSTYPE  LABEL                     MOUNTPOINT   SIZE
ITY3             sdc                                                  55,9G
                 |-sdc1                                                1,4M
                 |-sdc2                                                977K
                 |-sdc3 vfat    usbboot                              244,1M
                 |-sdc4 iso9660 Lubuntu 20.04.1 LTS amd64              1,7G
                 `-[COLOR="#cc0000"]**sdc5**[/COLOR] ext4    writable                                54G

$ sudo tune2fs -L home-rw /dev/[COLOR="#cc0000"]**sdc5**[/COLOR]
tune2fs 1.44.1 (24-Mar-2018)

```

See the first attached screenshot from a persistent live session by mkusb-dus with Lubuntu 20.04.1 LTS. There is memory of a previous session in BIOS mode, while the current sessions is in UEFI mode. You can also see how the persistent partition is mounted at [FONT=Courier New]**/home**[/FONT].

[HR][/HR]
[SIZE=3]Backup/Restore[/SIZE]

There are backup/restore options for [FONT=Courier New]**/home**[/FONT] the via the starter menu of mkusb-dus. See the second attached screenshot. I have not tested if/how they work for a separate home partition. Maybe they don't work in this case.

But you can do it **manually [when booted live-only] by creating a tarball of the whole content of the partition of persistence**. This is straightforward at least for a user who wants to tweak a persistent live drive as described here. Restoring from the tarball is also straightforward.

---

### Post by jsun-7 on 2020-10-20
> **sudodus said:**
> Try by changing the label 'writable' to 'home-rw' for the ext4 partition.

Changing the label seems to do the trick.  Thanks.

However, wifi setting is not persistent.  Any way to make it persistent?

Also, is there a way to tell liveCD to create "home-rw" partition instead of "writable" partition at the first place?

---

### Post by jsun-7 on 2020-10-20
My understanding is mkusb is a tool that makes bootable and persistent usb drive from ISO image, right?  I think it only runs on linux - correct me if I'm wrong.  I'm targeting average users who can use windows/mac/linux.  I'm hoping to distribute a ISO image they can burn with Etcher on any machine without any tech details.  

The liveCD seems pretty close at this point.  See my other follow-up message.  Right now I only have wifi setting persistence and creating "home-rw" at the first place 2 issues.  Would appreciate any pointers there.

---

### Post by sudodus on 2020-10-20
Wifi settings belongs to the system, and you would have to store the relevant file(s) in your home and copy files to where they belong in the system for this to happen. Maybe not easy, but should be possible.

You can create an own tool or modify an existing tool to do exactly what you want, for example "home-rw" partition instead of "writable" partition at the first place. I don't think there is a short-cut for this particular purpose, but it is not that difficult to use [FONT=Courier New]**tune2fs**[/FONT].

---

### Post by jsun-7 on 2020-10-20
Thanks for such a quick reply, sudodus!

> **sudodus said:**
> Wifi settings belongs to the system, and you would have to store the relevant file(s) in your home and copy files to where they belong in the system for this to happen. Maybe not easy, but should be possible.

The problem is during the process of creating LiveCD, I could not find the /home/ubuntu on the chroot/ directory.  Do you know where is the template/source for ubuntu, the default user, home directory?  Once I get that, I could easily create a system dir under /home/ubuntu to hold anything system data files that I want to persistent.  I will just make the original system data files as symbolic links.

> **sudodus said:**
> 
You can create an own tool or modify an existing tool to do exactly what you want, for example "home-rw" partition instead of "writable" partition at the first place. I don't think there is a short-cut for this particular purpose, but it is not that difficult to use [FONT=Courier New]**tune2fs**[/FONT].

What is the "existing tool" you are referring to?  What is the package specifically?  I'm already building the ISO from scratch.  So it might not be hard to hack a little here.

My goal is to give a very smooth end user experience.  Even though tune2fs is not hard (and I can could even hide it behind a script), but it will involve a reboot and some oddities during the process to an average user.  (for example, if user has already modified some data.  After changing the label, all will be lost.)

---

### Post by sudodus on 2020-10-20
If you first loop mount the iso file, then [FONT=Courier New]**casper/filesystem.squashfs**[/FONT] in the iso file, you will find [FONT=Courier New]**/home**[/FONT]. I guess you have extracted all this, so it should be possible to put some files in the home directory.

One existing tool is [**mkusb-plug**](https://help.ubuntu.com/community/mkusb/plug), and I think it would be rather easy for you to modify it. You could go directly into [FONT=Courier New]**mkusb-sedd**[/FONT], which is part of mkusb-plug. These modules are 'only' bash shellscripts, nothing fancy.

---

### Post by jsun-7 on 2020-10-20
The casper/filesystem.squashfs is created from deboostrap'ed chroot.  The home/ is empty.   So if we put anything there, it is likely be overridden later when we mount home-rw partition on top of it.

It would be nice to know how /home/ubuntu directory come from.  I also have another pending question on automatically starting an app, which would also require adding a startup file to ~ubuntu/.config/autostart directory.

---

### Post by jsun-7 on 2020-10-22
I was able to figure out how to create "home-rw" instead of "writable" partition.  It is a 2-step.  First, apply following patch.  Secondly, run "update-initramfs -u" inside chroot environment.


```
diff -Nru chroot/usr/share/initramfs-tools/scripts/casper-helpers.orig chroot/usr/share/initramfs-tools/scripts/casper-helpers
--- chroot/usr/share/initramfs-tools/scripts/casper-helpers.orig    2020-10-21 20:09:08.714542488 -0700
+++ chroot/usr/share/initramfs-tools/scripts/casper-helpers    2020-10-21 21:16:47.486258899 -0700
@@ -300,7 +300,9 @@
     echo "start=$start" | sfdisk --no-reread -q $DEVICE -a || return
     for d in ${DEVICE}$newpartno ${DEVICE}p$newpartno ${DEVICE}-part$newpartno; do
         if [ -e $d ]; then
-            mkfs.ext4 -q -L "$(root_persistence_label)" -F $d
+            # [eroas] create "home-rw" partition instead for better security
+            # mkfs.ext4 -q -L "$(root_persistence_label)" -F $d
+            mkfs.ext4 -q -L "home-rw" -F $d
             break
         fi
     done
```

Right now the problem is to make wifi settings persistent after this change.  Simply creating a symlink to /home/ubuntu/some-directory does not work!  Any pointers appreciated.

---

### Post by C.S.Cameron on 2020-10-22
To change the "writable" partition to "home-rw", I open GParted, right click the partition, click "Label File System", and change the label. To make a new "home-rw" partition I right click an empty space and select "New" then I add the "home-rw" label and select "Add".

Does using a script make anything different?

---

### Post by jsun-7 on 2020-10-25
> **C.S.Cameron said:**
> To change the "writable" partition to "home-rw", I open GParted, right click the partition, click "Label File System", and change the label. To make a new "home-rw" partition I right click an empty space and select "New" then I add the "home-rw" label and select "Add".

Does using a script make anything different?

Yes.   I'm creating a project that hopefully can be used many people.  By changing it in the script, none of my users will have to do this by hand later. :p

Actually in my project the default user ("ubuntu") is not a sudoer. Thus we cannot change "writable" to "home-rw" later.

The reason for such restriction is security.  The project is a bitcoin wallet called eroas.  If anyone is interested, take a look at [https://github.com/monkey-jsun/eroas](https://github.com/monkey-jsun/eroas)

---

### Post by jsun-7 on 2020-10-25
I have figured out how to make wifi connections persistent with "home-rw" persistency only.  Just want to share it here in case someone else chase the same issue later.

The main idea is to create a directory under /home partition (persistent) and bind mount that directory to /etc/NetworkManager/system-connections directory.   As I explained earlier, symbolic link does not work.

Detailed implementation is a little complicated.  The /home partition is automatically created by casper when system starts for the first time.  Thus we cannot pre-create it during build time.  Also, when NetworkManager starts /home partition is not mounted as rw yet (it is ro somehow).

To work around these challenges, I created a new systemd service, which runs at the end of startup sequence.  It will create and bind-mount the persistent directory for wifi settings under /home.  It will also re-start NetworkManager because NetworkManager has already started with ro directory earlier in the bootup process.

See the 2 files below for reference. 

 eroas.service - the system service desc file
```

[Unit]
Description=EROAS setup
After=graphical.target


[Service]
#ExecStartPre=/usr/bin/sleep 60
ExecStart=/usr/sbin/eroas_setup.sh
Type=idle               # we run last


[Install]
WantedBy=graphical.target

```

eroas_setup.sh : the script that does bind mount
```

#!/bin/bash


# create wifi persistent directory if not existing
if [ ! -d /home/casper ]; then
    mkdir -p /home/casper/etc/NetworkManager/system-connections
    chmod o-rx /home/casper
fi


# mount over the RO part and restart NetworkManager
mount --bind /home/casper/etc/NetworkManager/system-connections /etc/NetworkManager/system-connections
systemctl restart NetworkManager


# remove ubuntu from sudo/adm groups
sed -i "s#adm:x:4:ubuntu#adm:x:4:#" /etc/group
sed -i "s#sudo:x:27:ubuntu#sudo:x:27:#" /etc/group


exit 0

```

By now, with home/ only persistency and removing ubuntu sudoer priviledge, the system becomes immutable, a very important security property.  I need this for my bitcoin wallet project.  If you are interested, take a look at [https://github.com/monkey-jsun/eroas](https://github.com/monkey-jsun/eroas)

---

### Post by sudodus on 2020-10-26
Thanks for sharing your solution :KS

---

