---
title: "aufs root filesystem"
date: 2008-07-08
forum: General Help
---

### Post by Mannes on 2008-07-08
Hello Everyone,
I'm new here to the forums, bat have like a 5 year on and off experience with linux. First years mostly debian until I discovered Ubuntu, really think it's a wonderfull OS!

But i have a problem,

I Have Ubuntu installed on my eeepc 900, with 2gb of ram.
/dev/sda1 is the 4gb disk where ubuntu lives
/dev/sdb1 is the 16gb disk where my home dir lives
I have no swap or boot partition, which is working fine for as long as i worked with it

I read this article
[http://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash]("http://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash")
on how to reduce writes on my flashdisk. 

I pretty much have everything configured and installed how i wanted, so i thought it might be a good idea to 'freeze' my installation like this.

I followed every step of the tutorial and even added '[A nicer solution to add the kernel entries]("https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash#A%20nicer%20solution%20to%20add%20the%20kernel%20entries")'. 
But after rebooting 
- I get a lot of error messages of scripts and files that are not found
- /dev/sdb1 is not mounted (so no /home dirs)
- X isn't started (probably in the not found files somewhere)

When I alt+f1 to the first terminal it says in the top of the screen

```


aufs setup on /root

sed: no previous regexp.

ubuntu 8.04.1 binkeee tty1


```

the "aufs setup on /root" is a message from the [rootaufs script]("https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash#rootaufs%20Script") on the page mentioned earlier.
So the script get started, but then sed gives an error. since i have no experience with sed i don't know what the message means (also couldn't really find it so far) nor do i know if one of the sed commands is wrong.

forthermore;

on the alt+f8 'status console' if i can call it that. there's mentioned
```

* Mounting local filesystems...
mount: /dev/sda1 already mounted or /ro busy
   ...fail!

```

when i execute the 'df' command i can see that
/dev/sda1 is mounted on /ro
aufs is mounted on /
aufs-tmpfs is mounted on /rw

I'm not quite sure what is causing this, i can still boot without the aufs rootfs and then everything is working again, but i would like to get it to work with the aufs rootfs

any help would be greatly appreciated, also if there is a way how i can achieve the same on a different way

tested with kernels:
2.6.24-16-generic
2.6.24-19-eeepc
both with the exact same result

Kind Regards,

Mannes Brak

---

### Post by Mannes on 2008-07-09
Hello again,

I've done some further research in this matter and I think I've located the problem.

The [rootaufs]("https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash#rootaufs%20Script") script overwrites the standard fstab file so that all my other fstab entries get ignored.
This explains all the files not found because my /usr is in a squashfs/unionfs construction which doesn't get mounted,
just like my /home which is on my /dev/sdb1.

can someone help me out with rewriting the script so that it also mounts my other filesystems? since i still have no experience with those sed statements i don't know how to change them

any help would again be greatly appreciated!

---

### Post by nschembr on 2008-07-11
Thank you for your help.
Please change the title of  "A nicer solution to add the kernel entries" to  "Make Grub Menu changes persistent "   or "Make Grub Menu changes Permanent"

We need to add a credits section. 

I'm going to work on this project for ohio linux fest 2008. I think this can be made into a script.  I will  retest and add the sed script for fstab.
 
sudo sed -i s/'defoptions=quiet splash'/'defoptions=quiet splash aufs=tmpfs'/g /boot/grub/menu.lst

I'll look at the rest of the section to see about a sed one liners.

Send me your fstab. I'm new to sed as well. It's just so fast to make one liner changes.
I will have to review my notes. I need to edit fstab to keep the mounts in line. Without the changes df or mount report the wrong information.

My personal goal is to keep everything on one disk.  Aufs has on option to copy up or merge the changes.  I want to build this into an update/sync command. If you like your changes run the update else put the drive in rw mode and copy your files to the (base) normally ro dir.   It might be nice to have a dir like ~/Documents/ mounted rw with noatime. In my opinion all writes have some risk. :)

