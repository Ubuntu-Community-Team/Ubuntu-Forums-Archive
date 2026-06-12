---
title: "boot-repair broke resolution, alsa"
date: 2021-08-16
forum: General Help
---

### Post by bvargo on 2021-08-16
[https://paste.ubuntu.com/p/tNhnYvMfyM/](https://paste.ubuntu.com/p/tNhnYvMfyM/)

---

### Post by bvargo on 2021-08-16
I removed sda3 and sda4, increased the size of /boot on sda2, copied /  from sda8 to sda3 w/clonezilla, deleted sda8, increased the size of  /home on sda7 with the 30 gb from sda8.  I ran boot-repair to fix  everything afterwards.  

boot-repair broke everything, notably my screen resolution (800x600),  multi-monitor support (4 of them), and MPD > ALSA connection.

Latest "bis" (for whatever it is worth): [https://paste.ubuntu.com/p/tNhnYvMfyM/](https://paste.ubuntu.com/p/tNhnYvMfyM/)

Here's most of the pertinent system info:
```

/etc/default $  lsblk; blkid; cat ../fstab; cat grub ; screenfetch -n; env |grep  XDG_CURRENT_DESKTOP ; printf "default-display-manager: %s" $(cat  /etc/X11/default-display-manager)|grep default-display-manager; printf  "Kernel info (uname): %s" "$( uname -srvmpio)" |grep "Kernel info"

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0 950.4M  1 loop /snap/boa/217
loop1    7:1    0  10.2M  1 loop /snap/canonical-livepatch/102
loop2    7:2    0  10.2M  1 loop /snap/canonical-livepatch/104
loop3    7:3    0  99.4M  1 loop /snap/core/11420
loop4    7:4    0  55.4M  1 loop /snap/core18/2128
loop5    7:5    0  99.4M  1 loop /snap/core/11316
loop6    7:6    0   219M  1 loop /snap/gnome-3-34-1804/72
loop7    7:7    0  32.3M  1 loop /snap/snapd/12704
loop8    7:8    0    51M  1 loop /snap/snap-store/542
loop9    7:9    0  32.3M  1 loop /snap/snapd/12398
loop10   7:10   0   219M  1 loop /snap/gnome-3-34-1804/66
loop11   7:11   0  64.8M  1 loop /snap/gtk-common-themes/1514
loop12   7:12   0    51M  1 loop /snap/snap-store/547
loop13   7:13   0 243.9M  1 loop /snap/gnome-3-38-2004/39
loop14   7:14   0  65.1M  1 loop /snap/gtk-common-themes/1515
loop15   7:15   0  61.7M  1 loop /snap/core20/1026
loop16   7:16   0  61.8M  1 loop /snap/core20/1081
loop17   7:17   0  55.5M  1 loop /snap/core18/2074
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0    35M  0 part 
&#9500;&#9472;sda2   8:2    0   1.5G  0 part /boot
&#9500;&#9472;sda3   8:3    0  50.7G  0 part /
&#9500;&#9472;sda5   8:5    0     4G  0 part [SWAP]
&#9492;&#9472;sda7   8:7    0  55.7G  0 part /home
sdb      8:16   0   3.7T  0 disk 
&#9492;&#9472;sdb1   8:17   0   3.7T  0 part /library
sdc      8:32   1   963M  0 disk 
&#9500;&#9472;sdc1   8:33   1   880M  0 part /media/bvargo/Boot-Repair-Disk 64bit
&#9492;&#9472;sdc2   8:34   1   2.4M  0 part 
sr0     11:0    1  1024M  0 rom  
sr1     11:1    1  1024M  0 rom  
/dev/sda3:  UUID="f9a16522-7404-423f-9831-e0174bc2477b" TYPE="ext4" PARTLABEL="ssd  ubuntu 20.04 root" PARTUUID="ddc51cfe-2853-4d07-bc80-5ea78c6ddc9e"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sdb1: UUID="181208fe-b025-4156-a606-5213f27cb2fb" TYPE="ext4" PARTUUID="b525699e-1ed7-49e5-b66e-b1383c1b3bae"
/dev/sda1: SEC_TYPE="msdos" LABEL="BOOTEFI" UUID="178B-8074" TYPE="vfat" PARTUUID="72d37707-6cac-4631-bb48-7fc8a2719469"
/dev/sda2:  LABEL="ssd.boot" UUID="2f6beedb-b275-4c4e-a71f-2f37557e5c12"  TYPE="ext4" PARTUUID="2ea39837-82c8-4ca2-a10d-ef5b8610d907"
/dev/sda5:  LABEL="ssd.swap" UUID="3a696036-ee16-4be4-9524-d908ded95a10"  TYPE="swap" PARTLABEL="ssd swap partition"  PARTUUID="edcfaa3c-826c-4574-af69-4935c8ffe9f7"
/dev/sda7:  LABEL="ssd.home" UUID="24f9c26f-f54e-480d-b30c-6691200084fb" TYPE="ext4"  PARTLABEL="ssd home partition"  PARTUUID="c388a299-efa2-4c4a-ac1d-2df22e4b994c"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/sdc1:  UUID="2020-06-13-00-42-55-00" LABEL="Boot-Repair-Disk 64bit"  TYPE="iso9660" PTUUID="2c534026" PTTYPE="dos" PARTUUID="2c534026-01"
/dev/sdc2: SEC_TYPE="msdos" UUID="D055-8513" TYPE="vfat" PARTUUID="2c534026-02"
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=f9a16522-7404-423f-9831-e0174bc2477b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3a696036-ee16-4be4-9524-d908ded95a10 none            swap    sw              0       0

UUID=181208fe-b025-4156-a606-5213f27cb2fb /library         ext4    defaults 0 1                    # 4 TB hdd library

# /home on Kingston SSD:
UUID=24f9c26f-f54e-480d-b30c-6691200084fb  /home            ext4    noatime,defaults 0 2            # ssd.home

/dev/sr0       /mnt/dvd        auto            noauto,user,ro  0 0

UUID=2f6beedb-b275-4c4e-a71f-2f37557e5c12  /boot       ext4    defaults      0       2
UUID=178B-8074  /boot/efi       vfat    defaults      0       1
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash video=1028x720-24@60"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU xMach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
No value set for `/apps/metacity/general/theme'
 OS: Ubuntu 20.04 focal
 Kernel: x86_64 Linux 5.4.0-81-generic
 Uptime: 42m
 Packages: 2716
 Shell: bash 5.0.17
 Resolution: 800x600
 DE: GNOME 3.36.5
 WM: Metacity
 GTK Theme: Yaru [GTK2/3]
 Icon Theme: ubuntu-mono-light
 Font: Ubuntu 11
 Disk: 3.2T / 3.7T (90%)
 CPU: Intel Core i5-3570K @ 4x 3.8GHz [48.0°C]

 RAM: 4435MiB / 24013MiB
XDG_CURRENT_DESKTOP=GNOME-Flashback:GNOME
default-display-manager: /usr/sbin/gdm3
Kernel info (uname): Linux 5.4.0-81-generic #91-Ubuntu SMP Thu Jul 15 19:09:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by oldfred on 2021-08-16
Did you do the total reinstall of Grub from advanced mode?
You changed partitions around a lot & your /EFI/ubuntu/grub.cfg still refers to grub in /, not one in /boot.
And you do not show a grub.cfg in /boot?

I typically suggest not to use /boot partition with desktops.
It may be required with server or LVM type installs, but otherwise just adds another partition to manage.

---

### Post by bvargo on 2021-08-16
> **oldfred said:**
> Did you do the total reinstall of Grub from advanced mode?
You changed partitions around a lot & your /EFI/ubuntu/grub.cfg still refers to grub in /, not one in /boot.
And you do not show a grub.cfg in /boot?


Yes, I purged and reinstalled grub in boot-repair with the chroot commands it [boot-repair] told me to use (sometimes it didn't work b/c it needed --allow-uninstall-necessary or something and then I had to re-run the last chroot command to execute that).

I don't know why boot-repair doesn't automatically check the /boot on sda2 box but simply show a popup that says check options (i.e., specifically omitting which options, where). 

> **oldfred said:**
> 
I typically suggest not to use /boot partition with desktops.
It may be required with server or LVM type installs, but otherwise just adds another partition to manage.

It has been an LVM, probably will be again, and this is a desktop/server so who knows what might happen to it.

Regardless, the /boot has nothing to do with this problem near as I can tell.  Boot-repair does something to grub or something else that causes the graphics to fail.  It happened on another install (what was on sda3 i think), but I was able to get around it by going to advanced options in grub, selecting recovery mode, and then going to resume.

If I had to guess: the problem is boot-repair and nvidia.

---

### Post by bvargo on 2021-08-16
> **bvargo said:**
> 
If I had to guess: the problem is boot-repair and nvidia.

If you look at the output from ```
$ screenfetch -n
``` it seems pretty clear that boot-repair did something to disrupt the GPU (which is nvidia) because when it is run (after boot-repair), the GPU line is missing (it was there before as I had expected it to be when I posted its output and did not mention the nvidia part of the equation).
```

$ screenfetch -n
No value set for `/apps/metacity/general/theme'

 OS: Ubuntu 20.04 focal
 Kernel: x86_64 Linux 5.4.0-81-generic
 Uptime: 5h 18m
 Packages: 2755
 Shell: bash 5.0.17
 Resolution: 1024x768
 DE: GNOME 3.36.5
 WM: Metacity
 GTK Theme: Yaru [GTK2/3]
 Icon Theme: ubuntu-mono-light
 Font: Ubuntu 11
 Disk: 3.2T / 3.7T (90%)
 CPU: Intel Core i5-3570K @ 4x 3.8GHz [42.0°C]

 RAM: 6121MiB / 24013MiB

```

If you look at the output from a different machine, 

```

$ screenfetch -n
No value set for `/apps/metacity/general/theme'
 bvargo@inspiron
 OS: Ubuntu 18.04 bionic
 Kernel: x86_64 Linux 5.4.0-80-generic
 Uptime: 7m
 Packages: 3589
 Shell: bash 4.4.20
 Resolution: 1024x768
 DE: GNOME 
 WM: Metacity
 GTK Theme: Adwaita-dark [GTK2/3]
 Icon Theme: noia_kde_100
 Font: Ubuntu 9
 CPU: Intel Core i3-4010U @ 4x 1.7GHz
 GPU: llvmpipe (LLVM 10.0.0, 256 bits)
 RAM: 1817MiB / 7650MiB

```

you see the GPU sandwiched b/w CPU and RAM which is an empty line on the machine that has no graphics and 1/4 of its monitor's working.

---

### Post by bvargo on 2021-08-16
```
$ screenfetch -n
No value set for `/apps/metacity/general/theme'
 bvargo@gigabyte
 OS: Ubuntu 20.04 focal
 Kernel: x86_64 Linux 5.8.0-48-generic
 Uptime: 3m
 Packages: 2703
 Shell: bash 5.0.17
 Resolution: 7840x2560
 DE: GNOME 3.36.5
 WM: Metacity
 GTK Theme: Yaru [GTK2/3]
 Icon Theme: ubuntu-mono-light
 Font: Ubuntu 11
 Disk: 3.2T / 3.7T (91%)
 CPU: Intel Core i5-3570K @ 4x 3.8GHz [53.0°C]
 GPU: GeForce GTX 650 Ti BOOST
 RAM: 6136MiB / 24013MiB

```

I did the following:
[LIST=1]
[*]Split sda7 into a 30 gb sda4 with gparted.
[*]Booted into clonezilla live (could not do it inside ubuntu)
[*]Restored the image of the defunct sda8 to sda4
[*]Booted into sda3
[*]$ sudo mkdir -p /mnt/sda4 && sudo mount /dev/sda4 /mnt/sda4
[*]$ sudo mv /etc/default/grub /etc/default/grub~ && sudo mv /mnt/sda4/etc/default/grub /etc/default/grub
[*]$ sudo update-grub2
[*]Booted into sda3 from the updated grub menu
[*]Same result: one monitor @ 800×600
[*]Booted into sda4 from the updated grub menu
[*]Have my computer back!
[/LIST]

I don't know what idiosyncrasy of my setup doesn't work with boot-repair, but unless someone wants to dig into the root cause, I'm going to leave sda4 as /, move /home to sda3, merge sda7 into sda4, my partitions are sequential again, update-grub, problem solved.

Not sure how I do that and to be the primary boot partition.

---

### Post by oldfred on 2021-08-16
How did you install nVidia driver?
If you install directly from nVidia, you have to reinstall with every kernel update.
Best to just use Ubuntu repository.

What does this show?
#What is installed
dkms status

---

