---
title: "Please Help! I'm having a samba disaster..."
date: 2007-12-20
forum: General Help
---

### Post by Gang_Star on 2007-12-20
Hi everyone. I'm having a lot of trouble setting up my /windows partition to be shared to XP users on my network. I have tried many many different tutorials as well as advice given on other threads which seemed relevant. For some reason there doesn't seem to be any single way that everyone uses, which has left me confused...

So far I am confident I have installed samba using the repositories. I am able to use folders that XP users have shared.

I have also set up sharing to the point that my computer can be seen by XP computers on the correct network, although you can't access it (It requires a password I can't work out)

I have tried to set the permissions for /windows in windows properties. Originally I had full access to change these settings and they would immediately undo. Now since I have been following guides and editing my fstab all of the options are grey'd out. It says "You are not the owner...." at the bottom.

Here is the contents of my current fstab. Anything starting with #### is an attempt following a guide that did not work.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=34069c03-d747-4cee-85a6-3cdb5c565cbc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
####/dev/hda2         /media/winXP      vfat      defaults,users,ro  0              0
####/dev/hda2  /windows  vfat iocharset=utf8,umask=000 0 0
UUID=D7AE-81E1  /windows        vfat    defaults,utf8,umask=007,gid=46 0  
####UUID=D7AE-81E1  /windows        vfat    defaults,utf8,umask=0000,uid=1000,gid=1000 0     1
# /dev/hda5
UUID=5f2eeafd-4987-4ab0-8b5d-b54141877f6c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Thanks in advance for any help given

---

### Post by TeaSwigger on 2007-12-20
Networking can be a real pain in the  - eh, you know.

Welp, have you seen these two:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

Those two - and sheer persistence - were great help to me.

If those don't help, what's the network you're configuring? Wired ethernet type? One Ubuntu, one Windows? etc, more detail the better generally.

A few observations though. Assuming you mean that you have XP and Ubuntu installed on PC a, you want to run Ubuntu not XP on PC a, yet have PC b, c, etc which run XP access the XP parititon on PC a. Your Windows XP paritition on PC a should be using NTFS. You should have NTFS read/write support sorted first. If this is right, your fstab entry for the XP partition on the Ubuntu PC should read something like this:

```
# Entry for /dev/sda1 :
UUID=[blah blah] /windows ntfs-3g defaults,locale=en_US.UTF-8 0 1
```

But I'm not sure as to the security adviseability of sharing the partition XP's installed on. Sounds like it could be trouble, but I'm no expert. We might be crossing wires here, so please clarify the specifics.

And don't worry, you'll get it eventually. :)

---