Life and death on flash. 

As a side note, I just lost a flash dive on my phone.  I'm not sure what the "real recovery" software can do but it looks gone to me.  I assume all flash drive will fail and I will never get anything off of the disk.

Thank you for the feed back.  I will have time to work on this on  Monday night. Talk to later, Nick

---

### Post by Mannes on 2008-07-11
here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9f82a725-2797-41ee-a4e5-507a24941b86 /               ext2    noatime,errors=remount-ro 0       1
# /dev/sda1
UUID=a154b93d-6156-4f6e-8cf6-840fad676ea2 /boot           ext2    noatime        0       2
# /dev/sdb1
UUID=e646edf4-f7a2-4647-a6db-8af8c99e761a /home           ext2    noatime        0       2

#mount tmp dirs in ram memory, to reduce writes
tmpfs		/tmp		tmpfs	defaults,noatime,mode=0777	0	0
tmpfs		/var/tmp	tmpfs	defaults,noatime,mode=0777	0	0
tmpfs		/var/log	tmpfs	defaults,noatime,mode=0777	0	0

#mount the squashfs /usr directory and put a writable layer on top
/.filesystem/usr/usr.sqfs /usr squashfs ro,loop,nodev 0 0
unionfs /usr unionfs nodev,noatime,dirs=/.filesystem/usr/overlay=rw:/usr=ro 0 0

