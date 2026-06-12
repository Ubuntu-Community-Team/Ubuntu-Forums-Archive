---
title: "External Firewire Drive?"
date: 2007-04-17
forum: General Help
---

### Post by LearnedHand on 2007-04-17
I have an external firewire drive that seems to work fine with ubuntu, but only mounts in read-only mode. I originally just plugged it in, and ubuntu was able to mount the drive by itself in read-only mode. I tried unmounting it and mounting it again using the "mount" command and the "w" flag to explicitly tell it to mount in read/write mode. Even with this command, the drive still mounts in read-only mode. 

The drive seems to have the proper permissions, though any attempt to change them fails because the system can't write to the drive. The drive also works fine when I hook it up to my PowerBook. One possible explanation is that it's a problem related to my unusual firewire port. 

The firewire port is actually part of my sound card (SoundBlaster Audigy Platinum). I was quite surprised that ubuntu was able to mount a drive connected through a firewire port in my soundcard, but it does. The only thing I can think of is that, perhaps the firewire port on the sound card is designed only as an input device, but not as an output. Seems possible but unlikely to me. Wouldn't the port need to go both ways just to communicate with the device?

Another possible explanation is that the drive is formated hfsplus (is this a wonky format in the linux world?). The drive was originally formatted for use with my PowerBook, but it would be much more convenient for me to have it permanently hooked up to the ubuntu machine and I could read from and write to it over the network. Again, though, it doesn't seem likely that, if ubuntu can read the drive OK, it wouldn't be able to write to it because of a formatting issue.

Does anybody know what I could do to make this drive writable?

---

### Post by dfreer on 2007-04-17
from what I read hfsplus should have full read/write support on linux, although I don't use it so I can't be sure. could you post your /etc/fstab and /etc/mtab files when the hard drive is plugged in?

---

### Post by girishv on 2007-04-17
did you try writing as root ??
Sometimes, it might be a simple issue of permissions

Girish

---

### Post by LearnedHand on 2007-04-17
dfreer,

Here is /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=960b7e07-1cba-4f70-9c91-3894b7ef22ef /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4dd961da-db3f-4be6-bed0-64054333af1e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

One useful thing to note here is that System Monitor says that the firewire drive is mounted from /dev/sda6 which doesn't seem to appear here even though the drive is mounted and readable.

Here is /etc/mtab

```

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-generic/volatile tmpfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda6 /media/ieee1394disk hfsplus rw,nosuid,nodev,uid=1000,gid=1000 0 0

```

Seems /dev/sda6 shows up here. I'm inclined to think the "rw" has something to do with read/write capability. 

Also, girishv, I tried writing as root but had no success. Thanks for the suggestion.

Hopefully this will be meaningful. Thanks for your help.

---

### Post by dfreer on 2007-04-17
your welcome.

Hotpluggable devices are generally listed in /etc/mtab instead of /etc/fstab, I think it's because of the pmount program. Everything looks like it is mounted correctly, hmmm. Is there some sort of hardware switch that is write-protecting (like the VCR tapes used to have that tab...)

[http://www.linuxquestions.org/questions/showthread.php?t=514686](http://www.linuxquestions.org/questions/showthread.php?t=514686)

Seems like hfsplus should work just fine. try plugging in the drive, and then posting the output from the dmesg command. In particular I'm looking for a *sda: Write Protect is on* or something similiar...

---

### Post by dfreer on 2007-04-17
also, are you running edgy or dapper?

Check out this post, it has some info regarding a hfsplus with journaling turned on, which evidently prevents linux from writing to it.

[http://ubuntuforums.org/showthread.php?p=1859336](http://ubuntuforums.org/showthread.php?p=1859336)

---

### Post by LearnedHand on 2007-04-17
Thanks so much, dfreer. The link you gave me: [http://ubuntuforums.org/showthread.php?p=1859336](http://ubuntuforums.org/showthread.php?p=1859336) gave me the information i needed to fix it. My hfsplus drive did not have journaling enabled, but did require the procedures indicated in that link. Everything works perfectly now!


You rock!

---

### Post by dfreer on 2007-04-17
Your welcome! But for future reference (in case anyone else stumbles across this thread with the same problem), what were the steps you followed?

---

### Post by LearnedHand on 2007-04-18
I followed the directions at this link [http://ubuntuforums.org/showthread.php?p=1859336](http://ubuntuforums.org/showthread.php?p=1859336)

Essentially, i entered the series of commands detailed below.

```

cd /usr/src 
mkdir hfsplus_support
wget http://darwinsource.opendarwin.org/tarballs/apsl/diskdev_cmds-332.14.tar.gz
wget http://www.ecl.udel.edu/~mcgee/diskdev_cmds/diskdev_cmds-332.14.patch.bz2
tar zxf diskdev_cmds-332.14.tar.gz
bunzip2 -c diskdev_cmds-332.14.patch.bz2 | patch -p0
cd diskdev_cmds-332.14
make -f Makefile.lnx
cp fsck_hfs.tproj/fsck_hfs /sbin/fsck.hfsplus
cd /sbin
ln -s fsck.hfsplus fsck.hfs

```

After entering those commands in sequence, I then followed the instructions to "check" the filesystem in order to make the partition/drive read-write enabled.

```

fsck.hfsplus -r /dev/sda6

```

Where /dev/sda6 = the path do your mounted device

I only have the vaguest sense of what fsck does, but I know this worked for me.

One thing to mention is that after running the last command, I found that the drive was totally unaccessible. Once I unmounted it, unplugged it, and then plugged it back in, the automount procedure brought everything back up and the drive was writable.

Thanks so much for your help, and hopefully this thread will prove useful for someone else.

---

