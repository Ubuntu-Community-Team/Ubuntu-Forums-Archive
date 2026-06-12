---
title: "fsck died with exit status 8"
date: 2006-11-08
forum: General Help
---

### Post by Red Knuckles on 2006-11-08
I have a multi-partition computer with Kubuntu Edgy [/dev/hda1 & /dev/hda2], Fedora Core 6 [/dev/hda6], and Suse 10.1 [/dev/hda7]. After a rescent upgrade in Fedora I started getting the following error when booting into either Kubuntu partition:

Log of fsck -C -R -A -a
Wed Nov  8 14:19:54 2006

fsck 1.39 (29-May-2006)
/dev/evms/hda1: clean, 113661/9486336 files, 1510685/18944643 blocks
fsck.ext3: Unable to resolve 'UUID=1ba0e117-1c0c-4e2c-a2bd-0dfd679c4eda'
Replaying journal..
Reiserfs journal '/dev/evms/hda7' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0xfd04 of format 3.6 with standard journal
Blocks (total/free): 19159504/11701345 by 4096 bytes
Filesystem is clean
Reiserfs super block in block 16 on 0xfd04 of format 3.6 with standard journal
Blocks (total/free): 19159504/11701345 by 4096 bytes
Filesystem is clean
fsck died with exit status 8

I can continue booting by running Control 'D'. I have run 'fsck' on all partitions [isn't that what grub is trying to do anyway?]. I think the problem is in this line:

fsck.ext3: Unable to resolve 'UUID=1ba0e117-1c0c-4e2c-a2bd-0dfd679c4eda'

Here is /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
# /dev/hda1 -- converted during upgrade to edgy
UUID=0adcab9e-e1a1-4afc-a385-32fa090ab5cc /media/hda1 ext3 defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=1ba0e117-1c0c-4e2c-a2bd-0dfd679c4eda /media/hda6 ext3 defaults 0 2
# /dev/hda7 -- converted during upgrade to edgy
UUID=e6dfb206-315f-411d-9ba6-e78c9c6d1080 /media/hda7 reiserfs defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=453cbad6-f87c-4d0e-b9a9-95f647309ff1 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=4f326857-460c-4ad7-990d-921916a9e719 /                    ext3       defaults              1 1

One question is why does it label everything including swap as 'converted during upgrade to edgy'? The error line in the boot menu seems to indicate that it can't recognize the Fedora partition to run fsck on '/dev/hda6' resulting in error #8 which according to the man pages for fsck is 'operational error'. At any rate how to correct this? I don't think it's in 'boot/grub/menu.lst' as Fedora and Suse boot just fine. But here is the Fedora and Suse entries for '/boot/grub/menu.lst' anyway.

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title      Fedora Core (2.6.18-1.2798.fc6) (on /dev/hda6)
root      (hd0,5)
kernel      /boot/vmlinuz-2.6.18-1.2798.fc6 ro root=LABEL=1
initrd      /boot/initrd-2.6.18-1.2798.fc6.img
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title      SUSE Linux 10.1 (on /dev/hda7)
root      (hd0,6)
kernel      /boot/vmlinuz root=/dev/hda7 resume=/dev/hda5 splash=silent showopts
initrd      /boot/initrd
savedefault
boot

Anyone let me know if more info is needed or if I'm incorrect in my assumption that the problem is to get '/etc/fstab' to let 'grub' do 'fsck' on '/dev/hda6'. I am a noobie after all. ](*,) :mrgreen:

---