```

I would like to keep my home dir writeable, because that's where i download files and edit my documents. And this is something i would like to keep doing :)

maybe you can let this depend on a var in the script? writablehome=1 for example :)

maybe i could change my fstab to let my /usr dir make use of the aufs filesystem as well instead of unionfs

---

### Post by BlaY0 on 2008-07-15
> **Mannes said:**
> Hello again,

I've done some further research in this matter and I think I've located the problem.

The [rootaufs]("https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash#rootaufs%20Script") script overwrites the standard fstab file so that all my other fstab entries get ignored.
This explains all the files not found because my /usr is in a squashfs/unionfs construction which doesn't get mounted,
just like my /home which is on my /dev/sdb1.

can someone help me out with rewriting the script so that it also mounts my other filesystems? since i still have no experience with those sed statements i don't know how to change them

any help would again be greatly appreciated!


Hello,

The sed statement is wrong. That sed statement suppose to comment out the root partition but since it is not well written it just pops out with an error thus rewriting current fstab with no input (wiping it).

In this case sed statement would be a little bit more difficult to make since ROOTNAME variable consists of at least two slashes and slash is somehow sacred string to sed.

I would rather go with grep instead of sed:

```
grep -v $ROOTNAME /aufs/ro/etc/fstab > /aufs/etc/fstab
```

...that would strip fstab off of root partition. I would also comment out those three lines where new root partition is constructed and written back to /aufs/etc/fstab. You are getting:

```
mount: /dev/sda1 already mounted or /ro busy
```

...because script is trying to mount root partition (new one from fstab) that was already mounted.

Regards,

Blaz

---

### Post by nschembr on 2008-07-15
I wrote this to solve a problem that I was having with the eeepc, it needs work.

I just working through the install of 8.4.1. I'm going to have to build a test system that I can use to rebuild the howto faster. It takes to long to install and test on my eeepc 701.

It will take a few days for me to review how the real init scripts handle fstab. As Blaz pointed out, my sed needs work. I'm not sure grep will have the power needed to edit the files. I'm not a very good sed programmer, but sed is included in the initrd image. I'm trying to keep the changes need as small as I can.

That said, I will continue to look into your issue. I may need to rewrite the howto. Thank you for adding your section. I like to know why things work the way they do. 

Do you think we should have the script make the changes to the menu.lst the first time it is run? 

The main part of your issue is fstab on the aufs root needs to match the real fstab on the device.

This was short sighted of me.  The general case would need to assume that this is in a server env with 200 disk in the box. Yes, I can see the need to have fstab on aufs to match the real root fstab and to have uuid support.

In your last posts, you touched on something I wanted to mention, flash dies. I'm a skeptic, every flash drive that I have put under rw for general use has failed badly. The last one burned out in my cell phone after I took a picture.  I believe that putting your home dir on a rw flash disk is a bad idea. I think it would be better to use the system in a ro mode. your changes are store in ram on /rw. A script can run remountrw and copy the data from /rw to /ro.  I find I only rsync my home account after I make a major change to something. Most of the time I copy one or two file to flash.  I almost never use the internal /dev/sda for fear that I'm going to burn it out. I wish sda was just a socketed sdhc card.

Let's hear from the community, has anyone else had bad luck with Flash drives.    

Nicholas A, Schembri State College PA USA        

Note: I have only used ext2, ext3 and fat32 file systems on my flash devices.

---

### Post by BlaY0 on 2008-07-16
> **nschembr said:**
> I'm not sure grep will have the power needed to edit the files. I'm not a very good sed programmer, but sed is included in the initrd image. I'm trying to keep the changes need as small as I can.

What power do you need ;) grep is part of standard UNIX tools and is widely used everywhere.

Your script works if you use UUID= or LABEL= as value of 'root' boot parameter but it breaks if you use actual device names like /dev/sda1.

I use grep like I mentioned and it works. I also have writable home partition on my CF card and it mounts just fine.

> Do you think we should have the script make the changes to the menu.lst the first time it is run? 

Why would one want that? I have separate boot partition which is not even mounted at boot time. If someone uses syslinux or any other bootloader instead of grub, changing menu.lst doesn't make any sense. That should be part of some other script/hook.

---

### Post by nschembr on 2008-08-01
BlaY0, you are correct. Grep is the simplest and best way to edit out / and swap. 

I feel the user should see the the same fstab in both /ro/etc/fstab and /etc/fstab. This is to hard to code for this project. 

I used your example and ripped all ' / ' and swap lines from /ro/etc/fstab. 

Thank you for pointing out the error in sed. You saved me a lot of time with your bug report.


Mannes, I'm sorry for the delay. The new script should correct you errors.

Nicholas A. Schembri State College PA USA

PS. I'm going to Ohio LinuxFest 2008 October 11, 2008

---

### Post by AusIV4 on 2008-11-13
Has anyone used this with Intrepid?

I'm trying to do something similar, and get an error that aufs cannot load. I'm wondering if it's in my implementation, or if there's something wrong with Intrepid's aufs that won't let it load from the init-ramdisk.

[Edit]
Never mind, the problem was in my own implementation. I was building the initrd by hand, and had neglected to import some files essential for using aufs. Adding "aufs" to the modules file and running update-initramfs -u revealed which files I was missing.

---

### Post by mfeif on 2009-06-24
It's been a while since traffic in this thread, but I thought I'd ask a question...

This seems to be a pretty elegant solution, but what about integrating it in with runlevels?

It seems that most systems just use two (1 and 2). What if we used runlevel 3 as read-only with volatile changes, and runlevel 2 as full-on rw mode. This would allow one to switch into rw mode, do an aptitude upgrade, and then switch back, without having to reboot and select the grub option.

When there's a shutdown, things could sync, too, of course, but that's another discussion. I suppose some people might like the changes to be wiped, others would want them sync'd.

Thoughts?

---

### Post by Ebrius on 2009-11-15
I can no longer start my dhcpd service.

I am using dhcp3-server and when I start it I get the following error:
dhcpd self-test failed. Please fix the config file.
The error was:
/usr/sbin/dhcpd3: error while loading shared libraries: libcap.so.2: cannot open shared object file: No such file or directory

And dmesg shows the following errors:
[   61.388679] type=1503 audit(1258333308.864:16): operation="open" pid=969 parent=966 profile="/usr/sbin/dhcpd3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/ro/etc/ld.so.cache"
[   61.389098] type=1503 audit(1258333308.864:17): operation="open" pid=969 parent=966 profile="/usr/sbin/dhcpd3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/ro/lib/libcap.so.2.16"
[   61.392012] type=1503 audit(1258333308.864:18): operation="open" pid=970 parent=966 profile="/usr/sbin/dhcpd3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/ro/etc/ld.so.cache"
[   61.392559] type=1503 audit(1258333308.868:19): operation="open" pid=970 parent=966 profile="/usr/sbin/dhcpd3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/ro/lib/libcap.so.2.16"


I see this regardless if I have /ro mounted in read/write or read-only mode. Anyone have a solution?

---

### Post by cujgldkjge on 2009-11-15
> **mfeif said:**
> It's been a while since traffic in this thread, but I thought I'd ask a question...

This seems to be a pretty elegant solution, but what about integrating it in with runlevels?

It seems that most systems just use two (1 and 2). What if we used runlevel 3 as read-only with volatile changes, and runlevel 2 as full-on rw mode. This would allow one to switch into rw mode, do an aptitude upgrade, and then switch back, without having to reboot and select the grub option.

When there's a shutdown, things could sync, too, of course, but that's another discussion. I suppose some people might like the changes to be wiped, others would want them sync'd.

Thoughts?

Send me your fstab. I'm new to sed as well. It's just so fast to make one liner changes.
I will have to review my notes. I need to edit fstab to keep the mounts in line. Without the changes df or mount report the wrong information.

---

### Post by Ebrius on 2009-11-18
> **Ebrius said:**
> I can no longer start my dhcpd service.

I am using dhcp3-server and when I start it I get the following error:
dhcpd self-test failed. Please fix the config file.
The error was:
/usr/sbin/dhcpd3: error while loading shared libraries: libcap.so.2: cannot open shared object file: No such file or directory

And dmesg shows the following errors:
[   61.388679] type=1503 audit(1258333308.864:16): operation="open" pid=969 parent=966 profile="/usr/sbin/dhcpd3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/ro/etc/ld.so.cache"
[   61.389098] type=1503 audit(1258333308.864:17): operation="open" pid=969 parent=966 profile="/usr/sbin/dhcpd3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/ro/lib/libcap.so.2.16"
[   61.392012] type=1503 audit(1258333308.864:18): operation="open" pid=970 parent=966 profile="/usr/sbin/dhcpd3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/ro/etc/ld.so.cache"
[   61.392559] type=1503 audit(1258333308.868:19): operation="open" pid=970 parent=966 profile="/usr/sbin/dhcpd3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/ro/lib/libcap.so.2.16"


I see this regardless if I have /ro mounted in read/write or read-only mode. Anyone have a solution?


I wasn't sure if anyone had seen this before, but I did a little more testing and I found that when I tried to 'chmod' one of those files it would fail, first aufs would throw an error (something about how permissions should be reversed) and then chmod would throw an I/O error. What is kinda strange is I could modify other file's permissions (a couple in the /bin directory) successfully.

I can capture some more data if someone is interested in looking at this, its just a bit of a pain since this server is my router, and when I boot to aufs my dhcp server does not work.

---

### Post by philipp2084 on 2009-11-25
Have a look at this thread. [http://ubuntuforums.org/showthread.php?t=1220145]("http://ubuntuforums.org/showthread.php?t=1220145") 

This seems to be a common problem.

---

### Post by TimSylvester on 2010-02-21
I'm using this aufs-root script and it's working well, thank you for putting it together.

One minor issue I have is that when I run *remountrw *and *remountro *to make a minor change to the system, it seems to lock out any further changes.  If I later run *remountrw *again, I get:

```
mount: /ro not mounted already, or bad option
```This doesn't seem to have anything to do with the remount scripts themselves or the use of UUIDs, as I get the same result with a manual command:

```
$ sudo mount -o remount,rw /ro
mount: /ro not mounted already, or bad option
$ sudo mount -o remount,rw /dev/sda1
mount: /ro not mounted already, or bad option

