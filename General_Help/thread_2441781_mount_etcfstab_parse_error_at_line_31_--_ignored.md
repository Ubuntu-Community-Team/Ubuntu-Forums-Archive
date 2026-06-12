---
title: "mount: /etc/fstab: parse error at line 31 -- ignored"
date: 2020-04-26
forum: General Help
---

### Post by makem2 on 2020-04-26
I have an external drive mounted via usb at /media/ext-drive.

```

makem@ssdTOSH:/media$ ls -la
total 540
drwxr-xr-x   9 root root   4096 Apr 26 17:26 .
drwxr-xr-x  24 root root   4096 Apr 20 13:05 ..
drwxr-xr-x   3 root root   4096 Nov 11 18:20 data
lrwxrwxrwx   1 root root     45 Aug  4  2018 .directory -> /etc/kubuntu-default-settings/directory-media
drwxrwxrwx   1 root root   4096 Apr 26 18:15 ext-drive
lrwxrwxrwx   1 root root     42 Aug  4  2018 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxr-x---+ 14 root root   4096 Apr 26 18:11 makem
drwxr-xr-x   2 root root   4096 Aug  6  2019 mountpoint
drwxrwxrwt   3 root root     60 Apr 27 00:43 ramdisk
drwxrwxrwx   3 root root   4096 Aug  5  2018 testing
drwxrwxrwx   1 root root 524288 Apr 23 23:47 WinData
makem@ssdTOSH:/media$

```

```

makem@ssdTOSH:~$ sudo blkid
[sudo] password for makem: 
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="CCBC-12A0" TYPE="vfat" PARTUUID="0ca21933-62a8-4dbd-aa0e-d484ee6d028c"
/dev/sda2: UUID="7f90b906-206f-4806-b66d-a83db8f7f3d0" TYPE="ext4" PARTUUID="69d7a9ce-68dc-4ccd-aeb8-fed18280e943"
/dev/sda3: UUID="d78428d2-66ad-474b-a7bc-8144945dd6a1" TYPE="ext4" PARTUUID="1f4ce6eb-f591-4bfc-9418-a11129872523"
/dev/sda4: UUID="0178c9df-c13e-434d-bb57-b6c19095f4aa" TYPE="swap" PARTUUID="cc061ac3-0376-4483-b503-38463c893ae9"
/dev/sdb1: LABEL="WinRE" UUID="D8AC6421AC63F880" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="294fe5c5-7b1f-48fc-b9dd-c92842250842"
/dev/sdb2: LABEL="ESP" UUID="0A66-6E5B" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="e5a1951b-f090-441d-92ce-dbe518417005"
/dev/sdb3: UUID="11A8-6C10" TYPE="vfat" PARTLABEL="Microsoft reserved partition" PARTUUID="35435f1b-40ab-4a92-a704-01f2aa69d2f4"
/dev/sdb4: LABEL="Win10" UUID="BC9A68789A683156" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1db6050f-d9c9-424a-b92f-0b4a61ccee46"
/dev/sdb5: UUID="4CEE1C92EE1C7704" TYPE="ntfs" PARTUUID="afd08917-f568-4f79-a52d-0cc75a6bd1d0"
/dev/sdb6: LABEL="WinData" UUID="D232DC8B32DC75C7" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1d91cc7e-4481-4169-9117-c5b947315241"
/dev/sdb7: LABEL="Testing" UUID="aa855949-81f9-4362-b314-29d55969ea63" TYPE="ext4" PARTLABEL="Testing" PARTUUID="fc015577-785a-48a3-980c-edf0227a85c2"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/sdc1: LABEL="backup" UUID="7F98F12A1F6CCCA0" TYPE="ntfs" PTTYPE="dos" PARTUUID="a7a526d4-01"
makem@ssdTOSH:~$

```
/etc/fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


# / was on /dev/sda2 during installation
UUID=7f90b906-206f-4806-b66d-a83db8f7f3d0 /               ext4    errors=remount-ro 0       1


# /boot/efi was on /dev/sda1 during installation
UUID=CCBC-12A0  /boot/efi       vfat    umask=0077      0       0


# /home was on /dev/sda3 during installation
UUID=d78428d2-66ad-474b-a7bc-8144945dd6a1 /home           ext4    defaults        0       0


# swap was on /dev/sda4 during installation
#UUID=68342eb5-6386-48f4-a2ef-e1683ff58be5 none            swap    sw              0       0
UUID=0178c9df-c13e-434d-bb57-b6c19095f4aa none  swap    0       0


none /media/ramdisk tmpfs nodev,nosuid,noexec,nodiratime,size=1024M 0 0


#WinData
UUID=D232DC8B32DC75C7   /media/WinData  ntfs defaults   0       0


#testing
UUID=aa855949-81f9-4362-b314-29d55969ea63 /media/testing ext4 defaults  0       0


#backup
UUID=7F98F12A1F6CCCA0   /media/ext-drive        ntfs    defaults        nofail          0       0

```

Error:

```

makem@ssdTOSH:~$ sudo mount -a
mount: /etc/fstab: parse error at line 31 -- ignored
makem@ssdTOSH:~$

```

I wanted to achieve a 'hot mount' for that drive which was intended as an archive for use when needed.

When the drive was not attached the system would not boot until it was attached. I added the 'nofail' and got the parsing error.

---

### Post by TheFu on 2020-04-26
```
defaults        nofail
```
should be 
```
defaults,nofail
```

Spaces aren't allowed between mount options.
i use the automounter for sometimes-connected storage, so didn't check that those options are actually reasonable.

---

### Post by makem2 on 2020-04-27
Can you point me to the automounter please?

---

### Post by ajgreeny on 2020-04-27
The automounter is what normally happens when you attach an external USB drive; it will then mount at /media/username/UUID (or label, if it has one).

You seem to be making life more difficult for yourself than it needs to be.

---

### Post by TheFu on 2020-04-27
> **makem2 said:**
> Can you point me to the automounter please?

An example using the built-in systemd-automounter
[https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156)

There is also **autofs**, which many people have been using 10+ yrs. Automounters have been part of Unix since before I learned Unix in the early 90s.  Today, I'd use the systemd-automounter.

The reason to use automounter is when storage cannot be used by just a single userid. Automounters allow full control over the mount options, especially the location, any performance tuning options, and timeouts so unused mounts get removed automatically.

---

### Post by makem2 on 2020-04-27
Removing the tab between the options in /etc/fstab fixed the immediate problem. However, the automounter recommendation sounds better and I will follow that.

Thank you.

---

