---
title: "Advanced Grub2 help needed"
date: 2022-12-26
forum: General Help
---

### Post by MAFoElffen on 2022-12-26
I'm testing, migrating normal ext4 systems to a ZFS filesystem... I'll boot  on a disk with Ubuntu on it (on ext4)... on another disk (defined as attached to  the same machine in KVM) define a ZFS root pool with datasets on a  partition on that disk... or on another partition the same disk. (It doesn't matter at that  point where that partition resides.)

If I do not do any ZFS mounts defined... such at where it mounts or a  temporary mount, then I can actually copy to it by giving it a path...  for example:
```

## ...with /boot native in the same partition, no additional mounts
UUID=2204
zpool create rpool
zfs create rpool/ROOT
zfs create rpool/ROOT/ubuntu_$UUID
rysnc -a --one-file-system / /rpool/ROOT/ubuntu_$UUID/  # It ryncs
cd /rpool/ROOT/ubuntu_$UUID/
mount --bind /dev dev
mount --bind /proc proc
mount --bind /sys sys
mount -o bind /run run
update-grub
## ...and whatever I want to do...

```
And treat ZFS pools and datasets as if they were just a path... Even  though it is in another partition, maybe even on another disk.

If I do
```

## ...with /boot native in the same partition, no additional mounts
UUID=2204
zpool create -R /mnt rpool
zfs create rpool/ROOT
zfs create rpool/ROOT/ubuntu_$UUID
rysnc -a --one-file-system / /mnt/rpool/ROOT/ubuntu_$UUID
cd /mnt
mount --bind /dev dev
mount --bind /proc proc
mount --bind /sys sys
mount -o bind /run run
update-grub
## ...and whatever I want to do...

```
Except, that just doing that grub-probe starts failing, with occasional unknown filesystem errors on /boot ...and such, but if I start manipulating ZFS pool and dataset mounts with  root inside the pool, then grub gets confused, thinking it needs to use  the extended path of, instead of where it is really mounted. 

Unless I use a separate bpool (boot) pool which I 'ZFS mount' into the ZFS file system... Then it will start ID'ing that bpool as ZFS, but... (See were that is going yet?)

For example, if I do
     ```

zpool create -o mountpoint=/ -R /mnt rpool
zfs create -o canmount=off -o mountpoint=none /rpool/ROOT/
zfs create -o mountpoint=/ -R /mnt 
rsync -a --one-file-system / /mnt
cd /mnt
## mounts and such 

```
But with /boot and boot/grub in the native filesystem partition,  grub gets confused, thinking it is at (a full path of)  /rpool/ROOT/ubuntu_2204/boot/grub instead of at /boot/grub. (doesn't  follow the ZFS internal mounts). 

See attachment... To get this to boot, I can edit it like the second attachment, and it will boot...

[COLOR=#ff0000]So how do I override Grub to correct the path to? And for some reason,  it I write it out in 40_custom, update-grub is not picking it up...
[/COLOR]
For example, as a work around, I tried this as a 40_custom file (but grub is not picking it up to add to the grub menu)...
```

### BEGIN 40_linux_zfs ###
##
menuentry 'Ubuntu Lunar Lobster ZFS (custom)' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-rpool/ROOT/ubuntu_2304-5.19.0-21-generic' {
    recordfail
    load_video
    gfxmode ${linux_gfx_mode}
    insmod gzio
    if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    linux    "/boot/vmlinuz-5.19.0-21-generic" root=ZFS="rpool/ROOT/ubuntu_2304" ro --- splash ${vt_handoff}
    initrd    "/boot/initrd.img-5.19.0-21-generic"
}

```
This last condition is where I need help with. Letting grub know where /boot resides. In this last text case, I need to change were it resides to honor the path pointers.

EDIT1: I should probably mention that grub-probe returns "unknown filesystem" that I suspect is from /boot being native (located in root) in a Native ZFS encrypted root pool... And this happens with 22.04 also.

---

### Post by #&amp;thj^% on 2022-12-28
I miss him too ( DrDos,)
Some of the things I've learned, but not set in stone yet is
ZFS administration is very easy and intuitive. zpool and zfs are basicaly the only commands you need. Parameters and options can be learned quickly. Getting it on your root partition on a OS that doesn&#8217;t support ZFS natively for legal and &#8220;political&#8221; reasons, is very hard. Ubuntu Installer is really a blessing in that department for people who just want ZFS-on-root on their PC.

I would suggest, keep the boot/OS drive separate to the data drives. and go ahead and use ZFS on the data drives.

It is rare to get a un-bootable, but if you do ZFS on root, one might get into a problematic situation. but lots of people use it fine.
All this is something I suspect you already knew though, I wish i better advice for you. And I can't keep ZFS on this AMD machine. Far too many freeze's for my tastes.
My Intel i7 runs ZFS root like a champ though.

---

### Post by oldfred on 2022-12-28
Always interested in grub issues. But do not use nor plan to use zfs.

[https://openzfs.github.io/openzfs-docs/Getting%20Started/Debian/Debian%20Buster%20Root%20on%20ZFS.html#step-3-system-installation](https://openzfs.github.io/openzfs-docs/Getting%20Started/Debian/Debian%20Buster%20Root%20on%20ZFS.html#step-3-system-installation)
  Shows first quote before root=
And I do not have " around /boot entries on linux & initrd lines.

> 
[LIST]
[*]Workaround GRUB&#8217;s missing zpool-features support:
 vi /etc/default/grub
# Set: GRUB_CMDLINE_LINUX="root=ZFS=rpool/ROOT/debian"

 
[/LIST]


---

### Post by #&amp;thj^% on 2022-12-28
> **oldfred said:**
> Always interested in grub issues. But do not use nor plan to use zfs.

[https://openzfs.github.io/openzfs-docs/Getting%20Started/Debian/Debian%20Buster%20Root%20on%20ZFS.html#step-3-system-installation](https://openzfs.github.io/openzfs-docs/Getting%20Started/Debian/Debian%20Buster%20Root%20on%20ZFS.html#step-3-system-installation)
  Shows first quote before root=
And I do not have " around /boot entries on linux & initrd lines.

Nice Find oldfred, I'm now curious how MAFoElffen will fare with it.
> **oldfred said:**
> Always interested in grub issues. But do not use nor plan to use zfs.

Ahh come on where's your sense of adventure...:D

---

### Post by MAFoElffen on 2022-12-28
That is a problem of consistency... That is in the OpenZFS Debian instructions.The OpenZFS instructions are not consistent from Debian to Ubuntu...

For Ubuntu 20.04, it had ZSys installed by default in the installer. For the OpenZFS instructions...
> 
On Solaris systems, the root filesystem is cloned and the suffix is incremented for major system changes through pkg image-update or beadm. Similar functionality was implemented in Ubuntu with the zsys tool, though its dataset layout is more complicated, and zsys [is on life support]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1968150"). Even without such a tool, the rpool/ROOT and bpool/BOOT containers can still be used for manually created clones.

In Ubuntu 22.04, If you select to install ZFS-On-Root, it initially installs ZSys, but then uninstalls it during the setup's dpkg cleanup near the end of the installation process. It is no longer a default installed application.

For 23.04... The ZFS-On-Root option is gone from the installer. They are trying to implement ZFS differently, which it a no-go so far. Trying to treat it as if it was solely a filesystem, instead of a file manager (like LVM) with a filesystem (like ext4). "That change" is killing them in how they are trying to do that, because it is not solely a filesystem.

I'm figuring out easy ways to create the basic pool/dataset structure then rsync (clone) within it, using the basic premise of the first sentence in the quote above. It works very fast. Just by coincidence, how I've been doing that, is somehow similar to how the new installer process has changed. I don't mind, as the process is so much faster.

If I could just get grub to take hints better.

On the "root="... for Debian... If you look at the two attachments and my 40_custom, I think Ubuntu already addressed that, as even without adding that, it has that in the generated grub.cfg. Adding it manually did not make a difference. (I tried it.)

---

### Post by oldfred on 2022-12-28
Grub also shows 3 zfs .mod files.
```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/boot/grub/x86_64-efi**[/COLOR][COLOR=#000000]$ ll zfs* [/COLOR]
-rw-r--r-- 1 root root  8536 Dec  1 22:28 zfscrypt.mod 
-rw-r--r-- 1 root root 10728 Dec  1 22:28 zfsinfo.mod 
-rw-r--r-- 1 root root 57960 Dec  1 22:28 zfs.mod 
[/FONT]
```

Do you need to add insmod of one or more of these files, so grub knows about zfs?
Only some things are built into grub. For Example, it used to be you had to insmod gpt, but now it does not seem to be required.

---

### Post by MAFoElffen on 2022-12-29
ismod gpt still looks like IS there, as well as insmod zfs... This is from my main server:
```

### BEGIN /etc/grub.d/10_linux_zfs ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=1
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
function zsyshistorymenu {
    # $1: root dataset (eg rpool/ROOT/ubuntu_2zhm07@autozsys_k56fr6)
    # $2: boot device id (eg 411f29ce1557bfed)
    # $3: initrd (eg /BOOT/ubuntu_2zhm07@autozsys_k56fr6/initrd.img-5.4.0-21-generic)
    # $4: kernel (eg /BOOT/ubuntu_2zhm07@autozsys_k56fr6/vmlinuz-5.4.0-21-generic)
    # $5: kernel_version (eg 5.4.0-21-generic)

    set root_dataset="${1}"
    set boot_device="${2}"
    set initrd="${3}"
    set kernel="${4}"
    set kversion="${5}"

    menuentry 'Revert system only' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-${root_dataset}-${kversion}' {
        recordfail
        load_video
        gfxmode ${linux_gfx_mode}
        insmod gzio
        if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
        if [ ${boot_device} = /dev/nvme0n1p3 ]; then
            [COLOR=#ff0000]insmod part_gpt
            insmod zfs[/COLOR]
            search --no-floppy --fs-uuid --set=root aacf6553a7dbb896
        fi
        linux    "${kernel}" root=ZFS="${root_dataset}" ro -- splash kvm-intel.nested=1 video=uvsesafb:mode_option=1024x768-32,mtrr=3,scroll=ywrap,noedid ${vt_handoff}
        initrd    "${initrd}"
    }
    menuentry 'Revert system and user data' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-${root_dataset}-${kversion}' {
        recordfail
        load_video
        gfxmode ${linux_gfx_mode}
        insmod gzio
        if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
        if [ ${boot_device} = /dev/nvme0n1p3 ]; then
            insmod part_gpt
            insmod zfs
            search --no-floppy --fs-uuid --set=root aacf6553a7dbb896
        fi
        linux    "${kernel}" root=ZFS="${root_dataset}" ro -- splash kvm-intel.nested=1 video=uvsesafb:mode_option=1024x768-32,mtrr=3,scroll=ywrap,noedid ${vt_handoff} zsys-revert=userdata
        initrd    "${initrd}"
    }
    menuentry 'Revert system only (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-${root_dataset}-${kversion}' {
        recordfail
        load_video
        insmod gzio
        if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
        if [ ${boot_device} = /dev/nvme0n1p3 ]; then
            insmod part_gpt
            insmod zfs
            search --no-floppy --fs-uuid --set=root aacf6553a7dbb896
        fi
        echo Loading Linux ${kversion} ...
        linux    "${kernel}" root=ZFS="${root_dataset}" ro recovery nomodeset dis_ucode_ldr
        echo 'Loading initial ramdisk ...'
        initrd    "${initrd}"
    }
    menuentry 'Revert system and user data (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-${root_dataset}-${kversion}' {
        recordfail
        load_video
        insmod gzio
        if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
        if [ ${boot_device} = /dev/nvme0n1p3 ]; then
            insmod part_gpt
            insmod zfs
            search --no-floppy --fs-uuid --set=root aacf6553a7dbb896
        fi
        echo Loading Linux ${kversion} ...
        linux    "${kernel}" root=ZFS="${root_dataset}" ro recovery nomodeset dis_ucode_ldr zsys-revert=userdata
        echo 'Loading initial ramdisk ...'
        initrd    "${initrd}"
    }
}

menuentry 'Ubuntu 22.04.1 LTS' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-rpool/ROOT/ubuntu_2cwpns-5.15.0-56-generic' {
    recordfail
    load_video
    gfxmode ${linux_gfx_mode}
    insmod gzio
    if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod zfs
    search --no-floppy --fs-uuid --set=root aacf6553a7dbb896
    linux    "/BOOT/ubuntu_2cwpns@/vmlinuz-5.15.0-56-generic" root=ZFS="rpool/ROOT/ubuntu_2cwpns" ro -- splash kvm-intel.nested=1 video=uvsesafb:mode_option=1024x768-32,mtrr=3,scroll=ywrap,noedid ${vt_handoff}
    initrd    "/BOOT/ubuntu_2cwpns@/initrd.img-5.15.0-56-generic"
}
submenu 'Advanced options for Ubuntu 22.04.1 LTS' ${menuentry_id_option} 'gnulinux-advanced-rpool/ROOT/ubuntu_2cwpns' {
    menuentry 'Ubuntu 22.04.1 LTS, with Linux 5.15.0-56-generic' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-rpool/ROOT/ubuntu_2cwpns-5.15.0-56-generic' {
        recordfail
        load_video
        gfxmode ${linux_gfx_mode}
        insmod gzio
        if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod zfs
        search --no-floppy --fs-uuid --set=root aacf6553a7dbb896
        echo Loading Linux 5.15.0-56-generic ...
        linux    "/BOOT/ubuntu_2cwpns@/vmlinuz-5.15.0-56-generic" root=ZFS="rpool/ROOT/ubuntu_2cwpns" ro -- splash kvm-intel.nested=1 video=uvsesafb:mode_option=1024x768-32,mtrr=3,scroll=ywrap,noedid ${vt_handoff}
        echo 'Loading initial ramdisk ...'
        initrd    "/BOOT/ubuntu_2cwpns@/initrd.img-5.15.0-56-generic"
    }
    menuentry 'Ubuntu 22.04.1 LTS, with Linux 5.15.0-56-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-rpool/ROOT/ubuntu_2cwpns-5.15.0-56-generic' {
        recordfail
        load_video
        insmod gzio
        if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod zfs
        search --no-floppy --fs-uuid --set=root aacf6553a7dbb896
        echo Loading Linux 5.15.0-56-generic ...
        linux    "/BOOT/ubuntu_2cwpns@/vmlinuz-5.15.0-56-generic" root=ZFS="rpool/ROOT/ubuntu_2cwpns" ro recovery nomodeset dis_ucode_ldr
        echo 'Loading initial ramdisk ...'
        initrd    "/BOOT/ubuntu_2cwpns@/initrd.img-5.15.0-56-generic"
    }
    menuentry 'Ubuntu 22.04.1 LTS, with Linux 5.15.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-rpool/ROOT/ubuntu_2cwpns-5.15.0-53-generic' {
        recordfail
        load_video
        gfxmode ${linux_gfx_mode}
        insmod gzio
        if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod zfs
        search --no-floppy --fs-uuid --set=root aacf6553a7dbb896
        echo Loading Linux 5.15.0-53-generic ...
        linux    "/BOOT/ubuntu_2cwpns@/vmlinuz-5.15.0-53-generic" root=ZFS="rpool/ROOT/ubuntu_2cwpns" ro -- splash kvm-intel.nested=1 video=uvsesafb:mode_option=1024x768-32,mtrr=3,scroll=ywrap,noedid ${vt_handoff}
        echo 'Loading initial ramdisk ...'
        initrd    "/BOOT/ubuntu_2cwpns@/initrd.img-5.15.0-53-generic"
    }
    menuentry 'Ubuntu 22.04.1 LTS, with Linux 5.15.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os ${menuentry_id_option} 'gnulinux-rpool/ROOT/ubuntu_2cwpns-5.15.0-53-generic' {
        recordfail
        load_video
        insmod gzio
        if [ "${grub_platform}" = xen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod zfs
        search --no-floppy --fs-uuid --set=root aacf6553a7dbb896
        echo Loading Linux 5.15.0-53-generic ...
        linux    "/BOOT/ubuntu_2cwpns@/vmlinuz-5.15.0-53-generic" root=ZFS="rpool/ROOT/ubuntu_2cwpns" ro recovery nomodeset dis_ucode_ldr
        echo 'Loading initial ramdisk ...'
        initrd    "/BOOT/ubuntu_2cwpns@/initrd.img-5.15.0-53-generic"
    }
}
### END /etc/grub.d/10_linux_zfs ###

```
lines 48 & 49 above.

---

### Post by #&amp;thj^% on 2022-12-29
> **MAFoElffen said:**
> 
For 23.04... The ZFS-On-Root option is gone from the installer. They are trying to implement ZFS differently, which it a no-go so far. Trying to treat it as if it was solely a filesystem, instead of a file manager (like LVM) with a filesystem (like ext4). **_"That change" is killing them in how they are trying to do that, because it is not solely a filesystem._**



I'm just going to wait for them to get a little more serious about ZFS this is just not up to Canonical's usual code standard.
For now I have BTRFS (Better or Butter) LOL
We have been at this way to long now, I've used every suggestion posted in this thread and beyond to no avail for 23.04.
I'm growing weary with Ubuntu all together.  Time for me to move on now. ;) If they would stop trying to re-invent the wheel, and just improve what they have on their plate now, that would be good.

EDIT: if this helps:
```
on Thu Dec 29 at 02:50 PM in /boot/grub/x86_64-efi branch: (HEAD) 
>> ll zfs*
-rwxr-xr-x 1 root root  8536 Dec 25 11:28 zfscrypt.mod*
-rwxr-xr-x 1 root root 10728 Dec 25 11:28 zfsinfo.mod*
-rwxr-xr-x 1 root root 57960 Dec 25 11:28 zfs.mod*

```
and:
```
me on Thu Dec 29 at 02:44 PM in ~ branch: (HEAD) 
>> mount | grep /boot/grub
/dev/sdb1 on /boot/grub type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


```
Lay out:
```
cdFilesystem                                       Type         Size  Used Avail Use% Mounted on
sysfs                                            sysfs           0     0     0    - /sys
proc                                             proc            0     0     0    - /proc
udev                                             devtmpfs     5.7G     0  5.7G   0% /dev
devpts                                           devpts          0     0     0    - /dev/pts
tmpfs                                            tmpfs        1.2G  1.8M  1.2G   1% /run
rpool/ROOT/ubuntu_79wek3                         zfs          887G  5.1G  882G   1% /
securityfs                                       securityfs      0     0     0    - /sys/kernel/security
tmpfs                                            tmpfs        5.8G     0  5.8G   0% /dev/shm
tmpfs                                            tmpfs        5.0M   12K  5.0M   1% /run/lock
cgroup2                                          cgroup2         0     0     0    - /sys/fs/cgroup
pstore                                           pstore          0     0     0    - /sys/fs/pstore
efivarfs                                         efivarfs        0     0     0    - /sys/firmware/efi/efivars
bpf                                              bpf             0     0     0    - /sys/fs/bpf
systemd-1                                        -               -     -     -    - /proc/sys/fs/binfmt_misc
mqueue                                           mqueue          0     0     0    - /dev/mqueue
debugfs                                          debugfs         0     0     0    - /sys/kernel/debug
tracefs                                          tracefs         0     0     0    - /sys/kernel/tracing
hugetlbfs                                        hugetlbfs       0     0     0    - /dev/hugepages
configfs                                         configfs        0     0     0    - /sys/kernel/config
ramfs                                            ramfs           0     0     0    - /run/credentials/systemd-sysusers.service
fusectl                                          fusectl         0     0     0    - /sys/fs/fuse/connections
rpool/USERDATA/root_7uagh8                       zfs          882G  1.7M  882G   1% /root
rpool/USERDATA/me_7uagh8                         zfs          883G  1.7G  882G   1% /home/me
rpool/ROOT/ubuntu_79wek3/srv                     zfs          882G  128K  882G   1% /srv
rpool/ROOT/ubuntu_79wek3/var/lib                 zfs          885G  3.6G  882G   1% /var/lib
rpool/ROOT/ubuntu_79wek3/var/snap                zfs          882G  128K  882G   1% /var/snap
rpool/ROOT/ubuntu_79wek3/var/mail                zfs          882G  128K  882G   1% /var/mail
rpool/ROOT/ubuntu_79wek3/usr/local               zfs          882G  256K  882G   1% /usr/local
rpool/ROOT/ubuntu_79wek3/var/log                 zfs          882G   23M  882G   1% /var/log
rpool/ROOT/ubuntu_79wek3/var/games               zfs          882G  128K  882G   1% /var/games
rpool/ROOT/ubuntu_79wek3/var/www                 zfs          882G  128K  882G   1% /var/www
rpool/ROOT/ubuntu_79wek3/var/spool               zfs          882G  128K  882G   1% /var/spool
rpool/ROOT/ubuntu_79wek3/var/lib/AccountsService zfs          882G  128K  882G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_79wek3/var/lib/apt             zfs          882G   84M  882G   1% /var/lib/apt
rpool/ROOT/ubuntu_79wek3/var/lib/NetworkManager  zfs          882G  256K  882G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_79wek3/var/lib/dpkg            zfs          882G   43M  882G   1% /var/lib/dpkg
bpool/BOOT/ubuntu_79wek3                         zfs          1.8G  317M  1.5G  18% /boot
/dev/sdb1                                        vfat         505M   74M  431M  15% /boot/efi
/dev/sdb1                                        vfat         505M   74M  431M  15% /boot/grub
rpool/ROOT/ubuntu_79wek3                         zfs          887G  5.1G  882G   1% /var/snap/firefox/common/host-hunspell
/dev/loop0                                       squashfs     239M  239M     0 100% /snap/firefox/2186
/dev/loop1                                       squashfs      50M   50M     0 100% /snap/snapd/17883
binfmt_misc                                      binfmt_misc     0     0     0    - /proc/sys/fs/binfmt_misc
tmpfs                                            tmpfs        1.2G   80K  1.2G   1% /run/user/1000

```
For The Record I'm using rEFInd as my boot manager here only.
```
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: vmlinuz-5.19.0-26-generic in rpool/ROOT/ubuntu_79wek3
Found initrd image: initrd.img-5.19.0-26-generic in rpool/ROOT/ubuntu_79wek3
Found linux image: vmlinuz-5.19.0-21-generic in rpool/ROOT/ubuntu_79wek3
Found initrd image: initrd.img-5.19.0-21-generic in rpool/ROOT/ubuntu_79wek3
Found memtest86+ 64bit EFI image: /BOOT/ubuntu_79wek3@/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Adding boot menu entry for UEFI Firmware Settings ...
done

```
**This will leave an ** un-bootable ** system>>>"# Set: GRUB_CMDLINE_LINUX="root=ZFS=rpool/ROOT/debian""**

---

### Post by MAFoElffen on 2022-12-30
I forced it to take the 40_custom menu item from post #1...

---

### Post by #&amp;thj^% on 2022-12-30
Great work what did you do different this time?
I thought we tried that a few time already.
Any who, please keep this post current...I'm very curious when it does break...:lolflag:
```
 df -ha
df: /run/user/1000/doc: Operation not permitted
Filesystem                                        Size  Used Avail Use% Mounted on
sysfs                                                0     0     0    - /sys
proc                                                 0     0     0    - /proc
udev                                              1.9G     0  1.9G   0% /dev
devpts                                               0     0     0    - /dev/pts
tmpfs                                             393M  1.4M  391M   1% /run
/dev/mapper/keystore-rpool                        437M   28K  404M   1% /run/keystore/rpool
rpool/ROOT/ubuntu_78v15v                           18G  4.5G   13G  27% /
securityfs                                           0     0     0    - /sys/kernel/security
tmpfs                                             2.0G     0  2.0G   0% /dev/shm
tmpfs                                             5.0M  8.0K  5.0M   1% /run/lock
cgroup2                                              0     0     0    - /sys/fs/cgroup
pstore                                               0     0     0    - /sys/fs/pstore
bpf                                                  0     0     0    - /sys/fs/bpf
systemd-1                                            -     -     -    - /proc/sys/fs/binfmt_misc
mqueue                                               0     0     0    - /dev/mqueue
hugetlbfs                                            0     0     0    - /dev/hugepages
debugfs                                              0     0     0    - /sys/kernel/debug
tracefs                                              0     0     0    - /sys/kernel/tracing
fusectl                                              0     0     0    - /sys/fs/fuse/connections
configfs                                             0     0     0    - /sys/kernel/config
ramfs                                                0     0     0    - /run/credentials/systemd-sysusers.service
rpool/USERDATA/me_yx4dei                           13G   98M   13G   1% /home/me
rpool/USERDATA/root_yx4dei                         13G  384K   13G   1% /root
rpool/ROOT/ubuntu_78v15v/var/games                 13G  256K   13G   1% /var/games
rpool/ROOT/ubuntu_78v15v/var/lib                   15G  2.0G   13G  14% /var/lib
rpool/ROOT/ubuntu_78v15v/srv                       13G  256K   13G   1% /srv
rpool/ROOT/ubuntu_78v15v/var/log                   13G  4.2M   13G   1% /var/log
rpool/ROOT/ubuntu_78v15v/var/mail                  13G  256K   13G   1% /var/mail
rpool/ROOT/ubuntu_78v15v/usr/local                 13G  512K   13G   1% /usr/local
rpool/ROOT/ubuntu_78v15v/var/www                   13G  256K   13G   1% /var/www
rpool/ROOT/ubuntu_78v15v/var/spool                 13G  384K   13G   1% /var/spool
rpool/ROOT/ubuntu_78v15v/var/snap                  13G  1.3M   13G   1% /var/snap
bpool/BOOT/ubuntu_78v15v                          1.0G  262M  762M  26% /boot
rpool/ROOT/ubuntu_78v15v/var/lib/dpkg              13G   69M   13G   1% /var/lib/dpkg
rpool/ROOT/ubuntu_78v15v/var/lib/AccountsService   13G  256K   13G   1% /var/lib/AccountsService
/dev/vda2                                         512M   17M  496M   4% /boot/efi
rpool/ROOT/ubuntu_78v15v/var/lib/NetworkManager    13G  384K   13G   1% /var/lib/NetworkManager
/dev/vda2                                         512M   17M  496M   4% /boot/grub
rpool/ROOT/ubuntu_78v15v/var/lib/apt               13G   85M   13G   1% /var/lib/apt
/dev/loop1                                         64M   64M     0 100% /snap/core20/1778
/dev/loop2                                        128K  128K     0 100% /snap/bare/5
/dev/loop0                                         62M   62M     0 100% /snap/core20/1587
/dev/loop3                                        164M  164M     0 100% /snap/firefox/1635
/dev/loop4                                        239M  239M     0 100% /snap/firefox/2211
rpool/ROOT/ubuntu_78v15v                           18G  4.5G   13G  27% /var/snap/firefox/common/host-hunspell
/dev/loop5                                        401M  401M     0 100% /snap/gnome-3-38-2004/112
/dev/loop7                                         92M   92M     0 100% /snap/gtk-common-themes/1535
/dev/loop8                                         50M   50M     0 100% /snap/snapd/17883
/dev/loop6                                        347M  347M     0 100% /snap/gnome-3-38-2004/119
binfmt_misc                                          0     0     0    - /proc/sys/fs/binfmt_misc
tmpfs                                             393M   56K  393M   1% /run/user/1000
tmpfs                                             393M  1.4M  391M   1% /run/snapd/ns
nsfs                                                 0     0     0    - /run/snapd/ns/firefox.mnt
me@me-Standard-PC-Q35-ICH9-2009:~$ 

$ inxi -Sz
System:
  Kernel: 5.19.0-21-generic arch: x86_64 bits: 64 Desktop: Xfce v: 4.18.0
    Distro: Ubuntu 23.04 (Lunar Lobster)

```

---

### Post by MAFoElffen on 2022-12-30
Grub2 was installed multiple times on that disk. What I did was to purge all instances of grub2 off of it, then mounted it and started over with just one instance to the bootloader.

That way changes could be more organized and direct... Because grub was confused for that one, I had a manually written file for that one. If left to it's own, if didn't know about the internal zfs mounts.

To test thing out first, I just went by the grub cli prompt, to see what it saw, and how it saw it. Then changed my menu code to adapt to that.

On the "root =..." from the Debian instructions, that made things worse (in Ubuntu) by trying to add it twice... I'm not sure how grub tries to figure that out. On another it was prefaced by "/@/boot/..." and made things even worse. LOL.

I think if I understood just how grub see's it, then how it tries to put that together, then it would be easier to under how to change it to help it to be workable on it's on. Instead, I had to hard-code it with a custom menu item.

---

### Post by #&amp;thj^% on 2022-12-30
This is something that was a tough one to find, but now on my end I see why my previous attempts were meet with failure:
```
grub2 | 2.06-2ubuntu7           | jammy                     | source
 grub2 | 2.06-2ubuntu7           | jammy/universe            | amd64, ppc64el
 grub2 | 2.06-2ubuntu7.1         | jammy-proposed            | source
 grub2 | 2.06-2ubuntu7.1         | jammy-proposed/universe   | amd64, ppc64el
 grub2 | 2.06-2ubuntu12          | kinetic                   | source
 grub2 | 2.06-2ubuntu12          | kinetic/universe          | amd64, ppc64el
 grub2 | 2.06-2ubuntu12.1        | kinetic-proposed          | source
 grub2 | 2.06-2ubuntu12.1        | kinetic-proposed/universe | amd64, ppc64el
 grub2 | 2.06-2ubuntu16          | lunar                     | source
 grub2 | 2.06-2ubuntu16          | lunar/universe            | amd64, ppc64el

```
So my forced grub was instantly crushed with my method.
Just took a working grub and encrypted swap in jammy, and naturally upgraded to lunar, and my set-up is sweet again...
The End. :P

---