```Unfortunately, the only way I've found to get past this is to reboot, or leave /ro mounted read-write permanently.

Any ideas?

---

### Post by falconindy on 2010-02-21
The output of mount can be flakey as its based on /etc/mtab. The info provided by /proc/mounts is the accurate.

I've had issues with Ext4 and Aufs, but I think they were related to kernel 2.6.32 more than Aufs. In any case, the solution was to mount the Ext4 partition with the 'nobarrier' option. You might want to try this.

---

### Post by TimSylvester on 2010-02-23
Yes, that did it.  Thanks!

For the record, I added "rootflags=barrier=0" to the kernel command line.  ("nobarrier" seems to be the XFS equivalent).  Next step is to update grub2 so it happens automatically...

---

### Post by dave373 on 2010-03-23
I am trying to create a read-only root version of Ubuntu Karmic but am having difficulties with Grub2 not selecting the default kernel.

With a normal fstab, everything works perfectly, but after switching to a Read-only AUFS fstab, Grub2 will not boot automatically, it sits there and waits for an 'enter' keystroke

As the machine will be locked in a box, headless, with no keyboard, this is a real problem.

Is anyone familiar with this situation, or should I just roll-back to grub legacy...

Cheers for any help

Dave

---

### Post by cmcginty on 2010-03-31
Dave, funny you posted this question. I was just going to submit the say the same thing. I have a little more info.

The reason why grub2 hangs at boot (after working before) is because it writes a value to /boot/grub/grubenv. You can clear the value with the following command: 

```
grub-editenv /boot/grub/grubenv unset recordfail
```

I'm running my system in a VM right now, seeing the same issues. **This bug means that grub2 is writing to the FS, even though it should be RO**. So I'm trying figure out how to prevent grub2 from doing this, or maybe I should just roll back as well.

Doesn't anyone have any ideas?

---

### Post by cmcginty on 2010-03-31
[SIZE="3"][COLOR=Red]**Here is the fix to prevent Grub hanging during boot:**[/COLOR][/SIZE]

```
sudo rm /boot/grub/grubenv
```Now my system always boots up automatically.

---

### Post by gravyface on 2010-04-13
> **TimSylvester said:**
> Yes, that did it.  Thanks!

For the record, I added "rootflags=barrier=0" to the kernel command line.  ("nobarrier" seems to be the XFS equivalent).  Next step is to update grub2 so it happens automatically...

I'm having the same issue: remountrw appears to "work" although no changes are committed after a reboot.

cat /proc/mounts (before remountrw):
```

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev tmpfs rw,relatime,mode=755 0 0
**/dev/disk/by-uuid/2f4daaaa-ec96-426c-be68-f4bb6bfe4166 /ro ext4 ro,relatime,barrier=0,data=ordered 0 0**
none /sys/kernel/security securityfs rw,relatime 0 0
aufs-tmpfs /rw tmpfs rw,relatime 0 0
aufs / aufs rw,relatime,si=82ce0764d1af8a79 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
tmpfs /tmp tmpfs rw,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
tmpfs /var/log tmpfs rw,relatime 0 0
tmpfs /var/tmp tmpfs rw,relatime 0 0
tmpfs /var/lib/dhcp3 tmpfs rw,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/cmhaadmin/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0

