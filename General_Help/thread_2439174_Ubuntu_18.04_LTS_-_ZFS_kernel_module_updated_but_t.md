---
title: "Ubuntu 18.04 LTS - ZFS kernel module updated but tools still older version"
date: 2020-03-24
forum: General Help
---

### Post by LaMosca on 2020-03-24
I recently installed Ubuntu 18.04 LTS and ZFS for use with some existing OpenZFSonOSX pools migrating from a Mac.

I didn't check the ZFS kernel module when I built/installed, but checking it now via modinfo zfs shows it's 0.8.1 (and was installed as part of the linux-modules-5.3.0-40-generic package). The other ZFS packages are all on older version (0.7.5). I've applied updates several times since installing a few weeks ago.

$ modinfo zfs
filename:       /lib/modules/5.3.0-40-generic/kernel/zfs/zfs.ko
version:        0.8.1-1ubuntu14.3
license:        CDDL
author:         OpenZFS on Linux
description:    ZFS
alias:          devname:zfs
alias:          char-major-10-249
srcversion:     F3C94D5226BB5E654A00EF1
depends:        zlua,spl,znvpair,zcommon,icp,zunicode,zavl
retpoline:      Y
name:           zfs
vermagic:       5.3.0-40-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
<snip>

$ dpkg -S /lib/modules/5.3.0-40-generic/kernel/zfs/zfs.ko
linux-modules-5.3.0-40-generic: /lib/modules/5.3.0-40-generic/kernel/zfs/zfs.ko


$ dpkg -l | grep -i zfs
ii  libzfs2linux                               0.7.5-1ubuntu16.8                                amd64        OpeZFS filesystem library for Linux
ii  libzpool2linux                             0.7.5-1ubuntu16.8                                amd64        OpeZFS pool library for Linux
ii  zfs-zed                                    0.7.5-1ubuntu16.8                                amd64        OpeZFS Event Daemon
ii  zfsutils-linux                             0.7.5-1ubuntu16.8                                amd64        command-line tools to manage

I did a "pool upgrade" on one of my migrated pools as I thought I'd be bringing it up to the latest zpool version, but I'm thinking now that may not be the case. I am now getting an Errata #4 message:

# zpool status r10
  pool: r10
 state: ONLINE
status: Errata #4 detected.
   see: [http://zfsonlinux.org/msg/ZFS-8000-ER](http://zfsonlinux.org/msg/ZFS-8000-ER)
  scan: scrub repaired 0B in 10h47m with 0 errors on Sun Mar  8 12:11:59 2020
config:


    NAME        STATE     READ WRITE CKSUM
    r10         ONLINE       0     0     0
      mirror-0  ONLINE       0     0     0
        sdw     ONLINE       0     0     0
        sdx     ONLINE       0     0     0
      mirror-1  ONLINE       0     0     0
        sdr     ONLINE       0     0     0
        sds     ONLINE       0     0     0

Here you can see the message I was getting before the "zpool upgrade r10" I did (this is for the other pool I migrated but did NOT do a 'zpool upgrade' on):
errors: No known data errors
# zpool status rz2
  pool: rz2
 state: ONLINE
status: Some supported features are not enabled on the pool. The pool can
    still be used, but some features are unavailable.
action: Enable all features using 'zpool upgrade'. Once this is done,
    the pool may no longer be accessible by software that does not support
    the features. See zpool-features(5) for details.
  scan: scrub repaired 0B in 32h16m with 0 errors on Mon Mar  9 09:40:53 2020
config:


    NAME        STATE     READ WRITE CKSUM
    rz2         ONLINE       0     0     0
      raidz2-0  ONLINE       0     0     0
        sdz     ONLINE       0     0     0
        sdaa    ONLINE       0     0     0
        sdp     ONLINE       0     0     0
        sdq     ONLINE       0     0     0
        sdu     ONLINE       0     0     0
        sdv     ONLINE       0     0     0
        sdl     ONLINE       0     0     0
        sdm     ONLINE       0     0     0


errors: No known data errors


So now the question is, how do I proceed from here? I wouldn't have though the kernel module would have been updated without also updating the ZFS tools/utilities so they all match.

Thanks in advance for any help/guidance!

---

### Post by kneutron on 2020-04-07
--It's been a while since I've had to deal with this, I ended up scrapping the zfs dkms packages and reinstalling zfs from source :)

Try (as root): **[COLOR=#28FE14][FONT=Menlo]apt-get install --reinstall zfs-dkms zfsutils-linux[/FONT][/COLOR]**

---