```

Here's what it looks like after running remountrw:

```

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev tmpfs rw,relatime,mode=755 0 0
**/dev/disk/by-uuid/2f4daaaa-ec96-426c-be68-f4bb6bfe4166 /ro ext4 rw,relatime,barrier=0,data=ordered 0 0**
none /sys/kernel/security securityfs rw,relatime 0 0
aufs-tmpfs /rw tmpfs rw,relatime 0 0
aufs / aufs rw,relatime,si=82ce0764d1af8a79 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
tmpfs /tmp tmpfs rw,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
tmpfs /var/log tmpfs rw,relatime 0 0
tmpfs /var/tmp tmpfs rw,relatime 0 0
tmpfs /var/lib/dhcp3 tmpfs rw,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/cmhaadmin/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0

```

As you can see, the rw flag is set after remounting, but making changes doesn't commit (I tried 'touch foobar' in my sudo user's home directory, and then running remountro and rebooting).

My grub.cfg has been edited manually (that was another adventure altogether) for now, will fix once I have this working.

Here's my grub.cfg:

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 2f4daaaa-ec96-426c-be68-f4bb6bfe4166
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###



### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# aufs read-only grub menu items
menuentry "Ubuntu, Linux 2.6.31-20-generic READ-ONLY" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 2f4daaaa-ec96-426c-be68-f4bb6bfe4166
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=2f4daaaa-ec96-426c-be68-f4bb6bfe4166 ro quiet splash aufs=tmpfs rootflags=barrier=0
        initrd  /boot/initrd.img-2.6.31-20-generic
}

menuentry "Ubuntu, Linux 2.6.31-20-generic WRITEABLE" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 2f4daaaa-ec96-426c-be68-f4bb6bfe4166
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=2f4daaaa-ec96-426c-be68-f4bb6bfe4166 ro quiet splash
        initrd  /boot/initrd.img-2.6.31-20-generic
}


menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 2f4daaaa-ec96-426c-be68-f4bb6bfe4166
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=2f4daaaa-ec96-426c-be68-f4bb6bfe4166 ro single
        initrd  /boot/initrd.img-2.6.31-20-generic
}

### END /etc/grub.d/40_custom ###



### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

```

---

### Post by gravyface on 2010-04-13
Ok as a test (and after looking at /proc/mounts a bit more carefully), I ran remountrw and touched a file in /ro/home/gravyface, remountro'ed, and rebooted and the file was present in /home/gravyface.

Is this the expected behavior?  I could've sworn that with Voyage Linux (which this rootaufs script is based off of) you could run the system normally when remountrw'ed (i.e. apt-get install/remove, etc.).  Am I missing something?

I'm following these instructions:
[https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)

Running Ubuntu 9.10 2.6.31-20 64-bit; /dev/sda1 is a CompactFlash card (SATA-to-CF adapter) formatted with Ext4.

---

### Post by Perkins on 2010-05-31
For what it's worth, Puppy Linux does exactly this kind of thing when running from a flash drive...  You might take a look at their scripts and see if they're easily convertible for a full-size distribution...

---

### Post by zagaeski on 2010-08-18
Many thanks for this script! I use it every day. It really does the trick. 

I often remountrw or mount a scratch partition to store things across reboots. Of course, sometimes I forget to remountro before rebooting. I've noticed that this always causes fsck to complain about improper unmounting. After a little looking around it became clear that the umountfs and umountroot scripts in /etc/init.d are not set up to handle the rootaufs scenario. To fix them I added the following lines to the rootaufs script (after the fstab fixes):

```

cat /aufs/ro/etc/init.d/umountfs | \
    sed 's:\(PROTECTED_MOUNTS.*\)\^.... .. .. /:\1^aufs.* \\/ /:' \
    | sed 's:\(^\s*/|/proc.*\)):\1|/ro|/rw):' >/aufs/etc/init.d/umountfs

cat /aufs/ro/etc/init.d/umountroot | \
    sed 's:\(\s*\)\(mount.*dummytype.*dummydev.*\):\1for aroot in /ro /rw /; do\n\1\2:' \
    | sed '/mount.*dummytype.*dummydev/,/ES=/s:\(\s*\)\(.*\) /\([ ]*\):\1    \2 $aroot\3:' \
    | sed 's/\(\s*\)ES=\$?/\1done\n\1ES=$?/' >/aufs/etc/init.d/umountroot

```umountfs is expecting a /proc/mounts that has a line starting with "/some-dev / " somewhere after the first line. It leaves anything above this line mounted. In the rootaufs case, the script should instead look for a line starting with "aufs / ". As an extra precaution, add /ro and /rw to the list of mounts that umountfs should not touch.

For umountroot, run a loop that umounts /ro /rw and finally /, instead of just umounting /. I'm not certain what the best order is for umounting these, but this seems to work.


Cheers,
Brendan

---

### Post by kangarooks on 2012-01-18
I run this script on 11.04 and i have following errors:

from gnome panel:
```
"Indicator Applet Session" has quit unexpectedly
"Indicator Applet" has quit unexpectedly
```
and i have no sound

dmesg shows:

```
dmesg | cut -d ']' -f 2 | grep hardlink| sort | uniq
non-accessible hardlink creation was attempted by: compiz (fsuid 1000)
 non-accessible hardlink creation was attempted by: gconfd-2 (fsuid 1000)
 non-accessible hardlink creation was attempted by: gconfd-2 (fsuid 106)
 non-accessible hardlink creation was attempted by: gdm-session-wor (fsuid 1000)
 non-accessible hardlink creation was attempted by: gdm-simple-slav (fsuid 106)
 non-accessible hardlink creation was attempted by: gvfsd-metadata (fsuid 1000)
 non-accessible hardlink creation was attempted by: indicator-apple (fsuid 1000)
 non-accessible hardlink creation was attempted by: opera (fsuid 1000)
 non-accessible hardlink creation was attempted by: pulseaudio (fsuid 1000)
 non-accessible hardlink creation was attempted by: ubuntuone-login (fsuid 1000)
 non-accessible hardlink creation was attempted by: ubuntuone-syncd (fsuid 1000)
 non-accessible hardlink creation was attempted by: zeitgeist-daemo (fsuid 1000)

```
and couple of:
```
Error in vfs_unlink; rc = [-1]

```

apparmor is off

help pls, since i really wanna have my linux on pendrive :)
](*,):-({|=:cry:

---

### Post by mcduck on 2012-01-18
Considering that this is years old thread, and has absolutely nothing to do with the problem you are having, you really should just start a new thread of your own, with a title related to your problem.

---

### Post by kangarooks on 2012-01-18
k, found solution for it:

kernel.yama.protected_nonaccess_hardlinks=0 in boot options /etc/defautls/grub fixes it

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/663069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/663069)
:guitar:\\:D/

---

### Post by kangarooks on 2012-01-18
and that solution doesnt fix the problem... sucks, time to go for plan b, which is by hand tmpfs-aufs the main offenders... oh well

---

### Post by kangarooks on 2012-01-18
> **mcduck said:**
> Considering that this is years old thread, and has absolutely nothing to do with the problem you are having, you really should just start a new thread of your own, with a title related to your problem.

no.

i would suggest you should drop passive-agressive and/or authoritarian tone from your future posts, and maybe read what is really going on (i.e. that my post has EVERYTHING to do with aufs on root on ubuntu).

also, the help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash   howto points to this thread, if youre owner of that howto then please fix that...

kthxbai

---

### Post by chainu127 on 2012-03-03
I also came across the non-accessible hardlink creation problem, with xbmc. As stated, the kernel option kernel.yama.protected_nonaccess_hardlinks=0 is what needs to be done, but passing it as a kernel option in GRUB does not work. My solution was to embed it in a startup script instead:

```
sudo nano -w /etc/init.d/hardlinks_fix
```then save this in the new file:

```
#! /bin/sh
# /etc/init.d/hardlinks_fix
#

sysctl -w kernel.yama.protected_nonaccess_hardlinks=0

exit 0
```make it executable and add it to the default runlevel:

```
sudo chmod +x /etc/init.d/hardlinks_fix

sudo update-rc.d hardlinks_fix defaults
```After this, and the AppArmor workaround "aa-complain dhclient3" to get networking under aufs, xbmc seems to be working for me and I don't have the hardlinks creation error anymore.

---

